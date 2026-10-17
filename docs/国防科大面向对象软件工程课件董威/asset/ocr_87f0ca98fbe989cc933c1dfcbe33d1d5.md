# # Withdrawal Transaction Collaboration

![](bbox=[0.78, 0.05, 0.98, 0.2])

![](bbox=[0.82, 0.51, 0.98, 0.66])

![](bbox=[0.8, 0.84, 0.96, 0.99])

![](bbox=[0.29, 0.53, 0.46, 0.66])

![](bbox=[0.29, 0.84, 0.46, 0.99])

1.1: from = readMenuChoice("Account to withdraw from", availableAccounts menu)
[ while not valid amount ] 1.2: amount = amountValues [ readMenuChoice("Amount to withdraw", withdrawal amounts menu) ]
1: message = getSpecificsFromCustomer()
2: receipt = completeTransaction()
<< self >>
1.3: validAmount = checkCashOnHand(amount)
2.1: dispenseCash(amount)
1.4 << create >>
2.2 << create >>