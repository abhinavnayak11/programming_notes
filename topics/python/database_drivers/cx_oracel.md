*Link to api manual: https://cx-oracle.readthedocs.io/en/latest/api_manual/connection.html*

### Connecting
```
import cx_Oracle
dsn_tns = cx_Oracle.makedsn('Host Name', 'Port Number', service_name='Service Name')     # create data source name (dsn)
conn = cx_Oracle.connect(user=r'User Name', password='Personal Password', dsn=dsn_tns)   # connect to database
```

### Check version
`cx_Oracle.version`   # returns oracle version              
`cx_Oracle.clientversion()`  # return oracle client version. This will give an error if client libraries are not installed

### Queries
```
cur = conn.cursor()                             # create a cursor
cur.execute('select * from temp_lsf')           # execute query statement
cols = [row[0] for row in cur.description]      # get all columns from query
cur.fetchall()                                  # get all the rows from query
```
`cur.fetchone()`:   fetches one row     
`cur.fetchmany(n)`: fetches n rows     
`cur.fetchall()`:   fetches all rows

---
Links:
<br>
*1. Documentation: [Using bind variables](https://cx-oracle.readthedocs.io/en/latest/user_guide/bind.html#binding-by-name-or-position)    
2. Using batch execution statement: [Links](https://blogs.oracle.com/opal/post/efficient-and-scalable-batch-statement-execution-in-python-cx_oracle)*

## Uploading pandas dataframe to database
1. Using `cur.execute()`:
2. Using `cur.executemany()`: