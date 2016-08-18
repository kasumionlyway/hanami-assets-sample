source 'https://rubygems.org'

gem 'bundler'
gem 'rake'
gem 'hanami', github: 'hanami/hanami'
gem 'hanami-model', '~> 0.6'
gem 'hanami-view', github: 'hanami/view'
gem 'hanami-assets', github: 'hanami/assets'

group :development do
  # Code reloading
  # See: http://hanamirb.org/guides/applications/code-reloading
  gem 'shotgun'
end

group :test, :development do
  gem 'dotenv', '~> 2.0'
end

group :test do
  gem 'minitest'
  gem 'capybara'
end

group :production do
  # gem 'puma'
end
