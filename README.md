## Feature List / Optional Props

**sortable**: Boolean, To sort columns by ascending or descending when clicking the column name. This won't work for cell renderer components inside a column. Only for string and numbers


**caption**: String, This is the header props for the table, default behaviour has no header so headers are visible only when a caption is provided. It displays search, total rows, total filtered rows and filter.


**Search** Bar: Default disabled. Search will be enabled once captions are provided so its default behaviour depends on captions that enable headers.


**pagination**: Boolean, Default: Pagination is turned off by default so this prop is required if you want to enable the pagination.


**defaultRowsPerPage**: Number, By default the rows per page is enabled when pagination is enabled. Default rows per page are 6 if no value is provided.


**defaultPaginationLength**: Number, these set the limit for pagination numbers range for example a value of 5 will limit displaying 1-5 with next and previous buttons to jump to 6-10 and thus by it goes on till the rows end. The default pagination length is 5 if no value is provided.


**filterRowsByColumnGroup**: Array of Objects.

**Format**: ```[ { column: 'name of column 1', values: [ 'filter list of this column 1', 'multi filters for same columns' ] },  { column: 'name of column 2', values: [ 'filter list of this column 2', 'multi filters for same columns' ] } ]```.

The default behaviour of filters is disabled if filterRowsByColumnGroup is not provided. 

``` Example: filterRowsByColumnGroup={[{ column: 'status', values: ['failed', 'waiting', 'paid'] }, { column: 'name', values: ['Sai Barath', 'Lokesh'] }, { column: 'purchaseId', values: ['25602'] }]}```


**row**: Arrays of Objects, Rows Data. Format: ```[ { columnName: value }, { columnName: value }, { columnName: value } ] ```.


**headers**: Arrays of Objects, List of columns;

**Format**: ```[ { label: 'API name or local name', name: 'display name for header', cellRenderer: <react component>, optional, use only if you need to add components in row  }, { label: 'API name or local name', name: 'display name for header'} ]```

**cellRenderer**: React Component, the Default behaviour is to render a normal row value but if cellRenderer is provided then a callback function will return an array with array[0]: column name & array[1]: row value. For every single row, this cellRenderer will be called with new row values to give options to render different options based on row values instead of the same component.

**Example**:

```
const columnsData = useMemo<any>(() => [ { label: 'timeStamp', name: 'TimeStamp' }, { label: 'status', name: 'Status', cellRenderer: StatusRenderer }], []);

  function StatusRenderer(value: any[]) {
        const backgroundColor = value[1] === 'failed' ? 'bg-red-200' : value[1] === 'waiting' ? 'bg-yellow-100' : 'bg-green-200';
        return <div className={`flex items-center p-1 capitalize text-gray-800 font-medium text-sm rounded-lg justify-center min-w-[60px] ${backgroundColor}`}>{value[1]}</div>
    }

//Now the status renderer can provide different chips based on the row values

```
## Sample Table Pics

![Sample Table](https://github.com/SaiBarathR/Custom-Table/assets/58382813/8bea2f71-a85f-4405-bdfc-d4a816c48b89)

## Filter Pics

![Filter Example](https://github.com/SaiBarathR/Custom-Table/assets/58382813/d9907af6-1461-4874-8db9-2babf5908120)

## Search Pics

![Search Example](https://github.com/SaiBarathR/Custom-Table/assets/58382813/5d9574dc-ca1d-4aa0-9e40-51f31d3386cf)

## Libraries Used: Chakra-Ui

**Advanced Version:**  [If you guys need a more advanced version then check out my custom table created using React with Ag-grid library](https://github.com/SaiBarathR/react-reusable-components/tree/main/Custom-Ag-Grid)

Repo Link: https://github.com/SaiBarathR/react-reusable-components/tree/main/Custom-Ag-Grid


