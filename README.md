# drupal-patches

Patches applied by [`uo/uo_communications_substream`](https://git.uoregon.edu/projects/WCDM/repos/uo-communications-substream/browse)
to the UO Communications Drupal sites, hosted by the Digital Strategy team.

**This repo must stay public.** Pantheon's build downloads these patches anonymously through
`cweagans/composer-patches`; a private repo fails the build exactly like an unreachable URL.

## Why the patches live here

From 2026-10-23, `www.drupal.org/files/issues/…` and `git.drupalcode.org/…/merge_requests/N.patch`
answer non-browser clients with a JavaScript "Client Challenge" page (HTTP 200, HTML). Composer
downloads the page, cannot apply it, and the build fails. Two other patches were on personal
GitHub gists. Hosting all of them here removes both dependencies.

## How the substream references them

Always by **commit-pinned** raw URL, never a branch:

```
https://raw.githubusercontent.com/UO-Digital-Strategy/drupal-patches/<commit-sha>/<project>/<file>.patch
```

A pinned commit means the bytes a build downloads can never change underneath it. Adding or
changing a patch is a new commit here, then a new substream release pointing at that commit.

## Contents

Every file is byte-identical to its original source.

| Project | Applies to | File | Original source | sha256 |
|---|---|---|---|---|
| metatag | 2.2.0 | `metatag/metatag--2024-09-09--3315049--mr-140.patch` | https://www.drupal.org/files/issues/2024-09-09/metatag--2024-09-09--3315049--mr-140.patch (#3315049, MR !140) | `78218716fda4a22c73bf0c7cfcf0a6cd40d6db94394a3ecb3c81add2d57b9575` |
| entity_reference_revisions | 1.14 | `entity_reference_revisions/2799479-163-relationship-host-id.patch` | https://www.drupal.org/files/issues/2021-11-12/2799479-163-relationship-host-id.patch (#2799479) | `727b3a48739f5d1f608392b6b57b2fa82e0998da40822f7d42bf71ab0c57d3bf` |
| menu_condition | 2.0 | `menu_condition/menu_condition-add_negate_option.patch` | https://www.drupal.org/files/issues/2020-10-08/menu_condition-add_negate_option.patch | `8e2bdf11476599d53eac09667d8b29a09e937092be2d063ea91835b4a42813d7` |
| context | 5.0.0-rc2 | `context/context-mr-45.patch` | https://git.drupalcode.org/project/context/-/merge_requests/45.patch (MR !45, as of 2026-10-23) | `11845ab7c415e8528ebea998cbca9e98f6388a284d5ee32f855473cc6a60d061` |
| context | 5.0.0-rc2 | `context/context-5.0.0-rc2--d11-menu-active-trail-signature.patch` | https://gist.github.com/paulkozik/54aae14d47b53878e01aef7ada568042 (UO, written for the D11 upgrade) | `93f84fbfb23547690caa740e8d8e89ca50e76a9ab02578f5f5a81c46e1e54747` |
| image_effects | 4.0.0 | `image_effects/image_effects-version-fix.patch` | https://gist.github.com/mcoughli/7fae2349d2f459ad9adcffbee1f966cf | `ed79ebed5f7f80f2b7e4c8f4ee0c17c96bfcd69b570b0bc1dd5b79ac794ca238` |

**The two context patches are order-dependent:** MR !45 must apply before the D11 signature fix,
which edits the same file.

Verify a file against this table with `shasum -a 256 <file>`.
