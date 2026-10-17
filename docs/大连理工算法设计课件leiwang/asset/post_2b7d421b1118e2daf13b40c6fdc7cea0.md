

## Appendix: Punched-card technology

- Herman Hollerith (1860-1929)
- Punched cards
- Hollerith’s tabulating system
- Operation of the sorter
- Origin of radix sort
- “Modern” IBM card
- Web resources on punched-card technology

## Herman Hollerith (1860-1929)

- The 1880 U.S. Census took almost 10 years to process.
- While a lecturer at MIT, Hollerith prototyped punched-card technology.
- His machines, including a “card sorter,” allowed the 1890 census total to be reported in 6 weeks.
- He founded the Tabulating Machine Company in 1911, which merged with other companies in 1924 to form International Business Machines.

## Punched cards

- Punched card = data record.
- Hole = value.
- Algorithm = machine + human operator.

### Hollerith's tabulating system, punch card in Genealogy Article on the Internet

Image removed due to copyright restrictions.
Replica of punch card from the 1900 U.S. census. [Howells 2000]

## Hollerith’s tabulating system

- Pantograph card punch
- Hand-press reader
- Dial counters
- Sorting box

> “Hollerith Tabulator and Sorter: Showing details of the mechanical counter and the tabulator press.” Figure from [Howells 2000].

## Operation of the sorter

- An operator inserts a card into the press.
- Pins on the press reach through the punched holes to make electrical contact with mercury-filled cups beneath the card.
- Whenever a particular digit value is punched, the lid of the corresponding sorting bin lifts.
- The operator deposits the card into the bin and closes the lid.
- When all cards have been processed, the front panel is opened, and the cards are collected in order, yielding one pass of a stable sort.

Hollerith Tabulator, Pantograph, Press, and Sorter (http://www.columbia.edu/acis/history/census-tabulator.html)

## Origin of radix sort

Hollerith’s original 1889 patent alludes to a most-significant-digit-first radix sort:

> “The most complicated combinations can readily be counted with comparatively few counters or relays by first assorting the cards according to the first items entering into the combinations, then reassorting each group according to the second item entering into the combination, and so on, and finally counting on a few counters the last item of the combination for each group of cards.”

Least-significant-digit-first radix sort seems to be a folk invention originated by machine operators.

## "Modern" IBM card

- One character per column.

Image removed due to copyright restrictions.

To view image, visit http://www.museumwaalsdorp.nl/computer/ima ges/ibmcard.jpg

Produced by the WWW Virtual Punch-Card Server.

## So, that’s why text windows have 80 columns!

## Web resources on punched-card technology

- Doug Jones’s punched card index
- Biography of Herman Hollerith
- The 1890 U.S. Census
- Early history of IBM
- Pictures of Hollerith’s inventions
- Hollerith’s patent application (borrowed from Gordon Bell’s CyberMuseum)
- Impact of punched cards on U.S. history

# Introduction to Algorithms

6.046J/18.401J

- Randomized divide and conquer
- Analysis of expected time
- Worst-case linear-time order statistics
- Analysis

Prof. Erik Demaine

## Order statistics

Select the \(i\)th smallest of \(n\) elements (the element with **rank** \(i\)).

- \(i = 1\): **minimum**;
- \(i = n\): **maximum**;
- \(i = \lfloor (n+1)/2 \rfloor\) or \(\lceil (n+1)/2 \rceil\): **median**.

**Naive algorithm**: Sort and index \(i\)th element.
Worst-case running time = \(\Theta(n \lg n) + \Theta(1)\)
\(= \Theta(n \lg n)\),
using merge sort or heapsort (*not* quicksort).

