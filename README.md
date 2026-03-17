# TitleIdUpdater

This script is used to batch process Trackmania `.Map.Gbx` files in a specified folder (and its subdirectories). It parses each map file, checks its `TitleId`, and if the `TitleId` matches a specific value (`OrbitalDev@falguiere`), it changes it to `TMStadium` and overwrites the original file in-place.

## Features

- Recursively processes all `.Map.Gbx` files in a given directory.
- Continues processing even if an individual map file fails to parse.
- Tracks and displays a summary of the analysis at the end:
  - Total number of files processed successfully.
  - Number of files that had their `TitleId` changed.

## Requirements

This script relies on the [GBX.NET](https://github.com/BigBang1112/gbx.net) library to parse and save Trackmania map files. The required packages are referenced at the top of the file:
```csharp
#:package GBX.NET@2.*
#:package GBX.NET.LZO@2.*
```

## Usage

You can run this script using `dotnet-script` or compile it as a standalone executable. 

Provide the path to the folder containing your maps as the first argument:

```bash
# Using dotnet-script
dotnet script TitleIdUpdater.cs "C:\Path\To\Your\Map\Folder"

# Alternatively, if compiled to an executable or using `dotnet run` 
dotnet run TitleIdUpdater.cs "C:\Path\To\Your\Map\Folder"
```

## Example Output

```text
Saved: C:\Path\To\Your\Map\Folder\Campaign1\Map1.Map.Gbx
Failed to process C:\Path\To\Your\Map\Folder\CorruptMap.Map.Gbx: Exception message here
Saved: C:\Path\To\Your\Map\Folder\Campaign1\Map2.Map.Gbx

Analysis complete.
Files analyzed successfully: 15 out of 16
Title IDs changed: 2
```
