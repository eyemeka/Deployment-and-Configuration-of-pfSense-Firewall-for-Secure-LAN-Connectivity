# Deployment and Configuration of pfSense Firewall for Secure LAN Connectivity

<h2>Description:</h2>
Configured and deployed pfSense in a homelab to provide full LAN internet access and network security. Implemented firewall rules, NAT and DHCP/DNS services to manage traffic flow and ensure proper routing.

Gained hands-on experience in firewall administration, network segmentation, and securing network infrastructure using enterprise-grade open-source tools
<h2>Skills Demonstrated:</h2>
<ul>
 	<li>pfSense</li>
 	<li>Firewall configuration</li>
 	<li>NAT</li>
 	<li>DHCP/DNS</li>
 	<li>Network Security</li>
 	<li>Routing</li>
 	<li>Homelab Setup</li>
</ul>
<h2><strong class="mn he">Step 1: Downloading and installing pfSsense</strong></h2>
Install VirtualBox first. Then download the pfSense ISO file from the official website. You need an account before you can access the download. Choose between the Community Edition or pfSense Plus. This guide uses the Community Edition.

[caption id="attachment_174" align="aligncenter" width="1206"]<img class="size-full wp-image-174" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-140424.png" alt="" width="1206" height="724" /> Fig 1[/caption]

&nbsp;

Click DOWNLOAD. On the next page, select the image type shown in the screenshot. Then click ADD TO CART to move to the checkout page.

&nbsp;

&nbsp;

[caption id="attachment_175" align="alignnone" width="1420"]<img class="size-full wp-image-175" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-140857.png" alt="" width="1420" height="856" /> Fig 2[/caption]

&nbsp;

On the checkout page, download the ISO file for free

[caption id="attachment_176" align="alignnone" width="1395"]<img class="size-full wp-image-176" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-141401.png" alt="" width="1395" height="537" /> Fig 3.[/caption]

After the download finishes, open VirtualBox and click New to create a virtual machine.

[caption id="attachment_177" align="alignnone" width="1127"]<img class="size-full wp-image-177" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-141752.png" alt="" width="1127" height="965" /> Fig 4.[/caption]

Name the virtual machine pfSense. Extract the downloaded file first using WinZip or 7-Zip, then select the ISO image. Without extraction, the ISO will not appear in the download folder. After extraction, set the type to BSD and the version to FreeBSD 64-bit.

[caption id="attachment_178" align="alignnone" width="1012"]<img class="size-full wp-image-178" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-142507.png" alt="" width="1012" height="961" /> Fig 5.[/caption]

Allocate 1 GB of RAM at minimum. For better performance, use 2 GB.

[caption id="attachment_179" align="alignnone" width="1005"]<img class="size-full wp-image-179" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-142759.png" alt="" width="1005" height="963" /> Fig. 6.[/caption]

Create a virtual hard disk with 20 GB for testing. Select VDI as the disk type and variant. Click Finish to complete the setup.

[caption id="attachment_180" align="alignnone" width="1018"]<img class="size-full wp-image-180" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-144031.png" alt="" width="1018" height="965" /> Fig. 7.[/caption]

Before starting the VM, click <strong>Settings</strong> on the VirtualBox and go to <strong>Network.</strong> Use two adapters. Set<strong> Adapter 1</strong> to <strong>NAT</strong> for internet access. Set <strong>Adapter 2</strong> to <strong>Internal Network</strong> for LAN simulation. This setup represents a pfSense router with WAN and LAN ports.

[caption id="attachment_181" align="alignnone" width="998"]<img class="size-full wp-image-181" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-144632.png" alt="" width="998" height="962" /> Fig 8.[/caption]

&nbsp;

[caption id="attachment_182" align="alignnone" width="1002"]<img class="size-full wp-image-182" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-144807.png" alt="" width="1002" height="963" /> Fig 9[/caption]
<p data-start="0" data-end="157">In VirtualBox, network adapters are virtual interfaces that define how a virtual machine connects to networks. Each adapter type serves a specific purpose.</p>

<ul data-start="159" data-end="485">
 	<li data-start="159" data-end="219">
<p data-start="161" data-end="219">NAT provides internet access and is the default setting.</p>
</li>
 	<li data-start="220" data-end="325">
<p data-start="222" data-end="325">Bridged Mode places the VM on the same network as the host, making it behave like a physical machine.</p>
</li>
 	<li data-start="326" data-end="395">
<p data-start="328" data-end="395">Internal Mode allows communication only between virtual machines.</p>
</li>
 	<li data-start="396" data-end="485">
<p data-start="398" data-end="485">Host-Only Mode creates an isolated network between the host and its virtual machines.</p>
</li>
</ul>
<p data-start="487" data-end="613">During setup, it is important to note the MAC address of each adapter, as this will be required during pfSense installation.</p>
<p data-start="615" data-end="829">Once the network is configured, start the VM. If an error occurs, reboot and start again. When the VM boots, accept the Copyright and Trademark Notices, then select Install pfSense and follow the installer steps.</p>
&nbsp;

[caption id="attachment_183" align="aligncenter" width="738"]<img class="size-full wp-image-183" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-151815.png" alt="" width="738" height="513" /> Fig 10.[/caption]

&nbsp;

[caption id="attachment_184" align="aligncenter" width="739"]<img class="size-full wp-image-184" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-152056.png" alt="" width="739" height="526" /> Fig. 11[/caption]

&nbsp;

When the prompt for network setup appears, click <strong>OK</strong> (Fig 12)

[caption id="attachment_185" align="aligncenter" width="732"]<img class="size-full wp-image-185" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-152410.png" alt="" width="732" height="520" /> Fig 12[/caption]

Select the WAN port when prompted. Use the MAC address you noted earlier. If you did not record it, check under Settings &gt; Network. Then choose the correct MAC address for the WAN.

[caption id="attachment_186" align="aligncenter" width="725"]<img class="size-full wp-image-186" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-152908.png" alt="" width="725" height="516" /> Fig 13[/caption]

When prompted for the WAN network operation mode, click <strong class="mn he">Continue </strong>(Fig. 14).

[caption id="attachment_187" align="aligncenter" width="725"]<img class="size-full wp-image-187" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-153045.png" alt="" width="725" height="513" /> Fig 14[/caption]

Next, select the LAN (Fig 15)

[caption id="attachment_188" align="aligncenter" width="717"]<img class="size-full wp-image-188" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-153613.png" alt="" width="717" height="513" /> Fig 15[/caption]

Proceed with installation (Fig. 16)

[caption id="attachment_189" align="aligncenter" width="726"]<img class="size-full wp-image-189" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-153832.png" alt="" width="726" height="512" /> Fig 16[/caption]

Click Continue to confirm the interface assignment

[caption id="attachment_190" align="aligncenter" width="728"]<img class="size-full wp-image-190" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-154201.png" alt="" width="728" height="514" /> Fig 17[/caption]

After the connectivity check, you may see a validation failed message if there is no pfSense Plus subscription. In that case, select Install CE to use the free Community Edition. (Fig 18) If you have a pfSense Plus subscription, proceed with validation.

[caption id="attachment_191" align="aligncenter" width="853"]<img class="size-full wp-image-191" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-154550.png" alt="" width="853" height="467" /> Fig 18[/caption]

&nbsp;

[caption id="attachment_192" align="aligncenter" width="720"]<img class="size-full wp-image-192" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-154812.png" alt="" width="720" height="507" /> Fig 19[/caption]

&nbsp;

When prompted to select the file system type and partition scheme, click Continue to start the installation.

[caption id="attachment_193" align="aligncenter" width="719"]<img class="size-full wp-image-193" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-155017.png" alt="" width="719" height="510" /> Fig 20.[/caption]

Click OK to choose the ZFS virtual device configuration type.

&nbsp;

&nbsp;

[caption id="attachment_194" align="aligncenter" width="715"]<img class="size-full wp-image-194" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-155136.png" alt="" width="715" height="506" /> Fig 21.[/caption]

Click OK to select the highlighted disk for software installation. (Fig. 22.)

[caption id="attachment_195" align="aligncenter" width="725"]<img class="size-full wp-image-195" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-155344.png" alt="" width="725" height="509" /> Fig. 22.[/caption]

If prompted about destroying the contents of the disk, click Yes. (Fig. 23.)

[caption id="attachment_196" align="aligncenter" width="721"]<img class="wp-image-196 size-full" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-155702.png" alt="" width="721" height="513" /> Fig 23[/caption]

When asked which version of pfSense to install, select the <strong>Current Stable Version </strong>available at the time of setup. (Fig. 25)

[caption id="attachment_197" align="aligncenter" width="719"]<img class="wp-image-197 size-full" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-155905.png" alt="" width="719" height="510" /> Fig 24[/caption]

The installation will then begin (Fig. 25).

&nbsp;

[caption id="attachment_198" align="aligncenter" width="717"]<img class="size-full wp-image-198" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-160140.png" alt="" width="717" height="514" /> Fig 25.[/caption]

The installation time depends on your internet speed. Wait until it finishes.

When the process completes, click <strong>OK.</strong>

[caption id="attachment_199" align="aligncenter" width="715"]<img class="size-full wp-image-199" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-162016.png" alt="" width="715" height="506" /> Fig. 26[/caption]
<p data-start="615" data-end="829"><strong>PS: </strong>If you run into an error while the pfSense is installing that looks like this "<em><strong>at ata0 bus 0 scbus0 target 0 lun 0 3 more tries remain ada0: &lt;VBOX HARDDISK 1.0&gt; s/n VB5512e351-e0a41350 detached Solaris: WARNING: Pool 'pfsense' has encountered an uncorrectable I/O failure and has been suspended</strong></em>". Below is how you can fix it (Step-by-step)</p>

<ol data-start="879" data-end="1322">
 	<li data-start="879" data-end="956">
<p data-start="882" data-end="956">In VirtualBox Manager, select your pfSense VM open <strong data-start="931" data-end="953">Settings </strong>select<strong data-start="931" data-end="953"> Storage</strong>.</p>
</li>
 	<li data-start="957" data-end="1099">
<p data-start="960" data-end="1050">Under <strong data-start="966" data-end="985">Controller: IDE</strong>, <strong data-start="987" data-end="1013">remove the pfSense.vdi</strong> (right-click and <strong>Remove Attachment</strong>).</p>
</li>
</ol>
<ul>
 	<li data-start="1056" data-end="1099">Don’t delete the file — just detach it.</li>
 	<li data-start="1056" data-end="1099">Add Controller: AHCI (SATA)</li>
</ul>
<ol data-start="879" data-end="1322">
 	<li data-start="1100" data-end="1231">
<p data-start="1103" data-end="1158">Then, make sure under <strong data-start="1119" data-end="1146">Controller: AHCI (SATA)</strong> you have:</p>
</li>
</ol>
<ul>
 	<li data-start="1164" data-end="1189"><code data-start="1164" data-end="1177">pfSense.vdi</code> attached.</li>
 	<li data-start="1195" data-end="1231"><strong data-start="1195" data-end="1217">Use Host I/O cache</strong> = ✅ ticked.</li>
</ul>
<ol data-start="879" data-end="1322">
 	<li data-start="1232" data-end="1322">
<p data-start="1235" data-end="1322">Under <strong data-start="1241" data-end="1260">Controller: IDE</strong>, keep only the <strong data-start="1276" data-end="1291">pfSense.iso</strong> attached (as Optical Drive).</p>
</li>
</ol>
&nbsp;

When prompted to reboot, click Reboot, then power off the pfSense VM. (Fig. 27.)

[caption id="attachment_200" align="aligncenter" width="724"]<img class="size-full wp-image-200" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-24-162124.png" alt="" width="724" height="520" /> Fig 27.[/caption]

Power off the VM to remove the ISO from the virtual drive. This prevents the VM from booting into the installer again. Go to <strong>Settings &gt;</strong> <strong>Storage</strong> and select <strong>netgate-installer</strong> under <strong>Controller: IDE</strong>.

Under <strong>Attributes</strong>, click the disc icon next to <strong>IDE Secondary Device</strong> and choose <strong>Remove Disk from Virtual Drive</strong>. Click <strong>OK</strong> to save the settings. (Fig 28).

[caption id="attachment_204" align="aligncenter" width="1367"]<img class="size-full wp-image-204" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-082151.png" alt="" width="1367" height="753" /> Fig. 28[/caption]

Restart the pfSense VM. It will load in console mode and display the WAN and LAN interfaces with assigned IP addresses.

[caption id="attachment_205" align="aligncenter" width="723"]<img class="size-full wp-image-205" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-083550.png" alt="" width="723" height="505" /> Fig 29[/caption]
<h2 data-start="0" data-end="45">Step 2: Accessing the pfSense Web Interface</h2>
<p data-start="49" data-end="108">pfSense has a web interface you log into using a browser.</p>
<p data-start="111" data-end="187">It can be opened by typing the LAN IP of pfSense, which is usually <strong>192.168.1.1</strong></p>
<p data-start="190" data-end="293">That IP is also the “default gateway,” meaning it is the main path devices use to reach the internet.</p>
<p data-start="296" data-end="490">The gateway pfSense uses for the internet can be:</p>

<ul>
 	<li data-start="296" data-end="490">Manually set (static)</li>
 	<li data-start="296" data-end="490">Automatically assigned by DHCP from your router or ISP</li>
 	<li data-start="296" data-end="490">Given by PPPoE or other login-based connections</li>
</ul>
<p data-start="493" data-end="586">pfSense takes all traffic from the LAN and sends it to this gateway to reach the internet.</p>
<p data-start="589" data-end="680">Inside the LAN, devices (like my Kali VM) point to pfSense’s LAN IP as their gateway.</p>
<p data-start="683" data-end="842">To test this, I will switch the Kali’s network adapter to “<strong>Internal Network</strong>” so pfSense gives it an IP address. Then I will open the pfSense web GUI from Kali.</p>
<p data-start="720" data-end="914" data-is-last-node="" data-is-only-node="">To access the GUI, I will use the Kali VM. Set its network adapter to Internal Network so it receives an IP from pfSense. In Kali VM settings, go to <strong>Network</strong> and set the adapter to <strong>Internal Network</strong>.</p>


[caption id="attachment_206" align="aligncenter" width="982"]<img class="size-full wp-image-206" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-084921.png" alt="" width="982" height="823" /> Fig. 30[/caption]
<p data-start="0" data-end="67">Remember the LAN interface of pfSense is set to Internal Network.</p>
<p data-start="69" data-end="237" data-is-last-node="" data-is-only-node="">Start the Kali VM. Open the terminal and run the command <code data-start="128" data-end="138">ifconfig</code>. Check the IP address assigned. It should be in the 192.168.1.x range. For example, 192.168.1.100.</p>


[caption id="attachment_207" align="aligncenter" width="776"]<img class="size-full wp-image-207" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-090807.png" alt="" width="776" height="504" /> Fig. 31[/caption]

Now let’s check if we can access the internet through pfSense.

Enter the IP address of the pfSense dashboard (in this case, it is <strong>192.168.1.1</strong>) into the browser on the Kali VM. You might see a warning about a potential security risk. Click <strong class="mn he">Advanced</strong>, then <strong class="mn he">Accept the Risk and Continue </strong>(Fig. 32).

[caption id="attachment_208" align="aligncenter" width="1010"]<img class="size-full wp-image-208" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-091454.png" alt="" width="1010" height="727" /> Fig. 32.[/caption]

When the login page appears, enter <strong>admin</strong> as the username and <strong>pfsense</strong> as the password in lowercase to access the dashboard. (Fig. 33)

[caption id="attachment_209" align="aligncenter" width="1284"]<img class="size-full wp-image-209" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-091959.png" alt="" width="1284" height="581" /> Fig. 33[/caption]

The homepage opens (Fig. 34).

[caption id="attachment_210" align="aligncenter" width="1071"]<img class="size-full wp-image-210" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-092251.png" alt="" width="1071" height="589" /> Fig 34[/caption]

Click Next to start the setup wizard. This will guide you through timezone, interfaces, admin password, and other settings. (Fig 34).

On the General Information page, keep the default configuration and click Next. (Fig 35).

[caption id="attachment_211" align="aligncenter" width="1197"]<img class="size-full wp-image-211" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-092712.png" alt="" width="1197" height="715" /> Fig. 35[/caption]

Leave the configuration on the Time Server Information page and click <strong class="mn he">Next </strong>(Fig. 36).

[caption id="attachment_212" align="alignnone" width="1044"]<img class="size-full wp-image-212" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-093006.png" alt="" width="1044" height="517" /> Fig. 36[/caption]

On the next page, scroll down and uncheck the box for <strong class="mn he">Block RFC1918 Private Networks </strong>(Fig. 37).

[caption id="attachment_213" align="aligncenter" width="1177"]<img class="size-full wp-image-213" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-093340.png" alt="" width="1177" height="606" /> Fig 37[/caption]

On the LAN configuration page, keep the default settings and click <strong>Next. </strong>(Fig. 38)

[caption id="attachment_214" align="aligncenter" width="1120"]<img class="size-full wp-image-214" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-093745.png" alt="" width="1120" height="568" /> Fig 38[/caption]

Choose a new, secure password and click <strong class="mn he">Next </strong>(Fig. 39).

[caption id="attachment_215" align="alignnone" width="1190"]<img class="size-full wp-image-215" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-094008.png" alt="" width="1190" height="586" /> Fig. 39[/caption]

Next, click <strong class="mn he">Reload </strong>to reload pfSense with new changes (Fig. 40)

[caption id="attachment_216" align="aligncenter" width="1077"]<img class="size-full wp-image-216" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-094154.png" alt="" width="1077" height="481" /> Fig 40[/caption]

Click <strong>Finish,</strong> then accept the terms on the next page. (Fig. 41)

[caption id="attachment_217" align="aligncenter" width="1153"]<img class="size-full wp-image-217" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-094455.png" alt="" width="1153" height="689" /> Fig. 41[/caption]

Accept the terms presented on that page (Fig. 42).

[caption id="attachment_218" align="aligncenter" width="1186"]<img class="size-full wp-image-218" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-094611.png" alt="" width="1186" height="683" /> Fig. 42[/caption]

You can now access your dashboard (Fig. 43).

[caption id="attachment_219" align="alignnone" width="1278"]<img class="size-full wp-image-219" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-094836.png" alt="" width="1278" height="707" /> Fig. 43[/caption]
<h2 data-start="0" data-end="47"></h2>
<h2 data-start="0" data-end="47">Step 3: Configuring Firewall Rules in pfSense</h2>
<p data-start="49" data-end="205">To view firewall rules, click <strong>Firewall</strong> in the top menu, then select <strong>Rules</strong> and open the <strong>LAN</strong> tab. By default, pfSense adds three rules on the LAN interface:</p>

<ol data-start="207" data-end="732">
 	<li data-start="207" data-end="437">
<p data-start="210" data-end="437"><strong data-start="210" data-end="231">Anti-lockout rule</strong> – Keeps access to the pfSense web interface safe. It allows HTTP (port 80) and HTTPS (port 443) connections to the LAN IP from any source. Even if other rules are misconfigured, you will not lose access.</p>
</li>
 	<li data-start="438" data-end="644">
<p data-start="441" data-end="644"><strong data-start="441" data-end="476">Default allow LAN to any (IPv4)</strong> – Lets all IPv4 traffic from the LAN go to any destination using any port or protocol. This gives LAN devices full outbound access to the internet or other networks.</p>
</li>
 	<li data-start="645" data-end="732">
<p data-start="648" data-end="732"><strong data-start="648" data-end="683">Default allow LAN to any (IPv6)</strong> – Same as the IPv4 rule, but for IPv6 traffic.</p>
</li>
</ol>
<p data-start="734" data-end="861">These rules are fine for setup and testing. For production or security focused environments, these rules should be reviewed and adjusted them to meet your needs.</p>


[caption id="attachment_220" align="alignnone" width="1207"]<img class="size-full wp-image-220" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-100113.png" alt="" width="1207" height="525" /> Fig 44[/caption]

Now disable the two rules that allow unrestricted outbound access. Click each rule, then click the prohibition sign (<strong class="mn he">🚫)</strong> under the Action column. (Fig. 45)

[caption id="attachment_221" align="alignnone" width="1186"]<img class="size-full wp-image-221" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-100517.png" alt="" width="1186" height="442" /> Fig. 45[/caption]
<p id="4859" class="pw-post-body-paragraph ml mm hd mn b mo mp mq mr ms mt mu mv mw mx my mz na nb nc nd ne nf ng nh ni gw bl" data-selectable-paragraph="">Next, apply changes (Fig. 46).</p>


[caption id="attachment_222" align="alignnone" width="1242"]<img class="size-full wp-image-222" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-100756.png" alt="" width="1242" height="536" /> Fig. 46[/caption]

After disabling these two rules, any network connections from the Kali VM will fail (Fig. 47).

[caption id="attachment_223" align="aligncenter" width="1214"]<img class="size-full wp-image-223" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-101315.png" alt="" width="1214" height="634" /> Fig 47[/caption]
<p data-start="0" data-end="30">Adding Custom Firewall Rules</p>
<p data-start="32" data-end="64">You can add rules in two ways:</p>

<ul data-start="66" data-end="115">
 	<li data-start="66" data-end="90">
<p data-start="68" data-end="90">Add individual rules</p>
</li>
 	<li data-start="91" data-end="115">
<p data-start="93" data-end="115">Add rules as a group</p>
</li>
</ul>
<p data-start="117" data-end="148"><strong data-start="117" data-end="146">Adding an individual rule</strong></p>
<p data-start="150" data-end="318" data-is-last-node="" data-is-only-node="">A common rule to add is one that allows outbound ICMP traffic. This lets devices on the LAN ping themselves and external devices. Without this rule, ping will not work</p>


[caption id="attachment_224" align="alignnone" width="1112"]<img class="size-full wp-image-224" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-101655.png" alt="" width="1112" height="346" /> Fig. 48[/caption]

To add the ICMP rule, click the green upward arrow (Fig. 49). This places the rule at the top of the list so it takes priority over other rules.

[caption id="attachment_225" align="aligncenter" width="1192"]<img class="size-full wp-image-225" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-102025.png" alt="" width="1192" height="496" /> Fig. 49[/caption]

Click the green upward arrow to open the configuration page. Set up the rule as shown in the reference images. (Fig 50, 51)

[caption id="attachment_226" align="aligncenter" width="1231"]<img class="size-full wp-image-226" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-102457.png" alt="" width="1231" height="694" /> Fig. 50[/caption]

&nbsp;

[caption id="attachment_227" align="alignnone" width="1246"]<img class="size-full wp-image-227" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-102611.png" alt="" width="1246" height="648" /> Fig. 51[/caption]
<p data-start="0" data-end="90">This firewall rule lets LAN devices send ICMP traffic, such as ping, to any destination.</p>

<ul data-start="92" data-end="348">
 	<li data-start="92" data-end="145">
<p data-start="94" data-end="145"><strong data-start="94" data-end="104">Action</strong>: Pass, so matching packets are allowed</p>
</li>
 	<li data-start="146" data-end="168">
<p data-start="148" data-end="168"><strong data-start="148" data-end="161">Interface</strong>: LAN</p>
</li>
 	<li data-start="169" data-end="197">
<p data-start="171" data-end="197"><strong data-start="171" data-end="189">Address Family</strong>: IPv4</p>
</li>
 	<li data-start="198" data-end="246">
<p data-start="200" data-end="246"><strong data-start="200" data-end="212">Protocol</strong>: ICMP with all subtypes enabled</p>
</li>
 	<li data-start="247" data-end="274">
<p data-start="249" data-end="274"><strong data-start="249" data-end="259">Source</strong>: LAN subnets</p>
</li>
 	<li data-start="275" data-end="299">
<p data-start="277" data-end="299"><strong data-start="277" data-end="292">Destination</strong>: Any</p>
</li>
 	<li data-start="300" data-end="325">
<p data-start="302" data-end="325"><strong data-start="302" data-end="313">Logging</strong>: Disabled</p>
</li>
 	<li data-start="326" data-end="348">
<p data-start="328" data-end="348"><strong data-start="328" data-end="338">Status</strong>: Active</p>
</li>
</ul>
<p data-start="350" data-end="480" data-is-last-node="" data-is-only-node="">This rule makes it possible for LAN clients to run diagnostics like ping or traceroute with no limits on ICMP type or destination.</p>
<p data-start="350" data-end="480" data-is-last-node="" data-is-only-node="">Apply the changes (Fig. 52).</p>


[caption id="attachment_228" align="aligncenter" width="1237"]<img class="size-full wp-image-228" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-103119.png" alt="" width="1237" height="592" /> Fig 52[/caption]

<article class="text-token-text-primary w-full focus:outline-none scroll-mt-[calc(var(--header-height)+min(200px,max(70px,20svh)))]" dir="auto" tabindex="-1" data-turn-id="request-68d3e4d6-e6f0-8330-b915-98d6011b6b4e-46" data-testid="conversation-turn-92" data-scroll-anchor="true" data-turn="assistant">
<div class="text-base my-auto mx-auto pb-10 [--thread-content-margin:--spacing(4)] thread-sm:[--thread-content-margin:--spacing(6)] thread-lg:[--thread-content-margin:--spacing(16)] px-(--thread-content-margin)">
<div class="[--thread-content-max-width:40rem] thread-lg:[--thread-content-max-width:48rem] mx-auto max-w-(--thread-content-max-width) flex-1 group/turn-messages focus-visible:outline-hidden relative flex w-full min-w-0 flex-col agent-turn" tabindex="-1">
<div class="flex max-w-full flex-col grow">
<div class="min-h-8 text-message relative flex w-full flex-col items-end gap-2 text-start break-words whitespace-normal [.text-message+&amp;]:mt-5" dir="auto" data-message-author-role="assistant" data-message-id="b66c3a49-e5b8-41c8-ab28-41f4f66c85d7" data-message-model-slug="gpt-5">
<div class="flex w-full flex-col gap-1 empty:hidden first:pt-[3px]">
<div class="markdown prose dark:prose-invert w-full break-words dark markdown-new-styling">
<p data-start="0" data-end="51" data-is-last-node="" data-is-only-node="">Pinging the default gateway now works successfully. (Fig. 53)</p>


[caption id="attachment_229" align="alignnone" width="830"]<img class="size-full wp-image-229" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-103348.png" alt="" width="830" height="349" /> Fig. 53[/caption]
<p data-start="0" data-end="25">Adding Rules as a Group</p>
<p data-start="27" data-end="136" data-is-last-node="" data-is-only-node="">In addition to ICMP, LAN devices need internet access.</p>
<p data-start="27" data-end="136" data-is-last-node="" data-is-only-node="">At this point, trying to open a website will not work.</p>

</div>
</div>
</div>
</div>
<div class="z-0 flex min-h-[46px] justify-start"></div>
<div class="mt-3 w-full empty:hidden">
<div class="text-center">

[caption id="attachment_230" align="alignnone" width="1145"]<img class="size-full wp-image-230" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-103717.png" alt="" width="1145" height="651" /> Fig. 54[/caption]

</div>
</div>
</div>
</div>
</article>
<div class="pointer-events-none h-px w-px" aria-hidden="true" data-edge="true"></div>
<div aria-hidden="true" data-edge="true">
<p data-start="0" data-end="130">To enable internet connectivity, open key ports: <strong>53 for DNS</strong>, <strong>80 for HTTP</strong>, and <strong>443 for HTTPS</strong>. These can be grouped with an alias.</p>
<p data-start="132" data-end="181" data-is-last-node="" data-is-only-node="">Go to <strong>Firewall</strong> &gt; <strong>Aliases</strong> &gt; <strong>Ports.</strong> Then click <strong>Add.</strong></p>


[caption id="attachment_231" align="alignnone" width="1321"]<img class="size-full wp-image-231" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-104053.png" alt="" width="1321" height="516" /> Fig 55[/caption]

Configure the alias with your preferred settings. In this case, set it up as shown in the reference image. (Fig. 56)

[caption id="attachment_232" align="aligncenter" width="1206"]<img class="size-full wp-image-232" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-104506.png" alt="" width="1206" height="666" /> Fig. 56[/caption]

Save and apply the changes (Fig. 57)

[caption id="attachment_233" align="aligncenter" width="1235"]<img class="size-full wp-image-233" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-104611.png" alt="" width="1235" height="548" /> Fig 57[/caption]

</div>
<p data-start="0" data-end="31">Go to <strong>Firewall</strong> &gt; <strong>Rules</strong> &gt; <strong>LAN.</strong></p>
<p data-start="33" data-end="74">Click <strong>Add</strong> using the green upward arrow.</p>
<p data-start="76" data-end="128" data-is-last-node="" data-is-only-node="">Configure the rule as shown in the reference images. (Fig. 58, 59):</p>


[caption id="attachment_234" align="aligncenter" width="1250"]<img class="size-full wp-image-234" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-105214.png" alt="" width="1250" height="635" /> Fig 58[/caption]

&nbsp;

[caption id="attachment_235" align="alignnone" width="1277"]<img class="size-full wp-image-235" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-105323.png" alt="" width="1277" height="683" /> Fig. 59[/caption]

&nbsp;

This firewall rule lets LAN devices reach the internet.
<ul>
 	<li><strong>Action</strong>: Pass, so traffic is allowed</li>
 	<li><strong>Status</strong>: Active</li>
 	<li><strong>Interface</strong>: LAN</li>
 	<li><strong>Address Family</strong>: IPv4 only</li>
 	<li><strong>Protocol</strong>: TCP/UDP, covering traffic like <strong>HTTPS, HTTP,</strong> and <strong>DNS</strong></li>
</ul>
<ul data-start="60" data-end="300">
 	<li data-start="60" data-end="87">
<p data-start="62" data-end="87"><strong data-start="62" data-end="72">Source</strong>: LAN subnets</p>
</li>
 	<li data-start="88" data-end="167">
<p data-start="90" data-end="167"><strong data-start="90" data-end="105">Destination</strong>: Any, labeled as “Internet” using the alias created earlier</p>
</li>
 	<li data-start="168" data-end="231">
<p data-start="170" data-end="231"><strong data-start="170" data-end="196">Destination Port Range</strong>: Blank, so all ports are allowed</p>
</li>
 	<li data-start="232" data-end="253">
<p data-start="234" data-end="253"><strong data-start="234" data-end="241">Log</strong>: Disabled</p>
</li>
 	<li data-start="254" data-end="300">
<p data-start="256" data-end="300"><strong data-start="256" data-end="271">Description</strong>: “For LAN internet access”</p>
</li>
</ul>
<p data-start="302" data-end="457" data-is-last-node="" data-is-only-node="">In short, it permits unrestricted outbound IPv4 TCP/UDP traffic from LAN clients to the internet, supporting basic functions like web browsing and software updates.</p>
<p data-start="302" data-end="457" data-is-last-node="" data-is-only-node="">Then save and apply (Fig. 60).</p>


[caption id="attachment_236" align="aligncenter" width="1303"]<img class="size-full wp-image-236" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-105820.png" alt="" width="1303" height="719" /> Fig. 60[/caption]

Internet connection is now possible (Fig. 61).

[caption id="attachment_237" align="alignnone" width="1346"]<img class="size-full wp-image-237" src="https://eyemekacyberportfolio.name.ng/wp-content/uploads/2025/09/Screenshot-2025-09-25-110029.png" alt="" width="1346" height="827" /> Fig. 61[/caption]

You can add more rules to control specific types of inbound and outbound traffic.
<h2>Summary</h2>
This project gave me practical experience with pfSense as a firewall and router. I set up a virtual lab in VirtualBox, installed and configured pfSense, and connected it to a Kali client. I worked with firewall rules by disabling default unrestricted access, creating ICMP rules for diagnostics, and grouping essential ports to enable controlled internet access. Through this hands-on setup, I strengthened my skills in virtual networking, IP addressing, and firewall rule management.
