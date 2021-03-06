# Expense Management System with load balancing and failure detection using circuit breaker

Steps to setup and run program:


	docker run --name db -p 3306:3306 -e MYSQL_ROOT_PASSWORD=pass1234 -e MYSQL_ROOT_HOST=% -e MYSQL_USER=root -d mysql/mysql-server
	
	docker run -d --name redis -p 6379:6379 redis
	
	cd assignment1App1ForAssign2
	
	docker build -t app .
	
	docker run -d -p 3000:3000 --name app -e PYTHONUNBUFFERED=0 --link db:mysql --link redis:redis -d app
	
	cd ../assignment1App2ForAssign2
	
	docker build -t app1 .
	
	docker run -d -p 3001:3001 --name app1 -e PYTHONUNBUFFERED=0 --link db:mysql --link redis:redis -d app1
	
	cd ../assignment1App3ForAssign2
	
	docker build -t app2 .
	
	docker run -d -p 3002:3002 --name app2 -e PYTHONUNBUFFERED=0 --link db:mysql --link redis:redis -d app2
	
	cd ../assignment2
	
	docker build -t proxy .
	
	docker run -d -p 8000:8000 --name proxy -e PYTHONUNBUFFERED=0 --link redis:redis -d proxy	
	
To check the logs (logs contain the statements for incoming requests and failure count for each replica if the request fails.) :
	
	docker logs proxy
	
Currently timeout set is 7 seconds and max failures is 4

License
=======

This project is released under the [MIT License](https://github.com/siddharth-daftari/Expense-Management-System-load-balancing/blob/master/LICENSE.txt).
