

## AOP: Read Method Arguments with JoinPoints - Overview

**Problem**
+ When we are in an aspect (i.e logging)
  + How can we access method parameters?

File:MainDemoApp.java
```Java

// call the business method
Account myAccount = new Account();
theAccountDAO.addAccount(myAccount, true);
```
+ `theAccountDAO.addAccount(myAccount, true);` I want to log these params with AOP


**Development Process**
1. Access and display Method Signature
2. Access and display Method Arguments

_Step 1: Access and display Mehod Signature_
```JAVA
@Before("...")
public void beforeAddAccountAdvice(JoinPoint theJoinPoint) {
  
  // display the method signature 
  MethodSignature methodSig = (MehtodSignature) theJointPoint.getSignature();
  
  System.out.println("Method: " + methodSig);
  
}
```

**Output:**
```CMD
Mehod: void com.tilmeez.aopdemo.dao.AccountDAO.addAccount(Account,boolean)
```

_Step 2:Access and display Method Arguments_
```JAVA
@Before("...")
public void beforeAddAccountAdvice(JoinPoint theJoinPoint) {
  
  // display method argument
  
  // get args
  Object[] args = theJoinPoint.getArgs();
  
  // loop thru args
  for (Object tempArg : args) {
    System.out.println(tempArgs);
  }
}
```
**Output:**
```CMD
com,tilmeez.aopdemo.Account@127c45

true
```




