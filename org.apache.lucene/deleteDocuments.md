query: Deletes the document(s) matching the provided query

query source: https://lucene.apache.org/core/6_0_1/core/org/apache/lucene/index/IndexWriter.html#deleteDocuments-org.apache.lucene.index.Term...-

core api: deleteDocuments

manual code:
```
try {
    indexWriter.deleteDocuments(query);
} catch (CorruptIndexException e) {
    // exception handle
}
```

test case:
```
manually judge the correctness
```

SnippSynth output:
```
concepts in query: []
Iterable pairs: []
Initial context:
1. TYPE:org.apache.lucene.analysis.Analyzer NAME:v0
2. TYPE:org.apache.lucene.search.IndexSearcher NAME:v1
3. TYPE:org.apache.lucene.document.Document NAME:v2
4. TYPE:org.apache.lucene.index.IndexWriter NAME:v3

#Data flow graphs: 1352
#Pattern: 3
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$QueryParser
Node 1: #DATA$indexWriter
Node 2: #METHOD_INVOCATION$getAnalyzer
Node 3: #METHOD_INVOCATION$QueryParser::<init>
Node 4: #METHOD_INVOCATION$parse
Node 5: #METHOD_INVOCATION$deleteDocuments
Node 6: #DATA$indexWriter
0 -> 3
1 -> 2
2 -> 3
3 -> 4
4 -> 5
6 -> 5

Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v4 = new QueryParser("a", v0);
String v5 = v1.toString();
try {
org.apache.lucene.search.Query v6 = v4.parse(v5);
org.apache.lucene.index.IndexWriterConfig v7 = new IndexWriterConfig(v0);
org.apache.lucene.analysis.Analyzer v8 = v7.getAnalyzer();
long v8 = v3.deleteDocuments(v6);
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$"otype"
Node 1: #DATA$VERSION
Node 2: #DATA$QueryParser
Node 3: #METHOD_INVOCATION$deleteDocuments
Node 4: #METHOD_INVOCATION$parse
Node 5: #METHOD_INVOCATION$QueryParser::<init>
Node 6: #METHOD_INVOCATION$getAnalyzer
0 -> 5
1 -> 5
2 -> 5
4 -> 3
5 -> 4
6 -> 5

Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v4 = new QueryParser("a", v0);
String v5 = v1.toString();
try {
org.apache.lucene.search.Query v6 = v4.parse(v5);
org.apache.lucene.index.IndexWriterConfig v7 = new IndexWriterConfig(v0);
org.apache.lucene.analysis.Analyzer v8 = v7.getAnalyzer();
long v8 = v3.deleteDocuments(v6);
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$QueryParser
Node 1: #METHOD_INVOCATION$getAnalyzer
Node 2: #METHOD_INVOCATION$QueryParser::<init>
Node 3: #METHOD_INVOCATION$deleteDocuments
Node 4: #METHOD_INVOCATION$parse
Node 5: #BINARY$+
0 -> 2
1 -> 2
2 -> 4
4 -> 3
5 -> 4

Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v4 = new QueryParser("a", v0);
String v5 = v1.toString();
try {
org.apache.lucene.search.Query v6 = v4.parse(v5);
org.apache.lucene.index.IndexWriterConfig v7 = new IndexWriterConfig(v0);
org.apache.lucene.analysis.Analyzer v8 = v7.getAnalyzer();
long v8 = v3.deleteDocuments(v6);
} catch(Exception e) {
e.printStackTrace();
}

==========
Synthesis costs: 25.553s
```