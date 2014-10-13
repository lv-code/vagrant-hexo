source "https://supermarket.getchef.com"

metadata

## Use local (development) cookbooks if present
def depload(dep, options)
	cookbooks = '.cookbooks'
	if Dir.exists?("#{cookbooks}/#{dep}")
		cookbook dep, path: "#{cookbooks}/#{dep}"
	else
		cookbook dep, options
   	end
end

# Define cookbooks using Berksfile cookbook syntax
depload 'hexo', git: 'git://github.com/alt3-cookbooks/hexo.git'
depload 'heroku', git: 'git://github.com/alt3-cookbooks/heroku.git'
depload 'utilities', git: 'git://github.com/alt3-cookbooks/utilities.git'
