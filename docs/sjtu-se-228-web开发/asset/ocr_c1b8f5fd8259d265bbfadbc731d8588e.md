+   - Step 2 - Create The Action Class HelloWorldAction.java
+   - HelloWorld.java

```
package helloworld.action;

public class HelloWorldAction extends ActionSupport {
    private static final long serialVersionUID = 1L;
    private MessageStore messageStore;
    public String execute() throws Exception {
        messageStore = new MessageStore();
        return SUCCESS;
    }
    public MessageStore getMessageStore() {
        return messageStore;
    }
    public void setMessageStore(MessageStore messageStore) {
        this.messageStore = messageStore;
    }
}
```