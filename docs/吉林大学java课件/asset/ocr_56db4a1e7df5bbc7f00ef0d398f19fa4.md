# 不满足迪米特法则的系统

```
public class Someone
{
    public void operation1(Friend friend)
    {
        Stranger stranger=friend.provide();
        stranger.operation3();
    }
}
public class Friend
{
    private Stranger stranger=new Stranger();
    public void operation2()
    {
    }
    public Stranger provide()
    { return stranger;}
}
```