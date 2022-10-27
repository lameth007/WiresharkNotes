# Filtering the proper DHCP packet options is vital to finding an event of interest. 

"DHCP Request" packets contain the hostname information  - dhcp.option.dhcp == 3
"DHCP ACK" packets represent the accepted requests - dhcp.option.dhcp == 5
"DHCP NAK" packets represent denied requests - dhcp.option.dhcp == 6


-------
"DHCP Request" options for grabbing the low-hanging fruits:

    Option 12: Hostname.
    Option 50: Requested IP address.
    Option 51: Requested IP lease time.
    Option 61: Client's MAC address.


dhcp.option.hostname contains "keyword"

"DHCP ACK" options for grabbing the low-hanging fruits:

    Option 15: Domain name.
    Option 51: Assigned IP lease time.

    dhcp.option.domain_name contains "keyword"


"DHCP NAK" options for grabbing the low-hanging fruits:

    Option 56: Message (rejection details/reason).


# NetBIOS

nbns

nbns.name contains "keyword"

# Kerberos Analysis

kerberos
kerberos.CNameString contains "keyword"

CnameString = username
kerberos.CNameString and !(kerberos.CNameString contains "$" )

