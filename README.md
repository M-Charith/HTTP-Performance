# HTTP-Performance


# P4-Mininet Network Setup and Request Testing

This project sets up a basic and star topology using **P4-Mininet** on a hypervisor like Oracle VirtualBox. It includes instructions for installing the environment, setting up network requests between hosts, and observing request-response behavior with Mininet.

## Installation
1. Install P4-Mininet on a hypervisor (e.g., Oracle VirtualBox).
2. Clone or copy the `basic` and `star` folders, placing them in the following directory:
   ```bash
   /home/p4/tutorials/exercises
   ```
3. The IP addresses of hosts (`h1`, `h2`, and `h3`) are fixed for simplicity. The IP addresses used are:
   - `h1`: 10.0.1.1
   - `h2`: 10.0.1.2
   - `h3`: 10.0.1.3

> **Note:** IPs are hardcoded in `client.py`, `server.py`, and `cache.py` in both the `basic` and `star` setups to avoid entering IP addresses manually.

## Running the Basic Setup
1. Open a terminal and navigate to the `basic` directory:
   ```bash
   cd /home/p4/tutorials/exercises/basic
   ```
2. Clean up previous configurations:
   ```bash
   make clean
   ```
3. Run the Mininet simulation:
   ```bash
   make run
   ```
4. You will now be in the Mininet prompt.

5. **Open Host Terminals:**
   - Start terminals for each host using:
     ```bash
     xterm h1
     xterm h2
     ```

6. **Set up ARP and Run the Servers:**
   - On **h2's terminal**:
     ```bash
     bash h2-arp.sh       # Run once every time you run `make`
     python server.py
     ```
   - On **h1's terminal**:
     ```bash
     bash h1-arp.sh       # Run once every time you run `make`
     python client.py
     ```

## Running the Star Setup
1. Open a terminal and navigate to the `star` directory:
   ```bash
   cd /home/p4/tutorials/exercises/star
   ```
2. Clean up previous configurations:
   ```bash
   make clean
   ```
3. Run the Mininet simulation:
   ```bash
   make run
   ```
4. You will now be in the Mininet prompt.

5. **Open Host Terminals:**
   - Start terminals for each host using:
     ```bash
     xterm h1
     xterm h2
     xterm h3
     ```

6. **Set up ARP and Run the Servers:**
   - On **h2's terminal**:
     ```bash
     bash h2-arp.sh       # Run once every time you run `make`
     python cache.py
     ```
   - On **h3's terminal**:
     ```bash
     bash h3-arp.sh       # Run once every time you run `make`
     python server.py
     ```
   - On **h1's terminal**:
     ```bash
     bash h1-arp.sh       # Run once every time you run `make`
     python client.py
     ```

## Example Requests
Requests are sent from `h1`'s terminal to interact with the server on `h2` or `h3`. Use the following commands:

```plaintext
"PUT /assignment2/key1/val1 HTTP/1.1"
"GET /assignment2?request=key1 HTTP/1.1"
"DELETE /assignment2/key1 HTTP/1.1"
```

> **Note**: Enclose requests in quotes as shown above.

## Response Status Codes
After each request, `h1`’s terminal will display one of the following responses:

- **Connection OK**: `"HTTPS/1.1 200 OK"`
- **Bad Request**: `"HTTPS/1.1 400 Bad Request"`
- **Not Found**: `"HTTPS/1.1 404 Not Found"`

> Timestamps for each interaction are recorded with Wireshark for further analysis.

## Troubleshooting
- Ensure all ARP setup scripts are run (`h1-arp.sh`, `h2-arp.sh`, `h3-arp.sh`) each time after running `make`.
- If Mininet terminals don’t open, check the installation path and permissions.

--- 
