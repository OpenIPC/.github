# Security policy

OpenIPC replaces vendor firmware on IP cameras, DVRs and NVRs whose makers no longer ship
updates. For many of these devices our tree is the only place a fix can land, so we treat
security reports as a priority.

## Reporting a vulnerability

Report privately through GitHub:
**[Report a vulnerability](https://github.com/OpenIPC/firmware/security/advisories/new)**
(the *Security* tab of this repository → *Report a vulnerability*).

Please do **not** open a public issue, pull request or chat message for an unfixed
vulnerability.

A useful report includes:

- the affected component and version (the `BUILD_ID` line from `/usr/lib/os-release`, or the
  release tag and date);
- the SoC and board, if the issue is hardware-specific;
- steps to reproduce, or a proof of concept;
- the impact as you see it (remote or local, authentication required or not).

Reports in English are preferred; Russian and Chinese are also fine.

## What happens next

| Step                           | Target                                   |
| ------------------------------ | ---------------------------------------- |
| Acknowledgement of the report  | within 3 days                            |
| Triage and severity assessment | within 7 days                            |
| Fix for a validated issue      | within 7 days of validation              |
| Public advisory                | when the fixed build is published        |

If a fix depends on a vendor binary we cannot rebuild, we will tell you, publish a mitigation
where one exists, and say so in the advisory.

We publish advisories in this repository's
[Security Advisories](https://github.com/OpenIPC/firmware/security/advisories) and request a CVE
through GitHub when the issue qualifies. Reporters are credited unless they ask not to be.

## Supported versions

OpenIPC firmware is a rolling release. Fixes go into `master` and ship in the next nightly
build; we do not backport to older images. To get a fix, update to the latest release with
`sysupgrade`.

| Version                         | Supported |
| ------------------------------- | --------- |
| Latest release (nightly build)  | yes       |
| Older builds                    | no        |

## Scope

In scope — anything built from the OpenIPC organisation's repositories, including:

- this firmware tree: build system, root filesystem, overlay scripts, `sysupgrade`;
- kernels from [OpenIPC/linux](https://github.com/OpenIPC/linux) and bootloaders from
  [OpenIPC/u-boot](https://github.com/OpenIPC/u-boot);
- the streamers and tools shipped in images (Majestic, Divinus, Waybeam, Mini, Venc, the web
  interface). For a component that lives in another repository, report here anyway and we will
  route it.

Out of scope:

- the manufacturer's stock firmware that OpenIPC replaces;
- attacks that need physical access to the board's UART, JTAG or flash chip;
- the setup page of an unclaimed camera, which is open by design until a root password is set.

## Past advisories

- [GHSA-fjf7-9x3v-6mj6](https://github.com/OpenIPC/firmware/security/advisories/GHSA-fjf7-9x3v-6mj6)
  (High, September 2026) — `sysupgrade` did not verify TLS certificates when downloading
  firmware.
- [GHSA-75rq-mx37-fvx9](https://github.com/OpenIPC/firmware/security/advisories/GHSA-75rq-mx37-fvx9)
  (Low, October 2026) — off-by-one heap overflow in `hisi-gpio-watcher`.
