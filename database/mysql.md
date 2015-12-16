### If a row with unique key exsits update, else insert a new one

```
var insertQuery = 'INSERT INTO ' + qaDatasetTable + ' (datasetID, queryCount, criticalCount, warningCount, autoErrorRate_original, autoErrorRate_current, status) VALUES (?,?,?,?,?,?,?) ON DUPLICATE KEY UPDATE queryCount = VALUES(queryCount), criticalCount = VALUES(criticalCount), warningCount = VALUES(warningCount), autoErrorRate_original = IF(autoErrorRate_original IS NULL, VALUES(autoErrorRate_original), autoErrorRate_original), autoErrorRate_current = VALUES(autoErrorRate_current)';

getMysqlConnection(function(connection) {
    connection.query(insertQuery, [datasetID, data.queryCount, data.criticalCount, data.warningCount, data.errorRate, data.errorRate, 'NEW'], function(err, rows) {
        if (err) throw err;
        cb(data.data);
    });
    connection.release();
});   
```

---

### Update a field only if it is null, otherwise keep the old value

```
getMysqlConnection(function(connection) {
    connection.query('UPDATE ' +  qaDatasetTable + ' SET status = ?, manualErrorRate_original = IF(manualErrorRate_original IS NULL, ?, manualErrorRate_original), manualErrorRate_current = ?  WHERE datasetID = ?', [status, errorRate, errorRate, datasetID], 
    function(err, rows) {
        if (err) throw err;
        if (!_.isEmpty(rows[0])) {
            cb(true);
        } else {
            cb(false);
        }
    });
    connection.release();
});
```