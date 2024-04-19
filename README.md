# PSBT (Partially Signed Bitcoin Transaction)

This module allows you to create a Partially Signed Bitcoin Transaction (PSBT) in hexadecimal format. PSBTs are commonly used in multi-signature scenarios or when multiple parties need to collaboratively sign a Bitcoin transaction.

The format specifications can be found in [BIP-0174](https://github.com/bitcoin/bips/blob/master/bip-0174.mediawiki).

### Methods

### combinePsbts

Combine multiple PSBTs.

```jsx
{
  ecp: <ECPair Object>,
  psbts: [<BIP 174 Encoded PSBT Hex String>]
}

```

- **Throws:** Combine PSBT Error.
- **Returns:** `{ psbt: <BIP 174 Encoded PSBT Hex String> }`

### createPsbt

Create a PSBT.

```jsx
{
  outputs: [{
    script: <Output ScriptPub Hex String>,
    tokens: <Sending Tokens Number>
  }],
  utxos: [{
    id: <Transaction Id Hex String>,
    [sequence]: <Sequence Number>,
    vout: <Output Index Number>
  }],
  [timelock]: <Set Lock Time on Transaction To Number>,
  [version]: <Transaction Version Number>
}

```

- **Returns:** `{ psbt: <Partially Signed Bitcoin Transaction Hex Encoded String> }`

### decodePsbt

Decode a BIP 174 encoded PSBT.

```jsx
{
  ecp: <ECPair Object>,
  psbt: <Hex Encoded Partially Signed Bitcoin Transaction String>
}

```

- **Throws:** Invalid PSBT Error.
- **Returns:** Decoded PSBT structure.

### encodePsbt

Encode a Partially Signed Bitcoin Transaction.

```jsx
{
  pairs: [{
    [separator]: <Is Separator Bool>,
    [type]: <Type Buffer Object>,
    [value]: <Value Buffer Object>
  }]
}

```

- **Throws:** Failed To Encode Error.
- **Returns:** `{ psbt: <Hex Encoded Partially Signed Bitcoin Transaction String> }`

### extractTransaction

Extract a transaction from a finalized PSBT.

```jsx
{
  ecp: <ECPair Object>,
  psbt: <BIP 174 Encoded PSBT Hex String>
}

```

- **Throws:** Extract Transaction Error.
- **Returns:** `{ transaction: <Hex Serialized Transaction String> }`

### finalizePsbt

Finalize the inputs of a PSBT.

```jsx
{
  ecp: <ECPair Object>,
  psbt: <BIP 174 Encoded PSBT Hex String>
}

```

- **Throws:** Finalize PSBT Error.
- **Returns:** `{ psbt: <BIP 174 Encoded PSBT Hex String> }`

### signPsbt

Update a PSBT with signatures.

```jsx
{
  ecp: <ECPair Object>,
  network: <Network Name String>,
  psbt: <BIP 174 Encoded PSBT Hex String>,
  signing_keys: [<WIF Encoded Private Key String>]
}

```

- **Throws:** Sign PSBT Error.
- **Returns:** `{ psbt: <BIP 174 Encoded PSBT Hex String> }`

### transactionAsPsbt

Convert a signed transaction to a signed PSBT.

Note: not all signed transactions can be converted to a signed PSBT. For example, a preimage cannot be represented in a standard PSBT.

```jsx
{
  ecp: <ECPair Object>,
  spending: [<Spending Transaction Hex String>],
  transaction: <Hex Encoded Transaction String>
}

```

- **Throws:** Error.
- **Returns:** `{ psbt: <Signed PSBT String> }`

### updatePsbt

Update a PSBT.

```jsx
{
  [additional_attributes]: [{
    type: <Type Hex String>,
    value: <Value Hex String>,
    vin: <Input Index Number>,
    vout: <Output Index Number>
  }],
  [bip32_derivations]: [{
    fingerprint: <BIP 32 Fingerprint of Parent's Key Hex String>,
    path: <BIP 32 Derivation Path String>,
    public_key: <Public Key String>
  }],
  ecp: <ECPair Object>,
  psbt: <BIP 174 Encoded PSBT String>,
  [redeem_scripts]: [<Hex Encoded Redeem Script String>],
  [sighashes]: [{
    id: <Transaction Id String>,
    sighash: <Sighash Flag Number>,
    vout: <Spending Output Index Number>
  }],
  [signatures]: [{
    vin: <Signature Input Index Number>,
    hash_type: <Signature Hash Type Number>,
    public_key: <BIP 32 Public Key String>,
    signature: <Signature Hex String>
  }],
  [taproot_inputs]: [{
    vin: <Input Index Number>,
    [key_spend_sig]: <Taproot Key Spend Signature Hex String>
  }],
  [transactions]: [<Hex Encoding Transaction String>],
  [witness_scripts]: [<Witness Script String>]
}

```

- **Throws:** Update PSBT Error.
- **Returns:** `{ psbt: <Hex Encoded Partially Signed Bitcoin Transaction String> }`
