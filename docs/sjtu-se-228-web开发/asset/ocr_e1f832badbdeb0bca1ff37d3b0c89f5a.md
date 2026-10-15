+   - Multiple id properties with a dedicated identifier type

```
@Entity
@IdClass(CustomerId.class)
class Customer implements Serializable {
    @Id
    @OneToOne
    @JoinColumns({
        @JoinColumn(name="userfirstname_fk", referencedColumnName="firstName"),
        @JoinColumn(name="userlastname_fk", referencedColumnName="lastName")
    })
    User user;

    @Id
    String customerNumber;
    boolean preferredCustomer;
}

class CustomerId implements Serializable {
    UserId user;
    String customerNumber
    //implements equals and hashCode
}
```