# PrestHubot

## Installation

* Install dependencies
```bash
composer install
```
* Fetch a Github Token : https://github.com/settings/tokens/new?description=PrestHubot&scopes=repo,read:org

## Configuration

You can using parameters :
* `--ghtoken=<ghtoken>`
* `--username=<ghusername> `

**OR**

You can use .env file :
* Copy .env.dist to .env
* Define your token & username from Github
```
GH_TOKEN=<ghtoken>
GH_USERNAME=<ghusername>
```

## Usage

### Check PR
Permits to check PrestaShop PR (and their status)

```bash
php bin/console github:check:pr
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--request=<request>` | No | Use the title of a search request or create your specific request |
| `--exclude:author=<ghusername>` | No | Exclude for displaying PR created by <ghusername> |
| `--exclude:reviewer=<ghusername>` | No | Exclude for displaying PR approved by <ghusername> |
| `--filter:file=<ext>` | No | Filter on extensions file (one or many separated by comma) |
| `--filter:numapproved=<ext>` | No | Filter on number of approved reviews (one or many separated by comma) |
| `--orderBy=<order>` | No | Order by columns (one or many separated by comma : projectName, id, createdAt) |

#### Samples

* Fetch PR to review with 1 or 2 approved reviews, excluding Progi1984's PR and PR that Progi1984 has approved

`php bin/console github:check:pr --request "PR Waiting for Review" --filter:numapproved=2,1 --exclude:reviewer=Progi1984 --exclude:author=Progi1984`

### Check Module
Permits to check PrestaShop Modules

```bash
php bin/console github:check:module
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--module=<module>` | No | Filter only one module |
| `--branch=<branch>` | No | Branch for searching files (default: master) |


#### Informations
| Column | | Notes|
| ------------- | ------------- | ------------- |
| Files | .travis.yml | Check if .travis.yml is present<br>Check if `before_deploy` & `deploy` are present in the file |

### Check Repositories
Permits to check PrestaShop Repositories

```bash
php bin/console github:check:repository
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--public` | No | Filter only on public repositories |
| `--private` | No | Filter only on private repositories |

### Get Notifications
Get Github Notifications

```bash
php bin/console github:notifications
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |

### Get Stats
Get some stats

```bash
php bin/console github:stats
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--username=<ghusername>` | Yes/No | Use it or use .env |

### Get Stats from repository
Get some stats

```bash
php bin/console github:stats:repository
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--repository=<repository>` | No | Just a repository in PS Organization or all the org if it is not defined |
| `--pr:date:created=<date>` | No | Filter on creation date for PR |
| `--pr:date:merged=<date>` | No | Filter on merge date for PR |

### Slack Notifier for Core Team
Notify on Slack :
- Nightly Build Status
- If PR are needed to merge
- PR to review
- Modules releases
- Modules improvements

```bash
php bin/console slack:notifier:core
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--slacktoken=<slacktoken>` | Yes/No | Use it or use .env |
| `--slackchannel=<slackchannel>` | Yes/No | Use it or use .env |

### Slack Notifier for QA Team
Notify on Slack :
- Nightly Build Status

```bash
php bin/console slack:notifier:qa
```

#### Parameters
| Parameter | Required | Notes |
| ------------- | ------------- | ------------- |
| `--ghtoken=<ghtoken>` | Yes/No | Use it or use .env |
| `--slacktoken=<slacktoken>` | Yes/No | Use it or use .env |
| `--slackchannel=<slackchannel>` | Yes/No | Use it or use .env |
