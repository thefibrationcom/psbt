# Partially Signed Bitcoin Transactions (PSBTs)

This library provides a set of tools for working with Partially Signed Bitcoin Transactions (PSBTs), a format designed to facilitate collaboration and communication when dealing with Bitcoin transactions.
The format specifications can be found in BIP-0174 (https://github.com/bitcoin/bips/blob/master/bip-0174.mediawiki). 

## Usage

### Combine PSBTs

Combine multiple PSBTs into a single PSBT object.

```jsx
const psbtsLibrary = require('psbts-library');

const combinedPSBT = psbtsLibrary.combinePsbts(ecp, psbts);

```

### Create PSBT

Create a new PSBT object.

```jsx
const psbtParams = {
  outputs: [{
    script: '<Output ScriptPub Hex String>',
    tokens: '<Sending Tokens Number>'
  }],
  utxos: [{
    id: '<Transaction Id Hex String>',
    [sequence]: '<Sequence Number>',
    vout: '<Output Index Number>'
  }],
  [timelock]: '<Set Lock Time on Transaction To Number>',
  [version]: '<Transaction Version Number>'
};

const newPSBT = psbtsLibrary.createPsbt(psbtParams);

```

### Decode PSBT

Decode a BIP 174 encoded PSBT.

```jsx
const decodedPSBT = psbtsLibrary.decodePsbt(ecp, psbt);

```

### Encode PSBT

Encode a Partially Signed Bitcoin Transaction.

```jsx
const psbtPairs = [{
  [separator]: '<Is Separator Bool>',
  [type]: '<Type Buffer Object>',
  [value]: '<Value Buffer Object>'
}];

const encodedPSBT = psbtsLibrary.encodePsbt(psbtPairs);

```

### Extract Transaction

Extract a transaction from a finalized PSBT.

```jsx
const extractedTransaction = psbtsLibrary.extractTransaction(ecp, psbt);

```

### Finalize PSBT

Finalize the inputs of a PSBT.

```jsx
const finalizedPSBT = psbtsLibrary.finalizePsbt(ecp, psbt);

```

### Sign PSBT

Update a PSBT with signatures.

```jsx
const signedPSBT = psbtsLibrary.signPsbt(ecp, network, psbt, signingKeys);

```

### Transaction as PSBT

Convert a signed transaction to a signed PSBT.

```jsx
const psbtFromTransaction = psbtsLibrary.transactionAsPsbt(ecp, spendingTransactions, transaction);

```

### Update PSBT

Update a PSBT with additional attributes.

```jsx
const updatedPSBT = psbtsLibrary.updatePsbt(updateParams);

```

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.
