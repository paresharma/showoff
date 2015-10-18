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

# rspec-page-regression

Introducing rspec-page-regression

https://github.com/rprt/rspec-page-regression/tree/v1.0

    @@@ruby
    #Gemfile
    gem 'rspec-page-regression',
      git: 'https://github.com/rprt/rspec-page-regression.git',
      branch: 'v1.0'

    # in java_helper.rb
    require 'rspec/page-regression'

    # in your feature specs
    expect(page).to match_reference_screenshot


!SLIDE transition=fade

# Skip all the setup with

https://github.com/paresharma/rspec-manumit



!SLIDE transition=fade

Some links

https://github.com/jnicklas/capybara

https://relishapp.com/rspec/rspec-core/docs

http://www.rubydoc.info/github/jnicklas/capybara#The_DSL

https://www.relishapp.com/rspec/rspec-rails/docs/feature-specs/feature-spec

https://upcase.com/test-driven-rails-resources/rspec_acceptance.pdf

http://phantomjs.org/

https://github.com/teampoltergeist/poltergeist

And, for the presentation

https://github.com/puppetlabs/showoff


!SLIDE transition=fade

### That's it. ###
