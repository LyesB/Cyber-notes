<ol>
	<li>
		<a target="_blank" href="https://tryhackme.com/r/room/networkingconcepts">Networking Concepts</a>
    	<ul>
		<br>
    		<li>ISO OSI network model</li>
    		<li>IP addresses, subnets, and routing</li>
    		<li>TCP, UDP, and port numbers</li>
    		<li>How to connect to an open TCP port from the command line</li>
			<br>
    	</ul>
    </li>
    <li>
    	<a target="_blank" href="https://tryhackme.com/r/room/networkingessentials">Networking Essentials</a>
    	<ul>
		<br>
    		<li>Dynamic Host Configuration Protocol (DHCP)</li>
    		<li>Address Resolution Protocol (ARP)</li>
    		<li>Network Address Translation (NAT)</li>
    		<li>Internet Control Message Protocol (ICMP)
				<ul>
    				<li>Ping</li>
    				<li>Traceroute</li>
    			</ul>
    		</li>
			<br>
    	</ul>
    </li>
	<li>
		<a target="_blank" href="https://tryhackme.com/room/networkingcoreprotocols">Networking Core Protocols</a>
		<ol>
			<br>
			<li>DNS (Domain Name System): <span>Is the system responsible for properly mapping a domain name to an IP address, operates at the 7th layer(Application). DNS listens on default TCP/UDP port number 53.</span>
			</li>
			<br>
			<li>WHOIS: <span>S WHOIS record provides information about the entity that registered a domain name (name, phone number, email, address..etc), WHOIS records are accessible via online services or the command <code>whois</code>on linux.</span>
			</li>
			<br>
			<li>HTTPS (Hypertext Transfer Protocol Secure): <span>Is the protocol that defines how the web browsers communicates with the wev sercers, relies on TCP, some common http methods: <code>GET</code>,<code>POST</code>,<code>PUT</code>,<code>DELETE</code>. HTTP listens on default TCP port number 80 and HTTPS on 443.</span>
			</li>
			<br>
			<li>FTP (FILE TRANSFER PROTOCOL): <span>As the name implies, FTP is the protocol responsible for file trasfers, some common FTP commands are: <code>USER</code>,<code>PASS</code>,<code>RETR</code>,<code>STOR</code>. FTP listens on TCP port 21</span>
			</li>
			<br>
			<li>SMTP (Simple Mail Transfer Protocol): <span>Is basically FTP for mail, some common SMTP commands: <code>HELO</code>,<code>MAIL FROM</code>,<code>MAIL TO</code>,<code>DATA</code>,<code>.</code>, listens on TCP port 25.</span>
			</li>
			<br>
			<li>POP3 (Post Office Protocol 3): <span>Is designed to allow the client to retrieve email messages, listens on TCP port 110.</span>
			</li>
			<br>
			<li>IMAP (Inernet Message Access Protocol): <span>Allows synchronizing read, moved and deleted email messages, is convinient when checking email via multiple clients, listen on TCP port 143.</span>
			</li>
			<br>
		</ol>
	</li>
	<li>
		<a target="_blank" href="https://tryhackme.com/room/networkingsecureprotocols">Networking Secure Protocols</a>
		<ol>
			<br>
			<li>TLS (Transport Layer Security): <span>Is a cryptographic protocol operating ot the OSI model's transport layer, it allows a secure commuincation between a client and a server over an unsecure network. TLS ensures no one can read or modify the exchanged data (confidentiality an integrity).</span>
			</li>
			<br>
			<li>HTTPS, SMTPS, POP3S, and IMAPS: <span>Are HTTP, SMTP, POP3, and IMAP over TLS, which is the secure version of those protocols. The secure and unsecure protocols use different ports, making a request over the secure versions require 3 steps:</span>
				<ol>
					<li>Establish a TCP 3-way handshake</li>
					<li>Establish a TLS session</li>
					<li>Communicate using protocols(HTTP,SMTPS..etc)</li>
				</ol>
			</li>
			<br>
			<li>SSH (Secure SHELL): <span>Unlike TELNET protocol, SSH is secure way communicate over an unsecure network, OpenSSH (the open source implementation of SSH) offers several benefits, some of them: Secure Authentication, Confidentiality, Integrity, Tunneling, X11 Forwarding. SHH server listens on port 22.</span>
			</li>
			<br>
			<li>SFTP And FTPS: <span>SFTP is SHH FTP, and FTPS is FTP over TLS, SFTP is easy to setup, while FTPS requires a proper TLS certificate to run securly.</span>
			</li>
			<br>
			<li>VPN (Virtual Private Network): <span>Organizations use VPN to allow offsite users to securely access the office network over the Internet. VPN provides a convenient solution for companies to privatly exchange information in their virtual network.</span>
			</li>
			<br>
		</ol>
	</li>
	<li>
		<a target="_blank" href="https://tryhackme.com/room/wiresharkthebasics">Wireshark: The Basics</a>
		<br>
		<p>Wireshark is one of the most potent traffic analyser tools available, not an Intrustion Detection System (DSI). There are multiple purposes for its use:
			<ul>
				<li>Detecting and troubleshooting network problems</li>
				<li>Detecting security anomalities</li>
				<li>Investigating and learning protocol details</li>
			</ul>
			<br>
			This room also covers packet dissection, navigation, and filtering.
		</p>
	</li>
	<li>
		<a target="_blank" href="https://tryhackme.com/room/tcpdump">Tcpdump: The Basics</a>
		<br>
		<p>Tcpdump is a command line packet analyzer that lets you catpure network traffic in real-time. Tcpdump and it's library libpcap are written in C and C++, are very stable and offer optimal speed. Tcpdump offers basic capture, filtering, and displaying of packets</p>
	</li>
	<li>
		<a target="_blank" href="https://tryhackme.com/room/nmap">Nmap: The Basics</a>
		<p>Nmap is an open-source network scanner, it is powerfull and flexible and can be adabted to various scenarios, some of the basic nmap uses are: host discovery, port scanning, service detection, scan timing, real-time output, and scan reports.</p>
	</li>

</ol>
