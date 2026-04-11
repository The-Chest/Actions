# v1.0.0

## What's Added

* **dotnet-build**: Action for building .NET projects with `dotnet restore` and `dotnet build`, including optional artifact upload
* **dotnet-test**: Action for running tests with optional XPlat Code Coverage collection in OpenCover format
* **get-version**: Action to extract version strings from Git references (tags or branches)
* **publish-nuget**: Action for packing and publishing NuGet packages to nuget.org (initial release - Work in Progress)
* **upload-release-artifacts**: Action for uploading binaries to GitHub Releases

## Known Issues

* `publish-nuget` action is currently marked as Work in Progress and may need refinements for production use
* Coverage output in `dotnet-test` action only supports OpenCover format
* The "v1" tag is not definitive and will change when the sonar and github package actions are finished

## What's Next

* Enhance `publish-nuget` action for production stability
* Add an Action to run a sonar scan 
* Add an Action to publish a package on Github Package

**Full Changelog**: https://github.com/The-Chest/Actions/releases/tag/v1.0.0