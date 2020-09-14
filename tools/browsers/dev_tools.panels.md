# Chrome DEV Panels
## Render Panel
	- check the webpage koalastothemax.com
	- You need to go into options and in "more tools" select rendering tab
		- there you choose "Paint Flashing"
		- You can observe which parts of the webpage are re-rendered/re-painted
		- The aim is to re-rerender as least as possible
			- the worst case is to re-render whole page with every page

## NETWORKING
	- Filters in networking panel are actually pretty smart
		- they can search for multiple types (e.g., JS and CSS, you just need to hold CTRL when clicking on each of these buttons)
		- additionally for the search filed (filter search field)
			- you can type text and it will search for requests which have that text in their response bodies or headers
	- If you hold shift and hover over certain file/request… it will show you in green the initial file/request which created it… and in blue/red for which files/requests that particular one is responsible
		- it doesn't always give me info which I want, but it is worth trying again

https://www.mattzeunert.com/2016/02/08/chrome-devtools-restart-frame.html

## SOURCE (Debugging)
Conditional Break Points (Yellow Color) - If "something" then stop execution
  - Column Break Points
    - it is not only that you can stop at certain row (but also in specific parts of the row) - check blue arrows in the row where you want to place a break point
  - DOM Breakpoint
    - Dev Tools can stop execution when some HTML DOM related change happens
      - element is removed or there are some attribute changes or sth. else
  - XHR Breaktpoint
    - this is really good
      - when some API requests are made Chrome can pause its execution
        - this enables you to see changes which happen when fetching data
  - Step through Debugger nije time travelling - ne mozes da vratis egzekuciji u nesto sto je vec izvrseno
    - Callstack trace jeste time travelling sa druge strane… mozes da vidis ko koga zove I kojim redom

CSS and DOM elements
	- regarding CSS, Computed tab shows the FINAL CSS rules
	- when you are working with some colors (e.g., in CSS) these colors are always in a specific format (e.g., RGB)
		○ you can change format by holding shift and clicking on the color (NOT ON THE COLOR CODE) where you want to change format (e.g., from hex to rgb)


❗CHECK❗ - https://www.freecodecamp.org/news/awesome-chrome-dev-tools-tips-and-tricks/
   1. DEV tools
    - Ctrl + P (to launch Omnibox/Command Pallete)
	- stuff like all the different tabs, go offline and online
    - F1 - go to settings
	- Permanent Blackboxing: u Blackboxing sekciji
		- Check **"Blackbox Chrome Extension Scripts"**
		- Ovde mozes da dodas sve fajlove koje ne zelis da vidis u stack trace-u I gde ne zelis da pauzira debuger… (webpack, …)
Skripte mozes da blackboxujes I iz call-stack-a (desni klik na neku od funkcija iz call stacka) I onda "blackbox script"


# Firefox Developer Tools
- In Mozilla Firefox they are about to introduce time-travelling debugger
[Firefox replay](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/WebReplay)
