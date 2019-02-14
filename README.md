# Munro Library Challenge

### Swift SQLite Library

Functions include:

- Filtering of search by hill category (i.e. Munro, Munro Top or either). If this information is
not provided by the user it should default to either. This should use the “post 1997”
column and if it is blank the hill should be always excluded from results.
- The ability to sort the results by height in meters and alphabetically by name. For both
options it should be possibly to specify if this should be done in ascending or descending
order.
- The ability to limit the total number of results returned, e.g. only show the top 10
- The ability to specify a minimum height in meters
- The ability to specify a maximum height in meters
- Queries may include any combination of the above features and none are mandatory.
- Suitable error handling for invalid queries (e.g. when the max height is less than the
minimum height)


### Usage

- Run the importDatabase bash script to convert the csv to sqlite

```console
foo@bar:$ ./importDatabase
```
Use any of the available Swift functions to query the munros inside the sqlLibrary file

```swift
let d = SQLite3Conn()!
d.query(maxResults:10)
d.munroBy(name:"Beinn a' Chleibh")
d.munroBy(id:1)
d.munroBy(category:HillType.munro, maxResults:8)
d.munroBy(minHeight:990, maxResults: 10, orderByCategory:OrderCategory.height)
d.munroBy(minHeight:990, maxHeight:995, maxResults: 10, orderByCategory:OrderCategory.height)
d.munroBy(minHeight:990, maxHeight:995, orderByCategory:OrderCategory.height, orderByType: OrderType.descending)
```

Call it in the terminal like
```console
foo@bar:$ ./sqlLibrary
```

## Author

✨✨mzellhuber✨✨ [https://github.com/mzellhuber](https://github.com/mzellhuber)