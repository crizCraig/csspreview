csspreview is now cqstyle and can be found at http://code.google.com/p/cqstyle/  and http://www.cqstyle.com

_Idea_

This project intends to reduce the arduous edit, save, refresh IE, refresh Firefox, web page design cycle to just edit. Sliders, color pickers, etc can also greatly increase productivity in such a tool. Many paid programs exist, but none of them update multiple browsers at a time and since they're paid, they're obviously closed source.

_Proposed implementation_


My idea is to execute javascript, jQuery in particular, to change element's styles in real time using Selenium to hook into the browser. Using Selenium allows multiple browsers to be updated at once and ensures continuous support for the most relevant browsers. Selenium's HTTP API means the interface can also be a web app and therefore enjoy the cross-platform, forward looking goodness that web apps embody.

So, for example, say a user slides the slider responsible for the left margin of a class called test\_class. Then, AJAX calls will be made from the web app to the Selenium API's getEval function with new values for the margin.

Since jQuery is used, we first check that it's available within the target page's document before sending the margin values. If not, we use getEval to load in jQuery. We can go an extra step and check any jQuery version already being used on the page to make sure it's greater or equal to the one we want load in. jQuery could then select all the elements that have the class 'test\_class' into an array, removeClass('test\_class') and add the new style with the changed margin.

The web app could have options on which browsers to start and could handle Selenium sessions accordingly.

To get around the cross site scripting limitations of javascript, Selenium would have to be modified to allow JSONP or perhaps even serve the web app.

Since a web app does not have good access to the file system to save, the CSS can initially be copied from the web app editor to the file. Eventually, Selenium could be modified to save the css file.

_Note_

XRefresh offers a good start to what is being proposed and updates multiple browsers after saving. I've been using this and now depend on it, but still see a big need to reduce the process further to just editing and automatically seeing results with a guarantee that no refresh will occur. No refresh is nice for web apps that have long load times like Gmail.

I've also noticed that YUI offers some nice sliders and widgets that could be used for the editor.