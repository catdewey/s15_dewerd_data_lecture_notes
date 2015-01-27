# s15_dewerd_data_lecture_notes
####Spring 2015 Data Engineering CSCI 4830

---
## Lecture 1 1/12/15
###### online markdown site: dilllingeer.io
- does this one have a small font now too?
- this should be a list here.
odd, I seem to need at least one ret line after the list to make the next thing work.

## Lecture 2 1/15/15 
---
HW: Email him, get groups set up for REST HW

New paragraph by doing 2 spaces or 2 returns. Though I think that this is just going to be a new line.
Like this.

Classes Relevant to this one:
Big Data - Greg Greenstreet
Datacenter Scale Computing - Dirk Grunwald
Human Centered Computing - 
Data Mining - Christine Liu
Distributed Systems 

Inf Viz (more abstract)
Analytics
-this class-
Storage
OS
Clusters (more focused on hardware)

Social Networks
Data Analysis
- sampling 
- machine learning

Storage
- No SQL = better because schema (structure) of data evolves over time and its good at changing schema, and it is very fast but it can’t do any not optimized question. 
- mySQL = reliable/ robust, can optimize on some questions, can do any question

Statistics = built on sampling, not statistics if you know the answer.

Data modeling = easy to get wrong, bad for large scale, could have lots of data in wrong format, so difficult to change to.

Data collection (how to get and how to store)
Cleaning (when the data started, batch jobs to clean, before analysis)

Info Vis: how to display to the user
- D3 JS framework to do stuff in browser
- Tableaux
- R
- Scripting in general

UTF8 >> ACII

Data Lifecycle:
See written notes.

Tue Jan 20, 2015
-----
Due date for hw 1 is next week Thursday.

REST is architecture style. Used to developing web services that mimic the design of the Web itself. Documentation is a webpage.  Provides access to linked set of resources for each resource can CRUD or other operations. 
SOAP another architecture style. Very complex, very formal and thorough. REST won.

Put version num in url as well as api or js or css. Allows for parallel deployment. 
GET /users - all users list
GET /users/id - details of user “id”
POST /users - new user
PUT /users/id - modify user “id”

url ends in ? anything after is query parameters. Spaces may need to be hard coded. 

In request response cycle, each operation produces a response, typically synchronous. 
Responses in JSON usually. Other formats are possible HTML or XML. Can convert to maps, easily compressible, and fine control. Typically JSON both ways. Need authentication, OATH, easy in HTTP. 

Operations on 2 resources 
/user/0
/possessions/0
/users/0/possessions/0
can use nested or non nested

Issues
-security
-identity:= int ids are not as great, hackable. Names also bad.
-failure := http error codes 404, 301 302
-persistence how data stored

rspec is testing framework returns natural language results
fail fast will ret on first failed test.
rackup to bring up test data

use actual database like sql3


Thursday Jan 22
--------- 
get curl
make team, decide hw, work on it.

Git Version control (distributed) 
No 1 authoritative source
Files are in 1 of 5 status
- untracked
- unmodified
- modified
- staged
- remote (clone, new branch, checkout, modify, checkout, pull, merge, pull, push, repeat)

git init or git clone remote repository to start
1) git branch name (doesn’t move you into that branch)
2) git checkout name (moves into branch)
3) git add file (add or stage 1 file)
4) git commit -m “message” makes the file exist
5) git branch name (merges name into current branch)
6) resolve conflicts open file delete lines, choose, save, add and commit.

pull will choose default repo and need branch name
push remote repo name, pushes updated branch to remote one

git status (see status of files) -b (name of branch in)

````#```` is comment

fetch will get everything about the changes, you have the new things but not actually changed.

get move (use this instead of other things which register as a delete and create)

every branch has a head

git merge sort (pulls all changes into master branch)

Rebase- unless you know what you’re doing merge instead. Changes branch point.


Git Hub - using git with git hub

- have a master, create  (checkout) new branch, pull then serve into master again
- do good messages when committing
- @mention to message person 
- clone but still need collaborator access to push
- forking have own, and then sever 
- supports emojis, : thumbsup, 
- the github flow.

Challenge

http://epic-analytics.cs.colorado.edu:4000/
use curl??
curl website 
make sure have it on mahcine
some network library (how to make network request) typhus library

JS implementation of a web service
-Contact service in javaScript is easier

body parser, sql/ sql light.




Tuesday Jan 27, 2015
------
Lecture 5

Active record, sqlLite3, mongo 

Node.JS
- Code is packaged modules 
- http is core module, others are just extensions
- http.createServer(<function>)listen(1334, “127.0.0.1’); listens on port 1334 with the localhost method.
- functional langrage
- dynamic language, so no need to explicitly type things
- console.log(); is the printf of javascript world. 
- used to write servers and services
- event style programming, if you don’t want this, use Ruby
- user code is all single threaded built on top of library that uses thread pool for io
- user code is synchronous don’t have to worry about race conditions


get http module
create a server, register a function, start a server
print out a message

nodejs runs until there is no more work to be done in the future - so the listen function is very important.

Event loop: (GUI’s) just write handlers, code written is not control. If x happens, do this.
While (events to occur){
handle event
}
Never actually see the event loop, it is implied. 
``` 
console.log(“first”);
process.nextTick(function(){
	console.log(“third”);
};)
console.log(“second”);
````
On the first pass there registers a log, a nextTick and a log. On the next tick, it executes the function and calls 3rd. NextTick prioritizes this function before any of the other io stuffs. setImmediate allows io related callbacks to process first. setTimeout() takes 2 parameters, a function and a number of milliseconds before it is executed. setInterval(function, 1000) says run function 1 time a second. 

To run a .js program, node name.js

All the callbacks: great for asynchronous programming, but indent ad nausea. Functions that expect a callback have two parameters, the error handling is first then the second is the actual parameters the function needs to function. This can be avoided by using synchronous - frowned upon. Or you can use named callback functions, defining each function individually and then calling it where relevant.

Currying takes f(a,b,c) and changes it to f(a, f(b, f(c)))

Many other asynchronous mechanisms like event emitters and promises.


Exploration:
 curl http://epic-analytics.cs.colorado.edu:8080/api/1.0/methods
 curl http://epic-analytics.cs.colorado.edu:8080/api/1.0/first
 curl http://epic-analytics.cs.colorado.edu:8080/api/1.0/second
 curl http://epic-analytics.cs.colorado.edu:8080/api/1.0/third
 curl http://epic-analytics.cs.colorado.edu:8080/api/1.0/what
 curl -X POST —data ‘{“value”:1000, “author” : ”Catherine”}’ http://epic-analytics.cs.colorado.edu:8080/api/1.0/answer





