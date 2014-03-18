require 'rubygems'

require 'rake'
require 'rdoc'
require 'date'
require 'yaml'
require 'tmpdir'
require 'jekyll'

desc "Generate blog files"
task :generate do
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => "_includes.md",
    "destination" => "_includes"
  })).process
end

task :default => :generate
