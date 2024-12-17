
### Devices in the Network

- **Router**: Model: Cisco 2811
- **Switch 1**: Model: Cisco 2960-24TT
- **Laptop**: 210.3.14.2
- **Server0**: 210.3.14.3
- **PC1**: 210.3.14.4
- **PC0**: 210.3.14.5
- **PC3**: 210.3.14.6  ← Added

- **Switch 2**: Model: Cisco 2960-24TT
- **Server1**: 168.90.0.3
- **Server2**: 168.90.0.2
- **PC2**: 168.90.0.4
- **PC4**: 168.90.0.5  ← Added

### DHCP Configuration Steps on Router

#### Step-by-Step Commands:

1. **Enter CLI mode on the router:**
   - Access the router command line in Packet Tracer.

2. **Enable privileged mode:**
Router> enable

markdown
Copy code

3. **Enter global configuration mode:**
Router# configure terminal

markdown
Copy code

4. **Set up the DHCP pool for Switch 1 devices:**
Router(config)# ip dhcp pool SWITCH1 Router(dhcp-config)# network 168.90.0.0 255.255.0.0 Router(dhcp-config)# default-router 168.90.0.1 Router(dhcp-config)# exit

markdown
Copy code

5. **Set up the DHCP pool for Switch 2 devices:**
Router(config)# ip dhcp pool SWITCH2 Router(dhcp-config)# network 210.3.14.0 255.255.255.0 Router(dhcp-config)# default-router 210.3.14.1 Router(dhcp-config)# exit

java
Copy code

6. **Exclude IP addresses for static devices (e.g., servers):**
Router(config)# ip dhcp excluded-address 168.90.0.1 168.90.0.10 Router(config)# ip dhcp excluded-address 210.3.14.1 210.3.14.10

markdown
Copy code

7. **Verify DHCP is working:**
- Test on PCs and servers to confirm they receive IP addresses dynamically via DHCP.
Router# show ip dhcp binding
 
