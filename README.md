# Assignment 2

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
	
To check the logs (logs contain the statements for incoming requests and failure count for each replica if the request fails. Also it shows the remaining time till circuit breaker will remain open, if it received a request in open statement):
	docker logs proxy