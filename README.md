# OAuth Echo Authentication

Makes it dead easy to do OAuth Echo authentication with Rails.


## Usage

Add this to Gemfile.

    gem 'oauth_echo_authentication', :git => 'git://github.com/tkawa/oauth_echo_authentication.git'


## Examples

### Simple

    # app/controllers/users_controller.rb
    class UsersController < ApplicationController
      oauth_echo_authenticate_with :twitter

      def index
        render :json => @current_oauth_echo_user
      end
    end

### Advanced

    # app/controllers/users_controller.rb
    class UsersController < ApplicationController
      before_filter :authenticate

      def index
        render :json => @current_oauth_echo_user
      end

      private
      def authenticate
        @current_oauth_echo_user = authenticate_with_oauth_echo!
        # TODO: process it yourself
      end
    end


## Restriction

Supports the OAuth Service Provider only Twitter now.


## Copyright

Copyright (c) 2011 Toru KAWAMURA.

This project rocks and uses MIT-LICENSE.
