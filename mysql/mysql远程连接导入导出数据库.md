
远程连接
mysql -P 3306 -h ip -u root -p 
远程导入

远程连接后用source sql； 导入



远程导出但是有乱码
./mysqldump -P 3306  -h 172.22.1.152  -u root -p --default-character-set=utf8  pms > /Users/demo/Desktop/pms1.sql;