# Swagger-UI

This is a modular API based on Grape that can be used to create a simple API. 

## Getting started

Point your browser to http://swagger-ui.app.adcombi.com/

You can add the url parameter to the request, to specify the Swagger endpoint that you want to use. For example: 
```
http://localhost:5000/?url=http://petstore.swagger.io/v2/swagger.json
```

## Deploy to Deis cloud

```
$ deis register http://deis.app.adcombi.com

$ deis login http://deis.app.adcombi.com
$ deis create swagger-ui
$ deis keys:add
$ deis config:set TZ=Europe/Amsterdam
$ git push deis master
$ deis logs
$ deis info
```

## Destroy application from Deis cloud

```
$ deis destroy
 !    WARNING: Potentially Destructive Action
 !    This command will destroy the application: swagger-ui
 !    To proceed, type "swagger-ui" or re-run this command with --confirm=swagger-ui

> swagger-ui
Destroying swagger-ui... 
done in 7s
```
