## What Happens When You Type Google.com In Your Browser

1. First up , you type website address "google.com" in the browser's address bar
2. The browser checks its caches first . If there is a cache miss, it must find and ip address

   > [!IMPORTANT]
   > a cache miss is when the browser can find the name resolution locally in its caches
   > while a caches hit is when the browser is able to find the name resolution locally

3. DNS look up begins <span style='color:fuchsia'>The request goes through different DNS servers (root,TLD and authoritative). Finally the IP address is resolved</span>

   This process is called the DNS lookup process, and it works in detail. Let’s explore each one of them.

   1. if the request domain name is not is the browser caches , the browser makes a call to the browser
   2. if the browser does not find it on the os caches it then request the resolver name cache server which is (ips)
   3. if the resolver cache server doesn't have its name it asks the root server to give it the location name of the top leve domain
   4. The TLD responds with the name of the authoritative name-Server for the domain
   5. if the IP address is available the the browser send the request to the server at the ip

4. The browser the initiates a TCP connection handshake
   TCP stands for _Transmission Control Protocol_
   **the sequence is as follows :**
   the server performs a three way handshake with **SYN ,SYN-ACK and ACK** messages

   1. SYN (synchronize) : the client send the **SYN PACKET** to initiate the connection
   2. SYN-ACK (synchronize acknowledge) : if the server accepts the connection it send as **SYN-ACK** PACKET
   3. ACK (acknowledge) : The client send the **ACK** PACKET to the server

   > [!IMPORTANT]
   > The TCP Protocol ensures that data is send between the server and you computer while
   > IP address ensures data is send to the correct destination

5. Once the handshake is successful , the browser makes an HTTP REQUEST server and the server responds with HTML,CSS AND JS files
6. Finally the browser executes the JAVASCRIPT and render the page through various steps (tokenizers, parsers,render tree, layout, and painting)
7. Finally , the webpage appears on your screen
