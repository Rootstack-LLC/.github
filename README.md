# Rootstack 

## GitHub Organization

This organization hosts all client and internal projects. Repositories follow the naming convention `{client}-{repo-name}`. Access is managed through teams — one team per client.

## CI/CD Runners

We run self-hosted GitHub Actions runners on AWS. All workflows must use these runners instead of GitHub-hosted ones.

**x86 (Intel/AMD):**
```yaml
runs-on: [self-hosted, linux, x64]
```

**ARM64:**
```yaml
runs-on: [self-hosted, linux, arm64]
```

Runners scale automatically, they spin up on demand and terminate after each job. There is no queue wait time.

## Migrating a GitLab pipeline to GitHub Actions

<img src="https://i.makeagif.com/media/2-05-2021/mkErje.gif" alt="Pipelines!" width="400" />

If you have a `.gitlab-ci.yml` that needs to be converted to a GitHub Actions workflow, open a conversation with Claude and paste this:

```
I have this GitLab pipeline and need to migrate it to GitHub Actions for the repo [repo name]:

[paste your .gitlab-ci.yml here]
```

Claude will produce a ready-to-commit `.github/workflows/ci.yml` with the correct runner labels and all GitLab concepts mapped to their GitHub equivalents.

The skill and instructions are in [rootstack-ci-migration-skill](https://github.com/Rootstack-LLC/rootstack-ci-migration-skill).

## Resources

- [GitHub Organization Guidelines](https://github.com/Rootstack-LLC/rootstack-platform-utils) — naming conventions, teams, and access management
- [Platform Utils](https://github.com/Rootstack-LLC/rootstack-platform-utils) — organization-level automations
- [CI Migration Skill](https://github.com/Rootstack-LLC/rootstack-ci-migration-skill) — GitLab CI to GitHub Actions migration tool
