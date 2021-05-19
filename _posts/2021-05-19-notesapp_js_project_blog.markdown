---
layout: post
title:      "notesApp JS project Blog"
date:       2021-05-19 04:18:46 +0000
permalink:  notesapp_js_project_blog
---


So this project was difficult, but also at the same time not that difficult. That's in no way me being confident in my JS

skills, I've got so much to learn but am very excited to do so. The thing I feel like I realized during this project is that 

Javascript is an extremely powerful language, capable of so many things. I ended up doing a simple notes app due to my 

fear of doing something possibly too difficult causing me to take too long to complete the project, which would be fine on 

on my own but I *am* on a time limit. 
```

```
I think one of the most useful things I started doing with this project was creating new branches, I had been so worried in 

prior projects to mess up my whole app if I did something wrong, setting me back and stressing me out. So adding a new 

branch for each additional new feature I was trying to implement really was releaving. 
```

```
I have 3 .js files in my project; index.js, note.js and user.js

In my user.js and note.js files I have classes set up like this;

```
class User {

    static all = []
    static container = document.getElementById("user-profiles")

    constructor({id, name, img_url}) {
      this.id = id;
      this.name = name;
      this.img_url = img_url;
      
      this.element = document.createElement("img")

      this.element.addEventListener('click', this.handleImgClick)
     
   
      User.all.push(this)
    }
}
```

I think this blog will end up being about classes in my project. 

So, this isn't the only way to make a class in JS you can also make a functional class for example;

```
function Person(name, age) {
	this.name = name;
	this.age = age;
}
```

Then if you say;

```
alex = new Person(“Alex”, 32)
```

console returns;

Person {name: "Alex", age: 32}

```

```

Likewise if we set up an ES6 class like so; 

```
class Person { 
	constructor(name, age) {
	this.name = name;
	this.age = age;
	}
}
```

we'll get the same result;

```
alex = new Person(“Alex”, 32)
```

console returns;

Person {name: "Alex", age: 32}

```

```

So to discuss more of what's going on in my User class lets talk about the constructor, what is the constructor doing?

The constructor function is used like an initialize method in ruby, instantiating an object with these attributes where in a 

ruby class we'd say; 

```
class User
   def initialize(attribute)	 
       @attribute = attribute			 
     end
end
```

in JS we'd say; 

```
class User  {
      constructor(attribute) {			
			     this.attribute = attribute;			 
			}
}
```

so like using @ to symbolise an instance variable, in JS we are using 'this' in the same way.

What is 'static'? 

In JS we use the keyword 'static' to define a method or property for a class, much like in ruby where we'd say;

```
class User 
     def self.say_hi
          "hello"
     end 	 
end
```

So in my User class at the end of my constructor I'm saying;

```
User.all.push(this)
```

and have a static property for 'all' equal to an empty array [ ] 

so everytime I instantiate a new user I'm calling that 'all' property on the class and pushing 'this', which is that user 

instance into the array.

I'm also doing this in my Note class and it is beneficial as it would allow me to use a collection processing function like 

User.all.sort() or User.all.filter(). 

```

```

The last two things I can discuss about my User class are these; 

```
this.element = document.createElement("img")
```

and

```
static container = document.getElementById("user-profiles")
```

What's happening with these two lines involves two other functions I wrote;

```
render() {
      this.element.setAttribute("src", `${this.img_url}`)
      this.element.setAttribute("id", `${this.id}`)
      this.element.setAttribute("name", `${this.name}`)

      return this.element
    }
```

and 

```
attachUsersToDom() {      
      User.container.appendChild(this.render())        
    }
```

So what's happening in my render() is since I'm instantiating my User instances with an element, which is an img I'm just 

setting the attributes for this element which is unique to each instance then returning that element which is related to 

that instance.

```

```

Lastly my static container property is grabbing the element in my HTML file which is going to be the container for all my 

user profiles. 

So in my attachUsersToDom() function I'm saying User.container which is grabbing the container element where all user 

instances will be listed, and append this new instance to that container. 








