Learn-Everything: A collaborative wiki for learning all human knowledge

#How is it different from Wikipedia?

* Wikipedia's articles are written to be a reference, not as a pedagogical guide.
* Every article on Learn-Everything will start with a list of pre-requisites. E.g. the article of multiplication will state that you should know addition; the article on addition will state that you should know how to count; etc.
* The pedagogical content/material need not be contained in the Learn-Everything article itself; it's perfectly acceptable for an article to just be a link to some external source (e.g. to Wikipedia).
* Wikipedia's wiki syntax is terrible. Learn-Everything will use Markdown instead.

## ... And how is it similar to Wikipedia?

* Essentially a wiki that any user can edit.
* Learn-Everything will probably copy Wikipedia's idea of "disambiguation page" and "redirection page".

#How is it different from Khan Academy?

* Khan focuses on a couple of specific topics (e.g. math, history, economics, etc.), providing original content for each; Learn-Everything is intended to cover a much broader scope of topics, and can get by by not providing original content, and just linking to existing content on the web.
* Khan has interactive exercises; Learn-Everything is just plain markdown articles.

## ... And how is it similar to Khan Academy?

* I'd like for the site to eventually allow users to track what articles they already know, and to track "goal" pages that they hope to one day know, with the site computing the dependency graph to determine what the user needs to learn until they can reach their goal.

#Is it ready for the public?

NO! There is little more than this readme for now.

# What's the licensing like?

Undecided, but will be open source. E.g. if we use Sencha ExtJS for the UI, it'll probably end up being GPL3.

# What's the planned architecture

* [NodeJS](http://nodejs.org/)
* [ExpressJS](http://expressjs.com/)
* Some sort of JSON document store for the articles (perhaps [MongoDB](http://www.mongodb.org/)?)

Append-only; when you edit an article, you just post a new version of that article. When a user retrieves an article by title, it's assumed they want the latest version, and so we just give the one with the biggest timestamp.

## Example article format:

    {
      "title": "Multiplication",
      "updated": 20140116020714,
      "author": "nebu",
      "type": "article",
      "prereq": [ "Addition" ],
      "markdown": "Multiplication is just repeated addition."
    }


    {
      "title": "Cube",
      "updated": 20140116020714,
      "author": "nebu",
      "type": "disambiguation",
      "meanings": [
        "Cube (geometry)": "a 6 sided geometric figure",
        "Cube (operation)": "multiplying a number by itself three times"
      ]
    }


    {
      "title": "Saint Nick",
      "updated": 20140116020714,
      "author": "nebu",
      "type": "redirection",
      "redirectTo": "Santa Claus"
    }

# Ideas

* Detect and prevent cycles in dependency. It's okay for either the "Hot" article to be "Not cold" or the "Cold" article to be "Not hot", but not both.
* Guidelines, e.g. "Start with an extensional definition (examples), then proceed onto intensional definitions."
* Client side could optionally perform google-image search to provide extensional definition (e.g. article on dog; have a bunch of images of dogs via a google search by the client)
