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

<h2 id="addtokentowatchlist">Get Gas Price</h2>

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
<h2 id="addtokentowatchlist">Get Gas Price</h2>

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
