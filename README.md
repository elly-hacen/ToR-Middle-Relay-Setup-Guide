## Middle Relay Requirements

To operate effectively as a middle relay, ensure your system meets the following specifications:

- **Bandwidth:** At least 10 Mbit/s (16 Mbit/s recommended) both ways (upstream and downstream).
- **Connections:** Able to handle at least 7000 concurrent connections.
- **Monthly Traffic:** At least 100 GBytes (2 TB or more recommended).
- **RAM:** At least 512 MB if slower than 40 Mbps or 1 GB if faster.
- **IP:** IPv4 address, dynamic or static (preferred with at least 3 hours unchanged).
- **Disk Storage:** At least 200 MB.
- **Uptime:** Ideally 24/7 but more than 2 hours a day is advised.

Ensure your system meets these specifications to function optimally as a middle relay in the Tor network.

---

### Installation Steps

1. #### Installing `Tor`

    To install Tor, execute the following command in your terminal:

    ```bash    
    $ sudo pacman -S tor
    ```

2. #### Terminal Status Monitor for Tor (Nyx)

    To obtain a comprehensive overview of Tor's bandwidth usage and connection details, install Nyx using the command below:

    ```bash
    $ sudo pacman -S nyx
    ```

3. #### Enabling the Tor Service

    After installing Tor, it's essential to enable and start the Tor service using the following command:

    ```bash
    $ systemctl enable --now tor
    ```

### Configuring Tor

1. Open the Tor Configuration File:

    Use the following command to open the Tor configuration file in the nano text editor:
    
    ```bash
    $ sudo nano /etc/tor/torrc
    ```

2. Add the Following Configuration to the `torrc` file:

    ```bash
    ## BASE CONFIG
    
    Nickname your_nickname    # Change "your_nickname" to something you like
    ContactInfo your@email   # Write your e-mail and be aware it will be published
    ORPort 443               # You might use a different port
    ExitRelay 0
    SocksPort 0
    
    ## BANDWIDTH
    
    The following configuration limits both upload and download to a maximum of 800GB per month. 
    This limit resets at the beginning of each month, precisely at midnight on the 1st.
    
    AccountingMax 800 GBytes
    AccountingStart month 1 0:00
    
    ## MONITORING
    
    ControlPort 9051
    CookieAuthentication 1
    ```

### Run Nyx:

1. Run `nyx` by executing the following command in your terminal:

      ```bash    
      $ nyx
      ```

---

### Note

For Debian users, the procedure is similar, except for the installation of Tor. This guide is specifically tailored for Arch Linux users (i.e., "i use Arch btw ⚜️").

### Sources

- [Types of relays](https://community.torproject.org/relay/types-of-relays/)
- [Relay Requirements](https://community.torproject.org/relay/relays-requirements/)
- [The lifecycle of a new relay](https://blog.torproject.org/lifecycle-of-a-new-relay/)
- [Tor setup guide for different distributions](https://community.torproject.org/relay/setup/guard/)
