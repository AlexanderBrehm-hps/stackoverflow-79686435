# publish test

Seems to work over a UNC share when using .net sdk 8.0.110, but not 8.0.111

How to reproduce the issue:
- Ensure you have both .net sdk 8.0.110 and 8.0.111 installed.
- set the source/global.json's version to be 8.0.110
- navigate your command line to the source directory
- run `dotnet publish publish-test/publish-test.csproj --self-contained -r win-x64 -v d --output ./output-8-0-410`
- set the source/global.json's version to be 8.0.111
- run `dotnet publish publish-test/publish-test.csproj --self-contained -r win-x64 -v d --output ./output-8-0-411`

You should now have two folders that you can push to a UNC path to try and run the exe from. It's self contained, so you should just need to run the exe like so:
```
\\my-unc-path\output-8-0-410\publish-test.exe
```

If you look in the logs of Github-Actions, you can see the archives made by both builds, you should be able to download them from there and test them. I haven't gotten around to having them publish to a github release yet.
