query: access the month in a year

query source: http://joda-time.sourceforge.net/quickstart.html

core api: getMonthOfYear

manual code:
```
DateTime dt = new DateTime();
Property month = dt.monthOfYear();
```

test case:
```
boolean test(Property m) {
    return m.get() == new DateTime().getMonthOfYear();
}
```

SnippSynth output:
```
concepts in query: [month, year]
Iterable pairs: []
Initial context: []

#Data flow graphs: 69
#Pattern: 4
Min pattern frequency: 6
Min pattern nodes num: 4
=========
Node 0: #DATA$YearMonth
Node 1: #METHOD_INVOCATION$monthOfYear
Node 2: #METHOD_INVOCATION$monthOfYear
Node 3: #METHOD_INVOCATION$monthOfYear
Node 4: #METHOD_INVOCATION$YearMonth::<init>
0 -> 4
4 -> 1
4 -> 2
4 -> 3

Synthesized result:
org.joda.time.DateTime v0 = new DateTime();
org.joda.time.DateTime.Property v1 = v0.monthOfYear();

=========
Node 0: #DATA$YearMonth
Node 1: #DATA$6
Node 2: #METHOD_INVOCATION$monthOfYear
Node 3: #METHOD_INVOCATION$monthOfYear
Node 4: #METHOD_INVOCATION$monthOfYear
Node 5: #METHOD_INVOCATION$YearMonth::<init>
Node 6: #DATA$1972
0 -> 5
1 -> 5
5 -> 2
5 -> 3
5 -> 4
6 -> 5

Synthesized result:
org.joda.time.DateTime v0 = new DateTime();
org.joda.time.DateTime.Property v1 = v0.monthOfYear();

=========
Node 0: #DATA$YearMonth
Node 1: #DATA$6
Node 2: #METHOD_INVOCATION$monthOfYear
Node 3: #METHOD_INVOCATION$monthOfYear
Node 4: #METHOD_INVOCATION$monthOfYear
Node 5: #METHOD_INVOCATION$monthOfYear
Node 6: #METHOD_INVOCATION$YearMonth::<init>
Node 7: #DATA$1972
0 -> 6
1 -> 6
6 -> 2
6 -> 3
6 -> 4
6 -> 5
7 -> 6

Synthesized result:
org.joda.time.DateTime v0 = new DateTime();
org.joda.time.DateTime.Property v1 = v0.monthOfYear();

=========
Node 0: #DATA$YearMonth
Node 1: #DATA$6
Node 2: #DATA$1972
Node 3: #METHOD_INVOCATION$monthOfYear
Node 4: #METHOD_INVOCATION$monthOfYear
Node 5: #METHOD_INVOCATION$monthOfYear
Node 6: #METHOD_INVOCATION$YearMonth::<init>
Node 7: #DATA$6
Node 8: #METHOD_INVOCATION$check
Node 9: #DATA$1972
0 -> 6
1 -> 6
2 -> 6
6 -> 3
6 -> 4
6 -> 5
6 -> 8
7 -> 8
9 -> 8

Synthesized result:
org.joda.time.DateTime v0 = new DateTime();
org.joda.time.DateTime.Property v1 = v0.monthOfYear();
BAD SYNTHESIS
org.joda.time.DateTime.Property v1 = v0.monthOfYear();

==========
Synthesis costs: 1.143s
```