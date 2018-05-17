Kashcoin API
============


Most of the Kashcoin API calls are the same as they are in Bitcoin.

Required arguments are denoted inside < and > Optional arguments are inside [ and ].



======================	===============================================================================	===============================================================================================================================================================================================================================================================================================================================================================================================================================	========================
Command			Parameters									Description																																																			Requires unlocked wallet
======================	===============================================================================	===============================================================================================================================================================================================================================================================================================================================================================================================================================	========================
addmultisigaddress	<nrequired> <'["key","key"]'>	[account]					Add a nrequired-to-sign multisignature address to the wallet. Each key is a Kashcoin address or hex-encoded public key. If [account] is specified, assign address to [account].																															N			 
addnode			<node> <add/remove/onetry>							version 0.8 Attempts add or remove <node> from the addnode list or try a connection to <node> once.																																								N			 
backupwallet		<destination>									Safely copies wallet.dat to destination, which can be a directory or a path with filename.																																									N			 
bannode			<node> <expiration>								OMG2 only Bans <node> until unix timestamp <expiration>. Set <expiration> to -1 to unban a node.																																								N			 
createmultisig		<nrequired> <'["key,"key"]'>							Creates a multi-signature address and returns a json object																																																 
createrawtransaction	[{"txid":txid,"vout":n},...] {address:amount,...}				Creates a raw transaction spending given inputs.																																														N			 
decoderawtransaction	<hex string>									Produces a human-readable JSON object for a raw transaction.																																													N			 
dumpprivkey		<kashcoinaddress>								Reveals the private key corresponding to <kashcoinaddress>																																													Y			 
encryptwallet		<passphrase>									Encrypts the wallet with <passphrase>.																																																N			 
getaccount		<kashcoinaddress>								Returns the account associated with the given address.																																														N			 
getaccountaddress	<account>									Returns the current Kashcoin address for receiving payments to this account.																																											N			 
getaddednodeinfo	<dns> [node]									version 0.8 Returns information about the given added node, or all added nodes (note that onetry addnodes are not listed here) If dns is false, only a list of added nodes will be provided, otherwise connected information will also be available.																						N			 
getaddressesbyaccount	<account>									Returns the list of addresses for the given account.																																														N			 
getbalance		[account] [minconf=1]								If [account] is not specified, returns the server's total available balance.																																														 
													If [account] is specified, returns the balance in the account.																																													N			 
getbestblockhash											version 0.8.6.1 Returns the hash of the newest block in the longest block chain.																																										N			 
getblock		<hash>										Returns information about the block with the given hash.																																													N			 
getblockcount												Returns the number of blocks in the longest block chain.																																													N			 
getblockhash		<index>										Returns hash of block in best-block-chain at <index>; index 0 is the genesis block																																										N			 
getblocktemplate	[params]									Returns data needed to construct a block to work on																																														N			 
getconnectioncount											Returns the number of connections to other nodes.																																														N			 
getdifficulty												Returns the proof-of-work difficulty as a multiple of the minimum difficulty.																																											N			 
getinfo													Returns an object containing various state info.																																														N			 
getmininginfo												Returns an object containing mining-related information: blocks, currentblocksize, currentblocktx, difficulty, errors, generate, genproclimit, hashespersec, networkhashps, pooledtx, testnet																													N			 
getnetworkhashps	[blocks] [height]								Returns the estimated network hashes per second based on the last 120 blocks. Pass in [blocks] to override # of blocks, -1 specifies since last difficulty change. Pass in [height] to estimate the network speed at the time when a certain block was found. Optional [height] parameter added in 0.8.4.															N			 
getnewaddress		[account]									Returns a new Kashcoin address for receiving payments. If [account] is specified (recommended), it is added to the address book so payments received with the address will be credited to [account].																												N			 
getpeerinfo												Returns data about each connected node.																																																N			 
getrawmempool												Returns all transaction ids in memory pool																																															N			 
getrawtransaction	<txid> [verbose=0]								Returns raw transaction representation for given transaction id.																																												N			 
getreceivedbyaccount	[account] [minconf=1]								Returns the total amount received by addresses with [account] in transactions with at least [minconf] confirmations. If [account] not provided return will include all transactions to all accounts. (version 0.3.24)																										N			 
getreceivedbyaddress	<kashcoinaddress> [minconf=1]							Returns the total amount received by <kashcoinaddress> in transactions with at least [minconf] confirmations. While some might consider this obvious, value reported by this only considers *receiving* transactions. It does not check payments that have been made *from* this address. In other words, this is not "getaddressbalance". Works only for addresses in the local wallet, external addresses will always show 0.	N			 
gettransaction		<txid>										Returns an object about the given transaction containing: amount, confirmations, txid, time[1], details (an array of objects containing: account, address, category, amount, fee)																														N			 
gettxout		<txid> <n> [includemempool=true]						Returns details about an unspent transaction output (UTXO)																																													N			 
gettxoutsetinfo												Returns statistics about the unspent transaction output (UTXO) set																																												N			 
getwork			[data]										If [data] is not specified, returns formatted hash data to work on: midstate, data, hash1, target. If [data] is specified, tries to solve the block and returns true if it was successful.																													N			 
help			[command]									List commands, or get help for a command.																																															N			 
importprivkey		<kashcoinprivkey> [label] [rescan=true]						Adds a private key (as returned by dumpprivkey) to your wallet. This may take a while, as a rescan is done, looking for existing transactions. Optional [rescan] parameter added in 0.8.0.																													Y			 
keypoolrefill												Fills the keypool, requires wallet passphrase to be set.																																													Y			 
listaccounts		[minconf=1]									Returns Object that has account names as keys, account balances as values.																																											N			 
listaddressgroupings											Returns all addresses in the wallet and info used for coincontrol.																																												N			 
listbannednodes												OMG2 only Returns a list of currently banned nodes along with the ban expiration timestamps.																																									N			 
listlockunspent												Returns list of temporarily unspendable outputs.																																														N			 
listreceivedbyaccount	[minconf=1] [includeempty=false]						Returns an array of objects containing: account, amount, confirmations																																												N			 
listreceivedbyaddress	[minconf=1] [includeempty=false]						Returns an array of objects containing: address, account, amount, confirmations. To get a list of accounts on the system, execute kashcoind listreceivedbyaddress 0 true																															N			 
listsinceblock		[blockhash] [target-confirmations]						Get all transactions in blocks since block [blockhash], or all transactions if omitted.																																										N			 
listtransactions	[account] [count=10] [from=0]							Returns up to [count] most recent transactions skipping the first [from] transactions for account [account]. If [account] not provided will return recent transaction from all accounts.																													N			 
listunspent		[minconf=1] [maxconf=9999999] ["address",...]					Returns array of unspent transaction inputs in the wallet.																																													N			 
lockunspent		<unlock?> [array-of-Objects]							version 0.8 Updates list of temporarily unspendable outputs																																													N			 
move			<fromaccount> <toaccount> <amount> [minconf=1] [comment]			Move from one account in your wallet to another																																															N			 
sendfrom		<fromaccount> <tokashcoinaddress> <amount> [minconf=1] [comment] [comment-to]	<amount> is a real and is rounded to 8 decimal places. Will send the given amount to the given address, ensuring the account has a valid balance using [minconf] confirmations. Returns the transaction ID if successful (not in JSON object).																							Y			 
sendmany		<fromaccount> {address:amount,...} [minconf=1] [comment]			amounts are double-precision floating point numbers																																														Y			 
sendrawtransaction	<hexstring>									Submits raw transaction (serialized, hex-encoded) to local node and network.																																											N			 
sendtoaddress		<kashcoinaddress> <amount> [comment] [comment-to]				<amount> is a real and is rounded to 8 decimal places. Returns the transaction ID <txid> if successful.																																								Y			 
setaccount		<kashcoinaddress> <account>							Sets the account associated with the given address. Assigning address that is already assigned to the same account will create a new address associated with that account.																															N			 
setmininput		<amount>									<amount> is a real and is rounded to the nearest 0.00000001																																													N			 
settxfee		<amount>									<amount> is a real and is rounded to the nearest 0.00000001																																													N			 
signmessage		<kashcoinaddress> <message>							Sign a message with the private key of an address.																																														Y			 
signrawtransaction	<hexstring> [{"txid":txid,"vout":n,"scriptPubKey":hex},...] [<privatekey1>,...]	Adds signatures to a raw transaction and returns the resulting raw transaction.																																											Y/N			 
stop													Stop Kashcoin server.																																																		N			 
submitblock		<hex data> [optional-params-obj]						Attempts to submit new block to network.																																															N			 
validateaddress		<kashcoinaddress>								Return information about <kashcoinaddress>.																																															N			 
verifychain												version 0.8.6.1 Verifies chain database at runtime.																																														N			 
verifymessage		<kashcoinaddress> <signature> <message>						Verifies a signed message.																																																	N			 
walletlock												Removes the wallet encryption key from memory, locking the wallet. After calling this method, you will need to call walletpassphrase again before being able to call any methods which require the wallet to be unlocked.																									N			 
walletpassphrase	<passphrase> <timeout>								Stores the wallet decryption key in memory for <timeout> seconds.																																												N			 
walletpassphrasechange	<oldpassphrase> <newpassphrase>							Changes the wallet passphrase from <oldpassphrase> to <newpassphrase>.																																												N			 
======================	===============================================================================	===============================================================================================================================================================================================================================================================================================================================================================================================================================	========================