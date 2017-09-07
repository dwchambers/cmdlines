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
xpathSApply(rootNode, '//name', xmlValue)
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
 
MySQL:

```R
library(RMySQL)
ucscDb <- dbConnect(MySQL(), user='genome', host='genome-mysql.cse.ucsc.edu')
result <- dbGetQuery(ucscDb, 'show databases;'); dbDisconnect(ucscDb);  #list databases (show databases; is a MySQL command)
hg19 <- dbConnect(MySQL(), user='genome', db='hg19', host='genome-mysql.cse.ucsc.edu')  #pick database
allTables <- dbListTables(hg19)

dbListFields(hg19,'affyU133Plus2')   #column names
dbGetQuery(hg19, 'select count(*) from affyU133Plus2')    #number of rows

affyData <- dbReadTable(hg19, 'affyU133Plus2')    #store table as data frame
query <- dbSendQuery(hg19, 'select * from affyU133Plus2 where misMatches between 1 and 3')
affyMis <- fetch(query)
affyMisSmall <- fetch(query, n=10); dbClearResult(query);    #select only the first ten rows

dbDisconnect(hg19)     #close the connection

```

HDF5:

```R
source('http://bioconductor.org/biocLite.R')
biocLite('rhdf5')
library(rhdf5)
```

httr R package:

```R
library(httr)
html = GET('url', authenticate('user','passwd')
content = content(html, as='text')
parsedHtml = htmlParse(content, asText=TRUE)
xpathSApply(parsedHtml,  '//title', emlValue)

#use a handle to not have to reauthenticate
google = handle('http://www.google.com')
pg1 = GET(handle=google, path='/')
```

Other useful R packages:

foreign: Loads data from Minitab, S, SAS, SPSS, Stata, Systat, Octave
RPostgresSQL
RODBC: PostgreSQL, MySQL, Access, SQlite
RMongo, rmongodb
rdgal, rgeos, raster: read GIS data
tuneR, seewave: read music data
