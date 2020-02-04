# $Linux Screen Commands$

###### Resource Link: [https://linuxize.com/post/how-to-use-linux-screen/](https://linuxize.com/post/how-to-use-linux-screen/)

##### Create An Screen

```bash
screen -S [session_name]
```

##### List Of All Screen

```bash
screen -list
```

##### Attatch a Screen

```bash
screen -r [name or id]
```

##### Detach Current Screen

```bash
Ctrl+a + d
```

##### Killing An Screen

```bash
 screen -X -S [session # you want to kill] quit
```
