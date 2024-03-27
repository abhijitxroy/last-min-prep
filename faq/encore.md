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
         Answer.
   
5. Dirty read
   -
         Answer.

6. Using jdk-8, print array of name => char & their frequecny count
   -
         Answer.
   
7. How would you store password in DB? => BCrypt & Salt
   -
         Answer.

8. Sql injection?
   -
         Answer.

9. Differnce between object level lock & class level lock
   -
         Answer.
   
10. Proxy Design pattern implementation and real time usage.
    -
         Answer.
   
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
12. 
