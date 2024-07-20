# Teams Test Results Notification

> Send Microsoft Teams message with test result from popular testing frameworks

![Example view](assets/results.png)

## Help us grow CTRF

⭐ **If you find this project useful, please consider following the [CTRF organisation](https://github.com/ctrf-io) and giving this repository a star** ⭐

**It means a lot to us and helps us grow this open source library.**

## Features

- **Send Test Results to Teams**: Automatically send test results to a Teams channel.
- **Send Flaky Test Details to Teams**: Automatically send flaky test details to a Teams channel.
- **Conditional Notifications**: Use the `--onFailOnly` option to send notifications only if tests fail.

## Setup

You'll need a CTRF report generated by your testing framework. [CTRF reporters](https://github.com/orgs/ctrf-io/repositories) are available for most testing frameworks and easy to install.

**No CTRF reporter? No problem!**

Use [junit-to-ctrf](https://github.com/ctrf-io/junit-to-ctrf) to convert a JUnit report to CTRF

### Create a Teams Incoming Webhook

Setup an incoming webhook by following instructions on [Teams documentation](https://learn.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook?tabs=newteams%2Cdotnet)

### Set the Environment Variable

Set the webhook URL as an environment variable in your shell or CI environment:

```sh
export TEAMS_WEBHOOK_URL='https://hooks.teams.com/services/your/webhook/url'
```

Make sure to replace `'https://hooks.teams.com/services/your/webhook/url'` with your actual webhook URL.

You might want to store the webhook URL as a secret.

## Usage

To send the test results summary to Teams:

```sh
npx teams-ctrf results /path/to/ctrf-report.json
```

![Results view](assets/results.png)

To send flaky test report to Teams:

```sh
npx teams-ctrf flaky /path/to/ctrf-report.json
```

![Flaky view](assets/flaky.png)

### Send Only on Failures

To send the test results summary to Teams only if there are failed tests, use the `--onFailOnly` option:

```sh
npx teams-ctrf results /path/to/ctrf-file.json --onFailOnly
```

or using the alias:

```sh
npx teams-ctrf results /path/to/ctrf-file.json -f
```

## Options

- `--onFailOnly, -f`: Send notification only if there are failed tests.

- ## Merge reports

You can merge reports if your chosen reporter generates multiple reports through design, parallelisation or otherwise.

The [ctrf-cli](https://github.com/ctrf-io/ctrf-cli) package provides a method to merge multiple ctrf json files into a single file.

After executing your tests, use the following command:

```sh
npx ctrf merge <directory>
```

Replace directory with the path to the directory containing the CTRF reports you want to merge.

## What is CTRF?

CTRF is a universal JSON test report schema that addresses the lack of a standardized format for JSON test reports.

**Consistency Across Tools:** Different testing tools and frameworks often produce reports in varied formats. CTRF ensures a uniform structure, making it easier to understand and compare reports, regardless of the testing tool used.

**Language and Framework Agnostic:** It provides a universal reporting schema that works seamlessly with any programming language and testing framework.

**Facilitates Better Analysis:** With a standardized format, programatically analyzing test outcomes across multiple platforms becomes more straightforward.

## Support Us

If you find this project useful, consider giving it a GitHub star ⭐ It means a lot to us.
