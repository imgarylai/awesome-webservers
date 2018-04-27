# web-servers

This is a collection of one-liner server. The idea is from this [gist](https://gist.github.com/willurd/5720255). I create this repo because there are more solutions scattered in the comments. It would be better that we have a space to gather them. I appreciate all the contributors to the original discussion thread. 

I use the original setting for all the examples. All of them will run the server at port `8080` in your current working directory. 

## Contents

### Language

- [Erlang](#erlang)
- [Node.js](#nodejs)
- [Perl](#perl)
- [PHP](#php)
- [Python](#python)
- [Ruby](#ruby)
- [Other](#other)

### Meta

If you have any suggestions, drop them in a new pull request. To get on this list, a solution must:

1. serve static files using your current directory (or a specified directory) as the server root,
2. be able to be run with a single, one line command (dependencies are fine if they're a one-time thing),
3. serve basic file types (html, css, js, images) with proper mime types,
4. require no configuration (from files or otherwise) beyond the command itself (no framework-specific servers, etc)
5. must run, or have a mode where it can run, in the foreground (i.e. no daemons)

## Get started

#### Erlang

```shell
$ erl -s inets -eval 'inets:start(httpd,[{server_name,"NAME"},{document_root, "."},{server_root, "."},{port, 8000},{mime_types,[{"html","text/html"},{"htm","text/html"},{"js","text/javascript"},{"css","text/css"},{"gif","image/gif"},{"jpg","image/jpeg"},{"jpeg","image/jpeg"},{"png","image/png"}]}]).'
```

#### Node.js

##### http-server

```shell
$ npm install -g http-server   # install dependency
$ http-server -p 8000
```

##### node-static

```shell
$ npm install -g node-static
$ static -p 8000
```

#### Perl

```shell
$ cpan HTTP::Server::Brick
$ perl -MHTTP::Server::Brick -e '$s=HTTP::Server::Brick->new(port=>8000); $s->mount("/"=>{path=>"."}); $s->start'
```

##### Plack

```shell
$ cpan Plack
$ plackup -MPlack::App::Directory -e 'Plack::App::Directory->new(root=>".");' -p 8000
```

##### Mojolicious

```shell
$ cpan Mojolicious::Lite
$ perl -MMojolicious::Lite -MCwd -e 'app->static->paths->[0]=getcwd; app->start' daemon -l http://*:8000
```

#### PHP

```shell
$ php -S 127.0.0.1:8000
```

#### Python

##### Python 2

```shell
$ python -m SimpleHTTPServer 8000
```

##### Python 3

```shell
$ python -m http.server 8000
```

##### Twisted

```shell
$ pip install twisted
$ twistd -n web -p 8000 --path .
```

#### Ruby

```shell
$ ruby -run -ehttpd . -p8000
```

##### adsf

```shell
$ gem install adsf
$ adsf -p 8000
```

##### Sinatra

```shell
$ gem install sinatra
$ ruby -rsinatra -e'set :public_folder, "."; set :port, 8000'
```

#### Other

##### busybox httpd

```shell
$ busybox httpd -f -p 8000
```

##### webfs

```shell
$ webfsd -F -p 8000
```


##### IIS Express

```shell
C:\> "C:\Program Files (x86)\IIS Express\iisexpress.exe" /path:C:\MyWeb /port:8000
```
