# btlabs-epic.github.io

Public files for BT Labs projects, served by GitHub Pages:

- `btlabs.json`: BT Labs' signed public file (donation addresses, official links, nodes and
  relays). A DSSE v1 envelope signed with Ed25519; apps verify it with the keys they ship and
  ignore it otherwise.
- `btlabs-keyring.json`: the public keys that may sign it (rank 1 signs, rank 2 is the spare).

Never edit `btlabs.json` by hand: it is produced and signed by BT Labs' signing tool, and any
change to its bytes breaks the signature.
