1. 安装 sqlite3 並新増到 package.json
2. 在 db.js 中，使用 sqlite3 來操作資料庫，並開啟位置在 db/sqlite.db 的資料庫，需要確認是否成功打開資料庫
3. 若資料庫不存在，就新增資料庫
4. 在db.js 中，若＊movie_quotes”table 不存在，則自動建立一個新的table table scheme 如下


```sql
CREATE TABLE movie_quotes (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    provider TEXT NOT NULL,
    movie_name TEXT NOT NULL,
    quote TEXT NOT NULL,
    votes INTEGER DEFAULT 0
);
```