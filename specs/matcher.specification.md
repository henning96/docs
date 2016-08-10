# Functional specification
WAVES assets exchange

## Purpose

The purpose of the project is to develop an exchange service with the properties below:

1. Order matching must be significantly faster than adding a transaction to a blockchain and waiting for N confirmations.
1. Trades must be executed at speed of a usual WAVES transfer.
1. Exchange clients must not transfer any assets to exchange accounts to be able to trade. 
That's why it's impossible to steal assets from the exchange (because exchange doesn't own client's assets).

## Functional requirements

1. Matching of buy/sell orders by pairs of assets and to create trading deals.
1. Partial matching of orders.
1. Ability to save/restore of the exchange's state (orders, stats and so on).
1. API to retrieve all the market data.
1. Registration/unregistration of asset pairs.
1. Failure recovery mechanism.

## Technical requirements

1. An exchange must keep track of orders state, but trades must be written to blockchain.
1. API for the interaction with a node to put/cancel an order and to publish a trade transaction on blockchain.
1. REST API for lite clients to make them be able to display current state of the market.
1. API for streaming update of data on a client-side.
1. Add or remove asset pairs from the exchange ideally without need to restart the exchange.
1. A storage for orders should be chosen at the development stage.
1. An exchange must be implemented on top of JVM with akka infrastructure support.
1. Order price must be expressed in units of the second asset in a pair.

## Use cases

1. I, as a user, want to put orders to exchange one asset to another.
1. I, as a user, want to cancel my order if it wasn't full or partially executed.
1. I, as a user, want to see a current pool of buy orders for a particular asset pair.
1. I, as a user, want to see a current pool of sell orders for a particular asset pair.
1. I, as a user, want to see a today's min/max price for a particular asset pair.
1. I, as a user, want to see yesterday close price for a particular asset pair.
1. I, as a user, want to see a current market price, it's change and trades volume from the beginning of the day for a particular asset pair.
1. I, as a user, want to see a list of N last trades for a particular asset pair.
1. I, as a user, want to see a graph of price changes for a particular asset pair as candels aggregated by 15 mins, 30 mins, 1 hour, 2 hours, 6 hours and 24 hours.
1. I, as a user, want to see the list of all assets that can be exchanged.
1. I, as an owner, want to add/remove asset pairs from the exchange.
1. I, as an owner, want to get a fee for order matching and execution.
1. I, as an owner, want to start/stop the exchange.
