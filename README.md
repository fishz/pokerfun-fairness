# pokerfun-fairness
Daily signed tree heads of the PokerFun fairness log, published so anyone can confirm that past hand records were never changed or removed.

## Contents

- `heads/YYYY/MM/DD.json`: the log's signed tree head for each day, pushed hourly by PokerFun. This branch refuses force-pushes and deletion, so a day once published cannot be quietly rewritten.
- `verifier/verifier.html`: PokerFun's standalone hand verifier. It is one self-contained page that runs offline, from this site or from a saved copy (`file://`). Open it, then drop in a hand record downloaded from a table's "Verify this hand". It checks the shuffle proofs, the drand beacon, the dealers' signatures, the operator's signature and the hand's inclusion in the log, without trusting PokerFun's servers.

Hosted at https://fishz.github.io/pokerfun-fairness/verifier/verifier.html (GitHub Pages, not served by PokerFun).

## Checking the verifier

`verifier/verifier.html.sha256` holds its fingerprint. Compare it with your copy:

```bash
shasum -a 256 verifier.html
```

The page is built reproducibly from PokerFun's sources (`fairness/verifier/`, checked with `node fairness/verifier/build.js --check`). Each new version is committed here, so this repository's history is the verifier's changelog. Mirrors are welcome.
