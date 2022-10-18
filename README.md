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
#### 資料庫
![01](https://user-images.githubusercontent.com/84265782/196320055-9fa55971-1a00-4151-8120-13bd64ca5cb0.png)
#### 建立資料欄位
![02](https://user-images.githubusercontent.com/84265782/196320104-6533d864-1619-4aa0-9f60-0b271be94970.png)

## 第三題內容
### SQL語法
```sql
insert into member(name, username, password, follower_count) 
values("Wehelp", "test", "test", 52); -- 新增資料

insert into member(name, username, password, follower_count) 
values("Rocky", "rocky", "rocky", 10); -- 新增資料

insert into member(name, username, password) 
values("Leo", "leo", "leo"); -- 新增資料

insert into member(name, username, password, follower_count) 
values("John", "john", "john", 25); -- 新增資料

insert into member(name, username, password) 
values("David", "david", "david"); -- 新增資料

select * from member; -- 所有會員資料

select * from member order by time desc; -- 按照時間排序，由近至遠

select * from member order by time desc limit 1,3; -- 按照時間排序，由近至遠，再拿第2至4筆資料

select * from member where username = "test"; -- 只取得 username 是 test 的資料

select * from member where username = "test" and password = "test"; -- 取得 username 是 test 的和 password 是 test 的資料

update member set name="test2" where username="test"; -- 更新 username 是 test 的資料，將 name欄位 改成 test2

```

### 圖片
#### 建立資料5筆資料
![03](https://user-images.githubusercontent.com/84265782/196321709-cce83521-84b8-475f-bc56-401470a9c8fa.png)
#### 所有會員資料、按照時間排序，由近至遠、按照時間排序，由近至遠，再拿第2至4筆資料
![04](https://user-images.githubusercontent.com/84265782/196321927-18e49448-bdf0-4f8b-9323-d3ff76e565f7.png)
#### 只取得 username 是 test 的資料、取得 username 是 test 的和 password 是 test 的資料、更新 username 是 test 的資料，將 name欄位 改成 test2
![05](https://user-images.githubusercontent.com/84265782/196322045-c6066b71-5722-4901-ac96-80505b13627d.png)


