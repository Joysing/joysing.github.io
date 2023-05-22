# zupu

#### 介绍
蛇尾李氏族谱

#### 软件架构
使用“丝连族谱2021U38”维护族员信息。
使用“MSSQL”输出固定格式的Json


#### 安装教程

1.  使用“丝连族谱2021U38”维护好族员信息，默认会形成Access文件（.mdb）。
2.  把Access文件（.mdb）导入到mssql
3.  使用mssql脚本输出json：
```
select '{"id":"'+replace(replace(MEID,'{',''),'}','')
+'","parent":"'+case when UPID='' then '#' else replace(replace(UPID,'{',''),'}','') end
+'","type":"man","text":"'+Ming+' <span class=\"badge bg-secondary\">'+convert(varchar(3),DaiShu)+'世</span>","description":"'+isnull(JianJie,'')+'" },' from b_zongpu where UPGX=1
```
4.  把json数据复制到1.json
5.  完成

#### 效果图
![效果图1](dist/themes/default/%E6%95%88%E6%9E%9C%E5%9B%BE1.png)