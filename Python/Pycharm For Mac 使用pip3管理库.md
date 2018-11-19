# Pycharm For Mac 使用pip3管理库

PyCharm  --> Preferences  -->  Project：项目名  -->  Project Interpreter  -->  点击+  -->  安装。


### Pycharm 连接使用数据库

#### 增加数据
##### 静态插入数据
> 静态插入数据
> 
```python
import pymysql
# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

r = cursor.execute('insert into class(caption) values ("高级班级1啊")')
print(r)

conn.commit()

cursor.close()

conn.close()
```


##### 动态插入数据

> 动态字符串拼接。**这种禁止使用，会造成SQL注入。**
> 
```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()
inp = input('请输入班级名称：')
sql = 'insert into class(caption) values("%s")'
sql = sql %(inp)
r = cursor.execute(sql)
print(r)

conn.commit()

cursor.close()

conn.close()
```

##### 动态插入数据
> 动态参数形式拼接
> 
```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()
inp = input('请输入班级名称：')
r = cursor.execute('insert into class(caption) values(%s)',inp)
print(r)

conn.commit()

cursor.close()

conn.close()
```

#### 动态插入学生表
```python

import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

r = cursor.execute('insert into student(sid,gender,sname,class_id) values (%s,%s,%s,%s)',(8,'男','LCodee',3))
print(r)

conn.commit()

cursor.close()

conn.close()
```

#### 动态插入多条数据

> 使用 ```excutemany```函数
```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

l = (
    (9, '男','001',3),
    (10,'男','002',3),
    (11,'男','003',3),
    (12,'男','004',3),
)
r = cursor.executemany('insert into student(sid,gender,sname,class_id) values (%s,%s,%s,%s)',l)
print(r)

conn.commit()

cursor.close()

conn.close()
```
#### 改数据
##### 更新数据库
```python 
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()
r = cursor.execute('update student set sname=%s where sid=%s',('改名字',1))
print(r)
conn.commit()

cursor.close()

conn.close()
```
#### 删数据
##### 删除数据库数据
```python

import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

r = cursor.execute('delete from student where sid=%s',(1))
print(r)
conn.commit()

cursor.close()

conn.close()
```

#### 查找数据

> ```fetch```函数，这个函数的本质是将数据库中所有数据已经全部拿到内存中了，之后是从内存中操作数据。
> 拿到数据之后相当于是一个指针
##### 查找数据库全部数据
> 不需要 ```commit()```,```fetchall()```为查找全部数据
```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

r = cursor.execute('select * from student')
print(r) # 11 受影响条数

result = cursor.fetchall()
print(result) # ((2, '铁蛋', '女', 1), (3, '山炮', '男', 2), (4, '拉丝', '男', 3), (5, '法考', '女', 2), (6, '大大', '男', 3), (7, 'Lee', '男', 3), (8, 'LCodee', '男', 3), (9, '001', '男', 3), (10, '002', '男', 3), (11, '003', '男', 3), (12, '004', '男', 3))

cursor.close()

conn.close()
```

##### 查找单条数据
```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

r = cursor.execute('select * from student')
print(r)

result_one = cursor.fetchone()
print(result_one) # (2, '铁蛋', '女', 1)

cursor.close()

conn.close()
```

##### 查找多条数据
> 使用 ```fetchmany(size)```
> 
```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

r = cursor.execute('select * from student')
print(r)

result_many = cursor.fetchmany(5)
print(result_many) # ((2, '铁蛋', '女', 1), (3, '山炮', '男', 2), (4, '拉丝', '男', 3), (5, '法考', '女', 2), (6, '大大', '男', 3))

cursor.close()

conn.close()
```


##### 模拟登陆
> 说明为什么动态字符串拼接不可用
> 
- 正常写法

```python
import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

cursor.execute('select username,password from login where username=%s and password=%s',('lee','123456'))
result = cursor.fetchall()
print(result) # (('lee', '123456'),)
cursor.close()

conn.close()
```

- 字符串拼接正常写法

```python

import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

sql = 'select username,password from login where username="%s" and password="%s"'
sql = sql %('lee','123456')

cursor.execute(sql)
result = cursor.fetchall()
print(result)  # (('lee', '123456'),)
cursor.close()

conn.close()
```

- 字符串拼接正常写法，账号密码错误

```python

import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

sql = 'select username,password from login where username="%s" and password="%s"'
sql = sql %('lee','12345666')

cursor.execute(sql)
result = cursor.fetchall()
print(result)  # ()
cursor.close()

conn.close()
```

- 字符串拼接，账号密码错误仍可登陆（**SQL注入**）
> 账号拼接```('lee" or 1=1 -- ','12345666')```
```python

import pymysql

# 创建连接
conn = pymysql.connect(host='127.0.0.1',port=3306,user='root',passwd='1234567890',db='Table_Test')

# 打开游标
cursor = conn.cursor()

sql = 'select username,password from login where username="%s" and password="%s"'
sql = sql %('lee" or 1=1 -- ','12345666') # sql = sql %('lee" -- ','12345666') 同样可登陆成功

cursor.execute(sql)
result = cursor.fetchall()
print(result)
cursor.close()

conn.close()
```

> 拼接后
> ```python
> sql = 'select username,password from login where username="%s" and password="%s"'
> sql = sql %('lee" -- ','12345666')
> sql = 'select username,password from login where username="lee" -- " and password="%s"'
> ```
> 在SQL语句中使用 ```--```来注释
> 所以上语句中 ```" and password="%s"```都被注释掉
> ```python
> sql = 'select username,password from login where username="%s" and password="%s"'
> sql = sql %('leeddd" or 1=1 -- ','12345666')
> sql = 'select username,password from login where username="leeddd" or 1=1 == "and passwoed="%s"'
> ```
> 因为是 ```or```，所以```1=1```永远成立，无论输入账号密码是什么，永远可以登陆