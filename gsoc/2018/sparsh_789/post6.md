# Help & Support

Till now I have added almost all functions that are useful for the tool. Now last but not the least part that remains is to make user familiar with tool. So, for that some documentation should be there. Instead of user to open documenation file separately, it would be better if he/she can open help from tool itself. So, I added help and support feature in tool.

For "help" I made 5 files each explaining some features of tools.

![Help image](/web/gsoc/2018/sparsh_789/help.png)

Now, for support I had to make mail system. I had already made mail sytem in php before so I was familiar with smtp. In Qt, there were some difficulties but after some effort I was able to make mail system. But one thing that was coming as issue was format of mail. Like "from" section of mail was not coming properly (It was coming as name of host of smtp server). So for that I use MIME. After that issue was solved. Then I had to make form for entering message details.

![Support image](/web/gsoc/2018/sparsh_789/support.png)
