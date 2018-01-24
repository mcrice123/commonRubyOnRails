# Common Ruby on Rails commands

This repo stores some useful notes to myself to help me remember how to code in Ruby on Rails. 

Ruby on Rails is a web app framework that follows MVC (Model View Controller).

Overview of Ruby on Rails:
![alt text](https://i.stack.imgur.com/Sf2OQ.png "Visual Overview of Ruby on Rails")

`bundle install`: for installing dependencies referenced in Gemfile
(`bundle update`: for updating dependencies referenced in Gemfile)

## Deploying to Heroku:
### For initial deployment:
1. Move sqlite3 gem in Gemfile to development
2. Add 
```ruby
group :production do
  gem 'pg', '~> 0.18'
  gem 'rails_12factor'
end
```
   to end of Gemfile
3. Run `bundle install --without production`
4. Create Heroku account, if not already done: [See Heroku Instructions](https://devcenter.heroku.com/articles/getting-started-with-ruby#introduction)
5. Run `heroku create`
6. Run `git add .`
7. Run `git commit -m "pushing changes for deployment"`
8. Run `git push heroku master`
9. Run `heroku run rake db:migrate`
   OR
   Run`heroku run rails db:migrate`
10. Check to see if deployment worked at url given

### To change name of heroku app's url:
Run `heroku rename new-name`

## To create new model:
1. Run `rails generate scaffold Example title:string description:text foreign_key:references`
2. Run `rake db:migrate` OR `rails db:migrate` to create the table 
 - In '/db', new 'schema.rb' is added if none there previously OR 'schema.rb' is updated
 - In '/db/migrate', a new migration file is added
 - In '/app/models', a new file called 'example.rb' is added that looks like this:
 ```ruby
 class Example < ApplicationRecord
 end
 ```
 - In '/app/config/routes.rb', the line `resources :examples` is added near the top of the file
   - Running `rake routes` or `rails routes` shows the available routes, including the new ones created by this line
 - In '/app/controllers', a new file called 'examples_controller.rb' is added and it contains all CRUD (create, read, update, destroy) methods

### To destroy scaffold:
`rails destroy scaffold Example`

