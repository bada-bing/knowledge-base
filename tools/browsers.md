[how browsers work](./browsers.how-work.md)
[dev tools](./browsers.dev_tools.panels.md)

https://send.firefox.com/
  simple private file sharing (with files which destroy themselves after some time)

- Parametrized Bookmarks in Firefox
  - alternative in Chrome is called Search Engines: chrome://settings/searchEngines

Extensions:
- CodeCopy - https://github.com/zenorocha/codecopy
- Octotree,
- Octolinker - https://chrome.google.com/webstore/detail/octolinker/jlmafbaeoofdegohdhinkhilhclaklkp/related
- Toby Mini, OneTab, Daily 2.0

1. Chrome/Chromium/Brave
   ❗CHECK❗ - https://www.freecodecamp.org/news/awesome-chrome-dev-tools-tips-and-tricks/
   1. DEV tools
    - Ctrl + P (to launch Omnibox/Command Pallete)
	- stuff like all the different tabs, go offline and online
    - F1 - go to settings
	- Permanent Blackboxing: u Blackboxing sekciji
		- Check **"Blackbox Chrome Extension Scripts"**
		- Ovde mozes da dodas sve fajlove koje ne zelis da vidis u stack trace-u I gde ne zelis da pauzira debuger… (webpack, …)
Skripte mozes da blackboxujes I iz call-stack-a (desni klik na neku od funkcija iz call stacka) I onda "blackbox script"
   2. Flags - ```chrome://flags```
    		- Interesting Flags:
      		- Global Media Controls - Play/Pause button for audio/video in Chrome
          - Extensions Toolbar Menu - declutter extensions
          - [Omnibox Suggestion Transparency Options](chrome://flags/#omnibox-suggestion-transparency-options)
          - Enable Reader Mode
          - Smooth Scrolling
          - Enable QUIC protocol (HTTP/3)
          - Enable a Temporary Filesystem for Incognito Browsing

Some websites block content for anyone using Incognito mode, which can become frustrating when you try to visit their webpage. With the Filesystem API in Incognito flag, it creates a temporary filesystem in memory, which is usually disabled in Incognito mode. This makes websites think you’re using a regular instance of Chrome, unblocking the content. After the window closes, if anything was saved during your session, it’s deleted immediately. To prevent websites from polling your browser to check if you’re using Incognito, enable the Filesystem API in Incognito flag:

2. Firefox
In Mozilla they are about to introduce time-travelling debugger
[Firefox replay](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/WebReplay)

Knowledge
- The [Source Code of Chromium](https://cs.chromium.org/chromium/src/net/base/mime_sniffer.cc?sq=package:chromium&dr=CS&l=5)
- Web browsers have inside-implementation of sqlite
	- this is probably how they are storing internal memory/data of webpages/sites
