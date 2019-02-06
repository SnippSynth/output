query: create a Searcher to search using the Query

query source: http://www.lucenetutorial.com/lucene-in-5-minutes.html

core api: search

manual code:
```
int hitsPerPage = 10;
Directory index = new RAMDirectory();
IndexReader reader = DirectoryReader.open(index);
IndexSearcher searcher = new IndexSearcher(reader);
TopDocs docs = searcher.search(q, hitsPage);
ScoreDoc[] hits = docs.scoreDocs;
```

test case:
```
bool test(TopDocs docs) {
    return docs instanceof TopDocs;
}
```

SnippSynth output:
```
concepts in query: []
Iterable pairs: []
Initial context:
1. TYPE:org.apache.lucene.analysis.Analyzer NAME:v0
2. TYPE:org.apache.lucene.search.Query NAME:v1
3. TYPE:org.apache.lucene.index.IndexReader NAME:v2

#Data flow graphs: 231
#Pattern: 4
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$IndexSearcher
Node 1: #DATA$SearchQueryParser
Node 2: #DATA$Lucene
Node 3: #METHOD_INVOCATION$getPerFieldAnalyzer
Node 4: #DATA$Lucene
Node 5: #FIELD_ACCESS$LUCENE_VERSION
Node 6: #METHOD_INVOCATION$SearchQueryParser::<init>
Node 7: #METHOD_INVOCATION$parse
Node 8: #METHOD_INVOCATION$search
Node 9: #METHOD_INVOCATION$IndexSearcher::<init>
0 -> 9
1 -> 6
2 -> 3
3 -> 6
4 -> 5
5 -> 6
6 -> 7
7 -> 8
9 -> 8

Synthesized result:
org.apache.lucene.search.IndexSearcher v4 = new IndexSearcher(v2);
int v5 = v2.numDeletedDocs();
org.apache.lucene.search.TopDocs v6 = v4.search(v1, v5);
org.apache.lucene.queryparser.classic.QueryParser v7 = new QueryParser("a", v0);
String v8 = v1.toString();
try {
org.apache.lucene.search.Query v9 = v7.parse(v8);
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #METHOD_INVOCATION$hasNext
Node 1: #METHOD_INVOCATION$doc
Node 2: #FIELD_ACCESS$doc
Node 3: #METHOD_INVOCATION$next
Node 4: #METHOD_INVOCATION$iterator
Node 5: #FIELD_ACCESS$scoreDocs
Node 6: #METHOD_INVOCATION$search
4 -> 0
2 -> 1
3 -> 2
4 -> 3
5 -> 4
6 -> 5

Synthesized result:
org.apache.lucene.search.IndexSearcher v5 = new IndexSearcher(v2);
int v6 = v2.numDeletedDocs();
org.apache.lucene.search.TopDocs v7 = v5.search(v1, v6);
org.apache.lucene.document.Document v8 = v5.doc(v6);

=========
Node 0: #METHOD_INVOCATION$open
Node 1: #DATA$IndexSearcher
Node 2: #FIELD_ACCESS$doc
Node 3: #METHOD_INVOCATION$get
Node 4: #METHOD_INVOCATION$doc
Node 5: #METHOD_INVOCATION$search
Node 6: #METHOD_INVOCATION$IndexSearcher::<init>
0 -> 6
1 -> 6
2 -> 4
4 -> 3
6 -> 4
6 -> 5

Synthesized result:
org.apache.lucene.document.Document v5 = v2.document(1);
org.apache.lucene.index.IndexableField v6 = v5.getField("a");
java.io.Reader v7 = v6.readerValue();
org.apache.lucene.analysis.ja.dict.UserDictionary v8 = org.apache.lucene.analysis.ja.dict.UserDictionary.open(v7);
org.apache.lucene.search.IndexSearcher v9 = new IndexSearcher(v2);
int v10 = v2.numDeletedDocs();
org.apache.lucene.search.TopDocs v11 = v9.search(v1, v10);
org.apache.lucene.document.Document v12 = v9.doc(v10);
org.apache.lucene.analysis.ja.JapaneseTokenizer.WrappedPositionArray v12 = new WrappedPositionArray();
org.apache.lucene.analysis.ja.JapaneseTokenizer.Position v13 = v12.get(v10);

=========
Node 0: #DATA$IndexSearcher
Node 1: #DATA$QueryParser
Node 2: #METHOD_INVOCATION$QueryParser::<init>
Node 3: #METHOD_INVOCATION$parse
Node 4: #METHOD_INVOCATION$search
Node 5: #METHOD_INVOCATION$IndexSearcher::<init>
Node 6: #DATA$10
0 -> 5
1 -> 2
2 -> 3
3 -> 4
5 -> 4

Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v4 = new QueryParser("a", v0);
String v5 = v1.toString();
try {
org.apache.lucene.search.Query v1 = v4.parse(v5);
org.apache.lucene.search.IndexSearcher v6 = new IndexSearcher(v2);
org.apache.lucene.search.TopDocs v8 = v6.search(v6, 10);
} catch(Exception e) {
e.printStackTrace();
}

==========
Synthesis costs: 1.901s
```