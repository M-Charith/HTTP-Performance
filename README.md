# HTTP-Performance


```markdown
# P4-Mininet Setup for Basic and Star Topologies

This project involves setting up P4-Mininet on a Hypervisor like Oracle VirtualBox and running basic client-server interactions using fixed IP addresses for hosts.

## Prerequisites

- **P4-Mininet** installed on a Hypervisor (Oracle VirtualBox recommended)
- **Wireshark** for capturing and recording network traffic
- **Mininet** pre-installed with P4 language support

## Installation and Setup

1. **Install P4-Mininet** on a Hypervisor like Oracle VirtualBox.
2. Copy the `basic` and `star` folders and place them in `/home/p4/tutorials/exercises`.

## Running the Requests on the Basic Setup

1. Open a terminal and navigate to the `basic` directory:
   ```bash
   cd /home/p4/tutorials/exercises/basic
   ```
2. Run the following commands to clean and run the setup:
   ```bash
   make clean
   make run
   ```
3. You will be in the Mininet prompt. Now, open terminals for Host 1 and Host 2:
   ```bash
   xterm h1
   xterm h2
   ```

### Commands to Run on h2's Terminal:

1. Run the following command to set up the ARP:
   ```bash
   bash h2-arp.sh
   ```
   (Run this every time after `make` is executed.)

2. Start the server:
   ```bash
   python server.py
   ```

### Commands to Run on h1's Terminal:

1. Run the following command to set up the ARP:
   ```bash
   bash h1-arp.sh
   ```
   (Run this every time after `make` is executed.)

2. Run the client to make requests:
   ```bash
   python client.py
   ```

### Sample HTTP Requests

Run the following HTTP requests from h1's terminal to interact with the server:

- **PUT request:**
   ```bash
   "PUT /assignment2/key1/val1 HTTP/1.1"
   ```

- **GET request:**
   ```bash
   "GET /assignment2?request=key1 HTTP/1.1"
   ```

- **DELETE request:**
   ```bash
   "DELETE /assignment2/key1 HTTP/1.1"
   ```

> Note: Requests should be enclosed in quoted characters as shown above.

### Responses

- **Connection OK:**
   ```
   HTTPS/1.1 200 OK
   ```

- **Bad Request:**
   ```
   HTTPS/1.1 400 Bad Request
   ```

- **Not Found:**
   ```
   HTTPS/1.1 404 Not Found
   ```

## Running the Requests on the Star Setup

1. Open a terminal and navigate to the `star` directory:
   ```bash
   cd /home/p4/tutorials/exercises/star
   ```
2. Run the following commands to clean and run the setup:
   ```bash
   make clean
   make run
   ```
3. You will be in the Mininet prompt. Now, open terminals for Host 1, Host 2, and Host 3:
   ```bash
   xterm h1
   xterm h2
   xterm h3
   ```

### Commands to Run on h2's Terminal:

1. Run the following command to set up the ARP:
   ```bash
   bash h2-arp.sh
   ```
   (Run this every time after `make` is executed.)

2. Start the cache:
   ```bash
   python cache.py
   ```

### Commands to Run on h3's Terminal:

1. Run the following command to set up the ARP:
   ```bash
   bash h3-arp.sh
   ```

2. Start the server:
   ```bash
   python server.py
   ```

### Commands to Run on h1's Terminal:

1. Run the following command to set up the ARP:
   ```bash
   bash h1-arp.sh
   ```

2. Run the client to make requests:
   ```bash
   python client.py
   ```

### Sample HTTP Requests

Run the following HTTP requests from h1's terminal to interact with the server:

- **PUT request:**
   ```bash
   "PUT /assignment2/key1/val1 HTTP/1.1"
   ```

- **GET request:**
   ```bash
   "GET /assignment2?request=key1 HTTP/1.1"
   ```

> Note: Requests should be enclosed in quoted characters as shown above.

### Responses

- **Connection OK:**
   ```
   HTTPS/1.1 200 OK
   ```

- **Bad Request:**
   ```
   HTTPS/1.1 400 Bad Request
   ```

- **Not Found:**
   ```
   HTTPS/1.1 404 Not Found
   ```

## Wireshark Monitoring

Wireshark can be used to capture and record the request and response communication between hosts.

---

This README file should provide clear instructions for installing, setting up, and running the project in both the basic and star topologies.
