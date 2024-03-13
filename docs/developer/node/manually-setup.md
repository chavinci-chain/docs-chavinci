# Manually

## __Setting Up a Node on the Chavinci Network__

Welcome to the guide on setting up a node for the Chavinci Network. This step-by-step tutorial will walk you through the process of deploying your node on a server using Digital Ocean as an example. However, these steps are generally applicable to any server provider you choose.

## __Hardware and OS Requirements__
Chavinci is an incredibly lightweight protocol, so nodes can run on commodity hardware. Note that as network usage increases, hardware requirements may change.

* CPU: Equivalent of 2 CPU
* RAM: 2 GB
* Storage: 20-40 GB SSD

## __Prerequisites__
We recommend supported operating systems:

* Ubuntu 20.04
* Ubuntu 22.04

## __1. Server Setup__

- __Account Creation:__ <br/>
    Begin by navigating to (https://www.digitalocean.com) or your chosen server hosting site. If you're new, you'll need to create an account, or simply log in if you already have one.

- __Creating a Droplet:__ <br/>
    1. Click on the “Create” button in the top right corner, then select “Droplets” from the dropdown list.
    ![Figure1](../../assets/images/node/node-1.jpeg)<br/>
    2. Choose a server location that suits your needs from the list of available countries.
    ![Figure2](../../assets/images/node/node-2.jpeg)<br/>
    3. For the Operating System, select Ubuntu. 4. Opt for the 22.04 LTS (x64) version for optimal stability and performance. 
    ![Figure3](../../assets/images/node/node-3.jpeg)<br/>
    5. In the “CPU options” section, select the basic “Regular — Disc Type: SSD”. You may choose a higher model for increased processing power, enhancing your node’s performance within the network. 6. Recommended specs for optimal operation are 2 GB of RAM and 2 CPUs. However, the minimum viable specs are 1 GB of RAM and 1 CPU, though this is not advisable for optimal performance.
    ![Figure4](../../assets/images/node/node-4.jpeg)<br/>
    7. For the “Choose authentication method” section, select “Password”, although SSH keys are also an option. 8. Set your password.
    ![Figure5](../../assets/images/node/node-5.jpeg)<br/>
  

- __Finalizing Details:__ <br/>
    - Enter a Host name of your choosing. This can be any name you prefer.  — Click on the “Create Droplet” button to proceed. Once created, you’ll be directed to the “Learn” page.
    ![Figure6](../../assets/images/node/node-6.jpeg)<br/>

## __2. Node Installation__

- __Accessing Your Droplet:__ <br/>
    1. Click on the newly created droplet that bears the name you assigned.
    ![Figure7](../../assets/images/node/node-7.jpeg)<br/>
    2. Click on the "Console" option to open a new terminal tab.
    ![Figure8](../../assets/images/node/node-8.jpeg)<br/>
<br/>

- __Executing Commands:__ <br/>
    1. Download the Chavinci software package using <br/>
    ```
        wget https://github.com/chavinci-chain/chavinci-releases/releases/download/1.0.3/chavinci-linux.zip
    ```
    ![Figure9](../../assets/images/node/node-9.jpeg)<br/>
    2. Install unzip if not already available: `apt install unzip`. When prompted, select the `[*]packagekit.service` option and click <ok>.
    ![Figure10](../../assets/images/node/node-10.jpeg)<br/>
    3. List the directory contents with `ls` to verify the download.
    ![Figure11](../../assets/images/node/node-11.jpeg)<br/>
    4. Unzip the downloaded file: `unzip chavinci-linux.zip`.
    5. Create a directory for the blockchain data: `mkdir ~/.chachain`, and navigate into it with `cd .chachain`.
    ![Figure12](../../assets/images/node/node-12.jpeg)<br/>
    6. Generate a configuration file: `nano chachain.conf`. This will open a text editor.


- __Configuration:__  <br/> 
  In the editor, input the following configuration, replacing the placeholders (indicated by "") with your specific details:

```
        rpcuser=username   #Change "username" to your desired RPC username
        rpcpassword=password  #Change "password" to your desired RPC password
        daemon=1
        testnet=1
        staking=1   #Set to 1 to enable staking, 0 to disable, or remove the line entirely.
        
```
Save the file and exit the editor.

![Figure13](../../assets/images/node/node-13.jpeg)<br/>

- __Launching the Node:__
    1. Exit the `.chachain` directory with `cd ..`.
    ![Figure14](../../assets/images/node/node-14.jpeg)<br/>

    2. Start the node using `./chad`. You should see a message indicating that the "ChaChain server is starting".
    3. Verify the node operation with `./cha-cli getblockchaininfo`.
    ![Figure15](../../assets/images/node/node-15.jpeg)<br/>


- __Connecting to Peers:__
    - Add your node to the network by connecting to other master nodes:

```
    ./cha-cli addnode 157.245.19.145:22833 add
    ./cha-cli addnode 146.190.207.106:22833 add
    ./cha-cli addnode 139.59.207.170:22833 add
```
![Figure16](../../assets/images/node/node-16.jpeg)<br/>

!!! note
    Nodes are synchronized with the master node after 60 blocks, which is also pertinent for validating stake transactions.

- __Receiving an Address:__
    - Once fully synchronized and operational, use `./cha-cli getnewaddress` to generate a new address. You can now send CHA to this address, initiating the verification process and earning rewards for each validated block.

![Figure17](../../assets/images/node/node-17.jpeg)<br/>



This guide aims to provide a clear and straightforward pathway to setting up a Chavinci Network node. Follow each step carefully to ensure a smooth setup process and successful node operation. Happy staking!