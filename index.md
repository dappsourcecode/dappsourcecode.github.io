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

<p>Repository: <a href="http://mellow.link/3c59D">https://github.com/0fajarpurnama0/0fajarpurnama0.github.io/blob/master/_posts/2022-03-01-web3-source-code-collection.md</a></p>
