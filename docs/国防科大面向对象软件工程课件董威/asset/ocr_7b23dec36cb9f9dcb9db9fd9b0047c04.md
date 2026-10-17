# # Detail Design of Classes

Message

+ WITHDRAWAL: final int
+ INITIATE_DEPOSIT: final int
+ COMPLETE_DEPOSIT: final int
+ TRANSFER: final int
+ INQUIRY: final int
- messageCode: int
- card: Card
- pin: String
- serialNumber: int
- fromAccount: int
- toAccount: int
- amount: int