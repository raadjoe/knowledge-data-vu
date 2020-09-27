# Tutorial: Building a Semantic Web Application

This tutorial shows the basics for building Semantic Web applications based on what you have learnt so far.

## Goals of the tutorial
In this session you will learn how to:
* Set up a Web application
* Connect your Web app with your triplestore (i.e. GraphDB)
* Create nice visualisations of your data

## Things we will be using
* `vuDataset.ttl` as data example. This Turtle file contains only 9 triples, describing the teachers of certain courses.
* HTML file to generate the content in a Web page
* CSS style, following the [Bootstrap](https://getbootstrap.com/docs/4.0/components) toolkit
* [Angular](https://angular.io/), a Javascript framework to facilitate the bindings between  
* The [Chart.js](http://jtblin.github.io/angular-chart.js/) library to visualise data  

**N.B. The information above is only for reference!!** No need to install anything, everything you need is already in this repository.


## Setting up
* Download all files and subdirectories from this repository (by downloading `SW-Application.zip`):
  - Necessary files: `index.html`, `main.js`, and `vuDataset.ttl`
  - Necessary directories: `css` and `js`
* Start your GraphDB Workbench

## Steps
1. Create a new repository in GraphDB, and name it `repo-VU`
2. Import the `vuDataset.ttl` dataset into this repository (Import --> RDF --> Upload RDF Files)
3. Test the following SPARQL query in your `repo-VU` repository (see [Screenshot-Query](screenshots/Screenshot-Query.png) in this directory)
```
SELECT ?teacher (COUNT(?course) AS ?nbr_courses)
WHERE { ?teacher <http://example.org/vu/teaches> ?course }
GROUP BY (?teacher)
ORDER BY DESC(?nbr_courses)
```
4. Open `index.html` in your browser
5. Give a name for your Web application, and write it in the first text field
6. Paste the GraphDB repository URL in the second text field (see [Screenshot-Repository](screenshots/Screenshot-Repository.png) in this directory)
7. Paste the above SPARQL query in the third text field
8. Click the button `GO!`. Now you should see a Pie Chart showing the teaching distribution between the three teachers (see [Screenshot-WebApp](screenshots/Screenshot-WebApp.png) in this directory)

To understand what is happening, and play around with the interface and the queries, open `index.html` and the `main.js` in a text editor of your choice (preferably a text editor with syntax highlighting like `Atom` to see clearly the code).


## Problems? Some trouble-shooting:
* _I modified something on the `index.html` or `main.js`, but nothing has changed_ -->
Did you save your files again and reloaded the Web page?

* _How to see what kind of errors I'm getting?_ --> Right click anywhere on your Web page --> click `inspect` --> click on the tab `console`

* _I'm getting some connection error_ --> try to replace the IP address in the GraphDB repository URL with localhost. For instance, replace `http://192.168.0.102:7200/repositories/repo-VU` with `http://localhost:7200/repositories/repo-VU`.

* _I'm getting an error concerning `Access-Control-Allow-Origin`_ --> two possible ways to solve this error:
  - Solution 1: Install the [moesif CORS extension](https://chrome.google.com/webstore/detail/moesif-orign-cors-changer/digfbfaphojjndkpccljibejjbppifbc?hl=en-US) in your browser and turn it on.
  - Solution 2: Add the following line in your GraphDB settings `-Dgraphdb.workbench.cors.enable=True`
    (not in the GraphDB Workbench but in the settings, see [Screenshot-GraphDB-settings](screenshots/Screenshot-GraphDB-settings.png) in this directory)


* _If your problem is not listed here, and a couple of Google searches did not help as well, ask us and your colleagues on Piazza._
