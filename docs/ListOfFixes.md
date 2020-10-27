#List of fixes
##Fix 1
Add check for over bound deposit in deposit method.

Before:
```java
public boolean deposit(int sum)
    {
        if(blocked)
            return false;
        else if(sum < 0 || sum > bound)
            return false;
        else
        {
            balance += sum;
            return true;
        }
    }
```

After:
```java
    public boolean deposit(int sum)
    {
        if(blocked)
            return false;
        else if(sum < 0 || sum > bound || balance + sum > bound)
            return false;
        else
        {
            balance += sum;
            return true;
        }
    }
```

##Fix 2
Add blocked chek for setMaxCredit. 

Before:
```java
public boolean setMaxCredit(int mc)
    {
        if(mc < -bound || mc > bound)
            return false;
        else
            maxCredit = -mc;

        return true;
    }
```
After: 
```java
public boolean setMaxCredit(int mc)
    {
        if (!blocked)
            return false;
        else if(mc < -bound || mc > bound)
            return false;
        else
            maxCredit = -mc;

        return true;
    }
```