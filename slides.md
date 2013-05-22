## Agenda

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



## What is Static Analysis

Information about your code that is properties of your code. Mostly obtained by looking at your code statically not looking at runtime or dynamic data.


## blah



## What it Catches

Items there are 'easy' rules to enforce.


## Unessiary gstring

In Groovy:

`println "Bob's your uncle!"`

vs

`println 'Bob\'s your uncle'`


## Missing Triple Equals

In JavaScript doing: 

`if(x==y)`

vs

`if(x===y)`
    



## What it misses

The archetectural desisions you have made. For example chosing to always use mixins for adding shared functionalaity to controllers vs using inheritance. Just archetectural flaws in general. 


## What it misses

In general these tools are not going to help you from doing something silly like having a great distrubuted system that that all depends on a single MySQL node.



## The Tools 

  * CodeNarc
  * Cobertura
  * JSLint



## CodeNarc

"CodeNarc analyzes Groovy code for defects, bad practices, inconsistencies, style issues and more." - [CodeNarc](http://codenarc.sourceforge.net/)


## CodeNarc - Plugin

There is a grails plugin that you can use to give you CodeNarc. BuildConfig:

	plugins {
      compile ":codenarc:0.18.1"
      ...
    }


## CodeNarc - My Standard Config

	codenarc.processTestUnit = false
	codenarc.processTestIntegration = false
	codenarc.propertiesFile='grails-app/conf/codenarc.properties'
	codenarc.ruleSetFiles = "rulesets/basic.xml,rulesets/exceptions.xml, rulesets/imports.xml,rulesets/grails.xml, rulesets/unused.xml, rulesets/size.xml, rulesets/concurrency.xml,rulesets/convention.xml,rulesets/design.xml,rulesets/groovyism.xml,rulesets/imports.xml,rulesets/logging.xml"
    
	codenarc.reports = {
		MyXmlReport('xml') {               // The report name "MyXmlReport" is user-defined; Report type is 'xml'
			outputFile = 'target/test-reports/CodeNarcReport.xml'  // Set the 'outputFile' property of the (XML) Report
			title = 'CodeNarc'             // Set the 'title' property of the (XML) Report
		}
		MyHtmlReport('html') {             // Report type is 'html'
			outputFile = 'target/test-reports/CodeNarcReport.html'
			title = 'CodeNarc HTML'
		}
	}


## CodeNarc - Additional Dependancies

Some rules require more dependancies then what is included in grails, gmetrics jar.

    dependencies {
      compile 'org.gmetrics:GMetrics:0.6'
      ...
   	}
