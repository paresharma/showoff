!SLIDE transition=fade

# Acceptance testing

using Capybara, rspec, Phantomjs(poltergeist)


!SLIDE execute transition=fade

# Capybara

Capybara helps you test web applications by simulating how a real user would interact with your app.

* Provides neat DSL to interact the web pages
* visit ‘/’
* click_on ‘A link’
* find(‘A css’)
* Great driver support, comes with selenium by default. We will use poltergeist(PhantomJs driver).

Capybara waits for dom element to be loaded

    @@@Ruby
    gem 'showoff'

