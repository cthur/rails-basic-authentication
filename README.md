# README
Ruby version: 2.3.1
Rails version: 5.0.0

Purpose of this app:
This app will be dealing with a simple login system for users made from scratch. 

How to create this app:
-Command Line
  rails generate resource user email password_digest
  rake db:migrate
  rails generate controller sessions new

-Gemfile
  gem 'bcrypt', '~> 3.1.7'

-config/routes.rb
  get 'signup', to: 'users#new', as: 'signup'
  get 'login', to: 'sessions#new', as: 'login'
  get 'logout', to: 'sessions#destroy', as: 'logout'

  resources :users
  resources :sessions

-models/user.rb
  has_secure_password
  
  attr_accessible :email, :password, :password_confirmation
  
  validates_uniqueness_of :email
