# Global
    TCP
    UDP

# Only SYN
    tcp.flags == 2
    tcp.flags.syn == 1  # syn flag is set, ignore rest of bits

# only SYN ACK
    tcp.flags == 18 # Only SYN, ACK flags.
    (tcp.flags.syn == 1) and (tcp.flags.ack == 1) # SYN and ACK are set. The rest of the bits are not important.

# Nmap TCP connect scan filter - default for non privilege or nmap -sT
    tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024

# Nmap TCP SYN scan filter - nmap -sS
    tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size <= 1024

# Nmap UDP Scan - nmap -sU
    icmp.type==3 and icmp.code==3