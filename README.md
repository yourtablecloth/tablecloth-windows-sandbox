# TableCloth Windows Sandbox skill

[한국어](README.ko.md)

As of October 25, 2026, this package preserves the Windows Sandbox skill from [TableCloth commit f91a83d](https://github.com/yourtablecloth/TableCloth/tree/f91a83daac158130afdd24b261ad35de3d5f42cf). It explains local results supplied by TableCloth's Windows Sandbox host bridge.

This guide covers installation, the host bridge, credentials, supported operations and licensing. Installing the instructions does not enable Windows Sandbox or give Codex shell access.

## Installation from the repository root

Install through TableCloth's skill marketplace when this repository is listed, or import this folder through its installed-skills view. [SKILL.md](SKILL.md) resides at the repository root, so catalog entries use `Source.Path="."` with a pinned commit. The folder name and skill name are `tablecloth-windows-sandbox`.

## Results supplied by the TableCloth host bridge

A TableCloth build with the [Sandbox host bridge](https://github.com/yourtablecloth/TableCloth/blob/f91a83daac158130afdd24b261ad35de3d5f42cf/src/TableCloth.App/ManagedAi/ManagedAiSandboxBridge.cs) and a compatible Windows environment are required. The host runs an allowlisted `wsb.exe` command and supplies `LOCAL_WINDOWS_SANDBOX_REPORT` to the current AI turn. Codex does not run the command. Without the report, the skill cannot claim that an operation ran or succeeded.

## No additional service credentials

The skill requires no additional API key, token or client secret, and includes no executable helpers or third-party packages. TableCloth AI's existing account connection and execution permissions still apply. Installing [SKILL.md](SKILL.md) does not install `wsb.exe` or enable the Windows Sandbox feature.

## Allowlisted operations and reported outcomes

The host bridge supports `list`, default `start`, `stop`, `connect` and `ip`. Use an explicit Sandbox GUID or the sole listed ID for operations requiring a session; ask for a choice when multiple sessions exist. Stopping a Sandbox discards its state. Default start creates a regular Sandbox without TableCloth Catalog or Spork configuration. Arbitrary execution, `exec`, `share`, folder access and custom configuration remain outside the [skill's scope](SKILL.md).

## Upstream attribution and licensing

The instructions retain their original bytes. The upstream [copyright and license notice](https://github.com/yourtablecloth/TableCloth/blob/f91a83daac158130afdd24b261ad35de3d5f42cf/README.md#법적-고지) identifies the copyright holder as 남정현 and states:

> Copyright 2021-2026 rkttu.com. All rights reserved.

The original [AGPL-3.0 license text](LICENSE-AGPL) and [commercial-license contact notice](LICENSE-COMMERCIAL) are included unchanged. The commercial notice names Jung Hyun, Nam. This extraction does not grant a new license.
