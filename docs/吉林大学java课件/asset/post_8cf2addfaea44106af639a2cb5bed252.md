
![](img/b706331eacf49a62651c2c9b2de81ca5_928_0.png)

## Show
main()

## ShowMails
maxMails : int = 128
currentMails : int = 0
putMails()
getMails()
showAll()

## Mails
fromAddr : Logical View::java::lang::String
toAddr : Logical View::java::lang::String
showMe()

## Parcel
weight : double
Parcel()
showMe()

## Remittance
remitValue : double
Remittance()
showMe()

## PostParcel
isPosted : boolean
parcelFee : double = 1.2
PostParcel()
callPrice()
post()
showMe()

## Postemit
isPosted : boolean
remitFee : double = 0.1
Postemit()
callPrice()
post()
showMe()

## MailPost
callPrice()
post()

$showList[]

```
ShowMails
maxMails : int = 128
currentMails : int = 0
putMails()
getMails()
showAll()
```

```
Mails
fromAddr : Logical View::java::lang::String
toAddr : Logical View::java::lang::String
showMe()
```

```
Parcel
weight : double
Parcel()
showMe()
```

```
Remittance
remitValue : double
Remittance()
showMe()
```

```
<<Interface>>
MailPost
callPrice()
post()
```

```
PostParcel
isPosted : boolean
parcelFee : double = 1.2
PostParcel()
callPrice()
post()
showMe()
```

```
Postemit
isPosted : boolean
remitFee : double = 0.1
Postemit()
callPrice()
post()
showMe()
```

## Mails

```java
package mymails;

public abstract class Mails
{
    String fromAddr;
    String toAddr;

    abstract void showMe();
}
```

## Parcel

```
package mymails;
public class Parcel extends Mails
{
    double weight;
    Parcel(String from,String to,double weight){
        fromAddr = from;
        toAddr = to;
        this.weight = weight;
    }
    public void showMe()
    {
        System.out.println("This is a Parcel from " + fromAddr + " to " + toAddr);
        System.out.println("And its weight is " + weight);
    }
}
```

## Remittance

```java
package mymails;
public class Remittance extends Mails {
	double remitValue;
	Remittance(String from, String to, double remitValue) {
		fromAddr = from;
		toAddr = to;
		this.remitValue = remitValue;
	}
	public void showMe() {
		System.out.println("This is a Remittance " + remitValue + " from" + fromAddr + " to " + toAddr);
	}
}
```

## MailPost

```
package mymails;

public interface MailPost
{
    double callPrice();
    void post();
}
```

```
Postemit
package mymails;
public class Postemit extends Remittance implements MailPost
{
    boolean isPosted;
    static double remitFee = 0.1;
    Postemit(String from,String to,double remitValue)
    {
        super(from,to,remitValue);
        isPosted = false;
    }
    public double callPrice()
    {
        return remitFee * remitValue + 1.0;
    }
}
```

```
Postemit
    public void post(){
        isPosted = true;
        System.out.println("You have paid " + callPrice() + " for this Remittance...");

        System.out.println("Your remittance has been posted.");
    }
    public void showMe(){
        super.showMe();
        System.out.println("This remittance's fee is " + callPrice());
        if (isPosted){
            System.out.println("This remittance has been posted...");
        }
        else
        {
            System.out.println("This remittance has not been posted...");
        }
        System.out.println();
    }
}
```

## PostParcel

```
package mymails;
public class PostParcel extends Parcel implements MailPost
{
    boolean isPosted;
    static double parcelFee = 1.2;

    PostParcel(String from,String to,double weight)
    {
        super(from,to,weight);
        isPosted = false;
    }
    public double callPrice(){
        return parcelFee * weight + 1.0;
    }
}
```

## PostParcel

```
public void post(){
    isPosted = true;
    System.out.println("You have paid " + callPrice() + " for this Parcel...");
    System.out.println("Your parcel has been posted.");
}
public void showMe(){
    super.showMe();
    System.out.println("This Parcel's fee is " + callPrice());
    if (isPosted){
    System.out.println("This Parcel has been posted...");
    }
    else
    {
    System.out.println("This Parcel has not been posted...");
    }
    System.out.println();
}
```
