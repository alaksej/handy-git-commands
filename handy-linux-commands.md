### [Update time](https://unix.stackexchange.com/a/400176)
```sh
sudo date -s "$(wget -qSO- --max-redirect=0 google.com 2>&1 | grep Date: | cut -d' ' -f5-8)Z"
 ```
### [View path nicely](https://askubuntu.com/questions/600018/how-to-display-path-as-one-directory-per-line)
```sh
sed 's/:/\n/g' <<< "$PATH"
```
