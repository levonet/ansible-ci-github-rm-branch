# CI: Remove branch from github repository.

This role is useful in CI pipeline after merging Pull Request.

## Role Variables

- `ci_github_api` (default: https://api.github.com)
- `ci_github_username` (required): Github username.
- `ci_github_password` (required): [Github access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/).
- `ci_github_owner` (required): Github owner or organisation name.
- `ci_github_repo` (required): Github project repository name.
- `ci_github_ref` (required): Github ref name.
- `ci_github_ignore_error` (default: yes): Ignore any errors.

## Example Playbook

```yaml
- hosts: 127.0.0.1
  connection: local
  gather_facts: no
  vars:
    ci_github_username: ci-bot
    ci_github_password: secret
    ci_github_owner: myorg
    ci_github_repo: myapp
    ci_github_ref: "heads/{{ github_branch }}"
  roles:
    - role: levonet.ci_github_rm_branch
```

And run in Jenkins:

```bash
ansible-playbook myplaybook.yml -e github_branch="${X_GH_BRANCH}"
```

## License

[MIT](https://opensource.org/licenses/MIT)

## Author Information

This role was created by [Pavlo Bashynskyi](https://github.com/levonet)
