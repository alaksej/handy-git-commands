

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
