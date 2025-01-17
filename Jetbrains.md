## Summary

**-> [Back to Index](./README.md)**

* [Keyboard Shortcuts](#keyboard-shortcuts)
* [Interactive Rebase](#interactive-rebase)
* [Command-line Interface](#command-line-interface)

## Keyboard Shortcuts

| Keyboard Shortcut | Description                                            |
|-------------------|--------------------------------------------------------|
| Alt + n           | Open left bar tool number n                            |
| Alt + Enter       | Preview warnings or use intentions and apply quick-fix |
| Alt + F7          | Find usages                                            |
| Shift + F10       | run the code                                           |
| Shift x 2         | Search everywhere                                      |
| Ctrl + Shift + F  | Find in files                                          |
| Ctrl + Space      | Show completion                                        |
| Ctrl + E          | Recent files                                           |
| Ctrl + NUMPAD /   | Add/Remove comment                                     |
| Ctrl + Shift + t  | Create test                                            |
| Ctrl + Alt + B    | Navigate to implementation                             |
| Ctrl + Alt + L    | Reformat code                                          |
| Ctrl + Alt + S    | Settings                                               |

[Back to top](#summary)

## Interactive Rebase

This tutorial is showing how to use interactive rebase in JetBrains IDE with the new UI

1. Click 1. Click on the "Git" tab in the bottom left corner of the Intellij window.on the "Git" tab in the bottom left corner of the Intellij window.
2. Click on the "Log" tab in the top left corner of the Git window.
3. Select the branch you want to rebase.
4. Right-click on the commit you want to rebase and select "Interactive Rebase from Here".
5. In the "Interactive Rebase" dialog box, make the desired changes.
6. Click on the "Start Rebasing" button.
7. Type `git push --force` in the terminal to push the rebased commits to the remote repository.

[Back to top](#summary)

## Command-line Interface

To use Jetbrains IDE in command-line, add it to the windows PATH:

```shell
C:\Program Files\JetBrains\IntelliJ IDEA\bin
```

You can then open and use functions of IJ in cli

Usefull ressources:

- https://www.jetbrains.com/help/idea/working-with-the-ide-features-from-command-line.html
- https://www.jetbrains.com/help/idea/lightedit-mode.html

[Back to top](#summary)
