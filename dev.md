Git Commands                                                                                                            5735512121
============

_A list commands you have learn


--

### Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |

### Basic 

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file |
| `git commit -m "[commit message]"` | Commit changes |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout [branch name]` | Switch to a branch |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git stash` | Stash changes in a dirty working directory |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin https://github.com/[username]/[repository-name].git` | Add a remote repository |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |

##### Setting up git
| Command | Description |
| ------- | ----------- |
| `git config --global user.name "User Name"` | Setting username |
| `git config --global user.email "email` | Setting email |

