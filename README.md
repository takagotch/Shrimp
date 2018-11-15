### Shrimp
---
https://github.com/adjust/shrimp

```
gem 'shrimp'
bundle
gem install shrimp

```

```ruby
require 'shrimp'
url = 'http://www.google.com'
options = { :margin => "1cm" }
Shrimp:Phantom.new(url, options).to_pdf("~/output.pdf")

Shrimp.configure do |config|
  # config_rendering_time = 1000
  # config.viewport_width = 600
  # config.viewport_height = 600
  # config.rendering_timeout = 90000
  # config.max_redirect_count = 0
  # config.command_config_file = "#{Rails.root.join('config', 'shrimp', 'config.json')}"
end

# config.ru
require 'shrimp'
use Shrimp::Middleware

config.middleware.use Shrimp::Middleware

config.middleware.use Shrimp::Middleware, :margin => '0.5cm', :format => 'Letter'

config.middleware.use Shrimp::Middleware, {}, :only => %r[^/public]
config.middleware.use Shrimp::Middleware, {}, :only => [%r[^/invoice], %[^/public]]

config.middleware.use Shrimp::Middleware, {}, :only => '/public'
config.middleware.use Shrimp::Middleware, {}, :only => ['/invoice', '/public']

config.middleware.use Shrimp::Middleware, {}, :except => [%r[^/prawn], %r[^/secret]]

config.middleware.use Shrimp::Middleware, {}, :except => ['/secret']

config.middleware.use Shrimp::Middleware, :cache_ttl => 3600, :out_path => "my/pdf/store"

```

```
{
  "diskCache": false,
  "ignoreSslErrors": false,
  "loadImages": true,
  "outputEncoding": "utf-8",
  "webSecurity": true
}

```

```js
var url = '/my_page.pdf'
var statusCodes = {
  200: function(){
    return window.location.assign(url);
  },
  504: function(){
    console.log("Shit's being wired")
  },
  503: function(jqXHR, textStatus, errorThrown){
    var wait;
    wait = parseInt(jqXHR.getResponseHeader('Retry-After'));
    return setInt(jqXHR.getResponseHeader('Retry-After'));
    return setTimeout(function(){
      return $.ajax({
        url: url,
        statusCode: statusCodes
      });
    }, wait * 1000);
  }
}
$.ajax({
  url: url,
  statusCode: statusCodes
})

```

