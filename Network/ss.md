## Examples

| Command                                   | Description |
| ----------------------------------------- | ----------- |
| ss -tulpn \| awk '{print $1, $2, $5, $7}' |             |
|                                           |             |
|                                           |             |
|                                           |             |
## Usage

### Help

```text
Usage: ss [ OPTIONS ]
       ss [ OPTIONS ] [ FILTER ]
   -h, --help          this message
   -V, --version       output version information
   -n, --numeric       don't resolve service names
   -r, --resolve       resolve host names
   -a, --all           display all sockets
   -l, --listening     display listening sockets
   -o, --options       show timer information
   -e, --extended      show detailed socket information
   -m, --memory        show socket memory usage
   -p, --processes     show process using socket
   -i, --info          show internal TCP information
       --tipcinfo      show internal tipc socket information
   -s, --summary       show socket usage summary
   -b, --bpf           show bpf filter socket information
   -E, --events        continually display sockets as they are destroyed
   -Z, --context       display process SELinux security contexts
   -z, --contexts      display process and socket SELinux security contexts
   -N, --net           switch to the specified network namespace name

   -4, --ipv4          display only IP version 4 sockets
   -6, --ipv6          display only IP version 6 sockets
   -0, --packet        display PACKET sockets
   -t, --tcp           display only TCP sockets
   -S, --sctp          display only SCTP sockets
   -u, --udp           display only UDP sockets
   -d, --dccp          display only DCCP sockets
   -w, --raw           display only RAW sockets
   -x, --unix          display only Unix domain sockets
       --tipc          display only TIPC sockets
       --vsock         display only vsock sockets
   -f, --family=FAMILY display sockets of type FAMILY
       FAMILY := {inet|inet6|link|unix|netlink|vsock|tipc|help}

   -K, --kill          forcibly close sockets, display what was closed
   -H, --no-header     Suppress header line

   -A, --query=QUERY, --socket=QUERY
       QUERY := {all|inet|tcp|udp|raw|unix|unix_dgram|unix_stream|unix_seqpacket|packet|netlink|vsock_stream|vsock_dgram|tipc}[,QUERY]

   -D, --diag=FILE     Dump raw information about TCP sockets to FILE
   -F, --filter=FILE   read filter information from FILE
       FILTER := [ state STATE-FILTER ] [ EXPRESSION ]
       STATE-FILTER := {all|connected|synchronized|bucket|big|TCP-STATES}
         TCP-STATES := {established|syn-sent|syn-recv|fin-wait-{1,2}|time-wait|closed|close-wait|last-ack|listening|closing}
          connected := {established|syn-sent|syn-recv|fin-wait-{1,2}|time-wait|close-wait|last-ack|closing}
       synchronized := {established|syn-recv|fin-wait-{1,2}|time-wait|close-wait|last-ack|closing}
             bucket := {syn-recv|time-wait}
                big := {established|syn-sent|fin-wait-{1,2}|closed|close-wait|last-ack|listening|closing}
```

### Fields

`ss` does **NOT** have fixed fields like `netstat` — the columns depend on:

- protocol (`tcp`, `udp`, `unix`, `raw`, etc.)
- flags (`-t`, `-u`, `-p`, `-l`, `-n`, `-o`, `-i`, etc.)
- kernel version + iproute2 version

But I can give you:

1. **All possible columns that can appear**
2. **Meaning of each column**
3. A **matrix** showing which flag enables which field

---

#### ✅ **1. Master List — All Possible Fields in `ss`**

These are all the fields that can appear in `ss` output:
##### 🔹 **General Connection Fields**

| Field                  | Meaning                                             |
| ---------------------- | --------------------------------------------------- |
| **Netid**              | Protocol: tcp, udp, unix, raw, etc.                 |
| **State**              | TCP state: ESTAB, LISTEN, TIME-WAIT, SYN-SENT, etc. |
| **Recv-Q**             | Receive queue bytes                                 |
| **Send-Q**             | Send queue bytes                                    |
| **Local Address:Port** | Local IP and port                                   |
| **Peer Address:Port**  | Remote IP and port                                  |

##### 🔹 **Process Information (`-p`)**

| Field                                 | Meaning               |
| ------------------------------------- | --------------------- |
| **users:(("process",pid=1234,fd=5))** | Process name, PID, FD |

##### 🔹 **Timer Information (`-o`)**

|Field|Meaning|
|---|---|
|**timer:(on X msec ...) **|Retrans timer, keepalive timer|
|**retrans**|# of retransmissions|
|**uid**|UID of owning process|

##### 🔹 **TCP Internal Fields**

Requires `-i`.

|Field|Meaning|
|---|---|
|**ts sack**|TCP time stamps + SACK enabled|
|**wscale**|Window scale factor|
|**rcv_space**|Receive buffer size|
|**cwnd**|Congestion window|
|**rtt**|Round-trip time|
|**rttvar**|RTT variance|
|**mss**|Maximum segment size|
|**skmem:(r...)**|Kernel socket memory usage|
|**sndbuf, rcvbuf**|Buffers|
|**backlog**|Listen backlog|
|**syn_retries**|SYN retry count|

##### 🔹 **Socket ID (`-e`)**

|Field|Meaning|
|---|---|
|**ino**|Inode number of the socket|
|**sk**|Kernel socket pointer|
|**uid**|UID|
|**group**|GID|
|**fwmark**|Firewall mark|
|**cookie**|netfilter cookie|

##### 🔹 **UDP Stats**

|Field|Meaning|
|---|---|
|**drops**|Packet drops|
|**tx_queue**|Transmit queue length|

##### 🔹 **UNIX Socket Fields**

|Field|Meaning|
|---|---|
|**Path**|Path to UNIX socket|
|**Type**|stream/dgram|
|**Flags**|w, rw, etc.|

---

#### ✅ **2. What Fields Show Up Depends on Flags**

##### **Basic**

```
ss -t
```

Shows:

```
State  Recv-Q  Send-Q  Local Address:Port  Peer Address:Port
```

##### **With numeric ports**

```
ss -tn
```

##### **With process info**

```
ss -tnp
```

##### **With timers**

```
ss -tno
```

##### **With TCP internals**

```
ss -tni
```

##### **With extra socket details**

```
ss -tnie
```

##### **Full verbose**

```
ss -tnipeo
```

---

### 📌 **3. Example: Full field output (TCP)**

Command:

```bash
ss -tnipeo
```

Possible fields included:

```
State
Recv-Q
Send-Q
Local Address:Port
Peer Address:Port
uid
ino
sk
rtt
rttvar
cwnd
mss
retrans
timer
users(pid, process)
ts
wscale
rcv_space
sndbuf
rcvbuf
skmem
backlog
seq
socket role
... many more internal TCP metrics
```

---

#### 📌 **4. How to view the complete raw kernel socket info**

```bash
ss -ti
```

This prints all TCP advanced metrics (`ts`, `wscale`, `rtt`, etc.).

---

#### 📌 **5. Want to extract only specific fields?**

I can generate a custom `awk` script like:

```
local_ip | local_port | remote_ip | remote_port | pid
```

Just tell me the fields you want.

---

## All TCP states

Here is a **clean, complete, and easy-to-read table of all standard TCP connection states**, including their meanings and when they occur.

---

### 🧵 **TCP State Table (All States Explained)**

|**State**|**Meaning**|**When It Happens**|
|---|---|---|
|**CLOSED**|No connection|Initial state or after a connection is closed|
|**LISTEN**|Waiting for incoming connection|A server socket waiting for clients (`accept()`)|
|**SYN-SENT**|SYN sent, waiting for SYN+ACK|Client has started a TCP handshake|
|**SYN-RECEIVED**|SYN received, SYN+ACK sent|Server responding to a handshake but not yet established|
|**ESTABLISHED**|Active, successful connection|Normal data transfer state|
|**FIN-WAIT-1**|FIN sent, waiting for ACK|One side started closing the connection|
|**FIN-WAIT-2**|FIN acknowledged, waiting FIN|Remote side has not closed yet|
|**CLOSE-WAIT**|Received FIN, waiting to close|Local application hasn't closed the socket yet|
|**CLOSING**|Both sides have sent FIN|Very rare — simultaneous close|
|**LAST-ACK**|FIN sent after receiving FIN|Waiting for final ACK from remote|
|**TIME-WAIT**|Connection closed, but waiting 2MSL|Prevents delayed packets from mixing with new connections|
|**DELETE-TCB**|Socket being removed|Internal cleanup state (Linux-specific)|

---

### ⭐ Graph: TCP State Transition (shortcut version)

```
Client                               Server
------                               ------

CLOSED                               LISTEN
  |                                     |
  |---- SYN ---------------------------> |
  |                                     |
SYN-SENT                            SYN-RECEIVED
  |                                     |
  |<--- SYN+ACK ------------------------ |
  |                                     |
  |---- ACK ---------------------------> |
  |                                     |
ESTABLISHED                        ESTABLISHED
```

Closing (client-initiated):

```
ESTABLISHED → FIN-WAIT-1 → FIN-WAIT-2 → TIME-WAIT → CLOSED
```

Server:

```
ESTABLISHED → CLOSE-WAIT → LAST-ACK → CLOSED
```

---

### 🧠 Short Descriptions (Easy Memory Guide)

|**State**|**Short Description**|
|---|---|
|**LISTEN**|Waiting for connections|
|**SYN-SENT**|"Knock knock" (client sends SYN)|
|**SYN-RECEIVED**|Server says "come in"|
|**ESTABLISHED**|Data flowing|
|**FIN-WAIT-1**|I'm leaving|
|**FIN-WAIT-2**|I'm waiting for you to leave|
|**CLOSE-WAIT**|I heard you're leaving|
|**LAST-ACK**|I’m leaving too, acknowledge me|
|**CLOSING**|Both leaving at same time|
|**TIME-WAIT**|Taking a 2-minute pause to avoid ghosts|
|**CLOSED**|No connection|

---


### ✅ How packets flow through these states

Below is a **clean, text-based TCP state diagram** showing **exact packet flow**, **who sends what**, and **how states transition**.  
This is the closest to an RFC-level TCP flow diagram but easy to read.

---

#### 🖼️ **TCP 3-Way Handshake + Data + 4-Way Close (Full Packet Flow Diagram)**

```
CLIENT                                            SERVER
======                                            ======
            (no connection)
CLOSED                                            LISTEN
   |                                                |
   |---[SYN]--------------------------------------->|
   |                                                |
SYN-SENT                                        SYN-RECEIVED
   |                                                |
   |<--[SYN + ACK]----------------------------------|
   |                                                |
   |---[ACK]--------------------------------------->|
   |                                                |
ESTABLISHED                                   ESTABLISHED
   |                                                |
   |=========  DATA FLOW (SEND/RECV)  ==============|
   |                                                |

====================== CONNECTION CLOSE ======================

CLIENT INITIATES CLOSE:

ESTABLISHED                                       ESTABLISHED
   |                                                |
   |---[FIN]--------------------------------------->|
   |                                                |
FIN-WAIT-1                                     CLOSE-WAIT
   |                                                |
   |<--[ACK]----------------------------------------|
   |                                                |
FIN-WAIT-2                                     CLOSE-WAIT
   |                                                |
   |                        (application closes)     |
   |                                                |
   |<--[FIN]----------------------------------------|
   |                                                |
   |---[ACK]--------------------------------------->|
   |                                                |
TIME-WAIT                                      LAST-ACK
   |                                                |
(wait 2MSL)                                         |
   |                                                |
CLOSED                                            CLOSED
```

---

#### 📌 **Alternate: Server-Initiated Close**

```
CLIENT                                            SERVER
ESTABLISHED                                   ESTABLISHED
   |                                                |
   |<--[FIN]----------------------------------------|
   |                                                |
CLOSE-WAIT                                     FIN-WAIT-1
   |                                                |
   |---[ACK]--------------------------------------->|
   |                                                |
CLOSE-WAIT                                     FIN-WAIT-2
   |                                                |
   |---[FIN]--------------------------------------->|
   |                                                |
LAST-ACK                                       FIN-WAIT-2
   |                                                |
   |<--[ACK]----------------------------------------|
   |                                                |
CLOSED                                            CLOSED
```

---

#### 🧠 **TCP State Summary From Diagram**

|Packet|Client State|Server State|
|---|---|---|
|Client sends SYN|SYN-SENT|LISTEN|
|Server replies SYN+ACK|SYN-SENT|SYN-RECEIVED|
|Client ACK → connection open|ESTABLISHED|ESTABLISHED|
|Client FIN to close|FIN-WAIT-1|CLOSE-WAIT|
|Server ACKs|FIN-WAIT-2|CLOSE-WAIT|
|Server FIN|FIN-WAIT-2|LAST-ACK|
|Client ACK|TIME-WAIT|CLOSED|
|Client waits 2MSL → closes|CLOSED|CLOSED|

---

#### ⭐ Bonus: Why TIME-WAIT exists

**TIME-WAIT (2×MSL, usually ~60 sec)** ensures:

1. Delayed packets from the old connection cannot enter a new one
    
2. Last ACK can be retransmitted if server didn’t receive it
    

This prevents port reuse issues and “ghost” packets.

---

### ✅ A cheat sheet for debugging TCP issues

Here is a **concise but powerful TCP debugging cheat sheet** for Linux.  
Covers **SYN flood**, **TIME_WAIT exhaustion**, **CLOSE_WAIT leaks**, plus **commands**, **what to look for**, and **fix strategies**.

---

#### 🧠 **TCP Debugging Cheat Sheet (Linux)**

**Covers:**  
✔ Detecting SYN Flood  
✔ Fixing TIME_WAIT exhaustion  
✔ Debugging CLOSE_WAIT leaks  
✔ Recommended commands + interpretations

---

#### 🔥 **1. Detecting a SYN Flood**

##### 📌 **Symptoms**

- Many connections stuck in **SYN-RECEIVED**
- High CPU usage in the kernel
- Legitimate clients can’t connect
- Backlog full (errors in logs)

##### 📌 **Check SYN-RECEIVED count**

```bash
ss -tan state syn-recv | wc -l
```

##### 📌 **See top offenders (sorted by IP)**

```bash
ss -tan state syn-recv | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -nr
```

##### 📌 **Check SYN backlog overflow**

```bash
grep syn /proc/net/netstat
```

Look at:

- `SyncookiesSent`
- `SyncookiesFailed`
- `ListenDrops`

##### 📌 **Check if SYN cookies are on**

```bash
sysctl net.ipv4.tcp_syncookies
```

If `0`, enable:

```bash
sudo sysctl -w net.ipv4.tcp_syncookies=1
```

##### 📌 **Increase backlog**

```bash
sudo sysctl -w net.core.somaxconn=4096
sudo sysctl -w net.ipv4.tcp_max_syn_backlog=4096
```

---

#### 🧊 **2. TIME_WAIT Exhaustion**

TIME_WAIT happens on the **side that closes the connection first** (typically a client or proxy).

##### 📌 **Symptoms**

- Thousands of sockets stuck in **TIME-WAIT**
- Outgoing connections fail
- Errors: “Cannot assign requested address”
- Port exhaustion (ephemeral port shortage)

##### 📌 **Check TIME_WAIT count**

```bash
ss -tan state time-wait | wc -l
```

##### 📌 **Check ephemeral port usage**

```bash
cat /proc/sys/net/ipv4/ip_local_port_range
ss -tan | awk '{print $5}' | cut -d: -f2 | sort -n | uniq | wc -l
```

##### 📌 **Fix Options**

###### **✔ Change ephemeral port range**

```bash
sudo sysctl -w net.ipv4.ip_local_port_range="1024 65535"
```

###### **✔ Enable TCP reuse / recycle**

⚠ _Safe on clients, risky on servers_

```bash
sudo sysctl -w net.ipv4.tcp_tw_reuse=1
```

###### **✔ Reduce TIME_WAIT timeout**

```bash
sudo sysctl -w net.ipv4.tcp_fin_timeout=15
```

###### **✔ Avoid closing connections frequently**

Use:

- HTTP KeepAlive
- Connection pools
- Shared sockets

---

#### ⚠️ **3. CLOSE_WAIT Leak**

CLOSE_WAIT happens when:

**Server receives FIN → kernel ACKs → application fails to close() the socket.**

This means:  
➡ **Your application code is leaking sockets**  
➡ **NOT a Linux problem**

##### 📌 **Symptoms**

- Many connections stuck in **CLOSE-WAIT**
- File descriptors leak
- Application stops accepting new sockets
- “Too many open files”

##### 📌 **Check CLOSE_WAIT count**

```bash
ss -tan state close-wait | wc -l
```

##### 📌 Identify leaking process**

```bash
ss -tanp | grep CLOSE-WAIT
```

Or list file descriptors:

```bash
lsof -iTCP -sTCP:CLOSE-WAIT -nP
```

##### 📌 **Fixes**

###### ✔ Fix your application

**CLOSE_WAIT = missing `close()` in your code.**

Languages:

- **Go:** missing `conn.Close()`
    
- **Python:** missing `socket.close()` or not using context manager
    
- **Java:** missing `socket.close()` or forgetting to close streams
    

###### ✔ Increase FD limits (temporary workaround)

```bash
ulimit -n 65535
```

---

#### ⚡ **4. FIN_WAIT_1 / FIN_WAIT_2 Issues**

##### 📌 Symptoms

- One side closes, but the other side **never responds**
    
- Stuck in FIN_WAIT_2 forever
    

##### 📌 Check them:

```bash
ss -tan state fin-wait-1
ss -tan state fin-wait-2
```

##### 📌 Fix

- Check remote peer (it failed to close properly)
- Network middlebox dropping FIN packets
- Enable TCP keepalive to detect dead peers

Enable keepalive:

```bash
sudo sysctl -w net.ipv4.tcp_keepalive_time=60
sudo sysctl -w net.ipv4.tcp_keepalive_probes=5
sudo sysctl -w net.ipv4.tcp_keepalive_intvl=10
```

---

#### 🛠️ **5. Debugging Tools Quick Reference**

|Purpose|Command|
|---|---|
|List sockets|`ss -tuanp`|
|Filter by state|`ss -tan state established`|
|Show retransmissions|`ss -tno`|
|Show TCP internals|`ss -tni`|
|Who owns socket|`lsof -i`|
|Trace system calls|`strace -e trace=network -p PID`|
|Capture packets|`tcpdump -i eth0`|
|Show kernel TCP stats|`cat /proc/net/netstat`|
|Show TCP memory|`ss -m`|

---
## How to colorize ss outputs

`ss` has no built-in color support, but you _can_ colorize its output using external tools.  
Here are several practical and commonly used methods.

---

### ✅ **1. Colorize `ss` output using `grc` (recommended)**

`grc` (Generic Colouriser) automatically colorizes many commands.

##### **Install**

```bash
sudo apt install grc
```

##### **Use**

```bash
grc ss -tulnp
```

##### **Always colorize automatically**

Add this to your `~/.bashrc`:

```bash
alias ss='grc ss'
```

---

### ✅ **2. Colorize using `awk`**

You can add ANSI colors manually.

Example: highlight LISTEN sockets in green, ESTAB in blue:

```bash
ss -tuna | awk '
/LISTEN/ {print "\033[32m" $0 "\033[0m"; next}
/ESTAB/  {print "\033[34m" $0 "\033[0m"; next}
{print}
'
```

---

### ✅ **3. Colorize using `grep --color` (simple)**

Highlight patterns:

```bash
ss -tuna | grep --color=always -E "LISTEN|SYN-SENT|ESTAB|$"
```

Or highlight only IP:

```bash
ss -tuna | grep --color=always -E "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+|$"
```

---

### ✅ **4. Use `ccze` (another colorizer)**

```bash
sudo apt install ccze
ss -tulpn | ccze -A
```

---

# 🧪 **5. Example: fully custom colorized ss**

```bash
ss -tanp | awk '
/ESTAB/      {c="\033[32m"}   # green
/LISTEN/     {c="\033[34m"}   # blue
/CLOSE-WAIT/ {c="\033[31m"}   # red
/TIME-WAIT/  {c="\033[33m"}   # yellow
{print c $0 "\033[0m"; c=""}
'
```

---

### ⭐ Best Option?

If you want **automatic, nice-looking output without scripting**, use:

```bash
sudo apt install grc
grc ss -tulnp
```

---
