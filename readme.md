

* ### [Delete branch remotely and locally](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-remotely)

  ```$ git push -d origin <branch_name>```

  ```$ git branch -d <branch_name>```
  * #### Clean up deleted remote branches
    ```$ git remote prune origin```
  * #### Clean up merged branches
    * Check out 'master'
    * ```$ git branch --merged | egrep -v "(^\*|master|dev)" | xargs git branch -d```

* ### Start ignoring changes to a single already versioned file
  ```$ git update-index --assume-unchanged "main/dontcheckmein.txt"```

  and to undo that:

  ```$ git update-index --no-assume-unchanged "main/dontcheckmein.txt"```

* ### Search: 

  * by commit message:

    ```$ git log -g --grep=search_for_this```

  * by commit changes:

    ```$ git log -g -Ssearch_for_this```

  * this also works but may be slower, it only shows text-added results

    ```$ git grep search_for_this $(git log -g --pretty=format:%h)```


* ### Pull master without checking out to it
  ```$ git fetch origin master:master```

* ### [Storing credentials](https://stackoverflow.com/a/35942890)
  ```$ git config credential.helper store```
  ```$ git pull```
  
  ## User management
  * See current user:
  `$ git config user.name`
  `$ git config user.email`
  * Update current user globally
  `$ git config --global user.name "Aliaksei Yankou"`
  `$ git config --global user.email "yankouav@gmail.com"`
  
  ## [Cherry pick a range of commits](https://stackoverflow.com/a/3933416/5983311)
  * Will pick all commits between A (older, including A) and B (later, including B)
  
  ```$ git cherry-pick A^..B```
  
  ## [Untrack ignored files](http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/)
  1. Commit all your changes
  2. Remove everything from the repository
  ```$ git rm -r --cached .```
  3. Re add everything
  ```$ git add .```
  4. Commit
  ```$ git commit -m ".gitignore fix"```
  
  ## Pre-commit message
  To format messages like [branchName] commit message
  Update `.git/hooks/prepare-commit-msg` with the following
```bash
#!/bin/bash

# This way you can customize which branches should be skipped when
# prepending commit message. 
if [ -z "$BRANCHES_TO_SKIP" ]; then
  BRANCHES_TO_SKIP=(master develop test)
fi

BRANCH_NAME=$(git symbolic-ref --short HEAD)

BRANCH_EXCLUDED=$(printf "%s\n" "${BRANCHES_TO_SKIP[@]}" | grep -c "^$BRANCH_NAME$")
BRANCH_IN_COMMIT=$(grep -c "\[$BRANCH_NAME\]" $1)

if [ -n "$BRANCH_NAME" ] && ! [[ $BRANCH_EXCLUDED -eq 1 ]] && ! [[ $BRANCH_IN_COMMIT -ge 1 ]]; then 
  sed -i.bak -e "1s%^%[$BRANCH_NAME] %" $1
fi
```

## [Branch diff](https://stackoverflow.com/questions/2528111/how-can-i-calculate-the-number-of-lines-changed-between-two-commits-in-git/2528129)
```$ git diff --shortstat <branch_name>```

## [show branch graph](https://stackoverflow.com/a/2421063/5983311)
```sh
git config --global alias.lgb "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset%n' --abbrev-commit --date=relative --branches"

git lgb
```
  
