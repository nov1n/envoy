# Usage
1. `docker-compose build`
2. `docker-compose up`
3. `curl -v localhost:8082`
4. Curl output should include our headers:
```
* Rebuilt URL to: localhost:8082/                              
*   Trying 127.0.0.1...                                        
* TCP_NODELAY set                                              
* Connected to localhost (127.0.0.1) port 8082 (#0)            
> GET / HTTP/1.1                                               
> Host: localhost:8082                                         
> User-Agent: curl/7.55.1                                      
> Accept: */*                                                  
>                                                              
< HTTP/1.1 200 OK                                              
< x-powered-by: Express                                        
< content-type: application/json; charset=utf-8                
< content-length: 544                                          
< etag: W/"220-dPqidwXvd535GGy7DenmaB4UVsc"                    
< date: Mon, 05 Feb 2018 13:53:42 GMT                          
< x-envoy-upstream-service-time: 3                             
< response-body-size: 544                                   <-- This is our response header
< server: envoy                                                
<                                                              
{                                                              
  "path": "/",                                                 
  "headers": {                                                 
    "host": "localhost:8082",                                  
    "user-agent": "curl/7.55.1",                               
    "accept": "*/*",                                           
    "x-forwarded-proto": "http",                               
    "x-request-id": "8bba1230-dbd2-4a29-a2a1-588c7706b9b0",    
    "foo": "bar",                                           <-- This is our request header
    "x-envoy-expected-rq-timeout-ms": "15000",                 
    "content-length": "0"                                      
  },                                                           
  "method": "GET",                                             
  "body": "",                                                  
  "fresh": false,                                              
  "hostname": "localhost",                                     
  "ip": "::ffff:170.0.0.1",                                   
  "ips": [],                                                   
  "protocol": "http",                                          
  "query": {},                                                 
  "subdomains": [],                                            
  "xhr": false,                                                
  "os": {                                                      
    "hostname": "14b32d96e230"                                 
  }                                                            
* Connection #0 to host localhost left intact                  
}
