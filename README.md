# last-min-prep

Are you hands on architecting design and solution	
- 
What are the tools you have used	
- Draw.io, Confluence, Jira
  
Which methodology you are using?	
- Agile
  
How do you start design after getting the requirement from the client	
- Pros & cons of design 
	User base
	Resource availablity
	Available resource Licence
	Diagram flow
	Final create an epic in Jira
	Distribute the task based on the roles
	
What are the principles worked on m/s	Design pattern:
    - Circuit Breaker DP
    - CQRS DP - command query response 
    - Straguler DP
    - Orchestrastion of m/s
            ○ Two phase commit
            ○ Event plus way
	        
What is blue and green deployment Design pattern	
- 

Problem statement: 	
You have two m/s profile & statement and you are updating some profile details having dependency with statement m/s. but the statement service is down
- Use circuite breaker DP
  
What cloud computing you have worked (AWS)?	
- EC2, S3 => mostly use
- SNS, IAM, CloudFront(CDN), API GATEways
  
What are the diff services you have worked upon	
- Others Loadbalancer, security groups, vpn, private links, cloud formation (iAAS), Global accelator

Do you know kubernetes concepts? (ELK | EKS)	
- 

What are different commands you have used in Docker & Kubernates?
-

Using Stream API, You have to filter from the emp whose age is greater than 15	
- List.stream().filter( e-> e.getAge() > 15).collect(Collectors.toList());

Using Stream API, You have to filter from the emp whose age is greater than 30 need to update the type as senior and print the employee data for those.	
- list.stream().filter(e -> e.getAge() > 30).forEach(e -> {
	        e.setType("Senior");
	        StringJoiner sj = new StringJoiner(" | " , "<", ">");
	        sj.add(e.getName()).add(e.getType());
	        System.out.println(sj);
	        });
How do you handle exception in springboot	
- @RestControllerAdvice -> class level
	@ExcpetionHandling(MyException.class) -> method level

How do you make sure your application is optimized as part of memory management	
This are the ways to make your code make perfomant and leak proof
	- Memory leak check
	- Proper exception handling - try catch finaly, try-with-resource
	- Proper data structer & algo logic
	- Code review
	- DP (desgin pattern)
	
	
	

