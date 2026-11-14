<img src="assets/cube-header-v9.svg" width="100%" alt="VISHNU SRIVATSAVA" />

## What I do

Systems programmer. My merged patches fix real bugs in Microsoft's Q# compiler, CCExtractor, Neovim, Vim, curl
and Tesseract: code that runs on billions of machines.

## Open source, merged upstream

| Project | Contribution | Outcome |
|---|---|---|
| [microsoft/qdk](https://github.com/microsoft/qdk/pull/4271) | Q# compiler panic during QIR generation: defunctionalization dispatch branches shared argument nodes that a later pass rewired in place, leaving a sibling branch reading an unbound local | **Merged same day** |
| [microsoft/qdk](https://github.com/microsoft/qdk/pull/4272) | Q# evaluator panicked with "value should be callable" when a runtime-selected callable hit a functor application; the partial evaluation placeholder now propagates so the existing call check fails cleanly | **Merged same day** |
| [CCExtractor/ccextractor](https://github.com/CCExtractor/ccextractor/pull/2430) | SIGSEGV in RCWT teletext parsing: the mode decision was re-read from a buffer already overwritten with caption data | **Merged** |
| [neovim/neovim](https://github.com/neovim/neovim/pull/42560) | Regex engine crash on invalid multi-byte input | **Merged** |
| [vim/vim](https://github.com/vim/vim/pull/21689) | Backtracking regexp never matched a literal followed by \%C with 'ignorecase' | **Merged as [patch 9.2.1298](https://github.com/vim/vim/commit/ffb58fba60992bbe80f9ea5e3b9619d85cede1bd); [ported to Neovim](https://github.com/neovim/neovim/pull/42715) with solution credit** |
| [curl/curl](https://github.com/curl/curl/commit/a4eed8c7) | RFC 7838 Alt-Svc percent-encoded protocol names never matched | **Merged, my commit on master** |
| [tesseract-ocr/tesseract](https://github.com/tesseract-ocr/tesseract/pull/4669) | Renderer failure exited with code 0 | **Merged** |
| [faker-cxx](https://github.com/cieslarmichal/faker-cxx/pull/1035) | dataUri generator for SVG images, 100th contributor | **Merged** |

Also in review: [micropython](https://github.com/micropython/micropython/pull/19839) (FFI arity TypeError),
and a [race condition analysis + deterministic reproducer](https://github.com/openssl/openssl/issues/33399#issuecomment-6587629226) on an OpenSSL issue.

## SocketSweep

Android storage analyzer that bypasses MTP with a parallel C++17 scanner over ADB, a Rust/Tauri
desktop app and a React 19 UI. **93,239 files / 51 GB in 7.7 seconds** on a Galaxy S24 Ultra.
Presented at IndiaFOSS 2026.

[![Stars](https://img.shields.io/github/stars/VishnuSrivatsava/SocketSweep?style=social&label=%E2%98%85%20stars)](https://github.com/VishnuSrivatsava/SocketSweep)
[![Forks](https://img.shields.io/github/forks/VishnuSrivatsava/SocketSweep?style=social&label=forks)](https://github.com/VishnuSrivatsava/SocketSweep/network)

## Stack

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=c,cpp,rust,python,linux,git,kotlin,react,js,postgres,bash,docker" />
</a>

## Competitive programming

[Codeforces Specialist 1444](https://codeforces.com/profile/Cuber2113) ·
[LeetCode Guardian 2160](https://leetcode.com/mathcuber/) ·
[CodeChef 3★ 1739](https://www.codechef.com/users/mathcuber) ·
[WCA profile](https://www.worldcubeassociation.org/persons/2018SRIV11)

## Contests & CTFs

Security: Winner, Cryptic Hunt (IIIT Naya Raipur) · Winner, CyberStrike'24 (SNIST) · Runner-up,
nu11byt3 CTF Convergence (VNRVJIET)

Coding: Winner, Convergence R1 (VNRVJIET, 400+ competitors) · Finalist, Megathon (IIIT-H,
top 6 of 700+)

## Speedcubing

WCA competitor since 2018 · **5 medals (2 gold)** · top 50 in India, 3x3 One-Handed

## Bug autopsies

The full stories behind the merges above: trigger, root cause, fix.

**Microsoft Q# compiler.** Trigger: an operation selected by a static `if`, wrapped in a partial
application, itself selected by another static `if`, passed as the callable argument of a higher order
call. Root cause: the defunctionalization pass built dispatch leaves that shared the original call's
argument nodes; a later fixed-point iteration rewired a shared node in place and installed its binding
inside one branch only, so the sibling branch referenced an unbound local and the invariant checker
panicked. Fix: each dispatch leaf owns a copy of its argument tree, the contract its two sibling
functions already documented and enforced. Reviewed and merged by the subsystem owner in about two
hours.

**Neovim.** Trigger: a regex pattern walking input that contains an undecodable byte next to a
combining sequence. Root cause: the grapheme cluster walker treated every byte after a base
character as a combining continuation, so the invalid byte was folded into the cluster and the
backtracking engine crashed while the NFA engine did not. Fix: undecodable bytes terminate the
cluster.

**curl.** Trigger: an Alt-Svc header advertising HTTP/1.1. Root cause: RFC 7838 percent-encodes
protocol tokens containing reserved characters, so HTTP/1.1 arrives as http%2F1.1, and curl
compared the encoded token literally against decoded protocol names. Fix: percent-decode before
the ALPN mapping.

**Tesseract.** Trigger: a renderer failure such as a missing output configuration. Root cause:
the failure path exited with code 0, so scripts and CI believed a render succeeded when it had
not. Fix: propagate EXIT_FAILURE.

**Vim.** Trigger: searching for a literal followed by \%C with 'ignorecase' on text containing
composing characters. Root cause: cstrncmp() counted characters with MB_PTR_ADV(), which includes
composing characters, so the one byte pattern was compared against the base character plus its
combining marks and failed before the \%C atom could skip them. Fix: compare base characters on
both sides, the way the NFA engine already did. Applied upstream as patch 9.2.1298 and ported
into Neovim the next day, with the solution credited by name.

## Media tools

[TransPEG](https://github.com/VishnuSrivatsava/TransPEG) (PyQt + FFmpeg + Google Translate for
subtitle translation) and
[Video Grapher](https://github.com/VishnuSrivatsava/video-grapher) (WASM, extracts GIFs and
waveforms in the browser): my FFmpeg work.

## Reach me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/vishnusrivatsava)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:vishnusrivatsava@gmail.com)
