#############################################################################
#
# Modified version of jekyllrb Rakefile
# https://github.com/jekyll/jekyll/blob/master/Rakefile
#
#############################################################################

require 'rake'
require 'date'
require 'yaml'

CONFIG = YAML.load(File.read('_config.yml'))
USERNAME = CONFIG["username"] || ENV['GIT_NAME']
REPO = CONFIG["repo"] || "#{USERNAME}.github.io"

# Determine source and destination branch
# User or organization: source -> master
# Project: master -> gh-pages
# Name of source branch for user/organization defaults to "source"
if REPO == "#{USERNAME}.github.io"
  SOURCE_BRANCH = CONFIG['branch'] || "source"
  DESTINATION_BRANCH = "master"
else
  SOURCE_BRANCH = "master"
  DESTINATION_BRANCH = "gh-pages"
end

#############################################################################
#
# Helper functions
#
#############################################################################

def replace_header(head, header_name)
  head.sub!(/(\.#{header_name}\s*= ').*'/) { "#{$1}#{send(header_name)}'"}
end

def normalize_bullets(markdown)
  markdown.gsub(/\s{2}\*{1}/, "-")
end

def linkify_prs(markdown)
  markdown.gsub(/#(\d+)/) do |word|
    "[#{word}]({{ site.repository }}/issues/#{word.delete("#")})"
  end
end

def linkify_users(markdown)
  markdown.gsub(/(@\w+)/) do |username|
    "[#{username}](https://github.com/#{username.delete("@")})"
  end
end

def linkify(markdown)
  linkify_users(linkify_prs(markdown))
end

def liquid_escape(markdown)
  markdown.gsub(/(`{[{%].+[}%]}`)/, "{% raw %}\\1{% endraw %}")
end

def remove_head_from_history(markdown)
  index = markdown =~ /^##\s+\d+\.\d+\.\d+/
  markdown[index..-1]
end

def converted_history(markdown)
  remove_head_from_history(liquid_escape(linkify(normalize_bullets(markdown))))
end

# File activesupport/lib/active_support/inflector/transliterate.rb, line 80
def parameterize(string, sep = '-')
  # replace accented chars with their ascii
  # simplified from original to remove dependency
  parameterized_string = string.dup.force_encoding('US-ASCII')
  # Turn unwanted chars into the separator
  # changed from original: allow A-Z
  parameterized_string.gsub!(/[^a-zA-Z0-9\-_]+/, sep)
  unless sep.nil? || sep.empty?
    re_sep = Regexp.escape(sep)
    # No more than one of the separator in a row.
    parameterized_string.gsub!(/#{re_sep}{2,}/, sep)
    # Remove leading/trailing separator.
    parameterized_string.gsub!(/^#{re_sep}|#{re_sep}$/, '')
  end
  parameterized_string.downcase
end

def check_destination
  unless Dir.exist? CONFIG["destination"]
    sh "git clone https://#{ENV['GIT_NAME']}:#{ENV['GH_TOKEN']}@github.com/#{USERNAME}/#{REPO}.git #{CONFIG["destination"]}"
  end
end

#############################################################################
#
# Pull from Github
#
#############################################################################

desc "Pull updates from Github"
task :pull do
  puts "\n## Pulling from Github"
  status = system("git pull")
end


#############################################################################
#
# Commit to Github
#
#############################################################################

desc "Commit site update to Github"
task :commit => [:pull] do
  puts "\n## Staging modified files"
  status = system("git add -A")
  puts status ? "Success" : "Failed"
  puts "\n## Committing a site build at #{Time.now.utc}"
  message = "Update at #{Time.now.utc}"
  status = system("git commit -m \"#{message}\"")
  puts status ? "Success" : "Failed"
  puts "\n## Pushing commits to remote"
  status = system("git push origin source")
  puts status ? "Success" : "Failed"
end

#############################################################################
#
# Setup development environment
#
#############################################################################

desc "Setup your development environment"
task :setup do
  puts "\n## Install Homebrew"
  status = system('ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"')
  puts "\n## Install rvm"
  status = system("curl -sSL https://get.rvm.io | bash -s stable --ruby=")
  puts status ? "Success" : "Failed"
  puts "\n## Install Ruby 2.1.0 with rvm"
  status = system("rvm install ruby-2.1.0")
  puts status ? "Success" : "Failed"
  puts "\n## Default use Ruby 2.1.0 from rvm"
  status = system("rvm --default use 2.1.0")
  puts status ? "Success" : "Failed"
  puts "\n## Source rvm so it works in this session"
  status = system("source ~/.profile")
  puts status ? "Success" : "Failed"
  puts "\n## Install Bundler"
  status = system("gem install bundler")
  puts status ? "Success" : "Failed"
  puts "\n## Install repo requirements with Bundler"
  status = system("bundle install --binstubs=$GEM_HOME/bin/")
  puts status ? "Success" : "Failed"
end

desc "(Uninstall) Clean up your development environment"
task :clean do
  # puts "\n## Unlink ruby from Homebrew"
  # status = system("brew unlink ruby")
  # puts status ? "Success" : "Failed"
  puts "\n## Uninstall Homebrew"
  puts "\n## Most of the time you should select _NO_"  
  status = system('ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"')
  puts status ? "Success" : "Failed"
  puts "\n## Set Ruby to System"
  status = system("rvm --default system")
  puts status ? "Success" : "Failed"
  puts "\n## Uninstall rvm"
  status = system("rvm implode")
  puts status ? "Success" : "Failed"
  # puts "\n## Uninstall Bundler"
  # status = system("gem uninstall bundler")
  # puts status ? "Success" : "Failed"
end

#############################################################################
#
# Site tasks
#
#############################################################################

namespace :site do
  # puts "export GEM_PATH=$HOME/.gem/ruby/2.0.0/bin"
  desc "Add filenames to posts"
  task :edit do
    check_destination
    system "./_scripts/add-filenames-to-posts.sh >/dev/null"
  end
  
  desc "Generate the site"
  task :build do
    check_destination
    sh "jekyll build"
  end

  desc "Generate the site and serve locally"
  task :serve do
    check_destination
    sh " jekyll serve --config _config.yml,_config-dev.yml"
  end

  desc "Generate the site, serve locally and watch for changes"
  task :watch do
    sh "jekyll serve --watch --drafts --config _config.yml,_config-dev.yml"
  end

  desc "Generate the site and push changes to remote origin"
  task :deploy => [:edit] do
    # Detect pull request
    if ENV['TRAVIS_PULL_REQUEST'].to_s.to_i > 0
      puts 'Pull request detected. Not proceeding with deploy.'
      exit
    end

    # Configure git if this is run in Travis CI
    if ENV["TRAVIS"]
      sh "git config --global user.name '#{ENV['GIT_NAME']}'"
      sh "git config --global user.email '#{ENV['GIT_EMAIL']}'"
      sh "git config --global push.default simple"
    end

    # Make sure destination folder exists as git repo
    check_destination

    sh "git checkout #{SOURCE_BRANCH}"
    Dir.chdir(CONFIG["destination"]) { sh "git checkout #{DESTINATION_BRANCH}" }

    # Generate the site
    sh "jekyll build"

    # Commit and push to github
    sha = `git log`.match(/[a-z0-9]{40}/)[0]
    Dir.chdir(CONFIG["destination"]) do
      sh "git add --all ."
      sh "git commit -m 'Updating to #{USERNAME}/#{REPO}@#{sha}.'"
      sh "git push --quiet origin #{DESTINATION_BRANCH}"
      puts "Pushed updated branch #{DESTINATION_BRANCH} to GitHub Pages"
    end
  end
end

#############################################################################
#
# My personal rvm notes...because I'm not a ruby dev
#
#############################################################################
# rvm gemset create blog
# rvm gemset use blog
# Set default Ruby to 2.1.0 with rvm
# rvm --default use 2.1.0
