# ROOM

## Save data in a local database using Room
if u lose internet during using application , u want the data to stay locally before the internet go ,so using room u can do that . room use sqlLite to manage ur data in database . but with sqlLite u cant do anything like sql . using sqlLite u can do the following :

1-Compile-time verification of SQL queries.

2-Convenience annotations that minimize repetitive and error-prone boilerplate code.

3-Streamlined database migration paths.

## Setup

To use Room in your app, add the following dependencies to your app's build.gradle file:

```
dependencies {
    def room_version = "2.4.2"

    implementation "androidx.room:room-runtime:$room_version"
    annotationProcessor "androidx.room:room-compiler:$room_version"
}
```
________

## Primary components

1- The database class that holds the database and serves as the main access point for the underlying connection to your app's persisted data.

2-Data entities that represent tables in your app's database.
data entity like java spring in backend web , use @Entity to define class as entity in database .
```
@Entity
public class User {
    @PrimaryKey
    public int uid;

    @ColumnInfo(name = "first_name")
    public String firstName;

    @ColumnInfo(name = "last_name")
    public String lastName;
}
```
@PrimaryKey :to make the uid column have unique values .

@ColumnInfo :to decide how name of column how will appear in database.

@Iqnore :use it for If an entity has fields that you don't want to persist

3-Data access objects (DAOs) that provide methods that your app can use to query, update, insert, and delete data in the database.
The following code defines a DAO called UserDao. UserDao provides the methods that the rest of the app uses to interact with data in the user table.
```
@Dao
public interface UserDao {
    @Query("SELECT * FROM user")
    List<User> getAll();

    @Query("SELECT * FROM user WHERE uid IN (:userIds)")
    List<User> loadAllByIds(int[] userIds);

    @Query("SELECT * FROM user WHERE first_name LIKE :first AND " +
           "last_name LIKE :last LIMIT 1")
    User findByName(String first, String last);

    @Insert
    void insertAll(User... users);

    @Delete
    void delete(User user);
}
```

## Database
The following code defines an AppDatabase class to hold the database. AppDatabase defines the database configuration and serves as the app's main access point to the persisted data.
```
@Database(entities = {User.class}, version = 1)
public abstract class AppDatabase extends RoomDatabase {
    public abstract UserDao userDao();
}
```

_____

In Room, there are two ways to define and query a relationship between entities: you can model the relationship using either an **intermediate data class** with embedded objects, or a **relational query method with a multimap return type**.

### Intermediate data class
In the intermediate data class approach, you define a data class that models the relationship between your Room entities. This data class holds the pairings between instances of one entity and instances of another entity as embedded objects

```
@Dao
public interface UserBookDao {
   @Query("SELECT user.name AS userName, book.name AS bookName " +
          "FROM user, book " +
          "WHERE user.id = book.user_id")
   public LiveData<List<UserBook>> loadUserAndBookNames();
}

public class UserBook {
    public String userName;
    public String bookName;
}
```

### Multimap return types
you don't need to define any additional data classes. Instead, you define a multimap return type for your method based on the map structure that you want and define the relationship between your entities directly in your SQL query.

```
@Query(
    "SELECT * FROM user" +
    "JOIN book ON user.id = book.user_id"
)
public Map<User, List<Book>> loadUserAndBookNames();
```
_____________
## Accessing data using Room DAOs
You can define each DAO as either an interface or an abstract class. For basic use cases, you should usually use an interface. In either case, you must always annotate your DAOs with @Dao. DAOs don't have properties, but they do define one or more methods for interacting with the data in your app's database

```
@Dao
public interface UserDao {
    @Insert
    void insertAll(User... users);

    @Delete
    void delete(User user);

    @Query("SELECT * FROM user")
    List<User> getAll();
}
```
