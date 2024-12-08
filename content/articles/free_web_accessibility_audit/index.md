+++
title = "How to Run a Quick, Simple, Free, Web Accessibility Test Audit"
description = "You don't need to download or install special software. Your Chrome browser already has a built in free web Accessibility analysis and audit and reporting tool."
ShowPostNavLinks = false
author = ["Raj Duggal","Abi Vanniyasingam"]
hideMeta = false
[build]
    list = 'never'
+++

Chrome has a built in tool called [Lighthouse](https://developer.chrome.com/docs/lighthouse/overview) which can audit the web page you're visiting in both desktop browser and mobile browser modes.


## Step 1: Open the built in [Chrome Developer Tools](https://developer.chrome.com/docs/devtools)

* Open chrome
* In the top right corner, click the icon that contains a vertical column of three dots.
* Click "__More tools__".
* Click "__Developer Tools__".

![developer-tools](developer-tools.png)

## Step 2: Open the Lighthouse tab 

* Click the icon that contains two arrows pointing to the right.
![lighthouse](lighthouse.png)

* You will know you're in the right place, when the Lighthouse tab is underlined and in a blue font colour. Like this...
![lighthouse-tab](lighthouse-tab.png)

## Step 3: Configure the test report

* Check the "__Accessibility__" checkbox.
* Uncheck the the other checkboxes.
* Choose to generate the report for either how the web page will be displayed in "__Desktop__" computer mode, or "__Mobile__" phone mode.
* Click the "__Analyze page load__" button, and it will start analyzing the web page and generate a report.

![report](report.png)

## Step 4: Enjoy the report!

Check your audit score...

![result](result.png)

Did it score 100%?

Yipee!

Wait!

Don't get too excited!

This score ___only___ measures a [set of __automated__ accessibility audit tests](https://developer.chrome.com/docs/lighthouse/accessibility/scoring).

It's still necessary to perform [__manual accessibility testing__](https://web.dev/learn/accessibility/test-manual), which  uses keyboard, visual, and cognitive tests to find issues that these automated tools cannot.

Fortunately, there's plenty of resources online.

And, if you still need help you can [reach out to a web accessibility expert like me!](https://clarity.fm/rajduggal/precall/free)


