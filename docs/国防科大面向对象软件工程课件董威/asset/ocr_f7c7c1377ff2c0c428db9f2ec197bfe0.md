# Code

```
package atm.transaction;
import atm.ATM;
import atm.Session;

public class Inquiry extends Transaction {
    public Inquiry(ATM atm, Session session, Card card, int pin)
    {
        super(atm, session, card, pin);
    }

    protected Message getSpecificsFromCustomer() throws CustomerConsole.Cancelled
    {
        from = atm.getCustomerConsole().readMenuChoice(
            "Account to inquire from",
            AccountInformation.ACCOUNT_NAMES);
        return new Message(Message.INQUIRY,
            card, pin, serialNumber, from, -1, new Money(0));
    }

    protected Receipt completeTransaction()
    {
        return new Receipt(this.atm, this.card, this, this.balances) {
            String detailsPortion = new String[2];
            detailsPortion[0] = "INQUIRY FROM: " +
                AccountInformation.ACCOUNT_ABBREVIATIONS[from];
            detailsPortion[1] = "";
        };
    }

    private int from;
}
```