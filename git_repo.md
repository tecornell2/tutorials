## How do I edit my GitHub repository from my PC terminal?

### Install (Linux)
```sh
sudo apt update
sudo apt install gh
```

### View Repos
```sh
gh repo list
# example output
Showing 5 of 5 repositories in @tecornell2

NAME                       DESCRIPTION                              INFO          UPDATED           
tecornell2/tutorials       Bioinformatic tutorials                  public        about 3 hours ago
tecornell2/website                                                  public, fork  about 7 hours ago
tecornell2/bioinformatics  Personal bioinformatics files and notes  public        about 22 hours ago
tecornell2/BIOL8230        Macroevolutionary Methods                public        about 1 day ago
tecornell2/tecornell2                                               public        about 4 months ago
```

### Update Repository
```sh
git add -A
git commit -m "Rename directory"
git push origin <branch-name>
# don't know the master branch name?
# use `git branch`
```

