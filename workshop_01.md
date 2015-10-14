!SLIDE transition=fade


# Finally, RSpec

RSpec is a Behaviour-Driven Development tool for Ruby programmers

We will use it for Java :-)

RSpec focuses on the documentation and design aspects of TDD


!SLIDE transition=fade

### And, we will focus on RSpec features

Feature specs are high-level tests meant to exercise slices of functionality
through an application. They should drive the application only via its external
interface, usually web pages

The feature and scenario DSL correspond to describe and it


!SLIDE transition=fade

# some sample feature test

    @@@ruby
    RSpec.feature "Home Page" do
      scenario "Visits home page" do
        # Capybara DSL
        visit "/"
        # RSpec matcher
        expect(page.body).to have_text("Welcome Homie")
      end
    end


!SLIDE transition=fade

# Enough talk, let's DO

Clone this repo https://github.com/bring/TestingDemoWeb

And follow the README to get started

Run the server, and keep  it running


!SLIDE transition=fade

### Now, let's DO

    @@@
    # Make sure you have PhantomJS, preferably 1.9.8
    $ phantomjs -v
    $ brew install homebrew/versions/phantomjs198

Create a file called `Gemfile` under project root

    @@@ruby
    # in the Gemfile
    source 'http://rubygems.org'
    gem 'capybara'
    gem 'poltergeist'
    gem 'rspec'

    # Run
    $ bundle install
    $ rspec --init

Great, we're a good to go!!!


!SLIDE transition=fade

### Not quite... Some more configuration

`cd spec`

Create a file called `java_helper.rb`

    @@@ruby
    require 'spec_helper'
    require 'capybara/rspec'
    require 'capybara/poltergeist'
    Capybara.default_driver = Capybara.javascript_driver = :poltergeist
    # Capybara.app_host = 'http://localhost:9966'
    Capybara.app_host = ENV['APP_HOST']
    Capybara.run_server = false


!SLIDE transition=fade

### Time for some tests

Make a directory `spec/features/`

We will put all our specs in `features/`

Another file, `spec/features/homepage_spec.rb`

    @@@ruby
    require 'java_helper'

    RSpec.feature 'Home page', js: true do
      scenario 'visit homepage' do
        visit '/'
        expect(page.status_code).to eq(200)
        expect(page.has_content?('Customer Management')).to be true
      end
    end


!SLIDE transition=fade

### Run the tests

From the project root

    @@@
    $ APP_HOST=http://localhost:8080 bundle exec rspec

    # APP_HOST can be coded in java_helper.rb too

Hope it's all green...:-)


!SLIDE transition=fade

# Let's try some

1. Add a customer and verify (maybe, `features/add_customer_spec.rb`)


2. Edit a customer and verify


3. Delete a customer and verify
