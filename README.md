# Guide
![](http://i.imgur.com/y8g506n.png?1)



A `guide ` and some usefull `commands` in devops.

## Docker  <a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="30" height="30"/> </a>
```bash
docker run -d -p 3307:3306 --name mysqldbv1 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=test mysql
docker network create spring-net
docker network ls
docker network connect spring-net mysqldbv1
docker container inspect mysqldbv1
docker run -d -p 3307:3306 --name mysqldbv2 --network=spring-net -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=test mysql
docker exec -it mysqldbv1 /bin/sh
```
## Kubernetes  <a href="https://kubernetes.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="30" height="30"/> </a> 

After install, make sure to run `joe u`. This will download all `.gitignore` files in `~/joe-data/` folder.
### Shortcut
 api (short for api-server)
 cm (short for configmap)
 crd (short for custom resource definition)
 dep (short for deployment)
 etcd (short for distributed key-value store used by Kubernetes)
 ns (short for namespace)
 pvc (short for persistent volume claim)
 svc (short for service)

### Option 2: From source

```bash
$ git clone git@github.com:karan/joe.git
$ cd joe/
$ chmod +x tool.sh
$ ./tool.sh build
```

## Usage

### Commands:

```
ls | list       list all available files
u | update      update all available gitignore files
g | generate    generate gitignore files
```

### Basic usage

```bash
$ joe g java    # outputs .gitignore file for java to stdout
```

To update your `.gitignore` files at any time, simply run:

```bash
$ joe u
```

### Overwrite existing `.gitignore` file

```bash
$ joe g java > .gitignore    # saves a new .gitignore file for java
```

### Append to existing `.gitignore` file

```bash
$ joe g java >> .gitignore    # appends to an existing .gitignore file
```

### Multiple languages

```bash
$ joe g java,node,osx > .gitignore    # saves a new .gitignore file for multiple languages
```

### Create and append to a global .gitignore file

You can also use joe to append to a global .gitignore. These can be helpful when you want to ignore files generated by an IDE, OS, or otherwise.

```bash
$ git config --global core.excludesfile ~/.gitignore # Optional if you have not yet created a global .gitignore
$ joe g OSX,SublimeText >> ~/.gitignore
```

### List all available files

```bash
$ joe ls    # OR `joe list`
```

Output:

> actionscript, ada, agda, android, anjuta, appceleratortitanium, archives, archlinuxpackages, autotools, bricxcc, c, c++, cakephp, cfwheels, chefcookbook, clojure, cloud9, cmake, codeigniter, codekit, commonlisp, composer, concrete5, coq, craftcms, cvs, dart, darteditor, delphi, dm, dreamweaver, drupal, eagle, eclipse, eiffelstudio, elisp, elixir, emacs, ensime, episerver, erlang, espresso, expressionengine, extjs, fancy, finale, flexbuilder, forcedotcom, fortran, fuelphp, gcov, gitbook, go, gradle, grails, gwt, haskell, idris, igorpro, ipythonnotebook, java, jboss, jdeveloper, jekyll, jetbrains, joomla, jython, kate, kdevelop4, kohana, labview, laravel, lazarus, leiningen, lemonstand, libreoffice, lilypond, linux, lithium, lua, lyx, magento, matlab, maven, mercurial, mercury, metaprogrammingsystem, meteor, microsoftoffice, modelsim, momentics, monodevelop, nanoc, netbeans, nim, ninja, node, notepadpp, objective-c, ocaml, opa, opencart, oracleforms, osx, packer, perl, phalcon, playframework, plone, prestashop, processing, python, qooxdoo, qt, r, rails, redcar, redis, rhodesrhomobile, ros, ruby, rust, sass, sbt, scala, scons, scrivener, sdcc, seamgen, sketchup, slickedit, stella, sublimetext, sugarcrm, svn, swift, symfony, symphonycms, tags, tex, textmate, textpattern, tortoisegit, turbogears2, typo3, umbraco, unity, vagrant, vim, virtualenv, visualstudio, vvvv, waf, webmethods, windows, wordpress, xcode, xilinxise, xojo, yeoman, yii, zendframework, zephir

### BONUS ROUND: Alternate version control software

Joe isn't **just** a generator for `.gitignore` files. You can use it and its output wherever a SCM is used.

```bash
$ joe g java > .hgignore
```

## Contributing

#### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/karan/joe/issues) to report any bugs or file feature requests.

#### Developing

PRs are welcome. To begin developing, do this:

```bash
$ git clone git@github.com:karan/joe.git
$ cd joe/
$ go run *.go
```

#### `tool.sh`

This is a handy script that automates a lot of developing steps.


```bash
USAGE:
    $ $tool [-h|--help] COMMAND

  EXAMPLES:
    $ $tool deps      Install dependencies for joe
    $ $tool build     Build a binary
    $ $tool run       Build and run the binary
```
