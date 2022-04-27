<h2 id="connectwallet">Connect Wallet</h2>
<button onclick="connect()" id="connect">Connect</button>
<p>Account: <span id="showAccount"></span></p>

<script>
async function connect() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  document.getElementById("showAccount").innerHTML = account;
  
  if(ethereum.isConnected()){
  	document.getElementById("connect").innerHTML = "connected";
  }
}
</script>

```html
<h2 id="connectwallet">Connect Wallet</h2>
<button onclick="connect()" id="connect">Connect</button>
<p>Account: <span id="showAccount"></span></p>

<script>
async function connect() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  document.getElementById("showAccount").innerHTML = account;
  
  if(ethereum.isConnected()){
  	document.getElementById("connect").innerHTML = "connected";
  }
}
</script>
```

<br />

<h2 id="onaccountchange">On Account Change</h2>
<button onclick="connectchange()" id="connectchange">Connect</button>
<p>Account: <span id="showAccountchange"></span></p>

<script>
async function connectchange() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  document.getElementById("showAccountchange").innerHTML = account;
  
  if(ethereum.isConnected()){
  	document.getElementById("connectchange").innerHTML = "connected";
  }
}

ethereum.on('accountsChanged', function (accounts) {
  connectchange();
});
</script>

```html
<button onclick="connect()" id="connect">Connect</button>
<p>Account: <span id="showAccount"></span></p>

<script>
async function connect() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  document.getElementById("showAccount").innerHTML = account;
  
  if(ethereum.isConnected()){
  	document.getElementById("connect").innerHTML = "connected";
  }
}

ethereum.on('accountsChanged', function (accounts) {
  connect();
});
</script>
```

<br />

<h2 id="signpersonalmessage">Sign Personal Message</h2>
<button onclick="connect_personal_sign()" id="connect-personal-sign">Connect</button>
<p>Account: <span id="showAccount-personal-sign"></span></p>
<p>Personal Signature: <span id="personal-sign"></span></p>

<script>
async function connect_personal_sign() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  const message = "Hello from signer!";
  const signature = await ethereum.request({ method: 'personal_sign', params: [ message, account ] });
  
  if(ethereum.isConnected()){
    document.getElementById("showAccount-personal-sign").innerHTML = account;
    document.getElementById("connect-personal-sign").innerHTML = "connected";
    document.getElementById("personal-sign").innerHTML = signature;
  }
}

ethereum.on('accountsChanged', function (accounts) {
  connect_personal_sign();
});
</script>

```html
<button onclick="connect()" id="connect">Connect</button>
<p>Account: <span id="showAccount"></span></p>
<p>Personal Signature: <span id="personal-sign"></span></p>

<script>
async function connect() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  const message = "Hello from signer!";
  const signature = await ethereum.request({ method: 'personal_sign', params: [ message, account ] });
  
  if(ethereum.isConnected()){
    document.getElementById("showAccount").innerHTML = account;
    document.getElementById("connect").innerHTML = "connected";
    document.getElementById("personal-sign").innerHTML = signature;
  }
}

ethereum.on('accountsChanged', function (accounts) {
  connect();
});
</script>
```

<br />

<h2 id="getnativeassetbalance">Get Native Asset Balance</h2>

<button onclick="getnativebalance()">Connect</button>
<p>Native Balance Hexadecimal: <span id="native-balance-hexadecimal"></span></p>
<p>Native Balance 18 Decimals: <span id="native-balance-18decimal"></span></p>
<p>Native Balance: <span id="native-balance"></span></p>

<script>
async function getnativebalance() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  const balance = await ethereum.request({ method: 'eth_getBalance', params: [account, "latest"] });
  document.getElementById("native-balance-hexadecimal").innerHTML = balance;
  document.getElementById("native-balance-18decimal").innerHTML = parseInt(balance, 16);
  document.getElementById("native-balance").innerHTML = parseInt(balance, 16)/Math.pow(10, 18);
}
</script>

```html
<h2 id="getnativeassetbalance">Get Native Asset Balance</h2>

<button onclick="getnativebalance()">Connect</button>
<p>Native Balance Hexadecimal: <span id="native-balance-hexadecimal"></span></p>
<p>Native Balance 18 Decimals: <span id="native-balance-18decimal"></span></p>
<p>Native Balance: <span id="native-balance"></span></p>

<script>
async function getnativebalance() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  const balance = await ethereum.request({ method: 'eth_getBalance', params: [account, "latest"] });
  document.getElementById("native-balance-hexadecimal").innerHTML = balance;
  document.getElementById("native-balance-18decimal").innerHTML = parseInt(balance, 16);
  document.getElementById("native-balance").innerHTML = parseInt(balance, 16)/Math.pow(10, 18);
}
</script>
```

<br />

<h2 id="getgasprice">Get Gas Price</h2>

<button onclick="getgasprice()">Get⛽</button>
<p>Gas Price Hexadecimal: <span id="gas-price-hexadecimal"></span></p>
<p>Gas Price Wei: <span id="gas-price-wei"></span></p>
<p>Gas Price GWei: <span id="gas-price-gwei"></span></p>
<p>Gas Price Native Asset: <span id="gas-price"></span></p>

<script>
async function getgasprice() {
  let gasprice = await ethereum.request({method: 'eth_gasPrice', params: []});
  document.getElementById("gas-price-hexadecimal").innerHTML = gasprice;
  document.getElementById("gas-price-wei").innerHTML = parseInt(gasprice, 16);
  document.getElementById("gas-price-gwei").innerHTML = parseInt(gasprice, 16)/Math.pow(10, 9);
  document.getElementById("gas-price").innerHTML = parseInt(gasprice, 16)/Math.pow(10, 18);
}
</script>

```html
<h2 id="getgasprice">Get Gas Price</h2>

<button onclick="getgasprice()">Get⛽</button>
<p>Gas Price Hexadecimal: <span id="gas-price-hexadecimal"></span></p>
<p>Gas Price Wei: <span id="gas-price-wei"></span></p>
<p>Gas Price GWei: <span id="gas-price-gwei"></span></p>
<p>Gas Price Native Asset: <span id="gas-price"></span></p>

<script>
async function getgasprice() {
  let gasprice = await ethereum.request({method: 'eth_gasPrice', params: []});
  document.getElementById("gas-price-hexadecimal").innerHTML = gasprice;
  document.getElementById("gas-price-wei").innerHTML = parseInt(gasprice, 16);
  document.getElementById("gas-price-gwei").innerHTML = parseInt(gasprice, 16)/Math.pow(10, 9);
  document.getElementById("gas-price").innerHTML = parseInt(gasprice, 16)/Math.pow(10, 18);
}
</script>
```

<br />

<button onclick="estgaslimit()">Estimate ⛽ Limit</button>
<p>Recipient: <input type="text" id="recipient" name="recipient" value="0x6F937dC8f92E6b43f0853960b778BAF2D93022C1"/></p>
<p>Amount: <input type="number" id="amount" name="amount" value="1"/></p>
<p>Gas Limit Hexadecimal: <span id="gas-limit-hexadecimal"></span></p>
<p>Gas Limit: <span id="gas-limit"></span></p>

<script>
async function estgaslimit() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  
  document.getElementById("recipient").addEventListener("change", changerecipientinput);

  let recipient = document.getElementById("recipient").value;

  function changerecipientinput() {
      recipient = document.getElementById("recipient").value;
  }

  document.getElementById("amount").addEventListener("change", changeamountinput);

  let amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);
  
  function changeamountinput() {
	amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);
}
  
  let params = [{"from": account, "to": recipient, "value": amount}]
  
  try {
  	let gaslimit = await ethereum.request({method: 'eth_estimateGas', params});
  	document.getElementById("gas-limit-hexadecimal").innerHTML = gaslimit;
  	document.getElementById("gas-limit").innerHTML = parseInt(gaslimit, 16);
  } catch(err) {
 	document.getElementById("gas-limit-hexadecimal").innerHTML = err.message;
  }
}
</script>

```html
<button onclick="estgaslimit()">Estimate ⛽ Limit</button>
<p>Recipient: <input type="text" id="recipient" name="recipient" value="0x6F937dC8f92E6b43f0853960b778BAF2D93022C1"/></p>
<p>Amount: <input type="number" id="amount" name="amount" value="1"/></p>
<p>Gas Limit Hexadecimal: <span id="gas-limit-hexadecimal"></span></p>
<p>Gas Limit: <span id="gas-limit"></span></p>

<script>
async function estgaslimit() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  const account = accounts[0];
  
  document.getElementById("recipient").addEventListener("change", changerecipientinput);

  let recipient = document.getElementById("recipient").value;

  function changerecipientinput() {
      recipient = document.getElementById("recipient").value;
  }

  document.getElementById("amount").addEventListener("change", changeamountinput);

  let amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);
  
  function changeamountinput() {
	amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);
}
  
  let params = [{"from": account, "to": recipient, "value": amount}]
  
  try {
  	let gaslimit = await ethereum.request({method: 'eth_estimateGas', params});
  	document.getElementById("gas-limit-hexadecimal").innerHTML = gaslimit;
  	document.getElementById("gas-limit").innerHTML = parseInt(gaslimit, 16);
  } catch(err) {
 	document.getElementById("gas-limit-hexadecimal").innerHTML = err.message;
  }
}
</script>
```

<br />
<h2 id="sendnativeasset">Send Native Asset</h2>
<button onclick="sendeth()">Send Native Asset</button>
<br />
Recipient: <input type="text" id="recipient1" name="recipient1" value="0x6F937dC8f92E6b43f0853960b778BAF2D93022C1"/>
<br />
Amount: <input type="number" id="amount1" name="amount1" value="0"/>
<br />

<script>
document.getElementById("recipient1").addEventListener("change", changerecipient1input);

let recipient1 = document.getElementById("recipient1").value;

function changerecipient1input() {
	recipient1 = document.getElementById("recipient1").value;
}

document.getElementById("amount1").addEventListener("change", changeamount1input);

let amount1 = "0x" + (parseFloat(document.getElementById("amount1").value)*10 ** 18).toString(16);

function changeamount1input() {
	amount1 = "0x" + (parseFloat(document.getElementById("amount1").value)*10 ** 18).toString(16);
}

//Sending Ethereum to an address
async function sendeth() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  
  params = [
        {
          from: accounts[0],
          to: recipient1,
          value: amount1,
          gasPrice: await ethereum.request({method: 'eth_gasPrice', params: []}),
          gas: '' //auto,
        },
      ];
  
  ethereum
    .request({
      method: 'eth_sendTransaction',
      params,
    })
    .then((txHash) => console.log(txHash))
    .catch((error) => console.error);
}
</script>

```html
<button onclick="sendeth()">Send Native Asset</button>
<br />
Recipient: <input type="text" id="recipient" name="recipient" value="0x6F937dC8f92E6b43f0853960b778BAF2D93022C1"/>
<br />
Amount: <input type="number" id="amount" name="amount" value="0"/>
<br />

<script>
document.getElementById("recipient").addEventListener("change", changerecipientinput);

let recipient = document.getElementById("recipient").value;

function changerecipientinput() {
	recipient = document.getElementById("recipient").value;
}

document.getElementById("amount").addEventListener("change", changeamountinput);

let amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);

function changeamountinput() {
	amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);
}

//Sending Ethereum to an address
async function sendeth() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  
  params = [
        {
          from: accounts[0],
          to: recipient,
          value: amount,
          gasPrice: await ethereum.request({method: 'eth_gasPrice', params: []}),
          gas: '' //auto,
        },
      ];
  
  ethereum
    .request({
      method: 'eth_sendTransaction',
      params,
    })
    .then((txHash) => console.log(txHash))
    .catch((error) => console.error);
}
</script>
```
<br />

<h2 id="sendmessagetoanevmaddress">Send Message to an EVM Address</h2>
<button onclick="sendmsg()">Send Message</button>
<br />
Recipient: <input type="text" id="recipientmsg" name="recipientmsg" value="0x6F937dC8f92E6b43f0853960b778BAF2D93022C1"/>
<br />
<textarea id="message" rows="4" cols="50" name="message" value="Enter Message">Enter Message</textarea>
<br />
Amount: <input type="number" id="amountmsg" name="amountmsg" value="0"/>
<br />

<script>
document.getElementById("recipientmsg").addEventListener("change", changerecipientmsginput);

let recipient = document.getElementById("recipientmsg").value;

function changerecipientmsginput() {
	recipient = document.getElementById("recipientmsg").value;
}

function ascii_to_hex(str) {
    var arr1 = [];
    for (var n = 0, l = str.length; n < l; n ++) {
    	var hex = Number(str.charCodeAt(n)).toString(16);
        arr1.push(hex);
    }
    return arr1.join('');
}

document.getElementById("message").addEventListener("change", changemessageinput);

let message = "0x" + ascii_to_hex(document.getElementById("message").value);

function changemessageinput() {
	message = "0x" + ascii_to_hex(document.getElementById("message").value);
	console.log(message);
}

document.getElementById("amountmsg").addEventListener("change", changeamountmsginput);

let amount = "0x" + (parseFloat(document.getElementById("amountmsg").value)*10 ** 18).toString(16);

function changeamountmsginput() {
	amount = "0x" + (parseFloat(document.getElementById("amountmsg").value)*10 ** 18).toString(16);
}

//Sending Ethereum to an address
async function sendmsg() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  
  params = [
        {
          from: accounts[0],
          to: recipient,
          value: amount,
          gasPrice: await ethereum.request({method: 'eth_gasPrice', params: []}),
          gas: '', //auto
          data: message
        },
      ];
  
  ethereum
    .request({
      method: 'eth_sendTransaction',
      params,
    })
    .then((txHash) => console.log(txHash))
    .catch((error) => console.error);
}
</script>

```html
<button onclick="sendmsg()">Send Message</button>
<br />
Recipient: <input type="text" id="recipient" name="recipient" value="0x6F937dC8f92E6b43f0853960b778BAF2D93022C1"/>
<br />
<textarea id="message" rows="4" cols="50" name="message" value="Enter Message">Enter Message</textarea>
<br />
Amount: <input type="number" id="amount" name="amount" value="0"/>
<br />

<script>
document.getElementById("recipient").addEventListener("change", changerecipientinput);

let recipient = document.getElementById("recipient").value;

function changerecipientinput() {
	recipient = document.getElementById("recipient").value;
}

function ascii_to_hex(str) {
    var arr1 = [];
    for (var n = 0, l = str.length; n < l; n ++) 
        {
        var hex = Number(str.charCodeAt(n)).toString(16);
        arr1.push(hex);
        }
    return arr1.join('');
}

document.getElementById("message").addEventListener("change", changemessageinput);

let message = "0x" + ascii_to_hex(document.getElementById("message").value);

function changemessageinput() {
	message = "0x" + ascii_to_hex(document.getElementById("message").value);
    console.log(message);
}

document.getElementById("amount").addEventListener("change", changeamountinput);

let amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);

function changeamountinput() {
	amount = "0x" + (parseFloat(document.getElementById("amount").value)*10 ** 18).toString(16);
}

//Sending Ethereum to an address
async function sendmsg() {
  const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
  
  params = [
        {
          from: accounts[0],
          to: recipient,
          value: amount,
          gasPrice: await ethereum.request({method: 'eth_gasPrice', params: []}),
          gas: '', //auto
          data: message
        },
      ];
  
  ethereum
    .request({
      method: 'eth_sendTransaction',
      params,
    })
    .then((txHash) => console.log(txHash))
    .catch((error) => console.error);
}
</script>
```

<br />

<h2 id="addcustomnetwork">Add Custom Network</h2>

<button onclick="addchainmetamask()">Add<img style="height: 1em;" src="https://raw.githubusercontent.com/MetaMask/brand-resources/master/SVG/metamask-fox.svg"/></button>

<script>
async function addchainmetamask() {
  await ethereum.request({
    method: 'wallet_addEthereumChain',
    params: [{
      chainId: '0x1e',
      chainName: 'RSK Mainnet',
      nativeCurrency: {
        name: 'RSK BTC',
        symbol: 'RBTC',
        decimals: 18
      },
      rpcUrls: ['https://public-node.rsk.co'],
      iconUrls: ["https://www.rsk.co/img/rsk_logo.svg"],
      blockExplorerUrls: ['https://explorer.rsk.co']
  	}]
  });
}
</script>

```html
<h2 id="addcustomnetwork">Add Custom Network</h2>

<button onclick="addchainmetamask()">Add<img style="height: 1em;" src="https://raw.githubusercontent.com/MetaMask/brand-resources/master/SVG/metamask-fox.svg"/></button>

<script>
async function addchainmetamask() {
  await ethereum.request({
    method: 'wallet_addEthereumChain',
    params: [{
      chainId: '0x1e',
      chainName: 'RSK Mainnet',
      nativeCurrency: {
        name: 'RSK BTC',
        symbol: 'RBTC',
        decimals: 18
      },
      rpcUrls: ['https://public-node.rsk.co'],
      iconUrls: ["https://www.rsk.co/img/rsk_logo.svg"],
      blockExplorerUrls: ['https://explorer.rsk.co']
  	}]
  });
}
</script>
```
<br />

<button onclick="changenetwork()">Change Network</button>
	
<script>
async function changenetwork() {
  try {
    await ethereum.request({
      method: 'wallet_switchEthereumChain',
      params: [{ chainId: '0x38' }],
    });
  } catch (switchError) {
    // This error code indicates that the chain has not been added to MetaMask.
    if (switchError.code === 4902) {
      try {
        await ethereum.request({
          method: 'wallet_addEthereumChain',
          params: [
            {
              chainId: '0x38',
              chainName: 'Binance Smart Chain Main Network',
              rpcUrls: ['https://rpc.ankr.com/bsc', 'https://bsc-dataseed.binance.org/'] /* ... */,
            },
          ],
        });
      } catch (addError) {
        // handle "add" error
      }
    }
    // handle other "switch" errors
  }
}
</script>
	
```html
<button onclick="changenetwork()">Change Network</button>
	
<script>
async function changenetwork() {
  try {
    await ethereum.request({
      method: 'wallet_switchEthereumChain',
      params: [{ chainId: '0x38' }],
    });
  } catch (switchError) {
    // This error code indicates that the chain has not been added to MetaMask.
    if (switchError.code === 4902) {
      try {
        await ethereum.request({
          method: 'wallet_addEthereumChain',
          params: [
            {
              chainId: '0x38',
              chainName: 'Binance Smart Chain Main Network',
              rpcUrls: ['https://rpc.ankr.com/bsc', 'https://bsc-dataseed.binance.org/'] /* ... */,
            },
          ],
        });
      } catch (addError) {
        // handle "add" error
      }
    }
    // handle other "switch" errors
  }
}
</script>
```
<br />

<h2 id="addtokentowatchlist">Add Token to Watchlist</h2>

<button onclick="watchasset()">Add<img style="height: 1em;" src="https://raw.githubusercontent.com/MetaMask/brand-resources/master/SVG/metamask-fox.svg"/><img style="height: 1em;" src="https://github.com/Uniswap/docs/raw/main/static/img/favicon.png"/></button>

<script>
async function watchasset() {
  await ethereum.request({
    method: 'wallet_watchAsset',
    params: {
      type: 'ERC20',
      options: {
        address: '0x1f9840a85d5aF5bf1D1762F925BDADdC4201F984',
        symbol: 'UNI',
        decimals: 18,
        image: 'https://github.com/Uniswap/docs/raw/main/static/img/favicon.png',
      },
    },
  })
}
</script>

```html
<h2 id="addtokentowatchlist">Add Token to Watchlist</h2>

<button onclick="watchasset()">Add<img style="height: 1em;" src="https://raw.githubusercontent.com/MetaMask/brand-resources/master/SVG/metamask-fox.svg"/><img style="height: 1em;" src="https://github.com/Uniswap/docs/raw/main/static/img/favicon.png"/></button>

<script>
async function watchasset() {
  await ethereum.request({
    method: 'wallet_watchAsset',
    params: {
      type: 'ERC20',
      options: {
        address: '0x1f9840a85d5aF5bf1D1762F925BDADdC4201F984',
        symbol: 'UNI',
        decimals: 18,
        image: 'https://github.com/Uniswap/docs/raw/main/static/img/favicon.png',
      },
    },
  })
}
</script>
```

<br />

<h2 id="getspecifictokenbalance">Get Specific Token Balance</h2>
<p>Here I use <a href="https://docs.ethers.io/v5/api/contract/example/">Ethers library</a>, anyone knows how to use pure Ethereum RPC?</p>

<button onclick="gettokenbalance()">Get<img style="height: 1em;" src="https://raw.githubusercontent.com/MetaMask/brand-resources/master/SVG/metamask-fox.svg"/><img style="height: 1em;" src="https://avatars.githubusercontent.com/u/66380691?s=48&v=4"/></button>
<p>ERC20 Statera Balance 18 Decimals: <span id="statera-balance-18decimals"></span></p>

<p>ERC20 Statera Balance: <span id="statera-balance"></span></p>

<script src="https://cdn.ethers.io/lib/ethers-5.2.umd.min.js"
        type="application/javascript"></script>
        
<script>
async function gettokenbalance() {
	const provider = new ethers.providers.Web3Provider(window.ethereum);
    await provider.send("eth_requestAccounts", []);
    const signer = provider.getSigner();
    
    const minabi = [
    // Read-Only Functions
    "function balanceOf(address owner) view returns (uint256)",
    "function decimals() view returns (uint8)",
    "function symbol() view returns (string)",

    // Authenticated Functions
    "function transfer(address to, uint amount) returns (bool)",

    // Events
    "event Transfer(address indexed from, address indexed to, uint amount)"
	];
    
    const contract_address = "0xa7DE087329BFcda5639247F96140f9DAbe3DeED1";
    
    const erc20 = new ethers.Contract(contract_address, minabi, provider);
    
    const getBalance = await erc20.balanceOf(signer.getAddress());
    
    document.getElementById("statera-balance-18decimals").innerHTML = getBalance;
    document.getElementById("statera-balance").innerHTML = getBalance/Math.pow(10, 18);
}
</script>

```html
<button onclick="gettokenbalance()">Get<img style="height: 1em;" src="https://raw.githubusercontent.com/MetaMask/brand-resources/master/SVG/metamask-fox.svg"/><img style="height: 1em;" src="https://avatars.githubusercontent.com/u/66380691?s=48&v=4"/></button>
<p>ERC20 Statera Balance 18 Decimals: <span id="statera-balance-18decimals"></span></p>

<p>ERC20 Statera Balance: <span id="statera-balance"></span></p>

<script src="https://cdn.ethers.io/lib/ethers-5.2.umd.min.js"
        type="application/javascript"></script>
        
<script>
async function gettokenbalance() {
	const provider = new ethers.providers.Web3Provider(window.ethereum);
    await provider.send("eth_requestAccounts", []);
    const signer = provider.getSigner();
    
    const minabi = [
    // Read-Only Functions
    "function balanceOf(address owner) view returns (uint256)",
    "function decimals() view returns (uint8)",
    "function symbol() view returns (string)",

    // Authenticated Functions
    "function transfer(address to, uint amount) returns (bool)",

    // Events
    "event Transfer(address indexed from, address indexed to, uint amount)"
	];
    
    const contract_address = "0xa7DE087329BFcda5639247F96140f9DAbe3DeED1";
    
    const erc20 = new ethers.Contract(contract_address, minabi, provider);
    
    const getBalance = await erc20.balanceOf(signer.getAddress());
    
    document.getElementById("statera-balance-18decimals").innerHTML = getBalance;
    document.getElementById("statera-balance").innerHTML = getBalance/Math.pow(10, 18);
}
</script>
```

<br />

<h2>Get Balances on Multiple Chains Using a Single Web3 Wallet</h2>
	
<button onclick="gettokendexholders()">Get 0FP0EXP Token DEX Holders</button>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/825/small/bnb-icon2_2x.png?1644979850" alt="Binance Smart Chain Logo"/>BSC <img style="height: 1em" src="https://assets.coingecko.com/coins/images/12632/small/pancakeswap-cake-logo_%281%29.png?1629359065" alt="Pancake Swap Logo"/><a href="https://pancakeswap.finance/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Pancake Swap:</a> <span id="pancake-swap-holder"></span></p>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/4713/small/matic-token-icon.png?1624446912" alt="Polygon Logo"/>Polygon <img style="height: 1em" src="https://assets.coingecko.com/coins/images/13970/small/1_pOU6pBMEmiL-ZJVb0CYRjQ.png?1613386659" alt="Quick Swap Logo"/><a href="https://quickswap.exchange/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Quick Swap</a>: <span id="quick-swap-holder"></span></p>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/12559/small/coin-round-red.png?1604021818" alt="Avalanche Logo"/>Avalanche <img style="height: 1em" src="https://assets.coingecko.com/coins/images/14023/small/mXGnm3Eo_400x400.jpg?1644478963" alt="Pangolin DEX Logo"/><a href="https://app.pangolin.exchange/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Pangolin DEX</a>: <span id="pangolin-dex-holder"></span></p>
<p><img style="height: 1em" src="https://bridge.arbitrum.io/images/Arbitrum_Symbol_-_Full_color_-_White_background.svg" alt="Arbitrum Logo"/>Arbitrum <img style="height: 1em" src="https://assets.coingecko.com/coins/images/12271/small/512x512_Logo_no_chop.png?1606986688" alt="Sushi Swap Logo"/><a href="https://arbitrum.sushi.com/en/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Sushi Swap</a>: <span id="sushi-swap-holder"></span></p>
<p><img style="height: 1em" src="https://www.gitbook.com/cdn-cgi/image/width=40,height=40,fit=contain,dpr=1,format=auto/https%3A%2F%2F1384322056-files.gitbook.io%2F~%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FHVry7OTN1UZzjjhTeYXg%252Ficon%252FbEcQNGd1oiAjvoZ28Ek6%252FSymbol_Primary.png%3Falt%3Dmedia%26token%3Da606230a-2997-49ff-84b0-9797da6bb10a" alt="Thunder Core Logo"/><a href="https://ttswap.space/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">TT Swap</a>: <span id="tt-swap-holder"></span></p>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/5795/small/3218.png?1604798557" alt="Energi Logo"/><a href="https://app.energiswap.exchange/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Energi Swap</a>: <span id="energi-swap-holder"></span></p>

<script>
function gettokendexholders() {
  const evmrpcjson = new XMLHttpRequest();
  evmrpcjson.onload = async function() {
    const chains = JSON.parse(this.responseText);
    await changenetworkandget(chains['bscmn'], 'pancake-swap-holder', '0x4527094fb24bb1642cf52386af4842be47031da1');
    await changenetworkandget(chains['maticmn'], 'quick-swap-holder', '0x60b32bdc995d4ad49ddcbb0728928ee115c3541b');
    await changenetworkandget(chains['avaxccmn'], 'pangolin-dex-holder', '0x23babaa2fc7170d741f5183c9689c70b28bc91fe');
    await changenetworkandget(chains['arbtrmmn'], 'sushi-swap-holder', '0xbc443f7212dc071ae71c6eff2b779fa139852a04');
    await changenetworkandget(chains['ttmn'], 'tt-swap-holder', '0x07a2701342444108ff30fd973ee4e4854bb085bb');
    await changenetworkandget(chains['energimn'], 'energi-swap-holder', '0x3998a06CDA1c57318C7aa430f42468a56081d060');
  }
  evmrpcjson.open("GET", "https://0fajarpurnama0.github.io/assets/json/evmrpc.json");
  evmrpcjson.send();
}

async function changenetworkandget(chain, dex, holder) {
  try {
    await ethereum.request({
      method: 'wallet_switchEthereumChain',
      params: [{ chainId: chain['params'][0].chainId }],
    });
  } catch (switchError) {
    // This error code indicates that the chain has not been added to MetaMask.
    if (switchError.code === 4902) {
      try {
        let params = chain['params'];
        await ethereum.request({
          method: 'wallet_addEthereumChain',
          params,
        });
      } catch (addError) {
        // handle "add" error
      }
    }
    // handle other "switch" errors
  }
  getdextokenbalance(dex, holder);
}

async function getdextokenbalance(dex, holder) {
	const provider = new ethers.providers.Web3Provider(window.ethereum);
    await provider.send("eth_requestAccounts", []);
    const signer = provider.getSigner();
    
    const minabi = [
    // Read-Only Functions
    "function balanceOf(address owner) view returns (uint256)",
    "function decimals() view returns (uint8)",
    "function symbol() view returns (string)",

    // Authenticated Functions
    "function transfer(address to, uint amount) returns (bool)",

    // Events
    "event Transfer(address indexed from, address indexed to, uint amount)"
	];
    
    const contract_address = "0x99a828fe0c1d68d9aebbb8651cdbdbac65dc6207";
    
    const erc20 = new ethers.Contract(contract_address, minabi, provider);
    
    const getBalance = await erc20.balanceOf(holder);
    
    document.getElementById(dex).innerHTML = getBalance/10**18;
}
</script>

```html
<button onclick="gettokendexholders()">Get 0FP0EXP Token DEX Holders</button>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/825/small/bnb-icon2_2x.png?1644979850" alt="Binance Smart Chain Logo"/>BSC <img style="height: 1em" src="https://assets.coingecko.com/coins/images/12632/small/pancakeswap-cake-logo_%281%29.png?1629359065" alt="Pancake Swap Logo"/><a href="https://pancakeswap.finance/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Pancake Swap:</a> <span id="pancake-swap-holder"></span></p>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/4713/small/matic-token-icon.png?1624446912" alt="Polygon Logo"/>Polygon <img style="height: 1em" src="https://assets.coingecko.com/coins/images/13970/small/1_pOU6pBMEmiL-ZJVb0CYRjQ.png?1613386659" alt="Quick Swap Logo"/><a href="https://quickswap.exchange/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Quick Swap</a>: <span id="quick-swap-holder"></span></p>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/12559/small/coin-round-red.png?1604021818" alt="Avalanche Logo"/>Avalanche <img style="height: 1em" src="https://assets.coingecko.com/coins/images/14023/small/mXGnm3Eo_400x400.jpg?1644478963" alt="Pangolin DEX Logo"/><a href="https://app.pangolin.exchange/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Pangolin DEX</a>: <span id="pangolin-dex-holder"></span></p>
<p><img style="height: 1em" src="https://bridge.arbitrum.io/images/Arbitrum_Symbol_-_Full_color_-_White_background.svg" alt="Arbitrum Logo"/>Arbitrum <img style="height: 1em" src="https://assets.coingecko.com/coins/images/12271/small/512x512_Logo_no_chop.png?1606986688" alt="Sushi Swap Logo"/><a href="https://arbitrum.sushi.com/en/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Sushi Swap</a>: <span id="sushi-swap-holder"></span></p>
<p><img style="height: 1em" src="https://www.gitbook.com/cdn-cgi/image/width=40,height=40,fit=contain,dpr=1,format=auto/https%3A%2F%2F1384322056-files.gitbook.io%2F~%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FHVry7OTN1UZzjjhTeYXg%252Ficon%252FbEcQNGd1oiAjvoZ28Ek6%252FSymbol_Primary.png%3Falt%3Dmedia%26token%3Da606230a-2997-49ff-84b0-9797da6bb10a" alt="Thunder Core Logo"/><a href="https://ttswap.space/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">TT Swap</a>: <span id="tt-swap-holder"></span></p>
<p><img style="height: 1em" src="https://assets.coingecko.com/coins/images/5795/small/3218.png?1604798557" alt="Energi Logo"/><a href="https://app.energiswap.exchange/#/swap?outputCurrency=0x99a828fe0C1D68D9aeBBB8651CDBDbac65dc6207">Energi Swap</a>: <span id="energi-swap-holder"></span></p>

<script src="https://cdn.ethers.io/lib/ethers-5.2.umd.min.js" type="application/javascript"></script>
	
<script>
function gettokendexholders() {
  const evmrpcjson = new XMLHttpRequest();
  evmrpcjson.onload = async function() {
    const chains = JSON.parse(this.responseText);
    await changenetworkandget(chains['bscmn'], 'pancake-swap-holder', '0x4527094fb24bb1642cf52386af4842be47031da1');
    await changenetworkandget(chains['maticmn'], 'quick-swap-holder', '0x60b32bdc995d4ad49ddcbb0728928ee115c3541b');
    await changenetworkandget(chains['avaxccmn'], 'pangolin-dex-holder', '0x23babaa2fc7170d741f5183c9689c70b28bc91fe');
    await changenetworkandget(chains['arbtrmmn'], 'sushi-swap-holder', '0xbc443f7212dc071ae71c6eff2b779fa139852a04');
    await changenetworkandget(chains['ttmn'], 'tt-swap-holder', '0x07a2701342444108ff30fd973ee4e4854bb085bb');
    await changenetworkandget(chains['energimn'], 'energi-swap-holder', '0x3998a06CDA1c57318C7aa430f42468a56081d060');
  }
  evmrpcjson.open("GET", "https://0fajarpurnama0.github.io/assets/json/evmrpc.json");
  evmrpcjson.send();
}

async function changenetworkandget(chain, dex, holder) {
  try {
    await ethereum.request({
      method: 'wallet_switchEthereumChain',
      params: [{ chainId: chain['params'][0].chainId }],
    });
  } catch (switchError) {
    // This error code indicates that the chain has not been added to MetaMask.
    if (switchError.code === 4902) {
      try {
        let params = chain['params'];
        await ethereum.request({
          method: 'wallet_addEthereumChain',
          params,
        });
      } catch (addError) {
        // handle "add" error
      }
    }
    // handle other "switch" errors
  }
  getdextokenbalance(dex, holder);
}

async function getdextokenbalance(dex, holder) {
	const provider = new ethers.providers.Web3Provider(window.ethereum);
    await provider.send("eth_requestAccounts", []);
    const signer = provider.getSigner();
    
    const minabi = [
    // Read-Only Functions
    "function balanceOf(address owner) view returns (uint256)",
    "function decimals() view returns (uint8)",
    "function symbol() view returns (string)",

    // Authenticated Functions
    "function transfer(address to, uint amount) returns (bool)",

    // Events
    "event Transfer(address indexed from, address indexed to, uint amount)"
	];
    
    const contract_address = "0x99a828fe0c1d68d9aebbb8651cdbdbac65dc6207";
    
    const erc20 = new ethers.Contract(contract_address, minabi, provider);
    
    const getBalance = await erc20.balanceOf(holder);
    
    document.getElementById(dex).innerHTML = getBalance/10**18;
}
</script>
```
<br />
	
<p>Compilation Repository: <a href="http://mellow.link/3c59D">https://github.com/0fajarpurnama0/0fajarpurnama0.github.io/blob/master/_posts/2022-03-01-web3-source-code-collection.md</a></p>
