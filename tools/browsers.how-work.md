[❓Need to distinguish what should be a theoretic knowledge (e.g., how browsers work) and what should be practical (e.g., extensions, shortcuts, ...)]
Inside Look at Modern Browsers
1. [Browser Architecture - Chrome](https://developers.google.com/web/updates/2018/09/inside-browser-part1)
2. [What happens in Navigation](https://developers.google.com/web/updates/2018/09/inside-browser-part2)
  - when you type URL in address bar, the input is handled by browser process's UI thread
  - [Mime Types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) and Mime Sniffing
    - MIME indicates the nature and format of a document, file, or assortment of bytes
    - [Overview of Page Lifecycle States and Events](https://developers.google.com/web/updates/2018/07/page-lifecycle-api#overview_of_page_lifecycle_states_and_events) & [Page Lifecycle API](https://developers.google.com/web/updates/2018/07/page-lifecycle-api)
    - Service Workers also run in renderer process
3. [Renderer Process](https://developers.google.com/web/updates/2018/09/inside-browser-part3)
  - Renderer Process is responsible for everything that happens inside of a tab
		- sometimes this process includes worker thread (for service workers) and sometimes compositor and raster threads
		- It parses HTML & Constructs DOM
		- It does subresource (assets) preloading
			- search in article for more details
	- IMPORTANT:
  	- if the script tag does NOT change the shape of DOM (if it has something like document.write …) you can add async or defer attribute to <script> tag
		- JS is then loaded asynchronously and does not block parsing of JS
		- [Resource Prioritization](https://developers.google.com/web/fundamentals/performance/resource-prioritization)
		- It does Style Calculation
  	- what kind of style is applied to each el based on CSS selectors
		- you can see this info in computed section in DEV tools
		- It does the layout - geometry of elements
			- there is layout tree which has x and y coordinates and bounding box sizes
			- Layout tree may be similar structure to the DOM tree, but it only contains information related to what's visible on the page.
      - Rasterizing
  	- turning the information about the structure of document, styles and layout  of each element into pixels on screen is called Rasterizing
    	- Layer Panel in Chrome Dev (https://blog.logrocket.com/eliminate-content-repaints-with-the-new-layers-panel-in-chrome-e2c306d4d752/?gi=cd6271834cea)
- 4. [Compositor](https://developers.google.com/web/updates/2018/09/inside-browser-part4)
  - 		- User Event (Input) is registered first by browser process
			§ it knows the coordinates and the content of the event and passes the data to rendereer process
			§ Rendererer Process then finds the event target and runs event listeners that are attached




