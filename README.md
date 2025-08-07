# PostgreSQL 資料庫共享容器

此容器包含完整 PostgreSQL 資料庫與所有表格內容，透過 pg_dumpall 匯出，適用於開發團隊共享資料。

## 啟動方式

1. 進入專案目錄
```
cd postgres-container
```

2. 建立並啟動 container
```
docker-compose up --build -d
```

## **預設登入帳密（可於 docker-compose.yml 修改）**
- Host: localhost（或內網 IP）
- User: lorraine
- Password: 0000
- Port: 5432

## **資料來源**

來自 init/full_dump，為原始 PostgreSQL 匯出的資料庫內容, 第一次啟動時自動匯入。

## **注意事項**

- 初次啟動會自動建立所有資料庫與表格
- 若需更新資料內容，請重新執行 pg_dumpall 匯出並取代 full_dump

## **VScode 連線方法**
```
# !pip install psycopg2-binary
import psycopg2

conn = psycopg2.connect(
    host="localhost",
    database="postgres",
    user="lorraine",
    password="0000",
    port=5432
)


cur = conn.cursor()
cur.execute("SELECT * FROM basic_vege")
print(cur.fetchall())
```

## **資料庫表格一覽**
1. basic_vege
2. vege_alias
3. vege_nutrition
4. nutrition_info
5. main_recipe
6. ingredient
7. recipe_steps 
8. market_city_mapping
9. station_city_mapping
10. city_name_vs_city_id
11. veg_daily_market_price
12. daily_avg_price
13. weather_data
14. weather_en_zh
15. yearly_regional_normalized_yields
