# **Real-time parser implementation**

The current editor updates its content using text blocks. So, when the user clicks on an element from the interface the previous content is deleted and replaced by the new one. This content is saved into an object called cdsl_document.

  This implementation works fine when the user interacts with the graphical interface, but presents a shortcoming when the user updates the text editor manually. This is because the written content is not saved in the cdsl_document variable, so every manual change gets lost.

  To fix this problem, we have developed a real-time parser for the text editor, using the method parseAction(). This parser is checking the text continually, displaying the errors when they occur and saving the content when it's correct. Using this solution, we can switch between writing and pushing buttons without losing the information.

**Automatic update of check-box and combo-box**

We have also implemented the automatic upgrade of the graphical interface elements. So, every time the user changes the content manually, the check-boxes and combo-boxes update its contents. This functionality has been achieved by manipulating the graphical interface signals.

**Other changes**
-   The interfaces are sorted alphabetically.
-   The editor displays now the line number.
-   A beta version of an error highlighter was created.
-   Feedback information is displayed on the console.
-   The application catches Ctrl+C from terminal to close it.
-   The user gets a message when closing the application.
-   Some graphical issues were fixed.
