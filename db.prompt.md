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

5. 用 SQLite 在 movie_quotes table 新增一筆資料，要確認電影台詞不重複再新增，只要給我SQL 不用程式碼。
```sql
INSERT INTO movie_quotes (provider, movie_name, quote)
SELECT '提供者', '電影名稱', '電影台詞'
WHERE NOT EXISTS (
    SELECT 1 FROM movie_quotes WHERE quote = '電影台詞'
);
```
6. 用 SQLite 在 movie_quotes table 刪除重複的電影台詞，只要給我SQL不用程式碼
```sql
DELETE FROM movie_quotes
WHERE id NOT IN (
    SELECT MIN(id)
    FROM movie_quotes
    GROUP BY quote
);
```