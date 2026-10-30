<div align="center">

# btlabs-epic.github.io

**BT Labs' signed public files for Epic Cash Desktop and Epic Cash Mobile.**

[Documentation](https://docs.btlabs.uk) · [Security](#security)

</div>

The wallets read these files to learn about updates and BT Labs' services. Every file is a DSSE
v1 envelope signed with Ed25519; the apps verify it with the keys they ship and ignore anything
that does not verify. The apps read `update-v2.json` from three places and use the valid copy with
the higher serial:

1. BT Labs' server: `https://epiccash.btlabs.uk/api/v1/update.json`
2. this repository on GitLab:
   `https://gitlab.com/epic-cash-bt/btlabs-epic.github.io/-/raw/main/update-v2.json`
3. the latest GitHub release of wallet-for-epic:
   `https://github.com/BTLabsUK/wallet-for-epic/releases/latest/download/update-v2.json`

`btlabs.json` is read from
`https://gitlab.com/epic-cash-bt/btlabs-epic.github.io/-/raw/main/btlabs.json`. The address
`btlabs-epic.github.io` is no longer used (GitHub Pages is gone; the name is kept for this
repository).

Source: [GitLab](https://gitlab.com/epic-cash-bt/btlabs-epic.github.io) · Mirror:
[GitHub](https://github.com/BTLabsUK/btlabs-epic.github.io)

## Files

| File | Contents |
|---|---|
| `update.json` | The latest release of each app: version, download URLs, SHA-256 and size per platform, release notes, a serial and an expiry. The apps check it and use the valid copy with the higher serial. |
| `btlabs.json` | BT Labs' public file: official links, donation addresses, nodes and relays. |
| `btlabs-keyring.json` | The public keys that may sign the files (rank 1 signs, rank 2 is the spare). |

Never edit the signed files by hand: they are produced and signed by BT Labs' release tooling
(`tools/publish-update-json.sh` in [wallet-for-epic](https://gitlab.com/epic-cash-bt/wallet-for-epic)),
and any change to their bytes breaks the signature.

## Verify a file yourself

The payload is base64 in the envelope's `payload` field; the signature covers the DSSE
pre-authentication encoding of `payloadType` and the payload bytes. The apps' verifier is
`app/lib/src/btlabs_public.dart` in wallet-for-epic, and its test vectors are in
`app/test/fixtures/btlabs/`.

## Security

Report a problem privately to **support@btlabs.uk**. A file that fails verification is never used
by the apps; tell us if you see one served here.

## Licence

The files are public data published by BT Labs. The code that makes and checks them is
Apache-2.0, in wallet-for-epic.

<p align="center"><sub>Made by BT Labs</sub></p>
