## Loading, saving, and working with files.

Common functions:

`file.exists()`

`dir.create()`

`download.file('fileUrl', destfile = "sample.file")`

CSV and text files (flat files):

`read.table(file, sep=' ', header=TRUE)`
`read.csv()`

Excel:

`library(xlsx)`

`read.xlsx('file', sheetIndex=1, header=TRUE)`

`write.xlsx('file')`

XML:

```R
library(XML)
fileUrl <- 'http://file.xml'
doc <- xmlTreeParse(fileUrl, useInternal=TRUE)
rootNode <- xmlRoot(doc)
rootNode[[1]]
rootNode[[1]][[1]]
xmlSApply(rootNode, xmlValue)
xpathSApple(rootNode, '//name', xmlValue)
```

more info from http://www.stat.berkeley.edu/~statcur/Workshop2/Presentations/XML.pdf

HTML:

similar to XML but use `htmlTreeParse()` instead.

```R
fileUrl <- 'http://file.html'
doc <- htmlTreeParse(fileUrl, useInternal=TRUE)
names <- xpathSApply(doc, "//li[@class='names']", xmlValue)
```

JSON:

```R
library(jsonlite)
jsonData <- fromJSON('http://file')
names(jsonData)
myjson <- toJSON(dataset, pretty=TRUE)
```

more info on jsonlite http://www.r-bloggers.com/new-package-jsonlite-a-smarter-json-encoderdecoder/
 
