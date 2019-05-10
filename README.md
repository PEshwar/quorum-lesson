*List of commands to execute for Quorum 7-nodes exercise:

**Docker  basics:

docker-compose up -d

docker-compose down

docker ps

**To loginto a particular docker container shell and connect to quorum/geth node/console:

docker exec -it quorum-examples_node4_1 geth attach /qdata/dd/geth.ipc

or

docker exec -it quorum-examples_node4_1
geth attach /qdata/dd/geth.ipc


**To get transaction details in console:

eth.getTransaction(“0xe1ddd79703d1b79a27c1ab1259a99c3d3f49a78cd4985db77b2a2e055c7b1b1a")

**To get transaction receipt in console (contains contract address):

	eth.getTransactionReceipt(txHash)


**To get deployed contract instance and invoke methods on it:

var address = “0x1932c48b2bf8102ba33b4a6b545c32236e342f34"

var abi = [{“constant":true,"inputs":[],"name":"storedData","outputs":[{"name":"","type":"uint256"}],"payable":false,"type":"function"},{"constant":false,"inputs":[{"name":"x","type":"uint256"}],"name":"set","outputs":[],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"get","outputs":[{"name":"retVal","type":"uint256"}],"payable":false,"type":"function"},{"inputs":[{"name":"initVal","type":"uint256"}],"type":"constructor"}];

var private = eth.contract(abi).at(address)

private.get()

private.set()

**To execute script (javascript) from console:

loadScript(‘/examples/private-contract.js')


