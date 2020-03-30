---
layout: post
title:      "Adding a search form to my Rails project"
date:       2020-03-30 19:45:01 +0000
permalink:  adding_a_search_form_to_my_rails_project
---



For my Rails final project review I was asked to add a search function to my site and write a blog post about it so here we go. My rails project was a web app that allows users to make friendly challenges to others and keep track of who won/lost and what the payment is. To achieve this I would need to add a search bar to the index view, make adjustments to the controller to handle the information sent by the form, and the model to create the logic needed to process the information.

For the view page I decided to use form_tag because I did not want to associate the form with a model. I also had the form send the input to the controller as a get request to the index page as I wanted to reload the same page and was not making any changes to the database. Lastly I put the form into a partial so that it would keep the index page cleaner.
```
<%=form_tag(challenges_path, method: :get) do %>
  <%= text_field_tag(:search, params[:search]) %>
  <%= submit_tag ("Search") %>
<% end %>
```

For the controller I replaced @challenges = Challenge.all with the new Challenge method Challenge.search(params[:search]) allowing the model to select what challenges to present to the view page. I also had to add :search to the strong params so that Rails would allow the information to be passed to model. 

The last step was building the search class method. The method would need to return Challenge.all if no search had been made or return all the challenges that met the  search result. I also wanted to create a search with didn't require exact matches. Here is the code I came up with ...
```
  def self.search(search)
    if search
      user = User.where("username like ?", "%#{search}%")
      wager = Wager.where("name like ?", "%#{search}%")
      payment = Payment.where("name like ?", "%#{search}%")
      if user || wager || payment
        self.where(user_id: user.ids) + self.where(challenger_id: user.ids) + self.where(wager_id: wager.ids) + self.where(payment_id: payment.ids)
      else
        Challenge.all
      end
    else
      Challenge.all
    end
  end
```
This search uses the .where scope along with the 'like' modifier to search the database for items containing the search elements. It also is case insensitive making it easier for the user to find matches. It adds all the results together and then returns it to the controller to be passed to the view.

And that is it, the search function is up and running and working well.
