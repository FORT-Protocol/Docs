# System roles

---

|Role|Definition|
|---|---|
|Trader|Users who trade perpetual contracts and options in Hedge Protocol. Generally, it is a wallet address or smart contract.|
|DAO Contract|The counterparty of the trader. For the options module, the DAO contract acts as the seller of options; for perpetual contracts, when the user is in the long position, the DAO contract generates a corresponding short position, and when the user is bearish, the DAO contract generates a corresponding call position.|
|Settler|The object of liquidation of the position of the perpetual contract is generally completed by a robot, and the liquidator can obtain the residual value reward after the liquidation.|
|Governor|The objects participating in the governance of the Hedge system, the holders of DCUToken, revise and upgrade the Hedge system by initiating a vote.|