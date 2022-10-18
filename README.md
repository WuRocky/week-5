# week-5
## 第二題內容
### SQL語法
```sql

create database website; -- 建立資料庫

create table member(
	id bigint primary key auto_increment,
	name varchar(255) not null,
	username varchar(255) not null,
	password varchar(255) not null,
	follower_count int unsigned not null default 0,
	time datetime not null DEFAULT CURRENT_TIMESTAMP
); -- 建立資料欄位

```
### 圖片
![01](https://user-images.githubusercontent.com/84265782/196320055-9fa55971-1a00-4151-8120-13bd64ca5cb0.png)
![02](https://user-images.githubusercontent.com/84265782/196320104-6533d864-1619-4aa0-9f60-0b271be94970.png)
