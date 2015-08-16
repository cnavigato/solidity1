# Introducing: Roulette - Olympic

**Improvments**

- Better Pseudo Rand Algorithm.

- Lower transaction cost due to depositing Ether to the contract by approx. two order of magnitude.

- Bet on Dozen introduced

**Authenticity**

To check that the roulette.sol contract is actually the one on the ethereum blockchain, compile it with optimizations enabled, at https://chriseth.github.io/browser-solidity/ and compare the resulting Bytecode with the output of `web3.eth.getCode('0x580e45f982a0a01cfab3b36b3ec8df63fcc5d290');`
        
**Init Contract**

In geth console type: 

    var addressRoulette = '0x580e45f982a0a01cfab3b36b3ec8df63fcc5d290'
    
    var rouletteContract = web3.eth.contract([{"constant":false,"inputs":[],"name":"nonUpdatedBalance","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":true,"inputs":[],"name":"casinoBalance","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":false,"inputs":[{"name":"amount","type":"uint256"}],"name":"withdraw","outputs":[{"name":"","type":"bool"}],"type":"function"},{"constant":false,"inputs":[{"name":"number","type":"uint256"},{"name":"betSize","type":"uint256"}],"name":"betOnNumber","outputs":[{"name":"","type":"string"}],"type":"function"},{"constant":false,"inputs":[],"name":"kill","outputs":[],"type":"function"},{"constant":false,"inputs":[{"name":"dozen","type":"uint256"},{"name":"betSize","type":"uint256"}],"name":"betOnDozen","outputs":[{"name":"","type":"string"}],"type":"function"},{"constant":false,"inputs":[],"name":"updateBalance","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":true,"inputs":[],"name":"welcome","outputs":[{"name":"","type":"string"}],"type":"function"},{"constant":true,"inputs":[],"name":"userDepositedAmount","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":false,"inputs":[],"name":"deposit","outputs":[{"name":"","type":"bool"}],"type":"function"},{"constant":false,"inputs":[{"name":"color","type":"uint256"},{"name":"betSize","type":"uint256"}],"name":"betOnColor","outputs":[{"name":"","type":"string"}],"type":"function"},{"inputs":[],"type":"constructor"}]);
    
    var roulette = rouletteContract.at(addressRoulette);

  	roulette.welcome.call();
  
  	web3.fromWei(roulette.casinoBalance.call(), "ether");

**Deposit ETH**

In geth console type: 

    var amountDepo = 20; // In ETH bet 1 ETH and 100 ETH (Max deposit Limit 1000 ETH)
  
  	roulette.deposit.sendTransaction({from:eth.accounts[0], value: web3.toWei(amountDepo, 'ether'), gas: 400000});

assuming `eth.accounts[0]` is the desired account, otherwise change it.


**Withdraw ETH**

In geth console type: 
  
    var amountWith = 20; // In ETH bet 1 ETH and available Balance for User
  
  	roulette.withdraw.call(web3.toWei(amountWith, 'ether'), {from:eth.accounts[0], gas: 400000});

assuming `eth.accounts[0]` is the desired account, otherwise change it.


**Bet on Number**

In geth console type:

	var number = 17;

	var amount = 5; // In ETH bet 0.1 ETH and 10 ETH

	roulette.betOnNumber.sendTransaction(number, web3.toWei(amount,'ether'), {from:eth.accounts[0], gas: 400000});

	web3.fromWei(roulette.nonUpdatedBalance.call({from:eth.accounts[0]}),'ether');

	roulette.updateBalance.sendTransaction({from:eth.accounts[0], gas: 400000}); // Wait one Block before use

assuming `eth.accounts[0]` is the desired account, otherwise change it.


**Bet on Dozen**

In geth console type:

	var dozen = 0; // '0' = Bet on 1-12, '1' = Bet on 13-24 or '2' = Bet on 25-36
	
	var amount = 5; // In ETH bet 0.1 ETH and 100 ETH

	roulette.betOnDozen.sendTransaction(dozen, web3.toWei(amount,'ether'), {from:eth.accounts[3], gas: 400000});
	
	web3.fromWei(roulette.nonUpdatedBalance.call({from:eth.accounts[0]}),'ether');

	roulette.updateBalance.sendTransaction({from:eth.accounts[0], gas: 400000}); // Wait one Block before use
	

assuming `eth.accounts[0]` is the desired account, otherwise change it.

**Bet on Color** 

In geth console type:

	var color = 0; // '0' = red, '1' = black

	var amount = 5; // In ETH bet 0.1 ETH and 100 ETH

	roulette.betOnColor.sendTransaction(color, web3.toWei(amount,'ether'), {from:eth.accounts[3], gas: 400000});

	web3.fromWei(roulette.nonUpdatedBalance.call({from:eth.accounts[0]}),'ether');

  roulette.updateBalance.sendTransaction({from:eth.accounts[0], gas: 400000}); // Wait one Block before use

assuming `eth.accounts[0]` is the desired account, otherwise change it.

**Always process Bet after Betting and waiting for one Block to pass**

In geth console type:

	roulette.updateBalance.sendTransaction({from:eth.accounts[0], gas: 400000});

assuming `eth.accounts[0]` is the desired account, otherwise change it.

**Disclaimer**

NO WARRANTY

THE PROGRAM-CONTRACT IS DISTRIBUTED IN THE HOPE THAT IT WILL BE USEFUL, BUT WITHOUT ANY WARRANTY. IT IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM-CONTRACT IS WITH YOU. SHOULD THE PROGRAM-CONTRACT PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW THE AUTHOR WILL BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE THE PROGRAM-CONTRACT (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM-CONTRACT TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF THE AUTHOR HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES. 
