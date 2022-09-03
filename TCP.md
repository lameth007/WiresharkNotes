# Filter for 2 ports
tcp.port in {80 443}

# Filter for a range of ports (300 - 350)
tcp.port in {300 .. 350}


# TCP Values
    1 = SYN
    2 = SYN/ACK
    4 = ACK
    8 = Data
    16 = FIN
    32 = Reset

These values add up as they are present in the conversation, showing the completeness field's value. For example, to filter for conversations that only have the full handshake (SYN, SYN/ACK, ACK): tcp.completeness==7 (1+2+4)

# search for complete conversation
tcp.completeness==7


Stealth scans in NMAP will have a tcp completeness value of 35. These scans are only the SYN, SYN/ACK, and a Reset (1+2+32). An attempt that is filtered would be tcp.completeness==1. A port that is closed would be tcp.completeness==37(SYN, RST/ACK - 1+32+4). This is a good way to filter for connection attempts that were successful vs unsuccessful. 