## Piwigo has a background command execution vulnerability

Command injection vulnerability trigger point

![image-20210828215332817](https://i.loli.net/2021/08/28/lxITqKH4FfNUk1u.png)

Use admin to enter the background

![image-20210828215510232](https://i.loli.net/2021/08/28/sKeVBPObZ1Y2G7k.png)

Click settings to come to this page

![image-20210828215545287](https://i.loli.net/2021/08/28/RfMUySW8HFKwAJx.png)

Write in it

![image-20210828215622977](https://i.loli.net/2021/08/28/AeL5DfoZdgtYEiQ.png)

```php
<?phpvar_dump(1);}if(1){system('calc');?>
```

![image-20210828215714527](https://i.loli.net/2021/08/28/Qts93vCugXZpe2O.png)

Next breakpoint single step debugging

![image-20210828215744709](https://i.loli.net/2021/08/28/ZxdA17CvUfTRVIk.png)

You will find that this sentence is implemented here

![image-20210828215801888](https://i.loli.net/2021/08/28/EWLvQPHSTFlB1pV.png)



## code analysis

![image-20210828220311898](https://i.loli.net/2021/08/28/ip63X4euaHZwNQT.png)

Text is passed in ` $content without filtering_ File ` and then pass in the function

![image-20210828220404762](https://i.loli.net/2021/08/28/Mngkf3bQHaOI4dK.png)

The incoming code is spliced here. Caused code execution
