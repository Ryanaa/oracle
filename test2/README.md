## 第1步：以system登录到pdborcl，创建角色con_res_view和用户new_user，并授权和分配空间：
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test2/1.png)
## 第2步：新用户new_user连接到pdborcl，创建表mytable和视图myview，插入数据，最后将myview的SELECT对象权限授予hr用户。
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test2/2.png)
## 第3步：用户hr连接到pdborcl，查询new_user授予它的视图myview
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test2/3.png)