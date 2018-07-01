# web-servers

This is a collection of one-liner server. The idea is from this [gist](https://gist.github.com/willurd/5720255). I create this repo because there are more solutions scattered in the comments. It would be better that we have a space to gather them. I appreciate all the contributors to the original discussion thread. 

I use the original setting for all the examples. All of them will run the server at port `8000` in your current working directory. 

## Contents

### Language

- [Clojure](#clojure)
- [Crystal](#crystal)
- [Elixir](#elixir)
- [Erlang](#erlang)
- [Go](#go)
- [Haskell](#haskell)
- [Lisp](#lisp)
- [Node.js](#nodejs)
- [Perl](#perl)
- [PHP](#php)
- [Python](#python)
- [R](#r)
- [Ruby](#ruby)
- [Rust](#rust)
- [Other](#other)

### Meta

If you have any suggestions, drop them in a new pull request. To get on this list, a solution must:

1. serve static files using your current directory (or a specified directory) as the server root,
2. be able to be run with a single, one line command (dependencies are fine if they're a one-time thing),
3. serve basic file types (html, css, js, images) with proper mime types,
4. require no configuration (from files or otherwise) beyond the command itself (no framework-specific servers, etc)
5. must run, or have a mode where it can run, in the foreground (i.e. no daemons)

## Clogure

### Leiningen

```shell
$ lein simpleton 8000
```

## Crystal

```shell
$ crystal eval 'require "http/server"; HTTP::Server.new(8000, HTTP::StaticFileHandler.new(".")).listen'
```

## Elixir

```
elixir --no-halt --app inets -e ":inets.start(:httpd,[{:server_name,'s'},{:document_root,'.'},{:server_root,'.'},{:port,8000}])"
```

## Erlang

```shell
$ erl -s inets -eval 'inets:start(httpd,[{server_name,"NAME"},{document_root, "."},{server_root, "."},{port, 8000},{mime_types,[{"html","text/html"},{"htm","text/html"},{"js","text/javascript"},{"css","text/css"},{"gif","image/gif"},{"jpg","image/jpeg"},{"jpeg","image/jpeg"},{"png","image/png"}]}]).'
```

## Go

### Algernon
```shell
$ go get -u github.com/xyproto/algernon
$ algernon -x 8000
```

### Candy

```shell
caddy -port 8000
```

### Gost

```shell
$ go get github.com/vwochnik/gost
$ gost -port 8888 .
```

### Ram
```shell
$ go get -u github.com/m3ng9i/ran
$ ran -p 8000
```

### Spark

```shell
$ go get github.com/rif/spark
$ spark -port 8000 .
```

## Haskell

### maid
```shell
cabal install maid
maid 8000
```

### wai-app-static
```shell
cabal install wai-app-static
warp -p 8000
```

## Lisp

### Clack

```
$ ros install clack
$ clackup <(echo "(lack:builder (:static :path #'identity) #'identity)")
```

## Node.js

### Anywhere
```shell
$ npm install anywhere -g
$ anywhere -p 8000
```

### glance

```shell
$ npm install -g glance
$ glance -p 8000
```

### Harp
```shell
$ npm install -g harp
$ harp server --port 8000
```

### http-server

```shell
$ npm install -g http-server   # install dependency
$ http-server -p 8000
```

### node-static

```shell
$ npm install -g node-static
$ static -p 8000
```

### Superstatic
```shell
$ npm install -g superstatic
$ superstatic public --port 8000
```

## Perl

```shell
$ cpan HTTP::Server::Brick
$ perl -MHTTP::Server::Brick -e '$s=HTTP::Server::Brick->new(port=>8000); $s->mount("/"=>{path=>"."}); $s->start'
```

### Plack

```shell
$ cpan Plack
$ plackup -MPlack::App::Directory -e 'Plack::App::Directory->new(root=>".");' -p 8000
```

### Mojolicious

```shell
$ cpan Mojolicious::Lite
$ perl -MMojolicious::Lite -MCwd -e 'app->static->paths->[0]=getcwd; app->start' daemon -l http://*:8000
```

## PHP

```shell
$ php -S 127.0.0.1:8000
```

### Drush

```shell
$ drush rs 8000
```

### Laravel

```shell
$ php artisan serve --host=127.0.0.1 --port=8000
```

## Python

### Python 2

```shell
$ python -m SimpleHTTPServer 8000
```

### Python 3

```shell
$ python -m http.server 8000
```

### Twisted

```shell
$ pip install twisted
$ twistd -n web -p 8000 --path .
```

## R
```shell
$ Rscript -e 'servr::httd()' -p8000
```

## Ruby

```shell
$ ruby -run -ehttpd . -p8000
```

### adsf

```shell
$ gem install adsf
$ adsf -p 8000
```

### Knod
```shell
$ gem install knod
$ knod -p 8000
```

### Rack
```shell
$ gem install rack
$ rackup -b 'use Rack::Static, :index => 'index.html'; run Rack::File.new('.')"
```

### Serve

```shell
$ gem install serve
$ serve 8000
```

### Sinatra

```shell
$ gem install sinatra
$ ruby -rsinatra -e'set :public_folder, "."; set :port, 8000'
```

## Rust

### Host These Things Please

```shell
$ cargo install https
$ http -p 8000
```

### miniserve

```shell
$ cargo install miniserve
$ miniserve -p 8000 .
```

### simple-http-server

```shell
$ cargo install simple-http-server
$ simple-http-server -p 8000 -- .
```

## Other

### busybox httpd

```shell
$ busybox httpd -f -p 8000
```

### ngrok
```shell
$ ngrok http 8000
```

### webfs

```shell
$ webfsd -F -p 8000
```

### IIS Express

```shell
C:\> "C:\Program Files (x86)\IIS Express\iisexpress.exe" /path:C:\MyWeb /port:8000
```
