## Loading and saving files

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

`library(XML)`

`xmlTreeParse('fileUrl', useInternal=TRUE)`
