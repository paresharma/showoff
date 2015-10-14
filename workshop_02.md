!SLIDE transition=fade

# Let's try Selenum

Hope you have `Firefox` installed

    @@@ruby
    # in your Gemfile, add
    gem 'selenium-webdriver'
    # then run bundle install

    # in your java_helper.rb
    # change
    Capybara.default_driver = Capybara.javascript_driver = :poltergeist
    # To
    Capybara.default_driver = Capybara.javascript_driver = :selenium

And, run the tests


!SLIDE transition=fade

# Let's try with some actual app, say, Booking


!SLIDE transition=fade

# rspec-page-regression

Introducing rspec-page-regression

https://github.com/rprt/rspec-page-regression/tree/v1.0

    @@@ruby
    #Gemfile
    gem 'rspec-page-regression',
      git: 'https://github.com/rprt/rspec-page-regression.git',
      branch: 'v1.0'

    # in your feature specs
    expect(page).to match_reference_screenshot


!SLIDE transition=fade

# Skip all the setup with

https://github.com/paresharma/rspec_java


!SLIDE transition=fade

### That's it. ###
