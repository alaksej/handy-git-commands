# [Update time](https://unix.stackexchange.com/a/400176)
```sh
sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"
 ```
