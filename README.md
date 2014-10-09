vagrant-hexo
============

Chef provisioned [hexo](http://hexo.io) server with the following features:

- 64-bit Ubuntu 14.04 LTS
- running at `10.25.83.66`
- latest [nvm](https://github.com/creationix/nvm), [nodejs](http://nodejs.org/), git and hexo
- local blogs directory mounted as `/blogs`
- fully functional demo with light-theme and redirect example

# Requirements

- [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](http://www.vagrantup.com/downloads.html)

# Installation

	git clone https://github.com/alt3/vagrant-hexo.git
	cd vagrant-hexo
	vagrant up

## Configuration
Customize your server by creating `Vagrantfile.yml` and changing any of the following settings:

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

# Notes

- `--no-bin-links` required for npm installs (to prevent symlink errors)

# Additional information

- [Hexo documentation](http://hexo.io/docs/)
- [Hexo themes](https://github.com/hexojs/hexo/wiki/Themes)


#@TODO
- add post with redirect example to demo
- add alias to easify --no-bin-links?
- change git version to 2.1 (http://tecadmin.net/install-git-on-ubuntu/)
