# ElasticSearch cluster capabilities
ElasticSearch's cluster capabilities is pretty incredible when you actually use it for a scaling solution. [Andrew Glover](http://thediscoblog.com/blog/2013/09/03/effortless-elasticsearch-clustering/) wrote a blog post about how effortless ElasticSearch makes clustering. To discover other nodes within a cluster, as well as electing a master node, ElasticSearch uses the Discovery module. ElasticSearch uses [zen discovery](https://www.elastic.co/guide/en/elasticsearch/reference/1.6/modules-discovery-zen.html) by default and supports [other](https://www.elastic.co/guide/en/elasticsearch/reference/1.6/modules-discovery.html) discovery protocols as well. 

# Try it out
Using [brew](http://brew.sh/), [brew-cask](http://caskroom.io/), [docker](https://www.docker.com/), [docker-machine](https://github.com/docker/machine) and [docker-compose](https://github.com/docker/compose) we will install virtualbox with the extensions (manually), docker, docker-machine and docker-compose. Next we must create a new 'docker-machine' on virtualbox and test out ElasticSearch:

```bash
# install brew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# install brew cask
brew install caskroom/cask/brew-cask
# update
brew update
# install docker
brew install docker docker-compose docker-machine
brew cask install virtualbox
# create docker-machine
docker-machine create -d virtualbox dev
# evaluate docker-machine environment variables
eval "$(docker-machine env dev)"
# launch the example
./docker-machine-up.sh
./docker-machine-scale2.sh
./docker-machine-scale1.sh
./docker-machine-scale3.sh
./docker-machine-rm.sh
```

To look at the logs type `docker-machine logs` and to cleanup type `docker-machine-rm.sh`.

I hope you agree, ElasticSearch has a pretty incredible discovery module making it very easy to setup a cluster.

The discovery module is awesome, but maybe I must do more study on the subject to conclude the overall cluster design. [Viktor Klang](https://twitter.com/viktorklang) pointed me these two [blog](https://aphyr.com/posts/317-call-me-maybe-elasticsearch) posts, one that reviews [ElasticSearch](https://www.elastic.co) 1.1.0 and [a follow blog post](https://aphyr.com/posts/323-call-me-maybe-elasticsearch-1-5-0) that reviews [ElasticSearch](https://www.elastic.co) 1.5.0; both need a study on its own.

Have fun!
