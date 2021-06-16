# Rails API Basic Instructions

### Make the API
- Note: these instructions don't include relationships and are for a simple social media project build with no authentication
- `rails new bookface-backend --api`

### cors
- In config/initializers, we will have a cors.rb file
- Cors.rb is something that we will use to ensure that our requests are coming from permitted origins
- This file will automatically be generated with the api flag and you just have to comment it in (From Rails.application.config do to end)
- This is where we're going to put our site that our request is coming from:
- `origins 'example.com'`
- For now, our site is just going to be a file, we'll open up index.html
- So while we're just running this locally, we'll temporarily put a star here:
- `origins '*'`
- in our gemfile, we'll want to comment in our gem `rack-cors` 
- and then `bundle install`

### Users
- `rails g resource User name age:integer school`
- Gives us our migration, model, controller and routes, but no view folder
- then check migrations and run `rails db:migrate`

### Seeds
- make seed users
- run `rails db:seed`


### index
```
class UsersController < ApplicationController

    def index 
        users = User.all
        render json: users.to_json(except: [:created_at, :updated_at])
    end

end

```
- then run `rails s -p 3001` and go to `/users`
- could also use Serializer
