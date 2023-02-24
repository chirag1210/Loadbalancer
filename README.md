# Loadbalancer

Load balancer

***Prerequisite***: Learn first eureka, feign client, bais of spring boot

- ***Step 1***
  
Remove url in proxy class  
  
```  
//@FeignClient(name = "currency-exchange", url = "localhost:8000")  
@FeignClient(name = "currency-exchange")  
public interface CurrencyExchangeProxy {  
  
    @GetMapping("currency-exchange/from/{from}/to/{to}")  
    public CurrencyConversion getCurrencyExchange(@PathVariable String from, @PathVariable String to);  
  
}  
```

- ***Step 2***:  by default load balancing is available in eureka-client hierarchy previously 
we are using ribbion

- ***Step 3***:  launch currency-exchange with port:8001  
  
- ***Step 4***: url: localhost:8761/  for currency-exchange you will get 2 instances.  
  
- ***Step 5***: Go to   http://localhost:8100/currency-conversion-feign/from/USD/to/INR/quantity/10  
  
{  
  "id": 10001,  
  "from": "USD",  
  "to": "INR",  
  "conversionMultiple": 65.00,  
  "quantity": 10,  
  "totalCalculatedAmount": 650.00,  
  "environment": "8001"  
}  
  
You will get different environment after every 30 sec  
