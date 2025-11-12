[![add-on registry](https://img.shields.io/badge/DDEV-Add--on_Registry-blue)](https://addons.ddev.com)
[![tests](https://github.com/Metadrop/ddev-behat/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/Metadrop/ddev-behat/actions/workflows/tests.yml?query=branch%3Amain)
[![last commit](https://img.shields.io/github/last-commit/Metadrop/ddev-behat)](https://github.com/Metadrop/ddev-behat/commits)
[![release](https://img.shields.io/github/v/release/Metadrop/ddev-behat)](https://github.com/Metadrop/ddev-behat/releases/latest)

# DDEV Behat

## Overview

This add-on integrates Behat into your [DDEV](https://ddev.com/) project, providing a convenient `ddev behat` command that runs Behat tests inside the web container.

## Installation

```bash
ddev add-on get Metadrop/ddev-behat
ddev restart
```

After installation, make sure to commit the `.ddev` directory to version control.

## Usage

Once installed, you can run Behat tests using:

```bash
# Run all Behat tests
ddev behat

# Run specific feature file
ddev behat features/example.feature

# Run with specific tags
ddev behat --tags=@smoke

# Get help
ddev behat --help
```

## Configuration

### Behat Configuration

Behat configuration should be placed in your project's `behat.yml` file. Example:

```yaml
default:
  suites:
    default:
      contexts:
        - FeatureContext
  extensions:
    Behat\MinkExtension:
      base_url: http://web
      selenium2:
        wd_host: http://selenium:4444/wd/hub
```

### Requirements

Behat and its dependencies should be installed via Composer in your project:

```bash
ddev composer require --dev behat/behat
ddev composer require --dev drupal/drupal-extension  # For Drupal projects
```

## Credits

**Contributed and maintained by [@Metadrop](https://github.com/Metadrop)**
