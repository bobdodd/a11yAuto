# a11yAuto
Demonstrations of automated accessibility testing techniques that use AI.

The test is designed ot run Anthropic's Workbench tool, not directly
on the API with the tool generally runnin with 4,000 inoput tokens and
a Temperature of 1.0. This is the maximum allowed in Workbench. The
same prompts have also been tested with the Opus API running with 
200,000 input tokens in order to parse larger source files. Here we
limit ourselves to one small, if buggy, web page.

Five demos are provided that test for accessibility issues generally 
not covered by "classic" automated accessibility testing. Each demo
consists of: a prompt used to drive Anthropic's Claude.ai Opus model,
The response from Claude, a screenshot of the page being tested, and
a discussion document on the test.

Taking each demo in turn:

1. Language

This, relatively simple, demo inspects web pages for the human language used, looking to see what the dominant language is from the text itself, not relying on the HTML "lang" attribute, but comaring the result with it to see if the lang attribute is correct. This is something that is not provided currently by commercial automated testing and improves on reporting of WCAG Success Criteria 3.1.1 Language of Page.

The demo also considers text not in the dominant language of the page, and whether they are correctly wrapped in their ong lag attributes. This test is not available currently in commercial automated accessibility and provides a full test of WCAG 3.1.2 Language of Parts which currently must be found though close manual inspection of page text.

2. Headings

This demo inspects web pages looking for headings that have NOT been correctly marked up in HTML. Classic existing automated ccessibility test tools test the semantics found, or lack of them, they don't find non-marked up content. This demo does. It reports on apparent headings that are not marked up, and marked up headings that are not currently visible (i.e. obscured on screen). The issues found reportable as WCAG Success Criteria fails of 1.3.1 Info and Relationships and 2.4.7 Focus Visible.

3. Positioning

This demo inspects web pags looking for two common code blocks: cookie notices and language switchers. FOr those found, it looks to see how easily the may be tabbed to with the keyboard, and whether they are found within the window of a screen magnifier at 400% without veritcal scrolling. We test for these cases as it impacts on navigability of the web page with assistive technology. Sites and pages that do not support nornal usage of assistiv e technology fail confirmance according to WCAG section 5.2.4.
The demo also picks up some syntax and role issues that would be WCAG Success Criteria 4.1.2 Name, Role, Value fails.

4. Interactivity

This demo looks for unreachable content by comparing tab order with sreenp-reader style reading order. It also identifies drop-down menus and disculosure widgets looking for missing "aria-expanded" attributes. WCAG Success Criteria fails are identifable for 1.3.1 Info and Relationsips, 2.4.3 Focus Order, and 4.1.2 Name, Role, Value.

5. Modal Dialogs

This demo is focused specifically on modal dialogs, looking to detect them, to detect how they are opened and closed, and the structure of the dialog (heading, close button, escape key closure, inert background). It aims to catch issues shuch as focus not moving to the dialog on open, and not returning to the initiating element on closure. Generally none of the issues found by this demo are currently available in commercial automated test tools. A heads up: this is the most fragile of the demos, and relies heavily on the AI for detection; it needs significant testing in real-world situations to validate its usefulness.


