1. DB performance tuning
   -
   Database performance tuning is a critical aspect of ensuring that database systems operate efficiently and effectively. Here are some key strategies for tuning database performance:

   **Indexing:** Proper indexing can significantly improve query performance by allowing the database to quickly locate and retrieve data. Analyze query patterns and identify columns frequently used in WHERE clauses or JOIN conditions for indexing.
         
   **Query Optimization:** Review and optimize SQL queries to minimize resource consumption and execution time. Techniques include rewriting queries, using appropriate joins, avoiding unnecessary functions in WHERE clauses, and reducing data retrieval.
         
   **Database Schema Design:** Design the database schema to minimize redundant data and ensure efficient data storage and retrieval. Normalize the database structure to reduce data duplication while avoiding over-normalization that can lead to complex joins.
         
   **Hardware Optimization:** Ensure that the hardware infrastructure, including CPU, memory, storage, and network resources, is adequately provisioned to support the database workload. Consider factors such as disk I/O speed, memory allocation, and network bandwidth.
         
   **Query Caching:** Utilize query caching mechanisms provided by the database management system (DBMS) or implement application-level caching to store frequently accessed query results in memory, reducing the need for repeated query execution.
         
   **Partitioning:** Partition large tables or indexes into smaller, more manageable segments based on certain criteria (e.g., range, hash) to improve query performance and manageability.
         
   **Concurrency Control:** Optimize transaction isolation levels to balance data consistency requirements with concurrency and performance. Choose the appropriate isolation level (e.g., READ COMMITTED, REPEATABLE READ) based on the application's requirements.
         
   **Database Configuration Tuning:** Adjust database configuration parameters (e.g., buffer sizes, connection pool settings, caching mechanisms) to optimize performance based on workload characteristics and available hardware resources.
         
   **Monitoring and Profiling:** Continuously monitor database performance metrics (e.g., CPU usage, memory usage, disk I/O) using monitoring tools or built-in DBMS features. Identify performance bottlenecks and hotspots through profiling and performance analysis.
         
   **Regular Maintenance:** Perform routine maintenance tasks such as index reorganization, statistics updates, and database backups to ensure optimal performance and data integrity over time.
         
   By employing these strategies and continuously monitoring and optimizing database performance, organizations can ensure that their database systems meet performance requirements and scale effectively to handle growing workloads.
   
3. DB Isolation level
   -
**Read Uncommitted:**
    - This is the lowest isolation level. Transactions can read data that has been modified but not yet committed by other transactions, leading to dirty reads, non-repeatable reads, and phantom reads.

**Read Committed:** 
- This isolation level ensures that transactions only read committed data. It prevents dirty reads by allowing a transaction to read data only after it has been committed by other transactions. However, it may still encounter non-repeatable reads and phantom reads.

**Repeatable Read:** 
- In this isolation level, a transaction sees a consistent snapshot of the database as of the time the transaction started. It prevents non-repeatable reads by ensuring that data read within the transaction remains unchanged, but it may still experience phantom reads.

**Serializable:**
- This is the highest isolation level. It ensures strict transaction isolation by serializing transactions, preventing all concurrency anomalies (dirty reads, non-repeatable reads, and phantom reads). Serializable isolation achieves this by locking data more aggressively, which can lead to reduced concurrency and potential deadlock situations.

**Snapshot Isolation:**
- This isolation level provides a consistent snapshot of the database for each transaction, ensuring that each transaction sees a consistent view of the database as of the time it started. Snapshot isolation eliminates the risk of dirty reads and non-repeatable reads but may still encounter phantom reads.

The choice of isolation level depends on the application requirements for data consistency, concurrency, and performance. Higher isolation levels offer stronger consistency guarantees but may incur higher overhead due to increased locking and reduced concurrency. Conversely, lower isolation levels provide higher concurrency but may allow certain concurrency anomalies.

It's important for developers and database administrators to understand the characteristics and trade-offs of each isolation level and select the appropriate level based on the specific requirements of their applications. Additionally, some database systems may offer additional isolation levels or customizable isolation configurations beyond the standard levels defined by SQL standards.

   
5. Dirty read
   -
A dirty read occurs in a database transaction when one transaction reads data from a row that has been modified by another transaction but not yet committed. This means that the data being read might be in an inconsistent or intermediate state.

For example, consider Transaction A updating a particular row in a database and Transaction B reading that row before Transaction A commits its changes. If Transaction A ultimately rolls back its changes, Transaction B would have read data that was never meant to be persisted, leading to a dirty read.

Dirty reads are typically not desirable in database systems because they can lead to incorrect or misleading results. They can occur when transactions do not properly isolate their changes from each other, often due to lower isolation levels being used or insufficient concurrency control mechanisms.

To prevent dirty reads, databases typically implement isolation levels that control the visibility of data modifications made by concurrent transactions, ensuring that transactions see a consistent view of the database. These isolation levels, such as Read Committed or Serializable, help maintain data consistency and prevent concurrency anomalies.


6. Using jdk-8, print array of name => char & their frequecny count
   -
         Answer.
   
7. How would you store password in DB? => BCrypt & Salt
   -
- In Java, you can securely store passwords in a database using hashing and salting techniques. Here's a basic example using the bcrypt hashing algorithm with the BCrypt library:

- Add Dependency: First, you need to add the jBCrypt library to your project. You can do this by including the appropriate dependency in your build configuration. If you're using Maven, add the following dependency to your pom.xml:

      <dependency>
          <groupId>org.mindrot</groupId>
          <artifactId>jbcrypt</artifactId>
          <version>0.4</version>
      </dependency>
- Generate Salt and Hash Password: In your Java code, use BCrypt to generate a salt and hash the password before storing it in the database.

      import org.mindrot.jbcrypt.BCrypt;
      public class PasswordHashing 
      {
          public static String hashPassword(String password) 
          {
              // Generate a salt
              String salt = BCrypt.gensalt();
      
              // Hash the password with the salt
              String hashedPassword = BCrypt.hashpw(password, salt);
      
              return hashedPassword;
          }
      
          public static boolean verifyPassword(String password, String hashedPassword) 
          {
              // Check if the provided password matches the hashed password
              return BCrypt.checkpw(password, hashedPassword);
          }
      
          public static void main(String[] args) 
          {
              // Example usage
              String password = "user123";
              String hashedPassword = hashPassword(password);
              System.out.println("Hashed Password: " + hashedPassword);
      
              // Verify password
              boolean isMatch = verifyPassword(password, hashedPassword);
              System.out.println("Password Match: " + isMatch);
          }
      }
**Store Hashed Password:** 
- Store the hashed password and salt in your database. Make sure to securely manage the salt and store it alongside the hashed password.
When a user logs in, you can retrieve the hashed password and salt from the database, then use the verifyPassword method to compare the provided password with the stored hashed password.

- Remember to handle exceptions and error cases appropriately, and consider additional security measures such as encryption for sensitive data and secure transmission of passwords.


8. Sql injection?
   -
   
- SQL injection in Java typically occurs when user input is concatenated directly into SQL queries without proper validation or parameterization. Here's an example of how SQL injection can occur in a Java application:

         import java.sql.*;      
         public class SQLInjectionExample 
         {
      
          public static void main(String[] args) 
          {
              String userInput = args[0]; // Simulating user input
      
              try 
              {
                  // Establish database connection
                  Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydatabase", "username", "password");
      
                  // Vulnerable SQL query with concatenated user input
                  String query = "SELECT * FROM users WHERE username = '" + userInput + "'";
                  
                  // Execute the SQL query
                  Statement statement = connection.createStatement();
                  ResultSet resultSet = statement.executeQuery(query);
      
                  // Process the query results
                  while (resultSet.next()) {
                      System.out.println("User ID: " + resultSet.getInt("user_id"));
                      System.out.println("Username: " + resultSet.getString("username"));
                  }
      
                  // Close resources
                  resultSet.close();
                  statement.close();
                  connection.close();
              } catch (SQLException e) {
                  e.printStackTrace();
              }
          }
      }
- In this example, the userInput variable is directly concatenated into the SQL query without any validation or parameterization. If an attacker provides malicious input such as ' OR '1'='1, the resulting query becomes:

      SELECT * FROM users WHERE username = '' OR '1'='1'
- This query would return all records from the users table, bypassing any intended authentication mechanism.

- To prevent SQL injection in Java, you should use parameterized queries or prepared statements. Here's how you can rewrite the previous example using a prepared statement:

      import java.sql.*;

      public class SQLInjectionPreventionExample {
      
          public static void main(String[] args) {
              String userInput = args[0]; // Simulating user input
      
              try {
                  // Establish database connection
                  Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydatabase", "username", "password");
      
                  // Prepared statement with parameterized query
                  String query = "SELECT * FROM users WHERE username = ?";
                  PreparedStatement preparedStatement = connection.prepareStatement(query);
                  preparedStatement.setString(1, userInput);
      
                  // Execute the prepared statement
                  ResultSet resultSet = preparedStatement.executeQuery();
      
                  // Process the query results
                  while (resultSet.next()) {
                      System.out.println("User ID: " + resultSet.getInt("user_id"));
                      System.out.println("Username: " + resultSet.getString("username"));
                  }
      
                  // Close resources
                  resultSet.close();
                  preparedStatement.close();
                  connection.close();
              } catch (SQLException e) {
                  e.printStackTrace();
              }
          }
      }
- With parameterized queries, the user input is treated as a parameter value rather than part of the SQL query itself, effectively preventing SQL injection attacks.


9. Differnce between object level lock & class level lock
   -
- Object-level locking and class-level locking are two concurrency control mechanisms used in Java to synchronize access to shared resources among multiple threads. Here's the difference between them:

**Object-Level Locking:**
- In object-level locking, each instance of a class has its own lock associated with it.
When a synchronized method or block is invoked on an object, the lock acquired is specific to that instance of the object.
Only one thread can hold the lock on a particular object at a time. Other threads attempting to acquire the lock will be blocked until the lock is released by the owning thread.
Object-level locking is useful when different instances of a class need to be synchronized independently.
Example:

      public class MyClass 
      {
          public synchronized void synchronizedMethod() 
          {
              // This method is synchronized using object-level lock
          }
      }
**Class-Level Locking:**
- In class-level locking, a single lock is associated with the class itself rather than with individual instances.
When a synchronized static method or block is invoked on a class, the lock acquired is on the class object.
Only one thread can hold the lock on the class at a time, regardless of the number of instances of the class.
Class-level locking is useful when you want to synchronize access to static variables or static methods shared among all instances of the class.
Example:

      public class MyClass 
      {
          public static synchronized void synchronizedStaticMethod() 
          {
              // This method is synchronized using class-level lock
          }
      }
- In summary, object-level locking synchronizes access to instance methods or blocks on a per-object basis, while class-level locking synchronizes access to static methods or blocks on a per-class basis. The choice between them depends on the specific concurrency requirements and the shared resources being accessed in your Java application.
   
10. Proxy Design pattern implementation and real time usage.
    -
- The Proxy Design Pattern provides a surrogate or placeholder for another object to control access to it. It is useful in scenarios where you want to add additional functionality or control access to an object without modifying its code directly. Here's an implementation of the Proxy Design Pattern in Java along with a real-time usage example:

Implementation:

      // Subject interface
      interface Image 
      {
          void display();
      }

      // RealSubject class
      class RealImage implements Image 
      {
          private String filename;

          public RealImage(String filename)
          {
              this.filename = filename;
              loadFromDisk();
          }
      
          private void loadFromDisk() 
          {
              System.out.println("Loading image: " + filename);
          }
      
          @Override
          public void display() 
          {
              System.out.println("Displaying image: " + filename);
          }
      }

      // Proxy class
      class ProxyImage implements Image 
      {
          private RealImage realImage;
          private String filename;
      
          public ProxyImage(String filename)
          {
              this.filename = filename;
          }
      
          @Override
          public void display() 
          {
              if (realImage == null) 
              {
                  realImage = new RealImage(filename);
              }
              realImage.display();
          }
      }

      // Client class
         public class ProxyPatternExample 
         {
          public static void main(String[] args) 
          {
              // Usage of Proxy
              Image image = new ProxyImage("sample.jpg");
      
              // Image will be loaded from disk only when it's displayed for the first time
              image.display();
      
              // Subsequent calls will reuse the already loaded image
              image.display();
          }
      }
      
**Real-Time Usage Example:**
The Proxy Design Pattern is commonly used in various scenarios, such as:

**Virtual Proxy: **
- Delaying the creation and initialization of expensive objects until they are actually needed. For example, loading large images or documents on demand rather than loading them all at once.

**Protection Proxy: **
- Controlling access to sensitive resources or operations. For example, restricting access to certain methods or data based on user permissions or roles.

**Remote Proxy:**
- Acting as a local representative for an object that resides in a different address space, such as a remote server. The proxy handles the communication and data marshalling between the client and the remote object.

**Logging Proxy:**
- Adding logging functionality around method calls to track the behavior of the real object. This is useful for debugging and monitoring purposes.

**Caching Proxy:**
- Caching the results of expensive operations to improve performance. The proxy checks whether the result of an operation is already cached and returns it directly if available, reducing the need to execute the operation again.

In real-world applications, you may encounter situations where using proxies can simplify system architecture, improve performance, or add additional functionality without modifying existing code.


11. Different types of GC
    -
1. **Serial GC** -> runs on single core ( app run > GC pause(mark,sweep,compacting) > again app run > and so on 
2. **Parallel GC **-> Same as Serial GC but GC runs on multiple cores 
3. **Concurrrent Mark and Sweep GC** => app run > shorter GC pause for mark but sweep,compacting can be done with app run (no separate pause) > and so on 
4. **G1 GC **-> Heap is divided into region and they are garbage colleted in parallel fashion depending on whoever has more amount of garbage
  
**NOTE:** Default GC: 1.6 = Parallel GC but 1.7 = G1 GC

Link: https://www.youtube.com/watch?v=UnaNQgzw4zY
<img width="1233" alt="image" src="https://github.com/abhijitxroy/last-min-prep/assets/161963891/e724436f-e70e-4498-83e1-db6f0c0e9195">

11. Parallel GC VS CMS GC
    -
  - Parallel GC is similar to Serial GC but GC runs on multiple cores
  - Whereas app run > shorter GC pause for mark and remark but sweep,compacting can be done with app run (no separate pause) > and so on 

