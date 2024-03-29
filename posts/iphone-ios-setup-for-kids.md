
# iOS Setup for Kids (iPhone/iPad)
#### April 25th 2019

This is the basic iOS setup for iPhone I use to setup my kids iOS phone (and to an extent, mine too). As of writing the current version is 12.2.0 but I started when this was 12.1.x. The primary goals are control and privacy, and we went through it together, using it as an excercise with questions and discussion on how the internet works. 

We use Google's applications for email, calendar, and documents and this guide reflects that. In most cases you can substitute that with other services (like Apple's own iCloud which you get by having an Apple ID).

I recommend many of these steps for everyone. You should ask yourself 'Why would I do this?' at regular intervals. 

Please let me know if you catch mistakes or something that is no longer valid.

## Privacy, Ad Blocking & Tracking Apps

* 1Blocker or [Firefox Focus](https://itunes.apple.com/us/app/firefox-focus-privacy-browser/id1055677337)
   * I lean more towards "Firefox Focus" these days.
   * General recommendation is to pick one Content Blocker app and not multiple (slows things down)
   * Installed "1Blocker Legacy" (free), maybe "1Blocker" (paid)
   * [1Blocker FAQ](https://1blocker.com/faq/)
* "[1.1.1.1](https://itunes.apple.com/us/app/1-1-1-1-faster-internet/id1423538627)"
  * DNS and privacy from Cloudflare
  * Further reading: [Cloudflare’s speedy 1.1.1.1 DNS service now available on iOS and Android](https://www.theverge.com/2018/11/12/18087014/cloudflare-dns-service-ios-android-app) (Nov 2018)

## General nice apps to have

### Applications
* [The New York Times](https://itunes.apple.com/us/app/the-new-york-times/id284862083)
* [The New Yorker Today](https://itunes.apple.com/us/app/the-new-yorker-today/id1081530898)
   * Expand your mind and read whatever you like (subscription required)
* [Dark Skies](https://itunes.apple.com/us/app/dark-sky-weather/id517329357)
   * ToDo check [privacy policy](https://darksky.net/privacy)
* [Docs](https://itunes.apple.com/us/app/google-docs-sync-edit-share/id842842640)
   * Requires a _Google_ account.
* Spotify
   * We have Premium Family account and created her own account

### Games
This was heavily influenced by apps I already had on my phone and they already liked.

* Postnight
* Dots
* [Alto's Odyssey](https://itunes.apple.com/us/app/altos-odyssey/id1182456409)
* [Monument Valley](https://itunes.apple.com/us/app/monument-valley/id728293409)
* One Night
    * Companion app to board game [One Night Ultimate Werewolf](https://www.amazon.com/Bezier-Games-Night-Ultimate-Werewolf/dp/B00HS7GG5G/?tag=readah_20) (Referral link)

## Standard iOS Apps

Bear in mind that some of this has additional coverage later in _iOS Settings_ 

* Mail
    * Connected with Gmail which requires a Google account.
* Calendar
    * Connect with Google Calendar
* FaceTime
    * Setup with Apple ID
    * Disabled "FaceTime Live Photos"
* Messages
    * Setup with Apple ID
    * Settings you might want to think about...
      * Disabled "Send Read Recipts" (you might want to think about this one yourself)
      * Disabled "Send as SMS" (I would do this if phone plan allows low number of SMS messages)
      * "Keep Messages" - do you really need them "Forever"? I set this to "1 Year". Less is more.
    * "Filter Unknown Senders"
      * I planned to leave this disabled for first 3 months as we collected contact info.
      * Set a calendar reminder to enable after 3 months.
    * "Low Quality Image Mode"
      * Enable of you're not sending cherished photos (consider AirDrop instead) or have data plan limits
* Contacts
    * Added parents, siblings, and caregivers
    * Added the "Relationship" field (not a default)
    * Added the "Nickname" field (not a default) for friendlier names ("Mom") without stomping over the real name.
* Podcasts
    * Subscription to some content to start

## iOS Settings

The background motivation here is to reduce passive tracking, basic security, and also unnecessary notifications.

Turn on the phone, and starting at the Home Screen...

* Settings > General
    * Go to "About" and give your phone a meaningful name.
      * Nothing too personal as this will appear in places like AirDrop, Hotspot, Find My Friends etc.
    
* Settings > General > Background App Refresh
    * Turn "Books" _Off_
    * Turn "Maps" _Off_
    * Turn "News" _Off_
    * Turn "Stocks" _Off_
    * You can also set "Background App Refresh" to happen over "Wi-Fi" only
* Settings > General > Airdrop
    * Set this to "Contacts Only"
    * Further Reading: [Sending Lewd Nudes to Strangers Could Mean a Year in Jail](https://www.nytimes.com/2018/11/30/nyregion/airdrop-sexual-harassment.html) (NYTimes, Nov 2018)
* Settings > Bluetooth: _Off_
  * If you have a Bluettoth device this is a good time to have your child (not you) do the pairing process
* Settings > Notifications
    * For 'Notification Style', manually set "Allow Notifications" to _Off_
        * Except for harmless apps like Calendar etc.
        * Turned off _Sound_ on mostly everything else
        * For "Photos"
            * Shared Albums
                * Disabled Sound
                * Changed "Photo Options" to "Show Alerts from My Contacts"
            * Sharing Suggestions
                * Set "Allow Notifications" to _Off_
            * Memories
                * Set "Allow Notifications" to _Off_
    * Government Alerts 
      Decide if you want to do this. In a decade I've found them annoying and irrelevant.
      * Turn AMBER Alerts: _Off_
      * Emergency Alerts: _Off_
    * Siri Suggestions: 
      * Turned all _Off_ except for:
        * Calendar, Clock, Contacts, 
        * Find Friends, 
        * Maps, Messages, 
        * Settings, Safari, 
        * Wallet
* Settings > Sounds
    * Set "Sent Mail" to "None"
    * Turn "Keyboard Clicks" _Off_ (unless you really want to hear them when they type)
* "Cellular"
    * In the app list under "Cellular Data", consider disabling (limiting them to working on Wi-Fi):
        * App Store
        * Photos
* "Siri & Search"
    * Turn "Allow Siri When Locked" _Off_
    * Turn all three "Siri Suggestion" options _Off_
    * In the list of apps disable "Siri and Suggestion" in all
        * Exceptions might be Contacts, Calendar, etc
        * If you don't have an Apple Watch you should set "Show app" to _Off_ in "Watch"
* "Touch ID & Passcode"
    * Add a fingerprint for the parent
      * Consider giving it a name that indicates this
    * Highly recommended that you do not use a "4-Digit Numeric Code" 
        * Instead opt for "Custom Numeric Code" and use at least 5 numbers 
    * Highly recommended that keep "Require passcode" at "Immediately"
        * For practical reasons we set ours to "After 1 minute"
* "Emergency SOS"
    * Take a moment to set up an emergency contact in Health app
* "Privacy"
    * In "Location Services"
        * "System Services"
            * Disable the following:
                * Location-Based Alerts (maybe?)
                * Location-Based Apple Ads
                * Location-Based Suggestions
                * Wi-Fi Networking
                * iPhone Analytics
                * Popular Near Me
            * Set "Status Bar Icon" to _On_
    * In "Advertising"
        * Set "Limit Ad Tracking" to _On_
        * Try and remember to return weekly or monthly and tap the "Reset Advertising Identifier..."
* “Music”
    * Turn off “Show Apple Music”
    * Turn off “Cellular Data” (if you want to)
    * Enable “Volume Limit” and set it below maximum.
* “Game Center"
    * Disable "Game Center"
* "Safari"
    * Change default "Search Engine" from Google to "DuckDuckGo"
    * Disable "Search Engine Suggestions"
    * Disable "Safari Suggestions"
    * Disable "Preload Top Hit"
    * Disable "Check for Apple Pay"
    * Enable "Ask Websites Not to Track Me"
      * This not honored by majority of web sites, but it's worth standing your ground on this. With GDPR regulations in force in the EU, and laws coming into effect in California in 2020, this might become practical again.

## Delete

Consider deleting these apps if you don't use them:
* Home
* Watch
* Stocks
* News
  * This is one to re-visit in a few months/years. Right now it seems to surface a lot of tabloid and click-baiting sources.

## Contacts

Add a contact for every member of the family. Don't forget to include Street Address and backup phone numbers. I've found using the "Nickname" and "Relationship" fields very handy. Don't forget to have primary contacts set as Favorites.

With “Relationships” properly setup in contacts, they can say “_Hey Siri, call mom_”.

## Basic Concepts They Should Know

This is worth googling and reading more in.... #todo

* It's illegal to force someone to provide a passcode or password but not to use Touch ID to unlock a phone
* Tapping the ??? button 5 times calls Emergency Services
* How tracking and advertising on the web works
* Phones are essentially harmful to children but don't take my word for it
