# CHAPTER 4 SYNTAX ANALYSIS

# Section 5 LR parsers

# 12、 SLR(1) Parsing Table Algorithm

Method

+   - (2)

+   (a) If [A→α•aβ] is in Iᵢ and goto(Iᵢ,a)= Iⱼ, then set ACTION[i,a]=“Shift j”, here a must be a terminal.

+   (b) If [A→α•]∈Iₖ, then set ACTION[k,a]=rⱼ for all a in follow(A); here A may not be S`, and j is the No. of production A→α .

+   - (3) The goto transitions for state I are constructed for all non terminals A using the rule: if goto (Iᵢ,A)= Iⱼ, then goto[i,A]=j