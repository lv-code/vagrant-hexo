vagrant-hexo
============

Vagrant [hexo](http://hexo.io) server with the following features:

- 64-bit Ubuntu 14.04 LTS
- running at `10.25.83.66`
- local blogs directory mounted as `/blogs` 
- [nvm](https://github.com/creationix/nvm), [nodejs](http://nodejs.org/), [heroku-toolbelt](https://toolbelt.heroku.com/), ruby 1.9.3
- ready to deploy using git, rsync or heroku 
- fully functional demo with light-theme and redirect example

# Requirements

- [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](http://www.vagrantup.com/downloads.html)

# Installation

	git clone https://github.com/alt3/vagrant-hexo.git
	cd vagrant-hexo
	vagrant up

## Configuration

Override default settings by creating `Vagrantfile.yml`:

    hexo:
      install_demo  : true
      theme_git_url : https://github.com/kywk/hexo-theme-casper.git

    vm:
      hostname      : hexo
      ip_address    : 10.25.83.66

# Usage

## Launch demo blog

Point your your browser at [http://10.25.83.66:4000](http://10.25.83.66:4000) after running:

	vagrant ssh
	cd demo
	hexo server

## Create new blog

	vagrant ssh
	hexo init myblog
	cd myblog
	npm install --no-bin-links

## Restore existing blog

	vagrant ssh
	git clone git://github.com/<your-hexo-blog>.git
	cd <your-hexo-blog>
	git checkout source
	npm install --no-bin-links

# Additional information

##Notes

- use of `--no-bin-links` for npm installs is required to prevent (Vagrant caused) symlink errors

##Links
- [Hexo documentation](http://hexo.io/docs/)
- [Hexo themes](https://github.com/hexojs/hexo/wiki/Themes)

##Contributing

1. Fork it ( https://github.com/alt3/vagrant-hexo/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Adds some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

#TODO

- add post with redirect example to demo
- add alias to easify --no-bin-links?
- change git version to 2.1 (http://tecadmin.net/install-git-on-ubuntu/)
