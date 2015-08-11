# Introducing: Roulette

**Authenticity**

To check that the highstakespyramid.sol contract is actually the one on the ethereum blockchain, compile it with optimizations enabled, at https://chriseth.github.io/browser-solidity/ and compare the resulting Bytecode with the output of web3.eth.getCode('0x5fe5b7546d1628f7348b023a0393de1fc825a4fd');
        
**Init Contract**

In geth console type: 

var rouletteContract = web3.eth.contract([{"constant":true,"inputs":[],"name":"casinoBalance","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":false,"inputs":[],"name":"kill","outputs":[],"type":"function"},{"constant":false,"inputs":[{"name":"amount","type":"uint256"}],"name":"casinoWithdraw","outputs":[],"type":"function"},{"constant":false,"inputs":[{"name":"number","type":"uint256"}],"name":"betOnNumber","outputs":[{"name":"","type":"string"}],"type":"function"},{"constant":false,"inputs":[],"name":"casinoDeposit","outputs":[],"type":"function"},{"constant":false,"inputs":[{"name":"color","type":"uint256"}],"name":"betOnColor","outputs":[{"name":"","type":"string"}],"type":"function"},{"constant":true,"inputs":[],"name":"welcome","outputs":[{"name":"","type":"string"}],"type":"function"},{"inputs":[],"type":"constructor"}]);
var roulette = rouletteContract.at('0x5fe5b7546d1628f7348b023a0393de1fc825a4fd');

roulette.welcome.call();

web3.fromWei(roulette.casinoBalance.call(), "ether");

**Bet on Number**

In geth console type:

var number = 17;

var amount = 10; // In ETH

roulette.betOnNumber.sendTransaction(number,{from:eth.accounts[0], value: web3.toWei(amount, 'ether'), gas: 400000});
web3.fromWei(roulette.casinoBalance.call(), "ether");
web3.fromWei(eth.getBalance(eth.accounts[0]), "ether");

assuming eth.accounts[0] is the desired account, otherwise change it.

**Bet on Color** 

In geth console type:

var color = 0; // '0' = red, '1' = black

var amount = 10; // In ETH

roulette.betOnColor.sendTransaction(color,{from:eth.accounts[0], value: web3.toWei(amount, 'ether'), gas: 400000});
web3.fromWei(roulette.casinoBalance.call(), "ether");
web3.fromWei(eth.getBalance(eth.accounts[0]), "ether");

assuming eth.accounts[0] is the desired account, otherwise change it.

**Personal Note**

I understand that neither this nor the previous pyramid scheme adheres to some high moral compass.

I'm very much a believer of this project and what it stands for and have been ever since I first heard of it.

For me this is about growing as a programmer while sharing some little program-contracts, I myself would've liked to have, with the community.

**Disclaimer**

NO WARRANTY

THE PROGRAM-CONTRACT IS DISTRIBUTED IN THE HOPE THAT IT WILL BE USEFUL, BUT WITHOUT ANY WARRANTY. IT IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM-CONTRACT IS WITH YOU. SHOULD THE PROGRAM-CONTRACT PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW THE AUTHOR WILL BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE THE PROGRAM-CONTRACT (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM-CONTRACT TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF THE AUTHOR HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES. 
