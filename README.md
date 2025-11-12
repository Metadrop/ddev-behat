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

After installation:
1. Boilerplate files (`behat.yml`, `features/` directory) are automatically copied to your project root (existing files are not overwritten)
2. Install Behat and dependencies by running:
   ```bash
   ddev setup-behat
   ```
3. Commit the `.ddev` directory to version control

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

### Automatic Setup

Running `ddev setup-behat` automatically installs:
- `behat/behat` - Core Behat framework
- `metadrop/behat-contexts` ^1.0 - Metadrop's Behat contexts and utilities
- `drupal/drupal-extension` - Drupal-specific Behat extensions
- `behat/mink` - Browser emulation framework
- `behat/mink-selenium2-driver` - Selenium WebDriver integration
- `behat/mink-goutte-driver` - Headless browser driver

### Behat Configuration

A `behat.yml` configuration file is automatically created during installation. You can customize it for your project:

```yaml
default:
  suites:
    default:
      paths:
        - '%paths.base%/features'
      contexts:
        - FeatureContext
        - Metadrop\Behat\Context\DebugContext
        - Metadrop\Behat\Context\UIContext
  extensions:
    Behat\MinkExtension:
      base_url: 'http://web'
      sessions:
        default:
          selenium2:
            wd_host: 'http://selenium-chrome:4444/wd/hub'
            browser: chrome
    Drupal\DrupalExtension:
      api_driver: 'drupal'
      drupal:
        drupal_root: '/var/www/html/web'
```

### Manual Installation

If you prefer to install Behat manually:

```bash
ddev composer require --dev behat/behat metadrop/behat-contexts:^1.0
ddev composer require --dev drupal/drupal-extension behat/mink behat/mink-selenium2-driver behat/mink-goutte-driver
```

## Credits

**Contributed and maintained by [@Metadrop](https://github.com/Metadrop)**
