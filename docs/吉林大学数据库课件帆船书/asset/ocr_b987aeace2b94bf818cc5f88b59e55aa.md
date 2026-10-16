# Equivalence Rules (Cont.)

+   5. Theta-join operations (and natural joins) are commutative.
+   $E_1 \bowtie_{\theta} E_2 = E_2 \bowtie_{\theta} E_1$

+   6. (a) Natural join operations are associative:
+   $(E_1 \bowtie E_2) \bowtie E_3 = E_1 \bowtie (E_2 \bowtie E_3)$

+   (b) Theta joins are associative in the following manner:
+   $(E_1 \bowtie_{\theta1} E_2) \bowtie_{\theta2 \wedge \theta3} E_3 = E_1 \bowtie_{\theta1 \wedge \theta3} (E_2 \bowtie_{\theta2} E_3)$
+   where $\theta_2$ involves attributes from only $E_2$ and $E_3$.