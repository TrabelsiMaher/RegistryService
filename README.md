"# RegistryService" 
configurations ::
1-service-registry :
	*Dependency :
		spring-cloud-starter-netflix-eureka-server
	* ...Apllication.java 
		@EnableEurekaServer
	*application.properties
		à renommer to application.yaml
			server:
			 port: 8171
 			spring:
			 application:
			  name: serviceRegistry
			eureka:
			 instance:
			  hostname: localhost
			client:
			 register-with-eureka: false
             fetch-registry: false
			 serviceUrl:
			  defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
2- Configuration des services
	*Dependency :
		spring-boot-starter-actuator
		spring-boot-starter-web
		spring-cloud-starter-netflix-eureka-client
		spring-boot-starter-web
	* ...Apllication.java 
		@EnableEurekaServer
	*application.properties
		à renommer to application.yaml
			server:
			 port: 8172
 			spring:
			 application:
			  name: departement-service
    		eureka:
			 client:
			  serviceUrl:
              defaultZone: http://localhost:8171/eureka/
			  
start app and visit (la page d'acceuil du serveur des registres eureka)
http://localhost:8171/ 
 ==> on doit trouver le premier service est inscrit dans la liste des applications
