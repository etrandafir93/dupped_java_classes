# Duplicate Classes Demo

This project demonstrates the duplicate class loading issue described in 
the blog post [The Case of the Vanishing Schema Field](https://blog.etrandafir.com/blog/avro-duplicate-class-mystery/). 

It reproduces the problem where multiple JARs contain the same class with identical fully qualified names,
leading to non-deterministic runtime behavior depending on classloader order.

- `payment-api` - Contains `MoneyAmount` record with 2 fields
- `order-api` - Contains `MoneyAmount` record with 3 fields (newer version)
- `dummy-app` - Depends on both APIs, demonstrating the conflict

Run `mvn clean install` to see the Maven Enforcer Plugin detect 
and fail the build due to duplicate classes.


