SPARQL Environment
==================

A javascript based integrated query environment developed to improve on the default SPARQL query box and make it easier to query any SPARQL database.

Built using javascript and jQuery this IQE allows for the querying of SPARQL databases without knowledge of the underlying content. This framework can be used to create very simple text-based database interactions as well as data specific interactions using graphical user interfaces designed for end users.

## Setup and Installation

The SPARQL Environment runs in a browser client-side. To get up and running simply clone this repository and open the index.html file in your browser.

*Note: Not all browsers were created equal. Sadly there are compatibility issues, please see below if you run into problems.*

## Configs

The config files contain the nessesary information to start querying a dataset.

- Name & Description: These fields identify the dataset and should explain something about the data.
- Source: URL for the SPARQL Node.
- Prefixes: Define your prefixes to make querying much easier.
- Variables: Define common variables used with your database to make queries make more sense. (In-Development)
- Plugins: List the plugins this dataset will display.

Plugin specific config variables should also be set. Consult the markdown files for those plugins for which values need to be set.

## Basic Usability

The Environment is layed out to be extremely flexible. When completly uncollapsed the environment displays a left side bar, a middle workspace and a right side bar.

#### Data Sets

The left side bar lists all your datasets. To import new datasets click the down arrow icon and use whichever method (URL or File) you wish to select a config file. The config file will setup the dataset information. You can also perform simple edits on datasets by clicking edit next to the setlist name.

#### Workspace

The workspace is the center two panels of your screen. This area is divided into two sections: input and output.

##### Input

The input section contains all of the current dataset's input plugins. The objective of the section is to produce a query. When a query is made the environemnt performs the query and passes on the results to the output plugins.

##### Output

The output section contains all of the current dataset's output plugins. The objective of the section is to display query results. When query results come in the output plugins get updated and can update themselves with new information.

#### Details

The right side bar contains the datasets details plugins. The objective of the section is to assist the input and/or output plugins. They work in tandem with the other plugins and cannot do anything without user input being done in an input or output plugin. Examples include history, saved queries, and object viewer.

## Plugins

Plugins for SPARQL Environment are called SparqPlugs. Clever, we know. This gives us a namespace from which to operate. Files which begin with *"sparqplug."* depict plugins for the SPARQL Environment. We hope this will allow developers to create and share sparqplugs more efficiently. However, so we can sound like normal people we will describe them as plugins within the context of the SPARQL Environment.

Plugins are either agnostic (data independent) or specific (data dependent) and should be labeled clearly which they are. Examples of agnostic plugins are the "Text Query Editor" which is a sophisticated query editor and the "JSON Viewer". Both of these plugins will work with any dataset they're given.

There are three types of Plugins input, output and detail.

#### Input

The goal of an input plugin is to take user input and create a SPARQL query.  

#### Output

The goal of the output plugin is to present the user with the results of the SPARQL query.

#### Detail

The goal of the detail plugin is to be helpful and informative. Fill the gap of any functionality that doesn't fit as an input or output plugin.

### Plugin URN specifications

Plugins have their own URN specifications and can be 

### Plugin URN Resolvers

## Contribute

Create configs for your datasets, create specific plugins for your data and let us know if you're interested in advancing the underlying framework!

Checkout the *plugins/README.md* file for how to create plugins.

Checkout the *configs/README.md* file for how to create configs.

### Some other configs and plugins

1. [The Homer Multitext Project](https://github.com/SamuelHill/sparqplugs-hmt)
1. [Botanica Caroliniana](https://github.com/botcar/botcar-apps/tree/master/sparqplugs-botcar)

## Built-In Features

### GraphKit (In-Development)

A tool for creating and resolving GraphKit URNs. These URNs represent a specific look at a graph. The GraphKit *detail.graphkit* plugin will save any query called **Graph Selection Logic** (GSL) as RDF. Other data will be filled in as well if set properly. If given a SPARQL endpoint for updating, the RDF can be sent directly to a server.

```
<urn:cite:gsl:CollectionName.1> gsl:auth "Firstname Lastname @organization" ;
								gsl:date "2014-08-01T16:30:00" ;
								gsl:label "My Specific look at the Data" ;
								gsl:graphId <urn:graph:GraphName> ;
								gsl:gsl "prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> SELECT ?s ?v ?o WHERE { ?s rdf:type <http://www.your.data/type> }";
								gsl:lang "SPARQL" ;
								gsl:langVersion "1.1" .
```

### CiteKit (Beta)

CITEKit is a collection of scripts that allow easy end-user display of images, data, and textual passages using the CITE/CTS Architecture. The goal of CITEKit is to make it as easy to embed in HTML texts and data as it always has been to embed images from different sources on the internet.

## Browser Compatability

#### All

If you are getting any errors associated with "Access-Control-Allow-Origin" then try using python to serve a basic server instance on your localhost.

`python -m SimpleHTTPServer`

#### Safari

No common problems.

#### Chrome

Normally the Access-Control-Allow-Origin problem is the only issue.

#### FireFox

Ensure that you are using the latest version of Firefox.

If you are using the latest version of Firefox and it still does not work then ensure DOM Storage is enabled.

Type about:config in your address bar and hit Enter to view your internal browser settings.

Scroll down to dom.storage.enabled, if it is disabled then right click on it and hit Toggle to enable the DOM Storage.

#### IE

In nice terms... Try a modern browser. Currently we make no claims on this applications ability in IE.
