query: check if a year is a leap year

query source: https://kodejava.org/how-do-i-check-if-a-year-is-a-leap-year

core api: isLeap

manual code:
```
DateTime dt = new DateTime();
return dt.year().isLeap();
```

test case:
```
boolean test(boolean ans) {
    return ans == new DateTime().year().isLeap();
}
```

SnippSynth output:
```
concepts in query: [year]
Iterable pairs: []
Initial context:
1. TYPE:org.joda.time.DateTime NAME:v0

#Data flow graphs: 725
#Pattern: 5
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$instant
Node 1: #DATA$29
Node 2: #DATA$instant
Node 3: #METHOD_INVOCATION$get
Node 4: #BINARY$==
Node 5: #OP$RETURN
Node 6: #BINARY$&&
Node 7: #METHOD_INVOCATION$isLeap
Node 8: #METHOD_INVOCATION$monthOfYear
Node 9: #DATA$iChronology
0 -> 7
1 -> 4
2 -> 3
3 -> 4
4 -> 6
6 -> 5
7 -> 6
8 -> 7
9 -> 8

Synthesized result:
org.joda.time.DateTime.Property v2 = v0.year();
org.joda.time.DateTimeField v3 = v2.getField();
int v4 = v3.get(v1);
boolean v5 = v2.isLeap();
org.joda.time.DateTimeFieldType v6 = org.joda.time.DateTimeFieldType.monthOfYear();

=========
Node 0: #DATA$year
Node 1: #DATA$DateTime
Node 2: #DATA$0
Node 3: #DATA$0
Node 4: #DATA$1
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$isLeap
Node 7: #METHOD_INVOCATION$year
Node 8: #METHOD_INVOCATION$DateTime::<init>
Node 9: #DATA$1
0 -> 8
1 -> 8
2 -> 8
3 -> 8
4 -> 8
6 -> 5
7 -> 6
8 -> 7
9 -> 8

Synthesized result:
org.joda.time.DateTime.Property v2 = v0.yearOfEra();
boolean v3 = v2.isLeap();
org.joda.time.DateTimeFieldType v4 = org.joda.time.DateTimeFieldType.year();

=========
Node 0: #DATA$DateTime
Node 1: #METHOD_INVOCATION$roundFloorCopy
Node 2: #METHOD_INVOCATION$dayOfMonth
Node 3: #METHOD_INVOCATION$isLeap
Node 4: #METHOD_INVOCATION$year
Node 5: #METHOD_INVOCATION$getAsShortText
Node 6: #METHOD_INVOCATION$monthOfYear
Node 7: #METHOD_INVOCATION$DateTime::<init>
Node 8: #METHOD_INVOCATION$getAsText
Node 9: #METHOD_INVOCATION$monthOfYear
0 -> 7
2 -> 1
7 -> 2
4 -> 3
7 -> 4
6 -> 5
7 -> 6
7 -> 9
9 -> 8

Synthesized result:
org.joda.time.DateTime.Property v2 = v0.dayOfMonth();
org.joda.time.DateTimeField v3 = v2.getField();
String v4 = v3.getAsText(v1);
org.joda.time.DateTimeFieldType v5 = org.joda.time.DateTimeFieldType.monthOfYear();
String v6 = v3.getAsShortText(v1);
org.joda.time.DateTimeFieldType v6 = org.joda.time.DateTimeFieldType.monthOfYear();
boolean v6 = v2.isLeap();
org.joda.time.DateTimeFieldType v7 = org.joda.time.DateTimeFieldType.year();
org.joda.time.DateTime v7 = v2.roundFloorCopy();
org.joda.time.DateTimeFieldType v7 = org.joda.time.DateTimeFieldType.dayOfMonth();

=========
Node 0: #DATA$millis
Node 1: #DATA$365
Node 2: #DATA$366
Node 3: #OP$RETURN
Node 4: #OP$CONDITION_EXPR
Node 5: #METHOD_INVOCATION$isLeap
Node 6: #METHOD_INVOCATION$year
Node 7: #DATA$iChronology
0 -> 5
1 -> 4
2 -> 4
4 -> 3
5 -> 4
6 -> 5
7 -> 6

Synthesized result:
org.joda.time.DateTime.Property v2 = v0.yearOfEra();
boolean v3 = v2.isLeap();
org.joda.time.DateTimeFieldType v4 = org.joda.time.DateTimeFieldType.year();

=========
Node 0: #DATA$arg0
Node 1: #DATA$DateTime
Node 2: #METHOD_INVOCATION$now
Node 3: #METHOD_INVOCATION$withWeekyear
Node 4: #METHOD_INVOCATION$year
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$isLeap
0 -> 3
1 -> 2
2 -> 3
3 -> 4
4 -> 6
6 -> 5

Synthesized result:
org.joda.time.DateTime v2 = org.joda.time.DateTime.now();
org.joda.time.DateTime.Property v2 = v2.year();
org.joda.time.DateTimeField v3 = v2.getField();
int v4 = v3.getLeapAmount(v1);
org.joda.time.DateTime v5 = v5.withWeekyear(v4);
org.joda.time.DateTimeFieldType v5 = org.joda.time.DateTimeFieldType.year();
boolean v6 = v2.isLeap();

==========
Synthesis costs: 2.063s
```