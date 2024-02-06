### Formula Injection (price tampering) 

Simply changing the price mentioned in the request during basket/add or checkout
![image](https://github.com/Sameer484/methodology/assets/110039044/fc2e7ed9-2cdb-4513-ae65-91e05d31e84d)

### Quantity Tampering
 Change the quantity value to negative integer like (-1) from 1. Add two items, one with positive quantity integer and another with negative one and when both are added up, you will end up with lower combined price
 ![image](https://github.com/Sameer484/methodology/assets/110039044/514ebcde-5657-4159-8cd2-abc06dd0b88e)

Or change the quantity value to decimal value like 0.2 and when multiplying it with price in backend, it turns out lower price.
### Integer Overflow 
Somtimes, the quantity value is stored in 64 bit integer. If we send very high value, it may reset to negative number or even to 0. Try in price value too.


### Coupons

Are previous coupons expired?? Can you reuse previous tokens that may be leaked somewhere in wayback machine??
![image](https://github.com/Sameer484/methodology/assets/110039044/a66f6629-5a7a-4ca9-b754-cd1be4bc4caa)


### Currency Confusion

Changing the currency type from USD to INR or NPR 
![image](https://github.com/Sameer484/methodology/assets/110039044/63f7a099-2a16-4c94-b26b-9f461d449304)

