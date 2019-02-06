query: parse "example query"

query source: http://www.lucenetutorial.com/lucene-in-5-minutes.html

core api: org.apache.lucene.queryparser.classic.QueryParser.parse

manual code:
```
String str = "example query";
Query q = new QueryParser(str, analyzer).parse(str);
```

test case:
```
boolean test(Query q) {
    return q.toString().equals(
        "example query:example example query:query");
}
```

SnippSynth output:
```
concepts in query: []
Iterable pairs: []
Initial context:
1. TYPE:org.apache.lucene.analysis.Analyzer NAME:v0
2. TYPE:org.apache.lucene.search.IndexSearcher NAME:v1
3. TYPE:String NAME:"example query"

#Data flow graphs: 351
#Pattern: 4
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #METHOD_INVOCATION$copyToStringFromClasspath
Node 1: #DATA$MapperTests
Node 2: #METHOD_INVOCATION$newParser
Node 3: #METHOD_INVOCATION$copyToBytesFromClasspath
Node 4: #METHOD_INVOCATION$rootDoc
Node 5: #METHOD_INVOCATION$parse
Node 6: #METHOD_INVOCATION$parse
0 -> 6
1 -> 2
2 -> 6
3 -> 5
5 -> 4
6 -> 5

Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v3 = new QueryParser("example query", v0);
try {
org.apache.lucene.search.Query v4 = v3.parse("example query");
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$QueryParser
Node 1: #METHOD_INVOCATION$QueryParser::<init>
Node 2: #DATA$IndexSearcher
Node 3: #METHOD_INVOCATION$IndexSearcher::<init>
Node 4: #METHOD_INVOCATION$search
Node 5: #METHOD_INVOCATION$parse
0 -> 1
1 -> 5
2 -> 3
3 -> 4
5 -> 4
Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v3 = new QueryParser("example query", v0);
try {
org.apache.lucene.search.Query v4 = v3.parse("example query");
int v5 = v1.count(v4);
org.apache.lucene.search.TopDocs v6 = v1.search(v4, v5);
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$parser
Node 1: #DATA$Long
Node 2: #METHOD_INVOCATION$time
Node 3: #METHOD_INVOCATION$time
Node 4: #METHOD_INVOCATION$assertRange
Node 5: #METHOD_INVOCATION$parse
0 -> 5
1 -> 4
2 -> 4
3 -> 4
5 -> 4
Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v3 = new QueryParser("example query", v0);
try {
org.apache.lucene.search.Query v4 = v3.parse("example query");
BAD SYNTHESIS
BAD SYNTHESIS
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$analyzer
Node 1: #DATA$QueryParser
Node 2: #METHOD_INVOCATION$parse
Node 3: #METHOD_INVOCATION$QueryParser::<init>
Node 4: #FIELD_ACCESS$LUCENE_35
Node 5: #DATA$Version
0 -> 3
1 -> 3
3 -> 2
4 -> 3
5 -> 4
Synthesized result:
org.apache.lucene.queryparser.classic.QueryParser v3 = new QueryParser("example query", v0);
try {
org.apache.lucene.search.Query v4 = v3.parse("example query");
} catch(Exception e) {
e.printStackTrace();
}

==========
Synthesis costs: 7.172s
```