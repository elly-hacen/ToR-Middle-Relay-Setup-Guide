## Installation Steps

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

## Configuring Tor

1. #### Open the Tor Configuration File

    Use the following command to open the Tor configuration file in the nano text editor:

    ```bash
    $ sudo nano /etc/tor/torrc
    ```

2. #### Add the Following Configuration

    Append the following configurations to the `torrc` file:

    ```bash
    ## BASE CONFIG

    Nickname your_nickname    # Change "your_nickname" to something you like
    ContactInfo your@email   # Write your e-mail and be aware it will be published
    ORPort 443               # You might use a different port
    ExitRelay 0
    SocksPort 0

    ## BANDWIDTH
    
    ## The following configuration limits both upload and download to a maximum of 800GB per month. 
    ## This limit resets at the beginning of each month, precisely at midnight on the 1st.

    AccountingMax 800 GBytes
    AccountingStart month 1 0:00

    ## MONITORING

    ControlPort 9051
    CookieAuthentication 1
    ```

   Similar settings might already exist in the `torrc` file, but they are usually commented out. This section organizes all the configurations in one place for better management.

## Run Nyx

  Run `nyx` by running following command in your terminal:

  ```bash    
  $ nyx
  ```

### Note

For Debian users, the procedure is similar, except for the installation of Tor. This guide is specifically tailored for Arch Linux users (i.e., "i use Arch btw ⚜️").
