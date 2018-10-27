# SlackExtract
A PowerShell script to extract all messages and files from a User's slack account. Or, optionally specify a limited number of channels to download from.

## From Windows command line enter powershell with scripts enabled:

```powershell -exec bypass```

## Import the Module:

```Import-Module .\SlackExtract.ps1```

## Read Usage Instructions:

 ```Get-Help Invoke-SlackExtract -full```

## Required Parameters

1. SlackUrl (e.g. https://slackextract.slack.com)
2. OutputFolderName (e.g. my-extraction)
3. dCookie (e.g. wvxP...8%3D)   OR   SlackToken (e.g. xoxs-12...65)

## Example 1: Extract all files and messages

This will extract all messages and files from each channel the user has access to (up to the default limits). The default output location is Document/SlackExtract. A folder will be created for each Channel.

### Providing the dCookie

```Invoke-SlackExtract -OutputFolderName my-extraction -SlackUrl https://slackextract.slack.com -dCookie wvxPLsXuW%2BUjT2b5RiCvb%2BUBPlJEX2XWbnVpOTlQZUN1TFF6dkxrNlZJbExYTzN6TmNtdFZNTDY0Y2pVQlF6UXlannhZMkprcHRueE12TVpXaXRvRWtQZGhidlhPdEh2d0J1a0I0UjcxMlRJV2JmTndDMlh1czNlUCt0SWIyczExb0z1ZCtxL3JJRW9tenJFRDhIdmp2MWVIQytLc3Q0RWZLSEFvdTQxUFE9PSy1X4xNmoY5wXzFlw2GJL8%3D```

### Providing the API Token

```Invoke-SlackExtract -OutputFolderName my-extraction -SlackUrl https://slackextract.slack.com -SlackToken xoxs-420083410720-421837374423-440811613314-977844f625b707d5b0b268206dbc92cbc85feef3e71b08e44815a8e6e7657190```

## How to Obtain the dCookie and/or the API Token

See the [Authorization page on the wiki](https://github.com/clr2of8/SlackExtract/wiki/Authorization) for details on obtaining the dCookie or the SlackToken.

## Default Limits

| Limit Parameters        | Default Value   
| :-------------: |:-------------:
| MaxMessagesPerChannel       | 10,000 
| MaxFilesPerChannel     | 2,000      
| MaxUsers  | 100,000
| MaxAccessLogs* | 1000,0000

\* Accessible to Admins of Paid Workspaces Only

## Example 2: Extract User Profiles

Extract the profile of each user, up to the 1000 users as specified by the *MaxUsers* parameter. The details of each user will be written as individual json files in the *meta/Users* directory. An *all_users.csv* file is also created for easy viewing and sorting of the data in Excel.

```Invoke-SlackExtract -ExtractUsers -MaxUsers 1000 -OutputFolderName my-extraction -SlackUrl https://slackextract.slack.com -SlackToken xoxs-420083410720-421837374423-440811613314-977844f625b707d5b0b268206dbc92cbc85feef3e71b08e44815a8e6e7657190```

## Example 3: Extract Data from Only Private Channels

```Invoke-SlackExtract -PrivateOnly -OutputFolderName my-extraction -SlackUrl https://slackextract.slack.com -SlackToken xoxs-420083410720-421837374423-440811613314-977844f625b707d5b0b268206dbc92cbc85feef3e71b08e44815a8e6e7657190```

## Example 4: Extract Data from Only Specific Channels

Provide a comma separated list of Channel IDs to extract data from. The channel ID can be seen in URL bar of a web browser when connected to a Slack workspace. You can also exclude specific Channels with the *ExcludeChannelIds* parameter.

```Invoke-SlackExtract -ChannelIds DD0081E5C,CCC2FCAE4,GD00AAMFY -OutputFolderName my-extraction -SlackUrl https://slackextract.slack.com -SlackToken xoxs-420083410720-421837374423-440811613314-977844f625b707d5b0b268206dbc92cbc85feef3e71b08e44815a8e6e7657190```

## Example 5: Extract Access Logs

Access logs contain the IP address, User Agent and of each user as the connect to the Slack workspace. To extract access logs, the user must be an admin of a paid workspace.

```Invoke-SlackExtract -ExtractAccessLogs -MaxAccessLogs 200 -OutputFolderName my-extraction -SlackUrl https://slackextract.slack.com -SlackToken xoxs-420083410720-421837374423-440811613314-977844f625b707d5b0b268206dbc92cbc85feef3e71b08e44815a8e6e7657190```


See the Wiki for additional notes.
