---
chapter: 83
start: 382
end: 387
type: sub-chapter
read: true
---
> The term **information retrieval** generally refers to the querying of unstructured textual data.
> Textual data is traditionally organized into *documents*.
> In a DB any text-valued attributed can be considered *documents*, while in the context of the web, each web page can be considered a *document*

## Keyword queries
The simplest form of an information-retrieval system would be locating and returning all documents that contain all the keyword in the query. Adding relevance of documents to a query makes it more-sophisticated.

Web search engines are at core information retrieval systems.

### Relevance Ranking
Returns only a few judged as relevant not the thousands evaluated. Not an exact science but there are some well-accepted approaches.

#### Ranking Using TF-IDF
**Term** - refers to a keyword occurring in a document.

One approach is to deem the documents with more occurrences as more relevant. This does not consider the length of the document and 10 occurrences might not be 10 times more relevant.

One way of measuring **term frequency (TF)**

$TF(d, t) = log ( 1 + \frac{n(d, t)}{n(d)} )$

Furthermore more relevance can be given to terms in titles, or early in documents...

If we query for "database Silberschatz" and the term database is more frequent; documents that match "Silberschatz" but not "database" should rank higher than those that do the opposite. For this we use **inverse document frequency (IDF)**

$IDF(t) = \frac{1}{n(t)}$

$n(t)$ - number of documents that contain term *t*.

Finally the relevance of a document *d* to a query *Q* is:

$r(d, Q) = ∑_{t∈Q} TF(d, t) ∗ IDF(t)$

Adding weights to terms *w(t)* is done by simply multiplying $TF(T)$ with $w(t)$.

This above is the **TF-IDF** approach.
**Stop words** - 100 or so most common words that are ignored when indexing documents.
**Proximity** - If multiple provided terms appear close to each other in the document they rank higher.
#### Ranking Using Hyperlinks
Documents linked from many other documents are considered more important.

Google provides **PageRank** as a measure of popularity of a page based on the popularity of the pages that link to that page.

First web pages are given integer identifiers. The jump probability matrix $T$ is defined with $T[i,j]$ set to the probability that a random walker who is following a link out of page $i$ follows the link to page $j$. Each link having equal probability to be followed $T[i,j] = 1/N$, $N_i$ the number of links out of page $i$.

$P[j] = δ∕N + (1 − δ) ∗ \sum^{N}_{i=1} (T[i, j] ∗ P[i])$

$δ$ - constant between 0 and 1 (usually 0.15)
$N$ - Number of pages

More things are usually used to rank popularity. How often a site is visited, how frequently users click on a page when it is returned...

## Measuring Retrieval Effectiveness
Ranking of results is not an exact science. Two metrics are used to emasure how well an information-retrieval system is able to answer queries.
**Precision** - measures what percentage of the retrieved documents are actually relevant to the query.
**Recall** - the percentage of the documents relevant to the query that were retrieved.

Search engines usually find a large number of answers but users only look at 10 or 20 thus the measuring of precision@10 or recall@20 (examples).

## Keyword Querying on Structured Data and Knowledge graphs
Used instead of structured query languages (SQL) when the user does not know the exact schema and does not wish to take the effort to write SQL.

This is done by displaying tuples as a knowledge graph and find matches within it.

Another practical use is in combination with textual information. Querying "Stonebraker developed PostgreSQL" may infer the database researcher "Michael Stonebraker" and annotated by linking the word Stonebraker to the entity "Michael Stonebraker". The knowledge graph may also record that he won a Turing award. Now querying "Turing award PostgreSQL" can be answered using both information from the document and the knowledge graph.