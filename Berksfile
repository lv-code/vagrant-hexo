source "https://supermarket.getchef.com"

metadata

##
## TODO: define production cookbooks here
##
cookbook 'hexo', git: 'git://github.com/alt3-cookbooks/hexo.git'

cookbook 'heroku', git: 'git://github.com/alt3-cookbooks/heroku.git'

cookbook 'utilities', git: 'git://github.com/alt3-cookbooks/utilities.git'

##
## TODO: override if local cookbook is found
##
Dir.glob('cookbooks-dev/*').each do |path|
	puts "PATH = #{path}"
	#cookbook File.basename(path), path: path
end

##
## TODO: foreach set cookbook
##
