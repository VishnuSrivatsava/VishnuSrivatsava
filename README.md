<img src="assets/cube-header-v8.svg" width="100%" alt="VISHNU SRIVATSAVA" />

## What I do

Systems programmer. My merged patches fix real bugs in Neovim, curl and Tesseract: code that
runs on billions of machines.

## Open source, merged upstream

| Project | Contribution | Outcome |
|---|---|---|
| [neovim/neovim](https://github.com/neovim/neovim/pull/42560) | Regex engine crash on invalid multi-byte input: grapheme cluster walker now terminates on undecodable bytes | **Merged** |
| [curl/curl](https://github.com/curl/curl/commit/a4eed8c7) | RFC 7838 Alt-Svc: protocol tokens are percent-decoded before ALPN mapping | **Merged, my commit on master** |
| [tesseract-ocr/tesseract](https://github.com/tesseract-ocr/tesseract/pull/4669) | Renderer failure exited with code 0: now propagates EXIT_FAILURE | **Merged** |
| [faker-cxx](https://github.com/cieslarmichal/faker-cxx/pull/1035) | dataUri generator for SVG images, 100th contributor | **Merged** |

Also in review: [vim](https://github.com/vim/vim/pull/21689) (same fix backported),
[micropython](https://github.com/micropython/micropython/pull/19839) (FFI arity TypeError),
and a [race condition analysis](https://github.com/openssl/openssl/issues/33399#issuecomment-6556507520) on an OpenSSL issue.

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

[Codeforces Specialist 1412](https://codeforces.com/profile/Cuber2113) ·
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

## Media tools

[TransPEG](https://github.com/VishnuSrivatsava/TransPEG) (PyQt + FFmpeg + Google Translate for
subtitle translation) and
[Video Grapher](https://github.com/VishnuSrivatsava/video-grapher) (WASM, extracts GIFs and
waveforms in the browser): my FFmpeg work.

## Reach me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/vishnusrivatsava)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:vishnusrivatsava@gmail.com)
