############################

############################
# JAVA QUERY AND CRITERIA AND PREDICATE
############################

############################

# javax.persistence.Query

```java
Query query = getEntityManager().createQuery("SELECT u FROM UserEntity u WHERE u.id=:param1");
query.setParameter("param1", 99);
UserEntity userEntity = (UserEntity) query.getSingleResult();
```

__TypedQuery__ is the implementation of the Query. TypedQuery only stores the result class as a result, so we don't need to cast the executed result.

```java
TypedQuery<UserEntity> query = getEntityManager().createQuery("SELECT u FROM UserEntity u WHERE u.id=:param1");
query.setParameter("param1", 99);
UserEntity userEntity = query.getSingleResult();
```

__org.hibernate.query.NativeQuery__ ise javax.persistence.Query implementasyonudur. Kullanımı:

```java
Query nativeQuery = getEntityManager().createNativeQuery("SELECT * FROM users WHERE id=:param1", UserEntity.class);
query.setParameter("param1", 99);
UserEntity userEntity = (UserEntity) query.getSingleResult();
```

__NamedQuery__, Query implementasyonu değildir. Bir annotation'dur. Direk entity'de tanımlanmak üzere tasarlanmışlardır:

```java
@org.hibernate.annotations.NamedQueries({
    
    @org.hibernate.annotations.NamedQuery(name = "query1", 
      query = "from DeptEmployee where employeeNumber = :employeeNo"),
    
    @org.hibernate.annotations.NamedQuery(name = "quer2", 
      query = "from DeptEmployee where designation = :designation"),
    
    @org.hibernate.annotations.NamedQuery(name = "quer3", 
      query = "Update DeptEmployee set department = :newDepartment where employeeNumber = :employeeNo")
})
public class UserEntity {

    @Id
    private Long id;
    private String name;
}
```

"Named" prefix'i kullanıldığında ismi ile çağrıldığıdan dolayı verilmiştir. Örnek kullanım:

```java
Query namedQuery = getEntityManager().createNamedQuery("query1");
namedQuery.setParameter("employeeNo", id);
UserEntity userEntity = (UserEntity) namedQuery.getSingleResult();
```

# Criteria and Predicate classes of JPA

"Spring Data" da bu sınıfları kullanır. Çünkü Spring-Data, JPA'yı wrap ediyor.

```java
import javax.persistence.EntityManager;
import javax.persistence.TypedQuery;
import javax.persistence.criteria.CriteriaBuilder;
import javax.persistence.criteria.CriteriaQuery;
import javax.persistence.criteria.Root;
import javax.persistence.criteria.Predicate;
import javax.persistence.criteria.Order;

class BookDao {

    EntityManager entityManager;

    List<Book> findBooksByAuthorNameAndTitle(String authorName, String title) {
        CriteriaBuilder builder = entityManager.getCriteriaBuilder();

        // The result is Book class.
        // If we don't pass the "class" parameter then we have to cast the result.
        CriteriaQuery<Book> criteriaQuery = builder.createQuery(Book.class);

        // we init a new sql statement:
        // "select * from Book"
        //
        // The "result (on the above code line)" is the * (star) columns.
        //
        // At least 1 time from method should be called. Otherwise the statement could not be executed.
        //
        // There is also same method from(javax.persistence.metamodel.EntityType).
        // EntityType is a class which return every information to define the entity class.
        // (for example: Entity class name as String)
        Root<Book> from = criteriaQuery.from(Book.class);
        
        // This is optional method.
        // If we don't call this method, JPA will call all columns.
        //
        // There is also a method select(javax.persistence.criteria.Selection)
        // This method is same but it takes only 1 parameter.
        //
        // The equivalent SQL is:
        // SELECT totalPageCount, author FROM BOOK
        criteriaQuery.multiselect(from.get("totalPageCount"), from.get("author"));

        // condition 1
        Predicate whereAuthorName = builder.equal(from.get("author"), authorName);
        
        // condition 2
        Predicate whereTitle      = builder.like(from.get("title"), "%" + title + "%");
        
        // we add both conditions to query.
        criteriaQuery.where(whereAuthorName, whereTitle);

        // This is optional.
        Order order = builder.desc(from.get("author"));
        criteriaQuery.orderBy(order);

        // generates JPQL String from the most first instance (which is "criteriaQuery").
        TypedQuery<Book> typedQuery = entityManager.createQuery(criteriaQuery);

        // execute the SQL.
        return typedQuery.getResultList();
    }
}
```

MultiSelect example:

```java
// Select the the columns of employees and all the columsn of the mailing addresses
// which have the same address.
CriteriaBuilder criteriaBuilder = entityManager.getCriteriaBuilder();
CriteriaQuery criteriaQuery = criteriaBuilder.createQuery();
Root employee = criteriaQuery.from(Employee.class);
Root address = criteriaQuery.from(MailingAddress.class);
criteriaQuery.multiselect(employee, address);
criteriaQuery.where(criteriaBuilder.equal(employee.get("address"), address.get("address"));
Query query = entityManager.createQuery(criteriaQuery);
List<Object[]> result = query.getResultList();
```

Burada birçok Criteria API örnekleri mevcut: https://en.wikibooks.org/wiki/Java_Persistence/Criteria

# fetch join
SQL'de böyle bir keyword yok ve zaten ihtiyaç yoktur. JPQL'e ait bir terimdir.

```java
@Table
class Customer {
  String id;
  String name;

  @ManyToMany(fetch = FetchType.LAZY)
  String List<OrderEntity> orders;
}
```

Yukarıdaki entity üzerinden veritabanında data çekmeye kalktığımızda "order" bilgisi gelmeyecektir. Ancak "getOrders()" metotunu çağırdığımızda JPA otomatik olarak yeni bir SQL isteği atacaktır. Çünkü "LAZY" annotation'u vardır.

Eğer biz tek bir SQL sorgusunda tüm verinin dönmesini istiyorsak JPA'nın sunduğu "fetch join" özelliğini kullanabiliriz.

```java
Query query = em.createQuery("SELECT DISTINCT c FROM Customer c INNER JOIN FETCH c.oders o");
```

Ek not: Eğer alan LAZY olmasaydı ve biz sadece Cusotmer tablosunu çekseydik, JPA arkaplanda "join" yapacaktı. Yani aşağıdaki 2 query aynı anlama gelmektedir:

```java
Query query1 = em.createQuery("SELECT DISTINCT c FROM Customer c");
Query query2 = em.createQuery("SELECT DISTINCT c FROM Customer c INNER JOIN c.orders o");
```

# JPA Metamodel

```xml
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-jpamodelgen</artifactId>
    <version>5.3.7.Final</version>
</dependency>
```

Yukarıdaki bağımlılık build fazında tüm entity class'larımızı tarayıp, target dizini altına aşağıdaki kodları oluşturuyor:

```java
@Generated(value = "org.hibernate.jpamodelgen.JPAMetaModelEntityProcessor")
@StaticMetamodel(Student.class)
public abstract class Student_ {

    public static volatile SingularAttribute<Student, String> firstName;
    public static volatile SingularAttribute<Student, String> lastName;
    public static volatile SingularAttribute<Student, Integer> id;

    public static final String FIRST_NAME = "firstName";
    public static final String LAST_NAME = "lastName";
    public static final String ID = "id";
}
```

Biz bu sınıflar sayesinde aşağıdaki gibi kod hazabiliyoruz:

```java
Predicate p = builder.equal(Student_.LAST_NAME, authorName);

// Eğer bu sınıflar oluşturulmasaydı field ismini hardcode yazmak zorunda kalacaktık:
Predicate p = builder.equal(from.get("lastName"), authorName);
```