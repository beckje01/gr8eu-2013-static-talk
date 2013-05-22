# Agenda

* What is Static Analysis
* What it Catches
* What it misses
* The Tools
  * CodeNarc
  * Cobertura
  * JSLint
  * CSSLint(?)
  * Task List (ToDo search)
* Jenkins
* Dealing with Old Code
* Demo



# What is Static Analysis

Information about your code that is properties of your code. Mostly obtained by looking at your code statically not looking at runtime or dynamic data.


# blah



# What it Catches

Items there are 'easy' rules to enforce.


# Unessiary gstring

In Groovy:

`println "Bob's your uncle!"`

vs

`println 'Bob\'s your uncle'`


# Missing Triple Equals

In JavaScript doing: 

`if(x==y)`

vs

`if(x===y)`
    



# What it misses

The archetectural desisions you have made. For example chosing to always use mixins for adding shared functionalaity to controllers vs using inheritance. Just archetectural flaws in general. 


# What it misses

In general these tools are not going to help you from doing something silly like having a great distrubuted system that that all depends on a single MySQL node.