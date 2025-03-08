# Visits application


## This application is creating one redis container for multiple instance of node web server

### Restart policies
Example from docker-compose.yml  
restart: on-failure

"no" -> never attempt to restart  (**no must be in quotes**)  
always -> always attempt to restart  
on-failure -> only restart if the container stops with an error code  
unless-stopped -> always restart unless we (the developers) forcibly stop it