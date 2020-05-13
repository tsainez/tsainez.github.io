source "https://rubygems.org"
# This is where to manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve --livereload
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!

# This is the default theme for new Jekyll sites.
gem "minima"

# For GitHub pages implementation
gem "github-pages", group: :jekyll_plugins

# Plugins Section
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.6"
  gem 'jekyll-seo-tag'
  gem 'jekyll-spaceship'
  #gem 'jekyll-katex'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?
gem "wdm", "~> 0.1.0" if Gem.win_platform?