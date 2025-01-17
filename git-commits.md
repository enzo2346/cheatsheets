## Summary

* [In Code](#in-code)
* [In Infrastructure as Code or in scripts](#in-infrastructure-as-code-or-in-scripts)

## In Code

A commit must describe what was change and why it was change. But it should not describe how it was change

```Text
name of the ticket (issue ID) - name of the project - description of the commit

ECPT-9999 - ICE-tool1 - add README.md to describe the installation process
```

[Back to top](#summary)

## In Infrastructure as Code or in scripts

A commit must describe what was change (in Caps Lock), then explain how it was change (with dash)

```Text
ADDING JAVA ECLIPSE PROJECT IN CI PIPELINE
- Test presence of build.xml
- Build app with ant cmd
- Launch unit test with buildtest.xml
```

Do not hesitate to do a interactive rebase to remove mistake from your commit history

[Back to top](#summary)