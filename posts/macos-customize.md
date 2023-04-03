# macOS Customziations
#### 2021-07-19

### Disable Dictionary.app

Disable the Dictionary.app so it doesn't always pop-up when you accidentally highlight something, or sneeze.
 
Make these changes in the _System Preferences_ but note that you may need to adjust settings on some apps too.

* Open System Preferences > Keyboard > Shortcuts
* Click Services
* In Searching section, look for "Look Up in Dictionary" option
* Remove the checkmark

* Click the _Show All_ icon (grid of dots) to get back to System Preferences
* Open Trackpad
* Remove the checkmark for "Look up & data detectors"
* Remove the checkmark for "Force Click and haptic feedback"

### TextEdit: Open with a blank file by default

TextEdit should launch and present a blank file by default - and not a file picker. 

Open iTerm or Terminal apps and run this:

`defaults write com.apple.TextEdit NSShowAppCentricOpenPanelInsteadOfUntitledFile -bool false`

To do this for all apps, try:

`defaults write -g NSShowAppCentricOpenPanelInsteadOfUntitledFile -bool false`

Restart TextEdit.

To restore, try:

`defaults delete -g NSShowAppCentricOpenPanelInsteadOfUntitledFile`

