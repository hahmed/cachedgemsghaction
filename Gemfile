source "https://rubygems.org"
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

# Bundle edge Rails instead: gem "rails", github: "rails/rails", branch: "main"
gem "rails", "~> 7.0.7", ">= 7.0.7.2"

# The original asset pipeline for Rails [https://github.com/rails/sprockets-rails]
gem "sprockets-rails"

# Use mysql as the database for Active Record
gem "mysql2", "~> 0.5"

# Use the Puma web server [https://github.com/puma/puma]
gem "puma", "~> 6.0"

if RUBY_VERSION > "3"
  gem "webmock"
end

if RUBY_VERSION < "3"
  gem "minitest", ">= 5.15.0", "< 5.16"
else
  gem "minitest"
end

gem "redis"

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem "tzinfo-data", platforms: %i[ mingw mswin x64_mingw jruby ]

group :development, :test do
  # See https://guides.rubyonrails.org/debugging_rails_applications.html#debugging-with-the-debug-gem
  gem "debug", platforms: %i[ mri mingw x64_mingw ]
end

group :development do
  # Speed up commands on slow machines / big apps [https://github.com/rails/spring]
  # gem "spring"
end

# We need a newish Rake since Active Job sets its test tasks' descriptions.
gem "rake", ">= 13"

gem "propshaft", ">= 0.1.7"
gem "capybara", ">= 3.39"
if RUBY_VERSION < "3"
  gem "selenium-webdriver", "<= 4.9.0"
  gem "webdrivers"
else
  gem "selenium-webdriver", ">= 4.11.0"
end

gem "rack-cache", "~> 1.2"
gem "stimulus-rails"
gem "turbo-rails"
gem "jsbundling-rails"
gem "cssbundling-rails"
gem "importmap-rails"
gem "tailwindcss-rails"
gem "dartsass-rails"
# require: false so bcrypt is loaded only when has_secure_password is used.
# This is to avoid Active Model (and by extension the entire framework)
# being dependent on a binary library.
gem "bcrypt", "~> 3.1.11", require: false

# This needs to be with require false to avoid it being automatically loaded by
# sprockets.
gem "terser", ">= 1.1.4", require: false

# Explicitly avoid 1.x that doesn't support Ruby 2.4+
gem "json", ">= 2.0.0"

# Workaround until Ruby ships with cgi version 0.3.6 or higher.
gem "cgi", ">= 0.3.6", require: false

group :rubocop do
  gem "rubocop", ">= 1.25.1", require: false
  gem "rubocop-minitest", require: false
  gem "rubocop-packaging", require: false
  gem "rubocop-performance", require: false
  gem "rubocop-rails", require: false
  gem "rubocop-md", require: false
end

group :mdl do
  gem "mdl", require: false
end

group :doc do
  gem "sdoc", ">= 2.6.0"
  gem "rdoc", "~> 6.5"
  gem "redcarpet", "~> 3.2.3", platforms: :ruby
  gem "w3c_validators", "~> 1.3.6"
  gem "rouge"
  gem "rubyzip", "~> 2.0"
end

# Active Support
gem "dalli", ">= 3.0.1"
gem "listen", "~> 3.3", require: false
gem "libxml-ruby", platforms: :ruby
gem "connection_pool", require: false
gem "rexml", require: false
gem "msgpack", ">= 1.7.0", require: false

# for railties
gem "bootsnap", ">= 1.4.4", require: false
gem "webrick", require: false
gem "jbuilder", require: false
gem "web-console", require: false

gem "rack"

# Active Job
group :job do
  gem "resque", require: false
  gem "resque-scheduler", require: false
  gem "sidekiq", require: false
  gem "sucker_punch", require: false
  gem "delayed_job", require: false
  gem "queue_classic", ">= 4.0.0", require: false, platforms: :ruby
  gem "sneakers", require: false
  gem "backburner", require: false
  gem "delayed_job_active_record", require: false
end

# Action Cable
group :cable do
  gem "redis-namespace"

  gem "websocket-client-simple", github: "matthewd/websocket-client-simple", branch: "close-race", require: false
end

# Active Storage
group :storage do
  gem "aws-sdk-s3", require: false
  gem "google-cloud-storage", "~> 1.11", require: false
  gem "azure-storage-blob", "~> 2.0", require: false

  gem "image_processing", "~> 1.2"
end

# Action Mailbox
gem "aws-sdk-sns", require: false
gem "webmock"

# Add your own local bundler stuff.
local_gemfile = File.expand_path(".Gemfile", __dir__)
instance_eval File.read local_gemfile if File.exist? local_gemfile

group :test do
  gem "minitest-bisect"
  gem "minitest-ci", require: false
  gem "minitest-retry"

  gem "benchmark-ips"
end

platforms :ruby, :windows do
  gem "nokogiri", ">= 1.8.1", "!= 1.11.0"

  # Needed for compiling the ActionDispatch::Journey parser.
  gem "racc", ">=1.4.6", require: false

  # Active Record.
  gem "sqlite3", "~> 1.4"

  group :db do
    gem "pg", "~> 1.3"
    gem "mysql2", "~> 0.5"
    gem "trilogy", github: "github/trilogy", branch: "main", glob: "contrib/ruby/*.gemspec"
  end
end

platforms :jruby do
  if ENV["AR_JDBC"]
    gem "activerecord-jdbcsqlite3-adapter", github: "jruby/activerecord-jdbc-adapter", branch: "master"
    group :db do
      gem "activerecord-jdbcmysql-adapter", github: "jruby/activerecord-jdbc-adapter", branch: "master"
      gem "activerecord-jdbcpostgresql-adapter", github: "jruby/activerecord-jdbc-adapter", branch: "master"
    end
  else
    gem "activerecord-jdbcsqlite3-adapter", ">= 1.3.0"
    group :db do
      gem "activerecord-jdbcmysql-adapter", ">= 1.3.0"
      gem "activerecord-jdbcpostgresql-adapter", ">= 1.3.0"
    end
  end
end

# Gems that are necessary for Active Record tests with Oracle.
if ENV["ORACLE_ENHANCED"]
  platforms :ruby do
    gem "ruby-oci8", "~> 2.2"
  end
  gem "activerecord-oracle_enhanced-adapter", github: "rsim/oracle-enhanced", branch: "master"
end

gem "tzinfo-data", platforms: [:windows, :jruby]
gem "wdm", ">= 0.1.0", platforms: [:windows]

# The error_highlight gem only works on CRuby 3.1 or later.
# Also, Rails depends on a new API available since error_highlight 0.4.0.
# (Note that Ruby 3.1 bundles error_highlight 0.3.0.)
if RUBY_VERSION >= "3.1"
  gem "error_highlight", ">= 0.4.0", platforms: [:ruby]
end
