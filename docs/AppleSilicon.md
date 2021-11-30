# Apple Silicon on macOS Big Sur 11 beta, October 2, 2020

1 Safari on Big Sur can not currently inspect "My Mac" targets, so the weak xCode console is all we have for now.  
See Apple [Universal App Quick Start] private forum [662281](https://developer.apple.com/forums/thread/662281?login=true).  Also
a Qpple Beta Feedback Assistant issue has been lodged (FB8755308) titled "No Inspectable Applications" in Safari Debug Menu for targets with "My Mac" -- No response yet from Apple.
1. node-sass is tied to macOS versions, so it is not available for Big Sur yet.  Hopefully we will design it out 
of the We Vote Web App this year.  In the mean time, we need to build main.css on an intel Mac, and copy it to the 
Apple Silicon (ARM64) mac in order to have all the legacy styles work.
1. Firebase is not ready for Big Sur, so it has to be manually removed from WeVoteCordova, so we lose notification
in iOS until it is ready.  Remove "cordova-plugin-firebase-analytics" and "cordova-plugin-firebase-messaging" to stop compile errors.
1. cordova.plugins.diagnostic is needed to detect which processor the app is running on, so it is needed for the Apple Silicon build.
1. The Sign in with Twitter and Facebook are currently unavailable since there is a problem where opening a "tab" with corodova-plugin-inappbrowser
opens an empty modal dialog, and then opens the actual URL you send it in a tab in the Safari desktop browser, breaking oAuth 
flow. See [Universal App Quick Start] private forum issue [662697](https://developer.apple.com/forums/thread/662697)