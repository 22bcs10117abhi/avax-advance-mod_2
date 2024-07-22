
## AVAX-PROOF--Avalanche-HyperSDK

This project uses HyperSDK that provides the ability to create a custom virtual machine, which offers complete control over a custom blockchain. By using the HyperSDK, we have full control over the rules and functionality of your chain, allowing us to create a custom blockchain that is tailored to your startup's specific needs.
## Description
`consts/consts.go` contains the constants that is accessible across the hyperVM. The HRP, Name, and Symbol constants define information about the TokenVM, including its Human-Readable Part (HRP), name, and symbol.
This code is added in the consts/consts.go.

```js
const (
	// TODO: choose a human-readable part for your hyperchain
	HRP = "This is my personal chain"
	// TODO: choose a name for your hyperchain
	Name = "ATM"
	// TODO: choose a token symbol
	Symbol = "Am"
)
```
`registry/registry.go` contains the action that will be performed in the terminal during interaction.
```js 
// TODO: register action: actions.CreateAsset
consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false),
// TODO: register action: actions.MintAsset
consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false),
```
This code is added in `registry/registry.go`

## Steps of Execution

This project is execute on WSl on windows and GO installed inside wsl.

    1. run git clone (GitHub file link)
    2. run cd (file name)
    3. Github is not allowing me to upload the files due to large no of files so I added the zip file.
    4. Extract the Avalanche hyperSDK project
    5. cd '(foldername)' 
    6. In terminal run command MODE="run-single" ./scripts/run.sh and this will start our machine with 1 subnet and for 2 subnet run ./scripts/run.sh. after this command output will look like.
```js
    Ran 4 of 4 Specs in 103.332 seconds
SUCCESS! -- 4 Passed | 0 Failed | 0 Pending | 0 Skipped
PASS
cluster is ready!
avalanche-network-runner is running in the background...

use the following command to terminate:

killall avalanche-network-runner
```
7. To start interaction run ./scripts/build.sh. output will be :
```js 
/scripts/build.sh
Building tokenvm in ./build/tHBYNu8ikqo4MWMHehC9iKB9mR5tB3DWzbkYmTfe9buWQ5GZ8
Building token-cli in ./build/token-cli
This command will put the compiled CLI in ./build/token-cli.
```
 NOTE- default address is `token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp`

   8.  Lastly, we'll need to add the chains we created and the default key to the token-cli. run command:
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
chain import-anr connects to the Avalanche Network Runner server running in the background and pulls the URIs of all nodes tracking each chain you created..

## Creation and Minting process

## Step:-1 Asset Creation

To create an assest run the command:
`./build/token-cli action create-asset`
Enter the metadata, and confirm output looks like:
```js
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2aunvASmyp4SzxSxDzLN83wceU3HMJuTos8jeEp2L748YPyPmE
✔ metadata (can be changed later): gold█
✔ continue (y/n): y█
✅ txID: 2MgGttbdtX5t8dDETyFy57P1RdRz4wM1GsZzNVw1eNh5KTX6gZ

```


## Step:-2 Minting of asset

To mint the created assest run command:
`./build/token-cli action mint-asset`
output looks like:
```js
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
✔ assetID: 2MgGttbdtX5t8dDETyFy57P1RdRz4wM1GsZzNVw1eNh5KTX6gZ█
assetID: 2MgGttbdtX5t8dDETyFy57P1RdRz4wM1GsZzNVw1eNh5KTX6gZ
metadata: gold supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 100000
continue (y/n): y
✅ txID: moYv4q6nLBRPS24ak2iJh2KrDqGKsi3945vd9ZxmL2qXFLg31
```

## Step:-3 check balance

run the command:

`./build/token-cli key balance`

and enter the assetID of the token and output will be like:
```js 
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2aunvASmyp4SzxSxDzLN83wceU3HMJuTos8jeEp2L748YPyPmE
assetID (use TKN for native token): 2MgGttbdtX5t8dDETyFy57P1RdRz4wM1GsZzNVw1eNh5KTX6gZ
uri: http://127.0.0.1:51312/ext/bc/2aunvASmyp4SzxSxDzLN83wceU3HMJuTos8jeEp2L748YPyPmE
metadata: gold supply: 100000 warp: false
balance: 100000 2MgGttbdtX5t8dDETyFy57P1RdRz4wM1GsZzNVw1eNh5KTX6gZ
```


## Closing

run the command

`killall avalanche-network-runner`

This will close the blockchain we just deployed.


## Author
