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
); -- 建立 member 資料欄位

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

## 第四題內容
### SQL語法
```sql
select count(*) as 總共有幾筆會員資料 from member; -- 總共有幾筆資料 

select sum(follower_count) as 所有會員追蹤者的總和 from member; -- follower_count 欄位的總和
 
select avg(follower_count) as 所有會員追蹤者的總和的平均數 from member; --  follower_count 欄位的平均數

```

### 圖片
#### 取得 member 資料表中，總共有幾筆資料 ( 幾位會員 )、所有會員 follower_count 欄位的總和、所有會員 follower_count 欄位的平均數。
![06](https://user-images.githubusercontent.com/84265782/196322809-7fdb2199-8052-470b-bff1-2059bbb1883e.png)

## 第五題內容
### SQL語法
```sql
create table message(
	id bigint primary key auto_increment,
	member_id bigint not null,
	content varchar(255) not null,
	like_count int unsigned not null default 0,
	time datetime not null DEFAULT CURRENT_TIMESTAMP,
	foreign key (member_id) references member(id)
); -- 建立 message 資料欄位

insert into message(member_id, content, like_count) values(1, "好喜歡Wehelp喔", 70); -- 新增資料
insert into message(member_id, content, like_count) values(1, "大家加油!!!", 45); -- 新增資料
insert into message(member_id, content, like_count) values(1, "每天都要學習!!!", 50); -- 新增資料
insert into message(member_id, content, like_count) values(2, "加油喔", 3); -- 新增資料
insert into message(member_id, content, like_count) values(2, "腳傷快點好~", 2); -- 新增資料
insert into message(member_id, content, like_count) values(2, "辛苦了", 1); -- 新增資料
insert into message(member_id, content) values(3, "哈哈"); -- 新增資料
insert into message(member_id, content) values(3, "大家好"); -- 新增資料
insert into message(member_id, content) values(4, "天氣好差"); -- 新增資料
insert into message(member_id, content, like_count) values(5, "希望明天有太陽", 10); -- 新增資料
insert into message(member_id, content, like_count) values(5, "希望明天不要下雨", 20); -- 新增資料

select a.name as 會員姓名, b.content as 留言內容 
from member as a
inner join message as b
on a.id = b.member_id; -- JOIN 語法，取得所有留⾔，結果須包含留⾔者會員的姓名


select a.name as 會員姓名, b.content as 留言內容 
from member as a
inner join message as b
on a.id = b.member_id
where a.username="test"; -- JOIN 語法，取得 member 資料表中欄位 username 是 test 的所有留言，資料中須包含留⾔者會員的姓名

select a.username as 帳戶名稱 ,avg(b.like_count) as 所有留言平均按讚數 from member as a
left join message as b on a.id = b.member_id 
where a.username="test"; -- SQL Aggregate Functions 搭配 JOIN 語法，取得 member 資料表中欄位 userna

```

### 圖片
#### 建立 message 資料欄位、新增資料
![07](https://user-images.githubusercontent.com/84265782/196323793-8e99d21e-4fde-4bf4-b889-e4b981cc98c2.png)
#### JOIN 語法，取得所有留⾔，結果須包含留⾔者會員的姓名、取得 member 資料表中欄位 username 是 test 的所有留⾔，資料中須包含留⾔者會員的姓名、SQL Aggregate Functions 搭配 JOIN 語法，取得 member 資料表中欄位 username 是 test 的所有留⾔平均按讚數
![08](https://user-images.githubusercontent.com/84265782/196324219-8e6b0b97-0d18-411f-8f19-265915029641.png)

## 額外內容
### SQL語法
```sql
create table record_like(
    user_id  bigint not null,
    user_like bigint not null,
    click_like varchar(255) not null,
    PRIMARY KEY(user_id, user_like)
); -- 建立 record 資料欄位，user_id 和 user_like都是主鍵

-- record_like 的 user_id 和 user_like 分別是 member(id) 和 message(id) 外鍵 防止重複
alter table record_like add foreign key (user_id) references member(id);
alter table record_like add foreign key (user_like) references message(id);

insert into record_like(user_id, user_like, click_like) 
values(1, 11, "+1"),(1, 10, "+1"),(1, 1, "+1"),(2, 9, "+1"),(2, 8, "+1")
,(2, 1, "+1"),(3, 7, "+1"),(3, 6, "+1"),(3, 2, "+1"),(4, 5, "+1"),(4, 4, "+1")
,(4, 3, "+1"),(5, 3, "+1"),(5, 2, "+1"),(5, 5, "+1"),(5, 4, "+1"); -- 新增資料


select c.name 按讚的人, b.content as 按讚的內容, a.click_like as 按讚 from record_like as a 
inner join message as b on a.user_like=b.id 
inner join member as c on a.user_id=c.id;-- 查詢按讚的人和內容
```

### 圖片
#### 建立 record_like 資料欄位、關連到 member 和 message 主鍵外鍵、新增資料
![10-01](https://user-images.githubusercontent.com/84265782/196852033-1ad33151-dff8-4b07-ab1c-3dc7fef73515.png)
#### 查詢 record_like 資料欄位
![10-02](https://user-images.githubusercontent.com/84265782/196852052-e8eccfd0-bb74-4e3d-89b8-e1bcffcb2be7.png)
#### 如果同一個使用者重複對同一個留言按讚，會無法輸入
![10-03](https://user-images.githubusercontent.com/84265782/196852182-00752f07-24b8-42aa-b741-d80ed38a619b.png)
#### 查詢 按讚人員 和 按讚內容 
![10-04](https://user-images.githubusercontent.com/84265782/196852192-592ebdec-5242-4750-898a-58e12803719d.png)

