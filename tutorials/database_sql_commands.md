############################

############################
# DATABASE SQL COMMANDS
############################

############################

# basic SQL

- City ve Country sütunlarının her farklı kombinasyonunu döndürür. Dublicate olan sütunları dönmez. Örnek: Türkiye-İstanbul, Türkiye-Ankara'dan 1'er adet döner. Oysa customer tablomuzda Türkiye-Ankara'dan 1'den fazla customer olabilir. 

Yani DISTINCT; select yapılan tüm sutunlara bakar (sadece ilk sağındakie bakarak hareket etmez!).

```sql
SELECT DISTINCT City, Country FROM Customers;
```

- sıralı çekmek için

```sql
SELECT * FROM Customers
ORDER BY Country DESC, CustomerName ASC;

-- DESC -> descending
-- ASC -> ascending
```

- top vs limit vs rownum

Some keywords suppports only some servers:

- Top --> MicrosoftSQL Server
- LIMIT --> MySQL
- rownum -> Oracle

show only top X rows

```sql
SELECT TOP 3 * FROM Customers
WHERE Country='Germany';
```

```sql
SELECT * FROM Customers
WHERE Country='Germany'
LIMIT 3; 
```

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND ROWNUM <= 3;
```

- IN Operatörü

```sql
SELECT column_name(s)
 FROM table_name
 WHERE column_name IN (value1,value2,...);
```

- Beetween operatörü

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

- AS Operatörü

Result veya sorgu sırasında kolon isimlerinin değiştirilmesi

```sql
SELECT CustomerName, Address+', '+City+', '+PostalCode+', '+Country AS  Address
 FROM Customers;
```

başka bir örnek;

```sql
SELECT CustomerName, CONCAT(Address,', ',City,', ',PostalCode,', ',Country)  AS Address
 FROM Customers;
```

başka bir örnek;

```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders  AS o
WHERE c.CustomerName="Around the Horn" AND  c.CustomerID=o.CustomerID;
```

başka bir örnek;

```sql
SELECT Orders.OrderID, Orders.OrderDate, Customers.CustomerName
FROM  Customers, Orders
WHERE Customers.CustomerName="Around the Horn" AND  Customers.CustomerID=Orders.CustomerID;
```

# table merges

- JOIN Operatörü

```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM  Orders
INNER JOIN Customers
ON Orders.CustomerID=Customers.CustomerID;
```

- INNER JOIN: sadece iki taraftada olan satırları döndürüyor
- LEFT JOIN: sol tarafta (orders tablosu) olan tüm satırları döndürüyor
- RIGHT JOIN: sağ tarafta (dustomers) olan tüm satırları döndürüyor
- FULL JOIN: her iki tabloda olan satırların hepsini döndürüyor

Note: In some databases also "OUTER" keyword is using. example: "LEFT OUTER JOIN", "FULL OUTER JOIN".

- UNION Operatörü

```sql
SELECT CityName AS City FROM Customers
UNION
SELECT City FROM Suppliers
```

"UNION ALL" kullanılırsa; dublicate value'larda gelecektir.

# group by, having by, where

- Hazır fonksiyonlar

bazı hazır fonksiyonlar "__aggregation__" yaparlar bu sebeple __aggregate function__ ismini alırlar. her fonksiyon aggregate yapmayabilir örnek Date fonksyionları. 

Örnekte count (aggregate) fonksiyonunun kullanımı mevcuttur:

```sql
SELECT COUNT(*) AS NumberOfOrders FROM Orders;
```

- Group By operatörü

aşağıdaki örnekte column_name_Gr değerinin aynı olduğu tüm satırlar, my_function(column_name_Any) fonksiyonuna parametre olarak girerler. Yani aslında my_function bir array list alır ve sadece 1 adet değer döner.

```sql
SELECT my_function(column_name_Any)
FROM table_name
WHERE column_name_Wh > 99
GROUP BY column_name_Gr;
```

örnek 2:

product_tag'i aynı olan elemanlar için ücret ortalamaları ve kaç adet o tag'den olduğunu gösteren sorgu:

```sql
SELECT AVG(price), COUNT(product_id), product_tag
FROM products
GROUP BY product_tag;
```

"Group by" kullanılınca, WHERE konuşulları fonksiyon (örnekte my_function) çağrılmadan önce uygulanmaktadır. my_function çağrıldıktan sonra where tarzı koşul istenirse "HAVING" operatörü kullanılmak zorundadır. HAVING'in syntax'ı WHERE ile aynıdır. Fakat "HAVING" ile belirtilen koşulda, sütun ismi yazamaz. Onun yerine fonksiyon içermelidir. örnek:

```sql
HAVING COUNT(OrderID) > 10; 
```

Bunun sebebi database-server'ların internal'da "group by" operatörünü işletme sürecleri ile alakalı. DB-server'lar önce fonksiyonları çağırıyor ve her fonksiyon çıktısını geçici ayrı bir hafıza bölgesinde tutuyor. Daha sonra "having" ile belirtilen koşulları çağırıyor ve en sonda tüm hafızadakileri birleştirip tek bir tablo olarak sonuç döndürüyor. Dolayısı ile en sondaki tabloya alias verip "having" koşulunda o alias'ı kullanamıyoruz. örnek:

```sql
SELECT AVG(price), COUNT(product_id) as count_of_products, product_tag
FROM products
GROUP BY product_tag
HAVING count_of_products > 10 # burası mümkün değil. bu sorgu çalışmayacaktır.
```

# Scheme changing

- create table

```sql
CREATE TABLE Persons
(
PersonID int,
LastName varchar(255) NOT NULL,
FirstName varchar(255) UNIQUE,
Address varchar(255),
City varchar(255)
);
```

- tablo şeması değiştirme

```sql
ALTER TABLE Persons
ADD DateOfBirth date
```

- View yaratma

```sql
CREATE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition
```

# data manipulations

- Truncate VS delete

|                             | truncate   | delete          |
|-----------------------------|------------|-----------------|
| rollback inside transaction | impossible | can be rollback |
| locks                       | table      | rows            |
| command type                | DDL        | DML             |
| where clause                | not exist  | optional        |
| triggers                    | not fired  | fired           |

Farklar yukarıdakinden daha detaylı ve bazı database'lerde istisna durumlar olabiliyor. Bu sebeple hangi DB'ye olduğumuza göre çok ince ayrıntılar karşımıza çıkabilir.

- tabloya ekleme ya sütun isimleri belirtilerek, yada belirtilmezse kolon sırasına göre yapılır.

```sql
INSERT INTO table_name
VALUES (value1,value2,value3,...);
```

yada

```sql
INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);
```

birden fazla satır eklemek gerekirse:

```sql
INSERT INTO table_name
VALUES (value1,value2,...),
       (value3,value4,...),;
```

- update

```sql
UPDATE Customers
SET ContactName='Alfred Schmidt', City='Hamburg'
WHERE CustomerName='Alfreds Futterkiste';
```

- delete

```sql
DELETE FROM Customers
 WHERE CustomerName='Alfreds Futterkiste' AND ContactName='Maria Anders';
```

# Others

- GO

GO, bir SQL standart keyword'ü değildir. Sadece client SQL editor'ler tarafından kullanılır. Hatta editor'ler tarafından değiştirilebilirler (yani; editörler, go yerine farklı (istediğimiz) bir keyword'ü kullanmamıza olanak sağlarlar). Go keyword'ü sunucuda çalıştırılamaz (sunucuya yollanmaz).

"go" bir group işlemin (batch (or script)) sonuna konulur. bu şekilde onun aşağısında olan başka SQL kodları var ise onlar başka bir "batch (or script)" işlemi olarak uzak sunucuda işletilir. Örneğin; 2 adet bağımsız script'imiz olsun. ikisinde de local variable'larımız olsun. eğer 2 sinin arasına GO keyword'ünü koymazsak ve hepsini tek bir execution işlemi olarak uzak database server'ına yollarsa, o zaman local variable'lar 2 script'te de ortak variable olarak algılanacak ve hatalara sebep olacaktır.

Go komutunun yanında yorum satırı hariç hiçbir şey olmamalıdır (noktalı virgülde olmamalıdır). Tek istisna şudur: Go yanında bir integer alabilir. Bu sayı GOnun üstündeki batch'in tümüyle kaç kere üstüste işletileceğini belirler.

- EXEC

İlgili string'i execute eder. Javascript'teki "eval" fonksiyonu gibi çalışır.

```sql
EXEC ('USE my_db; SELECT * FROM person;');
```

- BEGIN ... END

arasına statement veya statement'ler bloğu alır. BEGIN - END; IF veya WHILE gibi terimlerden sonra kullanılmak için gerekli keyword'lerdir.

- comments

```sql
/*
 block comment
*/
SELECT * FROM PERSON
-- line comment
```

- Backslash (Line Continuation)

example of splitting a character string:

```sql
SELECT 'person_\  
ID' AS person_number
```

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# reserved keywords of SQL
(source-id: 236)

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

• • • • • • • • • • • • • • • • • • • • • • • •

# merge

```sql
MERGE INTO tablename USING table_reference ON (condition)
  WHEN MATCHED THEN
    UPDATE SET column1 = value1 [, column2 = value2 ...]
  WHEN NOT MATCHED THEN
    INSERT (column1 [, column2 ...]) VALUES (value1 [, value2 ...]);
```

Yukarıdaki ifade şuna denk gelmektedir:

```sql
-- UPSERT => update ve insert'in kısaltmasından gelmektedir.
UPSERT INTO Users VALUES (10, "John", "Smith", 27, 60000);
```

Bazı sistemlerde ise buna denk gelmektedir:

```sql
INSERT OR REPLACE INTO
```

Bazıları SQL standartlarında yok. Yukarıdakilere denk gelen diğer sorular: (source-id: 237) title: "Other non-standard implementations".
