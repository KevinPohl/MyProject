## MyProject

### environment
I work on a windows computer with bash in Visual Studio Code.

### create public repository on GitHub
With a click on the "+"-sign in the upper left corner on the GitHub main page a dropdown opens:
![screenshot of the button for new repository on GitHub](screenshots/new_repo_1.jpg)
There a click on "New Repository" opens a new site:
![screenshot of blank new repository form on GitHub](screenshots/new_repo_2.jpg)
Filled out, the form looks like this:
![screenshot of filled out new repository form on GitHub](screenshots/new_repo_3.jpg)
After creating the repository, i look up the link to the repository from the Code Button
![screenshot of repository link after creating a new repository on GitHub](screenshots/new_repo_4.jpg)
From there i keep the link [git@github.com:KevinPohl/MyProject.git](git@github.com:KevinPohl/MyProject.git) for later use.
After that i rename the main branch into master in the repository settings.
![](screenshots/new_repo_5.jpg)
### setting up the ssh key
The command `ls ~/.ssh/` leads to this output:
```git
id_rsa_github  id_rsa_github.pub  known_hosts  known_hosts.old
```
There is no further need to set up a new ssh key, as the files id_rsa_github and id_rsa_github.pub are already present in the directory, the .pub is uploaded to GitHub, as the page [https://github.com/settings/keys](https://github.com/settings/keys) shows.
![GitHub page for viewing ssh and other keys](screenshots/ssh_key.jpg)
## create local repository
changing to favored local project directory with these commands
`$ cd /e/Program\ Files/velptec/GitHub/Teilpruefungsleistungen/`

cloning the online repository locally with
`$ git clone git@github.com:KevinPohl/MyProject.git`
```git
Cloning into 'MyProject'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```
There i first create a folder to save all screenshots
`$ mkdir MyProject/screenshots`
and move all currently created screenshots there, which were temporarily saved in the subfolder "screenshots" of the main directory "Teilpruefungsleistungen":
`$ mv ./screenshots/ ./MyProject/`

Then, i move this document to the project folder, which was temporarily saved in the main directory Teilpruefungsleistungen and was called README\.md:
`$ mv README.md ./MyProject/`

After that, i change the directory to the project directory with `$ cd MyProject`, set up my config name `$ git config user.name "Kevin Pohl"`
```git
```
and email
`$ git config user.email "pohl.kevin@gmail.com"`
```git
```
`git config --get user.name`
```git
Kevin Pohl
```
`git config --get user.email`
```git
pohl.kevin@gmail.com
```
### initial commit
I create the file main\.py in MyProject with `$ touch main.py`, add several files to staging:
`$ git add main.py`
`$ git add README.md`
`$ git add ./screenshots/*`

and do an initial commit:
`$ git commit -m "initial commit"`
```git
[main (root-commit) 0906f5c] initial commit
 7 files changed, 51 insertions(+)
 create mode 100644 README.md
 create mode 100644 main.py
 create mode 100644 screenshots/new_repo_1.jpg
 create mode 100644 screenshots/new_repo_2.jpg
 create mode 100644 screenshots/new_repo_3.jpg
 create mode 100644 screenshots/new_repo_4.jpg
 create mode 100644 screenshots/ssh_key.jpg
```
I create and activate a new branch named feature `git checkout -b feature` (personally, i prefer `git switch -c feature`):
```git
Switched to a new branch 'feature'
```
On branch feature, i create a subdirectory and a file inside:
`$ mkdir utils`
`$ touch ./utils/database.py`.
I add and commit the changes:
`$ git add utils/database.py`
```git
```
`$ git commit -m "new feature added"`
```git
[feature f5cb98c] new feature added
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 utils/database.py
```
Back to main with
`$ git checkout main`

i add some code to main.py with
`$ printf "if __name__ == "__main__":.    print("hi there")" > main.py`

I then add the file to staging and commit
`git add main.py`
```git
warning: in the working copy of 'main.py', LF will be replaced by CRLF the next time Git touches it
```
`git commit -m "updated main file"`
```git
[main 4edd292] updated main file
 1 file changed, 2 insertions(+)
```
Trying to merge feature into main:
`git merge feature`









eof