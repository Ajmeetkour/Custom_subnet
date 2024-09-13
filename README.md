## Custom_subnet
Creating a Custom Subnet with Avalanche HyperSDK
In the previous section, we learned about pre-built subnets that can be deployed and interacted with. However, these templates may not always fit our specific use case. This is where the HyperSDK comes in.
The HyperSDK provides the ability to create a custom virtual machine, which offers complete control over a custom blockchain. With the HyperSDK, you can design a blockchain that perfectly suits your needs, such as creating and transferring tokens or implementing a traditional order book for asset trading. This level of customization provides a powerful tool for businesses and organizations seeking a tailored solution.
## Features
Custom Virtual Machine: Build and customize a blockchain using HyperSDK. Token Management: Define and manage rules for token creation, minting, and transfers. Order Book Management: Create and handle an order book for asset trading.

## Objective
Our startup aims to develop a custom virtual machine to facilitate token minting and transfer operations. HyperSDK offers the flexibility needed to construct a blockchain with precise functionality, including token management and asset trading.

## Important Note
HyperSDK is in its alpha phase. For stability, we are using the example token VM, which is among the few tested and supported configurations. Keep an eye on the repository for updates.

### Getting Started
Ensure that Go is installed on your system.

### Step by Step 
1. Clone the Repository:
2. git clone https://github.com/Metacrafters/tokenvm.git Normalize Dependencies:
3. Inside your project folder, run go mod tidy to normalize all the dependencies
4. Configure your project constants
   * Go to consts/consts.go and add the missing parts.
   * Register the Create_Asset and Mint_Assest actions in registry/registry.go
5. Run your VM locally
Make sure Go is on your path, defined on your terminal, if not you can do so by running export PATH=$PATH:$(go env GOPATH)/bin
If this path doesn’t work, you can also try export PATH=$PATH:/usr/local/go/bin
6. Run MODE="run-single" ./scripts/run.sh
7. Run ./scripts/build.sh
   If you get a permissions denied error, try running these scripts with the bash command (i.e.bash ./scripts/run.sh)
8. Load the demo private key included on the project ./build/token-cli key import demo.pk and ./build/token-cli chain import-anr

9. Interact with hyperchain
* Mint and Trade
#### Step 1: 
Create Your Asset
First up, let's create our own asset. You can do so by running the following command from this location:

./build/token-cli action create-asset When you are done, the output should look something like this:

database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
metadata (can be changed later): MarioCoin
continue (y/n): y
✅ txID: 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
txID is the assetID of your new asset.

The "loaded address" here is the address of the default private key (demo.pk). We use this key to authenticate all interactions with the tokenvm.

#### Step 2: 
Mint Your Asset
After we've created our own asset, we can now mint some of it. You can do so by running the following command from this location:

./build/token-cli action mint-asset When you are done, the output should look something like this (usually easiest just to mint to yourself).

database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
assetID: 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
metadata: MarioCoin supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 15000
continue (y/n): y
✅ txID: X1E5CVFgFFgniFyWcj5wweGg66TyzjK2bMWWTzFwJcwFYkF72
Step 3: View Your Balance
Now, let's check that the mint worked right by checking our balance. You can do so by running the following command from this location:

./build/token-cli key balance When you are done, the output should look something like this:

database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: Em2pZtHr7rDCzii43an2bBi1M2mTFyLN33QP1Xfjy7BcWtaH9
assetID (use TKN for native token): 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
metadata: MarioCoin supply: 10000 warp: false
balance: 15000 27grFs9vE2YP9kwLM5hQJGLDvqEY9ii71zzdoRHNGC4Appavug
Closing the Local Avalanche Network: To shut down the local Avalanche network, run:

10. killall avalanche-network-runner

## CONCLUSION
We have successfully created a custom virtual machine to handle token minting and transfers. By using HyperSDK, you can further tailor the blockchain to meet your specific requirements.

## Authors
Ajmeet
## LICENSE
This project is licensed under the MIT License - see the LICENSE.md file in details.
