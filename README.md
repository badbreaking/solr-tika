# solr-tika
Apache SOLR integration with Apache Tika

How to index document using admin web interface:

1) Select a core (testcore)

2) Open Documents page

3) Change Handler to /update/extract

4) Document Type select box should be - file upload

5) Open host directory and go to the files folder.

6) Select solr-word.pdf

7) Press update document.

You will not see any notifications of success/unsuccess so you will have to go to the Query page and check there.

How to check if the document was indexed.

Just go to the Query page and execute *.* query. 

Just go to the Query page and execute 
```
*.* query. 
```
The indexed pdf document doesn't have a full content from the document. In order to have it you need to change
the
```
_text_ field:
```

```
curl -X POST -H 'Content-type:application/json' --data-binary '{
 "replace-field" : {
 "name":"_text_",
 "type":"text_general",
 "indexed":"true",
 "stored":"true",
 "multiValued":"true"
 }
}' http://localhost:8983/solr/testcore1/schema
```

# Neo4j

How to create a graph for learning and playing with:

1) Open the database management interface: http://localhost:7474/

2) The authentication is disabled so you just click: connect

3) In the Try "Neo4jwith live data" block click on: Open guide

4) In the "Movie Graph Guide: panel click on: next

5) In the "Create" block click on "Click this code block and bring it into the Editor:"

After these steps you will see the Movie graph fully created.
