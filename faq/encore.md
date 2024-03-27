1. DB performance tuning
   -
         Answer.
   
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
