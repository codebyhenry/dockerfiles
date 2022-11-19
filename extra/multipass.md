# Multipass

an easy to run headless linux (LXD) containers as lightweight but powerfull alternative to virtualbox VM. you can install multipass on windows, mac and even linux itself.


[download and install](https://multipass.run/install)

`tip: install it via chocolatey on windows or brew.sh for mac and apt or yay on linux.`

`tip: build a zerotier network with tailscale`

```
  curl -fsSL https://tailscale.com/install.sh | sh
  sudo tailscale up
  ```



### commands

multipass info <instance>

example:

``` 
  multipass info mpdocker
  ```

## mount during launch
  
  you can create mount(bind) points to the VM. but you cant do this in the $HOME so you need to map it to a folder

example 

``` 
multipass launch docker --mount $HOME/mpdocker:~/mpdocker --cpus 4 --disk 40G --mem 4G --name mpdocker 
```

or 

```
multipass launch docker \
--mount $HOME/mpdocker:/home/ubuntu/mpdocker \
--c 4 \
--d 40G \
--m 4G \
--n mpdocker
```


## mount after launch

example if you want to mount an instance called mpdocker and have a same local folder you want to mount. 

  ```
  multipass mount $HOME/mpdocker mpdocker:~/mpdocker
  ```

other commands

  ```
  multipass list // shows you ip address and list of VM instances 
  ```
   
  ```
  multipass exec <instance> bash // opens the instance terminal 
  ```
  
  ```
  multipass info <instance>   
  ```

