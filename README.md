# E-Tourist deployment
## Install & Run
### Prerequisites
You need to:
1. Clone the repositories below:
    - backend: https://github.com/E-Tourist/backend.git
    - frontend: https://github.com/E-Tourist/frontend.git
    - deployment: https://github.com/E-Tourist/deployment.git
2. Use in terminal: 
`docker-compose -f docker-compose.yml --project-name e-tourist up -d --build --force-recreate` 
to build all not-commented services in docker-compose.yml
(you can comment out 'backend' and 'frontend' services and run them locally)
3. Get into: http://localhost:8080/auth (Keycloak Admin Console)
4. Login with credentials of: admin/password
5. Configure Keycloak realm:
- create 'E-Tourist' realm and configure it:
![img.png](images/img.png)
![img_1.png](images/img_1.png)
- add 'backend', 'frontend' clients:
![img_4.png](images/img_4.png)
![img_5.png](images/img_5.png)
![img_6.png](images/img_6.png)
- create 'admin' and 'user' roles:
![img_7.png](images/img_7.png)
- create your own users and assign them into roles
![img_9.png](images/img_9.png)
6. Setup both frontend and backend - use clients credentials to authenticate backend, frontend by properties:
- auth server url: http://localhost:8080/auth/
- realm: 'E-Tourist'
- resource/clientId: 'backend' or 'frontend'
- clientSecret: [generated by keycloak] (only backend)

Other parameters if needed:
- bearer-only: true,
- ssl-required: external,
- confidential-port: 443