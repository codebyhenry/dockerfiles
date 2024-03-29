# Multipass

a quick way to run headless linux instance. you can install multipass on windows, mac and even linux itself. Why you want to do that?. sometimes you want extra layers, so the host and guest machines only interact on parts you want or need. run containerized apps like a webserver with a database with the multipass docker & portainer image.


[download and install](https://multipass.run/install)

official tutorial:
[Windows](https://multipass.run/docs/windows-tutorial) |
[Apple](https://multipass.run/docs/mac-tutorial) | 
[Linux](https://multipass.run/docs/linux-tutorial)


tip: install it on:
 - windows via chocolatey (choco install multipass).
 - mac via brew.sh (brew install multipass).
 - or via yay, apt, zypper, etc... on linux.

### commands

multipass info <instance>

example:

``` 
  multipass info mpdocker
  ```

## mount during launch
  
  you can create mount(bind) points to the guest instance. but you cant do this in the $HOME so you need to map it to a folder, you can use any name and as much mounts you like.
  
  step 1: mkdir -p <name_of_the_workfolder>

  example
``` 
mkdir -p mpdocker
multipass launch docker --mount $HOME/mpdocker:~/mpdocker --cpus 4 --disk 40G --mem 4G --name mpdocker 
```

or 

```
mkdir -p mpdocker
multipass launch docker \
--mount $HOME/mpdocker:/home/ubuntu/mpdocker \
-c 4 \
-d 40G \
-m 4G \
-n mpdocker
```


## mount after launch

example if you want to bind a local (home)folder to the guest. 

  ```
  multipass mount $HOME/mpdocker mpdocker:~/mpdocker1
  multipass mount /path/to/mount mpdocker:~/mpdocker2 
  etc

  ```

other commands

  ```
  multipass list // shows you ip address and list of VM instances 
  multipass network // shows all your ip adresses 
  ```
   
  ```
  multipass exec <instance> bash // opens the instance terminal 
  ```
  
  or
  
  ```
  multipass shell <instance>
  ```
  
  ```
  multipass info <instance>   
  ```
  
  to delete and remove, 
  ```
  multipass delete <instance>  // if you want to restore use: recover
  multipass purge //  clean residuals  
  ```
  
  ```
  multipass start/stop/suspend
  
  Available commands:
  alias         Create an alias
  aliases       List available aliases
  unalias       Remove aliases

  more:
  authenticate  Authenticate client
  find          Display available images to create instances from
  get           Get a configuration setting
  help          Display help about a command
  set           Set a configuration setting
  transfer      Transfer files between the host and instances
  umount        Unmount a directory from an instance
  version       Show version details  
  
  
  ```
  
 
  tip: build a zerotier network with tailscale
  
```
  curl -fsSL https://tailscale.com/install.sh | sh
  sudo tailscale up
  ```


