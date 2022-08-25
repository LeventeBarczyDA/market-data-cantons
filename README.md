# market-data-cantons
Market Data Sharing

## Testing in VS Code

```sh 
cd market-data 
daml studio
```

...and check out `daml/Main.daml`.

## Running Locally

```sh
cd market-data
daml start
```

...which will start the Navigator with the scenario from `daml/Main.daml` that you can play with.

## Running on hub.daml.com

First, got to [hub.daml.com] and sign up for an account. 

Once you've signed up (after an Email verification), go to your Hub console and create a new project and ledger. This should take about five minutes.

Inside the new ledger, upload and deploy `market-data-0.0.1.dar` from `market-data/.daml/dist`. The .dar file gets created when you run locally, as described above. If it doesn't exist, then you can compile the dar file with:

```sh
cd market-data 
daml build
```
...which will create the .dar file for you.

Once the .dar file is uploaded and deployed, create some Identities:

- `Moodys`
- `Goldman`
- `BAML`
- et al.

In Live Data, as `Moodys`, create a `LicenseProposal` contract, provided by `Moodys`, and for the benefit of one of the clients. Specify some market/credit-data labels, and a fee, and create the contract.

As the client (`Goldman` or `BAML`) go ahead and accept the proposal. This will create a new License that you'll be able to request market data with.

## Proposed Next Steps

...for how I would improve the Daml model:

### More Realistic Fee Structures

Today, we simply charge a set fee for each request. I think the fees ought to depend on the type of request.

### A set list of requestable market-data

Today, each license can contain any Text fields. It'd be better if we had a set dictionary of market data labels, as well as some meta-data parameters around what the data can be. Today, market data is basically a `Decimal`.

### Reference Entity restrictions

Today, the reference entity label is just a bit of text; it'd be better if that too was known ahead of time.





