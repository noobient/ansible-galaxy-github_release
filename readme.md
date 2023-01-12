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
| `github_token` | no | `github_pat_ABCD1234...` | If set, GitHub API requests are authenticated using your token. See below for details. |

### GitHub Token

GitHub's API has very stringent rate limits, 60 requests per hour at the time of writing, so it is very easy to deplete,
and it's often not feasible to wait hours for playbooks to complete. For this reason, you can specify your GitHub personal access token,
which increases this limit to 5000 per hour. To acquire such a token, go to:

[Fine-grained personal access tokens](https://github.com/settings/tokens?type=beta)

You should restrict this token as much as possible, so the recommended scope is:

- Repository access: **Public Repositories (read-only)**
- Account permissions: **None**

The other main point is how you feed this token into Ansible. Never push this token into public, or shared repositories.
Save it into a Git-ignored variable file, e.g.:

```
---
github_token: github_pat_ABCD1234...
```

Or specify it from the command line, e.g.:

```
ansible-playbook foo.yml -e "github_token=github_pat_ABCD1234..."
```

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
