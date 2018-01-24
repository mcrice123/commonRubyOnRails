### Common Ruby on Rails commands

This repo stores some useful notes to myself to help me remember how to code in Ruby on Rails. 

Ruby on Rails is a web app framework that follows MVC (Model View Controller).

Overview of Ruby on Rails:
![alt text](https://i.stack.imgur.com/Sf2OQ.png "Visual Overview of Ruby on Rails")

`bundle install`: for installing dependencies referenced in Gemfile
(`bundle update`: for updating dependencies referenced in Gemfile)

On new project:
1. Move sqlite3 gem in Gemfile to development.
2. Add 
```ruby
group :production do
  gem 'pg'
end
```
3. Run `bundle install --without production`


