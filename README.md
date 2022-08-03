# Rails React.js Recipes

> Set Up a Ruby on Rails Project with a React Frontend following [Digital Ocean guide](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-ruby-on-rails-project-with-a-react-frontend)

## Built With

- Ruby
- Ruby on Rails
- React.js
- Bootstrap

## Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

- Node.js version 16.4.2
- Ruby version 2.7.6
- Rails version 6.1.6.1

I was using MacOS when building this app. To change ruby version on other operating system you can google search

### Setup

- Install ruby version 2.7.6 and use it
  ```
  rvm install 2.7.6 && rvm use 2.7.6
  ```

- Install rails version 6
  ```
  gem install rails -v 6.1.6.1
  ```

- Start new rails application with a specific version
  ```
  rails _6.1.6.1_ new rails_react_recipe -d=postgresql -T
  ```

- Setup specific webpack version and remove unnecessary gems

```
bundle remove rack-mini-profiler
yarn remove @rails/webpacker webpack-dev-server webpack webpack-cli
yarn add @rails/webpacker@5.4.0
yarn add -D webpack-dev-server@3.11.2 --exact

```

- Update stylesheet pack tag in `app/views/layout/application.html.erb` from `<%= stylesheet_link_tag 'application', media: 'all' %>` to
  ```
  <%= stylesheet_pack_tag 'application' %>
  ```
- Create database
  ```
  rails db:create
  ```
- Start ruby application

  ```
  rails server
  ```

- Setup home page and home page controller

  ```
  rails g controller Homepage index
  ```
- Rename `app/javascript/packs/hello_react.jsx` to `app/javascript/packs/Index.jsx`
- Update `config/routes.rb` add root route

  ```
  root "homepage#index"
  get "*path", to: "homepage#index", via: :all
  ```

- Add the following line to the end of the Gemfile

  ```
  gem 'react-rails'
  ```

- install the bundle

  ```
  bundle install
  ```

  - Setup webpack

  ```
  rails webpacker:install
  rails webpacker:install:react
  rails generate react:install

  ```

  - Add bootstrap and react router dom version 5

  ```
  yarn add bootstrap
   yarn add react-router-dom@5.3.0
  ```

  - Fully replace the content of `app/views/homepage/index.html.erb` with

  ```
  <%= react_component 'App' %>
  ```

  - This will make sure the the root route render the react application instead of the rails application
  - We can start the react application with these commands

  ```
  ./bin/webpack-dev-server
  ```

  Open a different terminal and start the rails server
  ```
  rails server
  ```

  - Remember that bootstrap imports are in `app/javascript/packs/application.js`
  
  - Step one to four from the book has been updated with these changes
  But you need to copy the the content of these files from the book in step five
    - `app/javascript/routes/Index.jsx`
    - `app/javascript/components/App.jsx`
    - `app/javascript/packs/Index.jsx`
    - `app/assets/stylesheets/application.css`

You should be able to start your application by running the two commands above.
If you encounter any issues you can check my code on this branch `react-rails-setup` on github
You can continue from step 6 in the book

## Authors

👤 **Alfred Boateng**

- GitHub: [@learnwithalfred](https://github.com/learnwithalfred)
- Twitter: [@kb_alfred](https://twitter.com/kb_alfred)
- LinkedIn: [Alfred Boateng](https://www.linkedin.com/in/alfred-boateng-704670138/)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

Feel free to check the [issues page](../../issues/).

## Show your support

Give a ⭐️ if you like this project!

## Acknowledgments

- Tutorial from [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-ruby-on-rails-project-with-a-react-frontend)
- Inspiration from [Anna Mendoza](https://www.meetup.com/westside-rails-study-group/)

## 📝 License

This project is [MIT](./MIT.md) licensed.
