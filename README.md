# Docker image with linters

[![Docker Hub](https://img.shields.io/badge/-Docker_Hub-0062cc?style=for-the-badge&logo=Docker&logoColor=white)][docker-hub]

In this Docker image, you will find some linters for your projects.

```shell
docker pull alvarofpp/linter:latest
```

Linters in this image and which command to invoke it:

| Linter                          | Command                       | Config file       |
|---------------------------------|-------------------------------|-------------------|
| [Commit (git)][linter-commit]   | `lint-commit <target_branch>` | `.commitlintrc`   |
| [Dockerfile][linter-dockerfile] | `lint-dockerfile`             | `.hadolint.yaml`  |
| [Markdown][linter-markdown]     | `lint-markdown`               | `.markdownlintrc` |
| [Python][linter-python]         | `lint-python`                 | `.ruff.toml`      |
| [Shell script][linter-shell]    | `lint-shell-script`           | `.shellcheckrc`   |
| [YAML][linter-yaml]             | `lint-yaml`                   | `.yamllint`       |

You can create a `.lint/` directory with your linters configs,
exceptionally the `.shellcheckrc` file must be in the main directory.

## How to use

```shell
docker run --rm -v $(pwd):/app alvarofpp/linter " \
  lint-commit origin/main \
  && lint-markdown \
  && lint-shell-script \
  && lint-yaml"
```

## Manual test

Build the image:

```shell
docker build -t alvarofpp/linter .
```

Run the command below to start using an image container for testing:

```shell
docker run -it --rm -v $(pwd):/app alvarofpp/linter /bin/bash
```

[docker-hub]: https://hub.docker.com/r/alvarofpp/linter
[linter-commit]: https://github.com/conventional-changelog/commitlint
[linter-dockerfile]: https://github.com/hadolint/hadolint
[linter-markdown]: https://github.com/igorshubovych/markdownlint-cli
[linter-python]: https://github.com/astral-sh/ruff
[linter-shell]: https://github.com/koalaman/shellcheck
[linter-yaml]: https://github.com/adrienverge/yamllint
