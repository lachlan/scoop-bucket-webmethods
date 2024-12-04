# [IBM webMethods Service Designer] for [Scoop]

Provides a [scoop] [bucket] for installing [IBM webMethods Service Designer]
on Windows.

## Install

Follow these instructions on how to install [IBM webMethods Service Designer]
on Windows using [scoop]:

### Install [scoop]

Open a [PowerShell] terminal (version 5.1 or later) and run:

```bat
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

### Install [git]

Open a command line terminal `cmd.exe` and run:

```bat
scoop install git
```

### Add [scoop] [bucket]

Open a command line terminal `cmd.exe` and run:

```bat
scoop bucket add webmethods https://github.com/lachlan/scoop-bucket-webmethods
```

### Install [IBM webMethods Service Designer]

Open a command line terminal `cmd.exe` and run:

```bat
scoop install service-designer
```

## Update

To update your [IBM webMethods Service Designer] installation to the latest
version, open a command line terminal `cmd.exe` and run:

```bat
scoop update service-designer
```

## Maintain

For repository maintainers, follow these instructions to manually keep this
[git] repository up to date with new versions of Service Designer:

1. Locate the new Service Designer version's download image:
   * Download the new version from the [IBM webMethods Service Designer Download page][IBM webMethods Service Designer Download] in a web browser
   * Note down the downloaded zip file's URI link from the web brower's
     downloads window
   * Note down the Service Designer icon resource file name (with the
     extension `.ico`) by opening the downloaded zip file and looking in the
     `wmServiceDesigner\Designer\resources` directory

2. Calculate a new SHA256 hash for the downloaded file:
   * Ensure you have [git] installed on Windows, as it will include the
     `sha256sum` command in `<git_install_directory>\current\usr\bin\`
     directory
   * Open a command line terminal `cmd.exe` and run the following command,
     replacing the `<placeholder>` tags with the correct values, then note
     down the calculated SHA256 hash, which is the
     `2cbd117332b1a4d15f5489ad567af216458ee60163b692b971066bc37880ed6f` number
     in the below example:

```bat
C:\><git_install_directory>\current\usr\bin\sha256sum <downloaded_file_name>
2cbd117332b1a4d15f5489ad567af216458ee60163b692b971066bc37880ed6f *<downloaded_file_name>
```

3. Update the `service-designer.json` [scoop] [app manifest] in this
   repository with the details captured about the new version, replacing the
   `<placeholder>` tags with the correct values for the new version:

```json
{
    "version": "<designer_version_number>",
    "description": "IBM webMethods Service Designer <designer_version_number>",
    "url": "<designer_file_download_uri>",
    "hash": "<designer_file_sha256_hash>",
    ...✄...
    "shortcuts": [
        [
            "ServiceDesigner.exe",
            "Service Designer <designer_version_number>",
            "",
            "Designer/resources/<designer_icon_file>"
        ]
    ]
}
```

4. Commit, tag, and push changes to [git] repository

[app manifest]: <https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests>
[bucket]: <https://github.com/ScoopInstaller/Scoop/wiki/Buckets>
[git]: <https://git-scm.com/>
[IBM webMethods Service Designer]: <https://community.ibm.com/community/user/viewdocument/ibm-webmethods-service-designer-ava?CommunityKey=82b75916-ed06-4a13-8eb6-0190da9f1bfa&tab=librarydocuments>
[IBM webMethods Service Designer Download]: <https://www.ibm.com/resources/mrs/assets?source=WMS_Designers>
[PowerShell]: <https://learn.microsoft.com/en-us/powershell/>
[scoop]: <https://scoop.sh/>
