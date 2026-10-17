# # How faster a processor for ideal

\(\frac{\text{CPU time with stalls}}{\text{CPU time with perfect cache}} = \frac{\text{I} \times \text{CPI}_\text{stall} \times \text{Clock cycle}}{\text{I} \times \text{CPI}_\text{perfect} \times \text{Clock cycle}}\)

\(= \frac{\text{CPI}_\text{stall}}{\text{CPI}_\text{perfect}} = \frac{5.44}{2} = 2.72\)

+   - What happens if the processor is made faster?

# ## Assume CPI reduces from 2 to 1

CPI with stall = CPI with perfect cache + total memory-stalls

\(=(1+3.44)\text{I} = 4.44\text{I}\)

\(\frac{\text{CPU time with stalls}}{\text{CPU time with perfect cache}} = \frac{\text{CPI}_\text{stall}}{\text{CPI}_\text{perfect}} = \frac{4.44}{1} = 4.44\)

Ratio time for Memory stalls

\(\text{from } \frac{3.44}{5.44} = 63\% \quad \text{to } \frac{3.44}{4.44} = 77\%\)