## Instagram packet sniffing - tcpdump-project
Running packet captures on my home network with tcpdump and analyzing them as searches for Instagram.com occur. IP addresses redacted and replaced with simpler names.

# Initial connection established 

The packet captures were filtered to include only TCP protocol packets with -v verbose level.

19:34:59.059529 IP6 syn[spectrum.com] > instagram[IP].https: Flags [S], seq 2147047963, win 65535, options [mss 1440,nop,wscale 6,nop,nop,TS val 1422416218 ecr 0,sackOK,eol], length 0

The source is an IPv5 TCP SYN packet from a device that is connected with the provider Spectrum. It is sent to an Instagram network. The packet contains a series of options which determine what size and how long it will take for future TCP packets to be sent and recieved.

19:34:59.100387 IP6 instagram[IP].https > syn[spectrum.com]: Flags [S.], seq 2922044658, ack 2147047964, win 65535, options [mss 1392,sackOK,TS val 4265973992 ecr 1422416218,nop,wscale 8], length 0

The Instagram server sends a SYN-ACK packet to acknowledge and send its own SYN.

19:34:59.100467 IP6 syn[spectrum.com] > instagram[IP].https: Flags [.], ack 1, win 2048, options [nop,nop,TS val 1422416259 ecr 4265973992], length 0

The device connected to Spectrum acknowledges. Now data will be sent.

# Sending data

19:34:59.101828 IP6 syn[spectrum.com] > instagram[IP].https: Flags [P.], seq 1:1043, ack 1, win 2048, options [nop,nop,TS val 1422416261 ecr 4265973992], length 1042

The device sends a PSH to be acknowledged to the Instagram server. This packet contains payload data, as signified by the length 1042.

19:34:59.143382 IP6 instagram[IP].https > syn[spectrum.com]: Flags [.], ack 1043, win 265, options [nop,nop,TS val 4265974036 ecr 1422416261], length 0

The Instagram server sends an acknowledgement to the device. A pattern of alternating PSH and ACK packets are exchanged. 







