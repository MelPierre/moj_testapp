# moj_testapp
A ruby application shell using the moj_template and moj_elements

Open the Gem file and add the following gem and save:
•	gem 'moj_template', ‘0.21.0'
•	Add dependencies in application.rb as set out in the template instructions:

* config.app_title = ''
* config.proposition_title = ''
* config.phase = ''
* config.product_type = ''
* config.feedback_url = ''
* config.ga_id = ''

•	Run bundle install, when complete
•	start the rails server ( rails s),  check project (http://0.0.0.0:3000)

# To see a working page complete the following:

•	In layout/ application.html.erb   replace everything with:

<% content_for :stylesheets do %>
  <%= stylesheet_link_tag "application", media: "all" %>
<% end %>
<% content_for :javascripts do %>
  <%= javascript_include_tag "application" %>
<% end %>
<%= render template: "layouts/moj_template" %>

•	Add a controller to test (static_controller.rb)

class StaticController < ApplicationController
end

•	add view to test (static / home.html.erb)

<h1> App Name </h1>
  First name: <input type="text" name="fname"><br>
  Last name: <input type="text" name="lname"><br>
  <input type="submit" value="Submit" class='button'>

•	add a route in routes.rb to point to page

root to: 'static#home'

Save the project, start server and check project is working, with the start page at on  (http://0.0.0.0:3000).


optional
Adding the MOJ Elements (to the moj_template)

Create a new root file in project called .bowerrc.
Add the required directory in the new file:
{
  "directory": "vendor/assets"
}

Then via the command line
•	bower install ministryofjustice/moj_elements –save
•	reference the files in the asset pipeline
*= require build/stylesheets/moj.tabs
//= require build/javascripts/moj.tabs

•	re-start the server and check project still works

Note:
•	moj_frontend_toolkit is now deprecated (gem 'govuk_frontend_toolkit', '2.0.1')
•	Replaced with moj_elements

Assets pipeline: three areas in ruby
•	App/assets/		normal course
•	Lib/assets/		additional libraries
•	Vendor/assets	vendor specific like bower used to install elements

In application manifest .js and .css files add //=require and name of the directory and file created so your project can recognize it.

Note: The asset pipeline automatically reads the first two subfolders so for example
In Vendor if the moj_elements are installed there is no need to explicitly add 

Assets/moj_elements
We only need 
//= require build/javascripts/moj.tabs
in the manifiest.

