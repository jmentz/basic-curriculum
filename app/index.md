---
title: Rails Girls Berlin
layout: default
---

# Get to know the tools

Text Editor

> Sublime Text, Komodo Edit, Vim, Emacs, and Gedit are examples of text editors your can use for writing code and editing files.

Terminal (known as Command Prompt on Windows)

> Where you start the rails server and run commands.

Web browser

> (Firefox, Safari, Chrome) for viewing your application.

## Important

It is important that you select the instructions specific to your operating system - the commands you need to run on a Windows computer are slightly different to Mac or Linux. 
If you’re having trouble check the Operating System switcher at the bottom of the commands.

# 1. Creating the application

We’re going to create a new Rails app called railsgirls.

First, let’s open a terminal:

* Mac OS X: Open Spotlight, type Terminal and click the Terminal application.
* Windows: Click Start and look for Command Prompt, then click Command Prompt with Ruby on Rails.
* Linux (Ubuntu): Search for Terminal on the dash and click Terminal.

Next, type these commands in the terminal:

    mkdir projects


You can verify that a directory named projects was created by running the list command: `ls`. You should see the projects directory in the output. Now you want to change the directory you are currently in to the projects folder by running:

    cd projects

You can verify you are now in an empty directory or folder by again running the `ls` command. Now you want to create a new app called railsgirls by running:

    rails new railsgirls

This will create a new app in the folder railsgirls, so we again want to change the directory to be inside of our rails app by running:

    cd railsgirls

If you run `ls` inside of the directory you should see folders such as `app` and `config`. You can then start the rails server by running:

    rails server

**Windows users: You may need to replace `bin\rails` with `script\rails`, depending on the version of Rails you have installed.**

Open `http://localhost:3000` in your browser. You should see “Welcome aboard” page, which means that the generation of your new app worked correctly.

Notice in this window the command prompt is not visible because you are now in the Rails server, the command prompt looks like this:

    $

When the command prompt is not visible you cannot execute new commands. If you try running `cd` or another command it will not work. To return to the normal command prompt:

Hit `CTRL-C` in the terminal to quit the server.

<span class="lead coach">Coach: Explain what each command does. What was generated? What does the server do?</span>

# 2. Create Idea scaffold

We’re going to use Rails’ scaffold functionality to generate a starting point that allows us to list, add, remove, edit, and view things; in our case ideas.

<span class="lead coach">Coach: What is Rails scaffolding? (Explain the command, the model name and related database table, naming conventions, attributes and types, etc.) What are migrations and why do you need them?</span>

    rails generate scaffold idea name:string description:text picture:string
    rake db:migrate
    rails server

Open `http://localhost:3000/ideas` in your browser. Click around and test what you got by running these few command-line commands.

Hit `CTRL-C` to quit the server again when you’ve clicked around a little.

# 3. Design

<span class="leach coach">Coach: Talk about the relationship between HTML and Rails.
What part of views is HTML and what is Embedded Ruby (ERB)? What is MVC and how does this relate to it? 
(Models and controllers are responsible for generating the HTML views.)</span>

The app doesn’t look very nice yet. Let’s do something about that. We’ll use the Twitter Bootstrap project to give us nicer styling really easily.

Open `app/views/layouts/application.html.erb` in your text editor and above the line

    <%= stylesheet_link_tag "application", media: "all", "data-turbolinks-track" => true %>

add

    <link rel="stylesheet" href="http://railsgirls.com/assets/bootstrap.css">

and replace

    <%= yield %>

with

    <div class="container">
      <%= yield %>
    </div>

Let’s also add a navigation bar and footer to the layout. In the same file, under `<body>` add

    <div class="navbar navbar-fixed-top">
      <div class="navbar-inner">
        <div class="container">
          <a class="brand" href="/">The Idea app</a>
          <ul class="nav">
            <li class="active"><a href="/ideas">Ideas</a></li>
          </ul>
        </div>
      </div>
    </div>

and before `</body>` add

    <footer>
      <div class="container">
        Rails Girls 2013
      </div>
    </footer>

Now let’s also change the styling of the ideas table. Open `app/assets/stylesheets/application.css` and at the bottom add

    body { padding-top: 100px; }
    footer { margin-top: 100px; }
    table, td, th { vertical-align: middle !important; border: none !important; }
    th { border-bottom: 1px solid #DDD !important; }

Now make sure you saved your files and refresh the browser to see what was changed. You can also change the HTML & CSS further.

<span class="lead coach">Coach: Talk a little about CSS and layouts.</span>