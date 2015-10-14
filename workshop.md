!SLIDE transition=fade

# Acceptance testing

### Capybara, Rspec, Phantomjs (Poltergeist) ###
### and ###
### *Java* ###


!SLIDE transition=fade

# Agenda

### Acceptance testing of Java apps

We will use `Capybara` to interact with our apps

We will make Capybara use `PhantomJS` to browse through the apps

Capybara will need `Poltergeist` to talk to PhantomJS

And, we sugar-coat our specs with `RSpec`


!SLIDE transition=fade

# Capybara

Capybara helps you test web applications by simulating how a real user would interact with your app.

Provides neat DSL to interact the web pages

Great driver support, comes with selenium by default. We will use poltergeist(PhantomJs driver).

Capybara waits for DOM to be loaded


!SLIDE transition=fade

# So, DSL I say

Navigating:

    @@@ruby
    visit('/projects')

Clicking links and buttons

    @@@ruby
    click_link('id-of-link')
    click_link('Link Text')
    click_button('Save')
    click_on('Link Or Button')


!SLIDE transition=fade

# DSL, contd...

Interacting with forms

    @@@ruby
    fill_in('First Name', :with => 'John')
    choose('A Radio Button')
    check('A Checkbox')
    uncheck('A Checkbox')
    attach_file('Image', '/path/to/image.jpg')
    select('Option', :from => 'Select Box')

Querying

    @@@ruby
    page.has_selector?('table tr')
    page.has_selector?(:xpath, '//table/tr')
    page.has_xpath?('//table/tr')
    page.has_css?('table tr.foo')
    page.has_content?('foo')

!SLIDE transition=fade

Some more

    @@@ruby
    page.execute_script("$('body').empty()")

    within("li#employee") do
      fill_in 'Name', :with => 'Jimmy'
    end

    find('#navigation').click_link('Home')

And a lot more...

http://www.rubydoc.info/github/jnicklas/capybara#The_DSL


!SLIDE transition=fade

# PhantomJS and poltergeist

PhantomJS is a headless WebKit scriptable with a JavaScript API. It has fast and native support for various web standards: DOM handling, CSS selector, JSON, Canvas, and SVG.

Poltergeist is a driver for Capybara that allows you to run your tests on a headless WebKit browser, provided by PhantomJS.


!SLIDE transition=fade

# PhantomJS is cool

Just like a Chrome or a Firefox, only you don't see what you're browsing

    @@@javascript
    // google.js
    console.log('Loading a web page');
    var page = require('webpage').create();
    var url = 'http://google.com/';
    page.open(url, function (status) {
      console.log(page.content);
      phantom.exit();
    });

    // and in the command line
    $ phantomjs google.js


!SLIDE transition=fade

# In comes Poltergeist

**But** PhantomJS best practice says:

### "Writing raw PhantomJS script is not everyone's cup of tea." ###

http://phantomjs.org/best-practices.html



!SLIDE transition=fade

### So, we harness it's power with Poltergeist

Poltergeist supports all the mandatory features for a Capybara driver, and the following optional features:

    @@@javascript
    page.evaluate_script and page.execute_script
    page.within_frame
    page.status_code
    page.response_headers
    page.save_screenshot
    page.driver.render_base64(format, options)
    page.driver.scroll_to(left, top)
    page.driver.basic_authorize(user, password)
    element.native.send_keys(*keys)
    window API
    cookie handling
    drag-and-drop
