# Configure MACsec PSK on VLAN Trunk Link

MACsec enables wire-speed AES encryption. This wire-speed encryption comes with all Catalyst 9000 switches. MACsec is the protocol that performs bulk data encryption. MACsec requires MKA (MACsec Key Agreement). MKA is the process that is used for key generation and key exchange. 

Refer to our network diagram and see that our Cat9300 switches are connected via GigabitEthernet1/0/1. 
[Network Diagram](/labs-pods.md)

In this example we create the necessary MKA configuration, MKA policy to enable
AES-256 encryption, and enable MACsec on the switchports.  Configuring MACsec PSK
is fairly simple for such a powerful encryption method. 

MACsec can also use Certificates instead of PSK, but we aren't going to do that
today. :-)  


<ol>

<li>View the MACsec Playbook using cat </li>
You will notice that this is a very long playbook with several tasks. Because all of these tasks are configured with NETCONF RPCs, putting them all into the same playbook is the most efficient. So now we will look at each of the RPCs in detail below. 
<br>
<code>cat playbooks/04a-config-macsec-psk-new.yaml</code>
<br><br>


This task will configure the MKA Keys, which will be attached to the interface later. The MKA Keys consist of a CKN (Connectivity Key Name) and a CAK (Connectivity Association Key). The CAK is the root of all other keys, including the SAK (Security Association Key), the actual key that does bulk data encryption.<br>
<img src="/images/04-04a-configure-mka-keys-web.png" alt="" width=600>
<br><br>
This task will configure the MKA policy. Inside of the MKA policy we configure AES-256-GCM mode for the bulk data encryption.  
<img src="/images/04-04b-configure-mka-policy-web.png" alt="" width=600>
<br><br>
This task will tie the MKA policy to the interfaces. 
<img src="/images/04-04c-configure-interface-mka-policy-web.png" alt="" width=600>
<br><br>
This task will tie the MKA keys to the interfaces.
<img src="/images/04-04d-configure-interface-mka-key-web.png" alt="" width=600>
<br><br>
Now that we've tied the keys and the policy to the interfaces, its time to enable MACsec Network Link. This task enables MACsec data encryption on the interface. 
<img src="/images/04-04e-configure-macsec-network-link-web.png" alt="" width=600>
<br><br>
This task runs 'no shutdown' on the interfaces! 
<img src="/images/04-04f-no-shut-interfaces-web.png" alt="" width=600>

<br>


<li>Run the Playbook on Cat9300X-PodA</li>
Cat9300X-PodA has 10 Gb. Cat9300-PodB has 1 Gb interfaces. Because of the naming difference we will a slightly modified playbook to account for the internaface name difference. All tasks in the Playbook perform the same actions. 
<br>
<code>ansible-playbook -i inventories/devnet-switches.yaml playbooks/04a-config-macsec-psk.yaml --ask-vault-pass
</code>
<br><br>
<img src="/images/04-09a-playbook-output-macsec-web.png" alt="" width=600>
<br><br><br> c


<li>Check the MKA Status on the Switch </li>
<br>
<code>show mka session</code>
<br><br>
<img src="/images/04-10-show-mka-status-web.png" alt="" width=600>
<br><br><br>


<li>Check the MACsec Status on the Switch </li>
<br>
<code>show macsec summary</code>
<br><br>
<img src="/images/04-11-show-macsec-summary-web.png" alt="" width=600>
<br><br><br>


</ol>


[Click here to Wrap Up.](/05-Wrap_Up.md)

