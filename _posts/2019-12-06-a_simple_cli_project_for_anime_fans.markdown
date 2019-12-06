---
layout: post
title:      "A Simple CLI Project For Anime Fans!"
date:       2019-12-06 21:29:44 +0000
permalink:  a_simple_cli_project_for_anime_fans
---



So for our first project we were required to create a CLI application demonstrating OOP as well as pull information from the internet to utilize in our program using an API or Scraper. 

I did feel overwhelmed at first doing a coding project when I'm entirely new to the code world and have only been coding since we've started Oct 7th and even though it is pretty nerve wreaking it is good to be put under pressure and to apply things we're learning immediately to gain that confidence in these new ideas as well as being given deadlines almost like its a job. With that said I did choose to make mine pretty simple, just meeting the main requirements, but for future projects I will definitely take a deeper dive and push myself further.

So there were two videos that really helped me out with this one, there was an Avi CLI Gem walkthrough video and another one I can't remember the title of but it was a basic video on setting up and API/making calls and kind of how our project should look like. 

Using what I saw in those videos as well as a quick 5 min video from the Google Doc demonstrating how to create a new gem/repo on Github helped me get things going. 


**Struggles**

So at first honestly I was having a difficult time finding an API to use, really I feel like that was my biggest struggle, I still don't know how to use RapidAPI, it gives demonstrations of how to set up your API call in different programming languages from a drop down menu but for Ruby the two examples were using Unirest and http::net, both things I'm not familiar with yet so I had found an IMDB API alternative called OMDB which seemed fairly simple. I got a key from the site and had my URL so I thought I was good to go but once I had it in my API class and entered pry to check out what "response" returned to me I started to doubt this was the API for me. It returned what I expected but for just 1 film, and I managed to make it return more films but it just wasn't anything I was interested in doing. I wanted to have it list out all Horror films released specifically in 2019 so the user could then ask for more information (Director, Actors, RT Score, Plot, etc..) on that film. 

**Process**

The process was pretty simple, we'd done this type of setup in other labs and the video's were extremely helpful about showing how things should be setup. So eventually I found a very simple API that required no key and was something I'm interested in, the Studio Ghibli API, it was incredibly straigh-forward and gave me all the information I needed to create this basic CLI application. So I made my API class and Object class first, that took less than 20 minutes, then after my one on one with Madeline and meeting with my study group I went ahead and built out my CLI. Building the CLI was what I found to be kind of difficult, really it's just a lot of trial and error with the menu method and film_details method. Keeping things abstract is something that usually scrambles my brain but with this project during my study group I figured out how to make my program more abstract.

if input.to_i > 0 && input.to_i < StudioGhibliCli::Film.all.size
        film_details(input)
      elsif input == "list"
        list
      elsif input == "exit"
        goodbye
      else 
        puts "\nINVALID INPUT: type 'list' or 'exit'".red
				
In this section of my code in the menu method I initially had;

if input.to_i > 0 

which works but breaks my code if you enter a number larger then the amount of films produced by Studio Ghibli, so that's not good, I want my program to continue working if the site is updated, if Studio Ghibli makes a new film or many new films I want my code to be able to handle those changes. 

so I wanted to have that line say "If user input is greater than 0 but is also less than the size of my @@all class variable which is an array containing all Studio Ghibli films, (20) in this case, then the program is good to move forward and pull the details for that user input" 

So I came up with this;

if input.to_i > 0 && input.to_i < StudioGhibliCli::Film.all.size

It actually felt pretty good to figure that out and try giving my program any input I can think of to see that it would either give me an error and present my options again or give me the details of the film related to my user input. 


**Conclusion**

Overall I think my project turned out ok, it is pretty simple but that's what I feel comfortable with at the moment. Now that I've reached this point, after we learn how to set up our own local environment in Atom or whichever editor we want to use I will definitely be constantly coding, collaborating with my study group and just trying to experiment, try to make mistakes, learn from those mistakes and get more comfortable coding!






