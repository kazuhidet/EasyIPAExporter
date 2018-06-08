# A script for easily exporting IPA from xcarchive output by Apple's Xcode (Version 8 or later)
From Xcode 8, to export IPA files from pre compiled binaries with CLI (xcodebuild) you need to export IPA using 'xcodebuild -exportArchive' with the parameters read from the plist file specified with the '-exportOptionsPlist' option.

This script is useful for creating a plist file containing parameters for this and exporting the IPA file with xcodebuild.

## How it works
When this script is executed, it searches the .app or .appex directory in the directory specified by <archive dir>, and obtains the Bundle ID of the application or extension from Info.plist of each directory.

Next, it searches for mobile provisioning matching Bundle ID from mobile provisioning installed in Xcode (usually stored in '/Users /${USER_NAME}/Library/MobileDevice/ Provisioning Profiles/') using the acquired Bundle ID will.

Finally, write information on the combination of the Bundle ID and the discovered mobile provisioning UUID to 'exportOptioins.plist' and xcodebuild to get the IPA file.

## Instaall
Copy the easyIPAexporter file to any executable path.

## Usage:
easyIPAexporter <archive dir> <export dir> <export method>

### <archive dir>
Compile the application with xcodebuild and specify the location where the archive (.xcarchive) was output. (Usually specified by -archivePath)

### <export dir>
Specify the plist file containing parameters for exporting and the directory to write the IPA file to be exported. (If the specified directory does not exist, it will be created.)

### <export method>
The export method of the .app to generate the .ipa file. Should be one in 'development', 'ad-hoc', 'enterprise' or 'app-store'.
