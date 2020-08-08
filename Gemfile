source "https://rubygems.org"
gem "minima"
gem "github-pages", group: :jekyll_plugins
group :jekyll_plugins do
  gem "kramdown", ">= 2.3.0"
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?
