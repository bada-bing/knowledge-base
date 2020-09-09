# Liber Primus
- This is the initial repository of the project to migrate the SW knowledge content to github
- The idea is to store the information in a single place and make it easily accesssible and managable


### Contents ###
1. Javascript
    1. [Javascript](./js/README.md)
    2. [Node.js](./node/README.md)
    3. [Typescript](./ts/README.md)
2. [Linux](./linux/README.md)
3. [Tools](./tools/README.md)
4. [Important Computer Science Topics](./CS) - Currently: FP and regex
5. [Important Software Engineering Topics](./se) - Currently: FP and regex
6. [Meta-Learning](./meta-learning/README.md) - Learning about Learning

### Glossary
Monorepo	code for many projects is stored in a single repository
Preset	a preset is an association of plugins and configurations

## Standards
Keyboard Shortcuts: all 2-key shortcuts will be written in the following format **CTRL-f**
Text/Content Shortcuts: **dir** -> directory

### External Content/Courses ###
1. [Frontend-Masters](./courses/README.md)

### Books
1. [To mock a mocking bird](https://archive.org/details/Raymond_m._smullyan-to_mock_a_mockingbird_and_other_logic_puzzles__including__an/page/n6/mode/2up)

# Security
- For tools check also the recommendations from: https://www.privacytools.io/
Essential Security
1. Password Manager
2. VPN - keeps the physical location of your pc hidden
   - information & communication will be encrypted
   - Important to Consider:
     - It should be on all my devices (desktop, laptop, smartphone)
     - should not affect my internet speed a lot (it should be fast)
     - VPN should not track any data about me (any browsing data)
     - VPN Service should not be based in country which is part of "Five Eyes" Program (Australia, Canada, US, New Zealand, UK - especially US and UK)
   - Options:
     - [Linux Privacy oriented VPNs](https://itsfoss.com/best-vpn-linux/)
     - 2 most probable options right now are : Protonvpn vs expressvpn
       - also [Mulvad](https://thebestvpn.com/reviews/mullvad-vpn/)
       - also [OVPN](https://www.thevpnlab.com/reviews/ovpn-review/) (but the speed is not good)
       - also [Mozilla VPN](https://fpn.firefox.com/vpn)
3. 2fa - 2-Factor Authentification
  - list of websites which support 2fa: https://twofactorauth.org/
  - i.e., 2 pieces of puzzle to access your account (e.g., after logging-in you need to enter the code which you get over sms)
4. Other:
   1. Cover your cameras & microphone
   2. Consider Signal as messaging app (at least for important stuff)


# CSS & UI
## [WiredJS](https://wiredjs.com/)
- A set of common UI elements with a hand-drawn, sketchy look. These can be used for wireframes, mockups, or just the fun hand-drawn look.

[CSS Box Model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
- is this same as Flexbox?
## Flexbox
[Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox) general organization of content on the webpage
- [A Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [12-flexbox-tips-tricks-which-you-need-to-know-as-a-web-developer](https://medium.com/quick-code/12-flexbox-tips-tricks-which-you-need-to-know-as-a-web-developer-8d847695fb20)

- [Benefits of CSS preprocessors](https://htmlmag.com/article/an-introduction-to-css-preprocessors-sass-less-stylus)

- Tip1: CSS classes not be named for the style they apply, but rather the meaning of the style — i.e., don’t call it redAndBold, but rather activeMenuItem

# Web Components
Web Components
	1. In general we want to decouple the component's state from DOM
		- it is faster & it is less complicated
		- e.g., if we have a simple toggle-button (2 states: on and off)
		- Reading whether the toggle is on or off is a fast operation (in Javascript as the property of the object).
		- Much faster than looking up a class name or reading the text value of a DOM node. (e.g., if the class "is_active" is attached to the corresponding DOM element)
	- let’s have a go at separating things out. We’ll create a function (called render()) that will take the component’s state as a parameter. Then, given that state, it will work out what HTML should go in the DOM.

# MISC
- Best Practice 1: in general you should discourage using root for any operations. Do not ssh to your remote server as root. Create dedicated user and disable root.
	- you should create user with more privileges and disable completely login with root
- Best Practice 2: change the port where your ssh-agent (ssh-server) is (by default it is 42)
	- since it is default, hackers try by default to log in using this port
		- by changing the port it gives you some small amount of increased security
- X is in general used for "cross"
	- in US sometimes they use "Xing" for "crossing"
	- I suppose that is why Xing is called like that
In general "elastic computing" refers to "scalable computing", i.e., based on the demand

[if-python-is-interpreted-what-are-pyc-files](https://stackoverflow.com/questions/2998215/if-python-is-interpreted-what-are-pyc-files)
