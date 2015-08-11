## Fiddler via Docker on a Mac

  Run [Fiddler](http://www.telerik.com/fiddler) on a Mac in a container.

Attribution and helpful links:

+ https://github.com/docker/docker/issues/8710
+ https://github.com/mono/docker/blob/master/3.12.0/Dockerfile

```
$ git clone git@github.com:jwieringa/docker-fiddler.git
$ cd fiddler
$ docker build -t fiddler .
$ brew install socat
# install cask for brew if not already installed
$ brew cask install xquartz
$ open -a XQuartz
$ socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"
# In a new terminal, using the Mac IP (not the docker host IP)
$ docker run -e DISPLAY=192.168.1.185:0 fiddler
```
