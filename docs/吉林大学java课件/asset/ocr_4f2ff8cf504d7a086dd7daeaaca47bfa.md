# 使用同步代码块解决以上的同步问题

```
class MyThread implements Runnable{        // 实现Runnable接口
    private int ticket = 5 ;                // 一共5张票
    public void run() {                     // 覆写run()方法
        for(int i=0;i<100;i++){             // 超出票数的循环
            synchronized (this) {           // 设置需要同步的操作
                if(ticket>0){               // 判断是否有剩余票
                    try {
                        Thread.sleep(300) ;     // 加入延迟
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println("卖票: ticket = " + ticket--);
                }
            }
        }
    }
};
```