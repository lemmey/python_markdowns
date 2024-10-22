___
[[GitHub]]
[[CLI - Command Line Interface (shell)]]
[[version_control]]
#git
___

## Begriffe

#### Repository

Ein Verzeichnis, in dem jegliche Änderungen von Git nachvollzogen werden.
CLI Tip to locate hidden .git files, hence identifying your local repositories:
```
Get-ChildItem . -Attributes Directory+Hidden -ErrorAction SilentlyContinue -Filter ".git" -Recurse
```

To delete a git-marked repository, navigate to path and:
```
rm -Recurse -Force .git*
```
This will remove the .git folder, and all the .gitignore, .gitattributes files in Windows PowerShell.
#### Branch

#### Commit

#### Push

#### Fetch

#### Merge

#### Pull (Fetch + Merge)

#### Cursor



___
## Remote


___
## Local