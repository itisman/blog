# How to quickly insert multiple records in MYSQL db from JSON file

```js
const mysql = require("mysql2/promise");

// Create a connection to the database
const config = {
    host: "localhost",
    port: 3306,
    user: "root",
    password: "password",
    database: "db",
};

async function saveDb(tableName, arr) {
    if (arr.length === 0) {
        return;
    }
    const connection = await mysql.createConnection(config);
    try {
        const values = arr.map((jsonData) => Object.values(jsonData));

        // Insert multiple JSON records into the database
        const sql = `INSERT INTO ${tableName} (${Object.keys(arr[0]).join(", ")}) VALUES ?`;

        // Use prepared statements to insert data securely
        const [rows, fields] = await connection.query(sql, [values]);

        console.log(`${rows.affectedRows} rows inserted.`);
        return [rows, fields];
    } catch (error) {
        console.error("Error occurred:", error);
    } finally {
        // Close the connection
        await connection.end();
    }
}

async function main() {
    const json = fs.readFileSync("./data.json");
    const jsonData = JSON.parse(json);

    const results = jsonData.map((l) => ({
        id: l.id,
        // ... map all the json field to db fields
    }));

    await saveDb("db_name", results);
}

main();
```
