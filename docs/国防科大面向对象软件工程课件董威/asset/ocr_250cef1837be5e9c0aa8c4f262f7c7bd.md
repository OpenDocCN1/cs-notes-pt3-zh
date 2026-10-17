# # Detail Design of Classes



+   - atm: ATM
+   - pin: int
+   - state: int
+   - READING_CARD_STATE: final int
+   - READING_PIN_STATE: final int
+   - CHOOSING_TRANSACTION_STATE: final int
+   - PERFORMING_TRANSACTION_STATE: final int
+   - EJECTING_CARD_STATE: final int
+   - FINAL_STATE: final int

+   + Session(atm: ATM)
+   + performSession()
+   + setPIN(int pin)