[![add-on registry](https://img.shields.io/badge/DDEV-Add--on_Registry-blue)](https://addons.ddev.com)
[![tests](https://github.com/Metadrop/ddev-behat/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/Metadrop/ddev-behat/actions/workflows/tests.yml?query=branch%3Amain)
[![last commit](https://img.shields.io/github/last-commit/Metadrop/ddev-behat)](https://github.com/Metadrop/ddev-behat/commits)
[![release](https://img.shields.io/github/v/release/Metadrop/ddev-behat)](https://github.com/Metadrop/ddev-behat/releases/latest)

# DDEV Behat

## Overview

This add-on integrates Behat into your [DDEV](https://ddev.com/) project.

## Installation

```bash
ddev add-on get Metadrop/ddev-behat
ddev restart
```

After installation, make sure to commit the `.ddev` directory to version control.

## Usage

| Command | Description |
| ------- | ----------- |
| `ddev describe` | View service status and used ports for Behat |
| `ddev logs -s behat` | Check Behat logs |

## Advanced Customization

To change the Docker image:

```bash
ddev dotenv set .ddev/.env.behat --behat-docker-image="ddev/ddev-utilities:latest"
ddev add-on get Metadrop/ddev-behat
ddev restart
```

Make sure to commit the `.ddev/.env.behat` file to version control.

All customization options (use with caution):

| Variable | Flag | Default |
| -------- | ---- | ------- |
| `BEHAT_DOCKER_IMAGE` | `--behat-docker-image` | `ddev/ddev-utilities:latest` |

## Credits

**Contributed and maintained by [@Metadrop](https://github.com/Metadrop)**
