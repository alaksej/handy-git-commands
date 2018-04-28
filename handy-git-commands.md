

* ### [Delete branch remotely and locally](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-remotely)

  ```$ git push -d origin <branch_name>```

  ```$ git branch -d <branch_name>```
  * #### Clean up deleted remote branches
    ```$ git remote prune origin```

* ### Start ignoring changes to a single already versioned file
  ```$git update-index --assume-unchanged "main/dontcheckmein.txt"```

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