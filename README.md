# About

[![Build Status](https://gitlab.com/alexs-sh/aichat-buildroot/badges/master/pipeline.svg)](https://gitlab.com/alexs-sh/aichat-buildroot/-/commits/master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A helper project to integrate [aichat](https://github.com/sigoden/aichat)
into [Buildroot](https://buildroot.org/). The patches submitted to the Buildroot team can be found here
[here](https://patchwork.ozlabs.org/project/buildroot/list/?series=&submitter=&state=&q=aichat&archive=&delegate=)

# Status

AiChat works on the test platforms: Raspberry Pi 3 (ARM32), QEMU (AArch64), and
Orange Pi (AArch64).

However, I encountered crashes and rendering issues while working over a serial
port. This seems to be the exact problem I saw earlier in Helix, and it's likely
caused by the `crossterm` crate.

Here are related issues & PRs:
- [Crossterm](https://github.com/crossterm-rs/crossterm/pull/1007) - the main problem
- [AiChat](https://github.com/sigoden/aichat/pull/1366) - here you can find workarounds
- [Helix crash](https://github.com/helix-editor/helix/pull/14050) and [Helix render](https://github.com/helix-editor/helix/issues/14101)  - similar issues, but in Helix editor

I didn’t dig too deeply into the problem because:
- running AiChat over a serial line is a very unlikely scenario, and there’s a
simple workaround.
- serve/SSH/display modes work fine. In my opinion, this is the main use case(s).
- it’s very likely the same issue as with Helix. Let’s revisit it if the upstream
fixes don’t work for AiChat.

# Examples

**QEMU aarch64**

![QEMU](./pics/aichat-qemu.png "QEMU")

**Raspberry PI3**

![Raspberry PI](./pics/aichat-rpi.png "Raspberry PI3")
