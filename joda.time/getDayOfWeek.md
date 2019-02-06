query: get week days with jodatime

query source: https://stackoverflow.com/questions/15338196/joda-time-get-week-days

core api: getDayOfWeek

manual code:
```
LocalDate date = new LocalDate();
return date.getDayOfWeek();
```

test case:
```
boolean test(int d) {
    return d == new LocalDate().getDayOfWeek();
}
```

SnippSynth output:
```
concepts in query: [week, day]
Iterable pairs: []
Initial context:
1. TYPE:org.joda.time.DateTime NAME:v0

#Data flow graphs: 346
#Pattern: 5
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$"/Jan/2004"
Node 1: #DATA$t
Node 2: #DATA$0
Node 3: #METHOD_INVOCATION$getChild
Node 4: #METHOD_INVOCATION$getText
Node 5: #DATA$SIMPLE_DATE_FORMAT
Node 6: #DATA$LocalDate
Node 7: #METHOD_INVOCATION$getDayOfWeek
Node 8: #METHOD_INVOCATION$LocalDate::<init>
Node 9: #METHOD_INVOCATION$parse
Node 10: #BINARY$+
0 -> 10
1 -> 3
2 -> 3
3 -> 4
4 -> 10
5 -> 9
6 -> 8
8 -> 7
9 -> 8
10 -> 9

Synthesized result:
org.joda.time.DateTime.Property v1 = v0.dayOfMonth();
org.joda.time.DateTimeField v2 = v1.getField();
String v3 = v2.getAsText(1);
org.joda.time.DateTime v4 = org.joda.time.DateTime.parse(v3);
org.joda.time.LocalDate v4 = new LocalDate();
int v5 = v4.getDayOfWeek();

=========
Node 0: #DATA$1
Node 1: #FIELD_ACCESS$number
Node 2: #DATA$dayOfWeek
Node 3: #DATA$cm
Node 4: #FIELD_ACCESS$year
Node 5: #DATA$LocalDate
Node 6: #DATA$cm
Node 7: #FIELD_ACCESS$month
Node 8: #DATA$1
Node 9: #DATA$cm
Node 10: #METHOD_INVOCATION$addEvent
Node 11: #DATA$1
Node 12: #DATA$cm
Node 13: #FIELD_ACCESS$month
Node 14: #BINARY$==
Node 15: #METHOD_INVOCATION$getMonthOfYear
Node 16: #METHOD_INVOCATION$plusDays
Node 17: #METHOD_INVOCATION$LocalDate::<init>
Node 18: #METHOD_INVOCATION$getDayOfWeek
Node 19: #BINARY$==
Node 20: #BINARY$&&
Node 21: #BINARY$==
Node 22: #OP$ASSIGNMENT
Node 23: #BINARY$+
Node 24: #DATA$1
0 -> 22
1 -> 21
2 -> 19
3 -> 4
4 -> 17
5 -> 17
6 -> 7
7 -> 17
8 -> 17
9 -> 10
17 -> 10
11 -> 16
12 -> 13
13 -> 14
15 -> 14
16 -> 15
17 -> 16
17 -> 18
18 -> 19
19 -> 20
21 -> 20
22 -> 21
22 -> 23
24 -> 23

Synthesized result:
org.joda.time.LocalDate v1 = new LocalDate();
int v2 = v1.getDayOfWeek();
org.joda.time.LocalDate v3 = v3.plusDays(v2);
int v3 = v3.getMonthOfYear();

=========
Node 0: #DATA$cm
Node 1: #FIELD_ACCESS$year
Node 2: #DATA$LocalDate
Node 3: #DATA$cm
Node 4: #FIELD_ACCESS$month
Node 5: #DATA$cm
Node 6: #METHOD_INVOCATION$addEvent
Node 7: #DATA$null
Node 8: #OP$ASSIGNMENT
Node 9: #OP$PHI
Node 10: #OP$PHI
Node 11: #DATA$dayOfWeek
Node 12: #BINARY$==
Node 13: #METHOD_INVOCATION$getDayOfWeek
Node 14: #METHOD_INVOCATION$LocalDate::<init>
Node 15: #DATA$cm
Node 16: #FIELD_ACCESS$month
Node 17: #BINARY$==
Node 18: #METHOD_INVOCATION$getMonthOfYear
Node 19: #METHOD_INVOCATION$plusDays
Node 20: #DATA$1
0 -> 1
1 -> 14
2 -> 14
3 -> 4
4 -> 14
5 -> 6
10 -> 6
7 -> 8
8 -> 9
9 -> 10
10 -> 9
14 -> 10
11 -> 12
13 -> 12
14 -> 13
14 -> 19
15 -> 16
16 -> 17
18 -> 17
19 -> 18
20 -> 19

Synthesized result:
org.joda.time.LocalDate v1 = new LocalDate(1, 1, 1);
int v2 = v1.getDayOfWeek();
org.joda.time.LocalDate v3 = v3.plusDays(v2);
int v3 = v3.getMonthOfYear();

=========
Node 0: #DATA$"/"
Node 1: #DATA$t
Node 2: #METHOD_INVOCATION$getChild
Node 3: #METHOD_INVOCATION$getText
Node 4: #DATA$t
Node 5: #METHOD_INVOCATION$getChild
Node 6: #METHOD_INVOCATION$getText
Node 7: #DATA$"/2004"
Node 8: #DATA$SIMPLE_DATE_FORMAT
Node 9: #DATA$LocalDate
Node 10: #METHOD_INVOCATION$getMonthOfYear
Node 11: #METHOD_INVOCATION$getDayOfWeek
Node 12: #METHOD_INVOCATION$LocalDate::<init>
Node 13: #METHOD_INVOCATION$parse
Node 14: #BINARY$+
Node 15: #BINARY$+
Node 16: #BINARY$+
0 -> 16
1 -> 2
2 -> 3
3 -> 16
4 -> 5
5 -> 6
6 -> 15
7 -> 14
8 -> 13
9 -> 12
12 -> 10
12 -> 11
13 -> 12
14 -> 13
15 -> 14
16 -> 15

Synthesized result:
org.joda.time.DateTime.Property v1 = v0.dayOfMonth();
org.joda.time.DateTimeField v2 = v1.getField();
String v3 = v2.getAsText(1);
org.joda.time.DateTime v4 = org.joda.time.DateTime.parse(v3);
org.joda.time.LocalDate v4 = new LocalDate(1, 1, 1);
int v5 = v4.getDayOfWeek();
int v6 = v4.getMonthOfYear();

=========
Node 0: #DATA$"/Jan/2004"
Node 1: #DATA$t
Node 2: #DATA$1
Node 3: #METHOD_INVOCATION$getChild
Node 4: #METHOD_INVOCATION$getText
Node 5: #DATA$SIMPLE_DATE_FORMAT
Node 6: #DATA$LocalDate
Node 7: #METHOD_INVOCATION$getDayOfWeek
Node 8: #METHOD_INVOCATION$LocalDate::<init>
Node 9: #METHOD_INVOCATION$parse
Node 10: #BINARY$+
0 -> 10
1 -> 3
2 -> 3
3 -> 4
4 -> 10
5 -> 9
6 -> 8
8 -> 7
9 -> 8
10 -> 9

Synthesized result:
org.joda.time.DateTime.Property v1 = v0.dayOfMonth();
org.joda.time.DateTimeField v2 = v1.getField();
String v3 = v2.getAsText(1);
org.joda.time.DateTime v4 = org.joda.time.DateTime.parse(v3);
org.joda.time.LocalDate v4 = new LocalDate(1, 1, 1);
int v5 = v4.getDayOfWeek();

==========
Synthesis costs: 13.367s
```