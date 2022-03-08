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
