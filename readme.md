# bviktor.github_release

## Synopsys

This role lets you find the asset URLs of the releases of GitHub projects.

## Parameters

| Name | Required | Example | Description |
|---|---|---|---|
| `owner` | yes | `SteamRE` | GitHub repo owner. |
| `repo` | yes | `DepotDownloader` | GitHub repo name. |
| `prefix` | yes | `depotdownloader-` | Pattern the asset filename must start with. |
| `suffix` | yes | `.zip` | Pattern the asset filename must end with. |
| `tag` | no | `v2.7.1` | GitHub release tag. If omitted, `latest` is used. |
| `ratelimit` | no | `false` | If false, don't check if GitHub rate limit is reached, and don't wait for it to reset. The request will most likely fail. |
| `verbose` | no | `true` | If true, print more diagnostic messages. |

## Examples

```yml
- include_role:
    name: bviktor.github_release
  vars:
    owner: 'SteamRE'
    repo: 'DepotDownloader'
    prefix: 'depotdownloader-'
    suffix: '.zip'
    verbose: true

- include_role:
    name: bviktor.github_release
  vars:
    owner: 'wp-cli'
    repo: 'wp-cli'
    tag: 'v2.7.1'
    prefix: 'wp-cli-'
    suffix: '.phar'
    ratelimit: false
```

## Return Values

| Key | Type | Example | Description |
|---|---|---|---|
| `github_release.url` | string | `https://github.com/wp-cli/wp-cli/releases/download/v2.7.1/wp-cli-2.7.1.phar` | Download URL for the matching asset. |

## Support

| Platform | Support | Status |
|---|---|---|
| Linter | ✅ | [![Lint](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/lint.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/lint.yml) |
| AlmaLinux 8 | ✅ | [![AlmaLinux 8](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/almalinux-8.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/almalinux-8.yml) |
| AlmaLinux 9 | ✅ | [![AlmaLinux 9](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/almalinux-9.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/almalinux-9.yml) |
| Fedora 37 | ✅ | [![Fedora 37](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/fedora-37.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/fedora-37.yml) |
| Ubuntu 18.04 | ✅ | [![Ubuntu 18.04](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/ubuntu-18.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/ubuntu-18.04.yml) |
| Ubuntu 20.04 | ✅ | [![Ubuntu 20.04](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/ubuntu-20.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/ubuntu-20.04.yml) |
| Ubuntu 22.04 | ✅ | [![Ubuntu 22.04](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/ubuntu-22.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-github_release/actions/workflows/ubuntu-22.04.yml) |
