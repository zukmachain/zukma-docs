# <b>Waffle Tool</b>
---

 [Waffle](https://www.getwaffle.io/) is a popular development framework for testing Solidity smart contracts. Since Zukma is Ethereum compatible, with a few lines of extra configuration, you can use Zukma as you usually would with Ethereum to develop on Zukma.

 **Configure Waffle to Connect to Zukma**

 Assuming you already have a JavaScript project, install Waffle:

 ```
 npm install ethereum-waffle
 ```

 To configure Waffle to run tests against a Zukma development node or the Zukma Testnet, within your tests create a custom provider and add network configurations:

 **Javascript**

 ```javascript
 describe ('Test Contract', () => { 
     // Use custom provider to connect to Zukma or Edgeware development node const 
     ZukmaProvider = new ethers.providers.JsonRpcProvider(('https://rpc.zukma.org') 
     const devProvider = new ethers.providers.JsonRpcProvider('http://localhost:9933/'); })
 ```

 <br></br>

<p align=right> Written by Zukma Team </p>
