
## Other Types of Mining
- **Text mining**: application of data mining to textual documents
  - cluster Web pages to find related pages
  - cluster pages a user has visited to organize their visit history
  - classify Web pages automatically into a Web directory
- **Data visualization** systems help users examine large volumes of data and detect patterns visually
  - Can visually encode large amounts of information on a single screen
  - Humans are very good at detecting visual patterns

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1162_0.png)

## End of Chapter

## Figure 20.01
data source 1

data source 2

data source n

data loaders

DBMS

data warehouse

query and analysis tools

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1163_0.png)

## Figure 20.02
![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1164_0.png)

## Figure 20.03
![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1165_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1167_0.png)

## Chapter 21: Information Retrieval

## Chapter 21: Information Retrieval
- Relevance Ranking Using Terms
- Relevance Using Hyperlinks
- Synonyms, Homonyms, and Ontologies
- Indexing of Documents
- Measuring Retrieval Effectiveness
- Web Search Engines
- Information Retrieval and Structured Data
- Directories

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1169_0.png)

## Information Retrieval Systems
- **Information retrieval (IR)** systems use a simpler data model than database systems
  - Information organized as a collection of documents
  - Documents are unstructured, no schema
- Information retrieval locates relevant documents, on the basis of user input such as keywords or example documents
  - e.g., find documents containing the words “database systems”
- Can be used even on textual descriptions provided with non-textual data such as images
- Web search engines are the most familiar example of IR systems

## Information Retrieval Systems (Cont.)
- Differences from database systems
  - IR systems don’t deal with transactional updates (including concurrency control and recovery)
  - Database systems deal with structured data, with schemas that define the data organization
  - IR systems deal with some querying issues not generally addressed by database systems
    - Approximate searching by keywords
    - Ranking of retrieved answers by estimated degree of relevance

## Keyword Search
- In **full text** retrieval, all the words in each document are considered to be keywords.
  - We use the word **term** to refer to the words in a document
- Information-retrieval systems typically allow query expressions formed using keywords and the logical connectives *and, or, and not*
  - *Ands* are implicit, even if not explicitly specified
- Ranking of documents on the basis of estimated relevance to a query is critical
  - Relevance ranking is based on factors such as
    - Term frequency
      - Frequency of occurrence of query keyword in document
    - Inverse document frequency
      - How many documents the query keyword occurs in
        - Fewer ➔ give more importance to keyword
    - Hyperlinks to documents
      - More links to a document ➔ document is more important

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1171_0.png)

## Relevance Ranking Using Terms
![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1172_0.png)

- TF-IDF (Term frequency/Inverse Document frequency) ranking:
- Let n(d) = number of terms in the document d
- n(d, t) = number of occurrences of term t in the document d.
- Relevance of a document d to a term t

```
TF(d, t) = log (1 + n(d,t)/n(d))
```

The log factor is to avoid excessive weight to frequent terms

- Relevance of document to query Q

```
r(d, Q) = \sum_{t \in Q} \frac{TF(d,t)}{n(t)}
```
