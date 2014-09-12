### ヘルパーメソッドも定義出来る

```
# web_sites.yml
  rubyonrails:
    id: 1
    name: Ruby on Rails
    url: http://www.rubyonrails.org

  google:
    id: 2
    name: Google
    url: http://www.google.com

```

```ruby
 module FixtureFileHelpers
   def file_sha(path)
     Digest::SHA2.hexdigest(File.read(Rails.root.join('test/fixtures', path)))
   end
 end
 ActiveRecord::FixtureSet.context_class.send :include, FixtureFileHelpers


 photo:
   name: kitten.png
   sha: <%= file_sha 'files/kitten.png' %>
```
