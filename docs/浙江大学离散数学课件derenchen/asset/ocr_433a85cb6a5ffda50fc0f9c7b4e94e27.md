(3) \( (p \vee q) \rightarrow r \Leftrightarrow \neg (p \vee q) \vee r \)

\( \Leftrightarrow (\neg p \wedge \neg q) \vee r \)

\( \Leftrightarrow (\neg p \wedge \neg q \wedge (\neg r \vee r)) \vee ((\neg p \vee p) \wedge (\neg q \vee q) \wedge r) \)

\( \Leftrightarrow (\neg p \wedge \neg q \wedge \neg r) \vee (\neg p \wedge \neg q \wedge r) \vee (\neg p \wedge \neg q \wedge r) \vee (\neg p \wedge q \wedge r) \vee (p \wedge \neg q \wedge r) \vee (p \wedge q \wedge r) \)

\( \Leftrightarrow m_0 \vee m_1 \vee m_3 \vee m_5 \vee m_7 \)

故该公式是可满足式，但不是重言式。