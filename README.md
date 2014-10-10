vagrant-hexo
============

Chef-librarian provisioned [hexo](http://hexo.io) server with the following features:

- 64-bit Ubuntu 14.04 LTS
- running at `10.25.83.66`
- local blogs directory mounted as `/blogs` 
- [nvm](https://github.com/creationix/nvm), [nodejs](http://nodejs.org/), ruby 1.9.3 and hexo
- ready to deploy using git, rsync or [heroku](https://www.heroku.com) 
- fully functional demo with light-theme and redirect example

# Requirements

- [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](http://www.vagrantup.com/downloads.html)

# Installation

	git clone https://github.com/alt3/vagrant-hexo.git
	cd vagrant-hexo
	vagrant up

## Configuration
The default server settings should suffice in most cases. However, feel free to override them by creating `Vagrantfile.yml` and changing any of the following settings:

<table>
  <tr>
	<td>Node</td>
    <td>Setting</td>
    <td>Description</td>
    <td>Default</td>
  </tr>
  <tr>
	<td><code>hexo</code></td>
    <td><code>install_demo</code></td>
    <td>True to install and configure a hexo demo blog with theme in /blogs.</td>
    <td><em>true</em></td>
  </tr>
  <tr>
	<td><code>hexo</code></td>
    <td><code>theme_git_url</code></td>
    <td>URL to a git repository holding a hexo theme.</td>
    <td><em>(see .yml)</em></td>
  </tr>
  <tr>
	<td><code>vm</code></td>
    <td><code>hostname</code></td>
    <td>Name of your hexo server.</td>
    <td><em>hexo</em></td>
  </tr>
  <tr>
	<td><code>vm</code></td>
    <td><code>ip_address</code></td>
    <td>IP-address of your hexo server.</td>
    <td><em>10.25.83.66</em></td>
  </tr>
</table>

# Usage

## Launch demo blog

	vagrant ssh
	cd demo
	hexo server

Point your browser at [http://10.25.83.66](http://10.25.83.66)

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

#@TODO
- add ruby (heroku now standalone)
- add post with redirect example to demo
- add alias to easify --no-bin-links?
- change git version to 2.1 (http://tecadmin.net/install-git-on-ubuntu/)
