## What happens when you type google.com in your browser

1. First up , you type website address "google.com" in the browser's address bar
2. The browser checks its caches first . If there is a cache miss, it must find and ip address

   > [!IMPORTANT]
   > a cache miss is when the browser can find the name resolution locally in its caches
   > while a caches hit is when the browser is able to find the name resolution locally

3. DNS look up begins <span style='color:fuchsia'>The request goes through different DNS servers (root,TLD and authoritative). Finally the IP address is resolved</span>

4. The browser the initiates a TCP connection handshake

- the sequence is as follows : the server performs a three way handshake with SYN ,SYN-ACK and ACK messages

5. Once the handshake is successful , the browser makes an HTTP REQUEST server and the server responds with HTML,CSS AND JS files
6. Finally the browser executes the JAVASCRIPT and render the page through various steps (tokenizers, parsers,render tree, layout, and painting)
7. Finally , the webpage appears on your screen
