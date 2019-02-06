query: number of days between two dates in Joda-time

query source: https://stackoverflow.com/questions/3802893/number-of-days-between-two-dates-in-joda-time?rq=1

core api: daysBetween

manual code:
```
DateTime dt1 = new DateTime();
DateTime dt2 = new DateTime();
Days days = Days.daysBetween(dt1.toInstant(), dt2.toInstant());
int num = days.getDays();
```

test case:
```
boolean test(Days ans) {
    return Days.daysBetween(new DateTime().toInstant(), new DateTime().toInstant()).getDays() == ans.getDays();
}
```

SnippSynth output:
```
concepts in query: [day, date]
Iterable pairs: []
Initial context:
1. TYPE:org.joda.time.DateTime NAME:v0

#Data flow graphs: 428
#Pattern: 3
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #METHOD_INVOCATION$toLocalDate
Node 1: #DATA$Days
Node 2: #METHOD_INVOCATION$getDays
Node 3: #METHOD_INVOCATION$daysBetween
Node 4: #METHOD_INVOCATION$toLocalDate
Node 5: #METHOD_INVOCATION$DateTime::<init>
Node 6: #DATA$DateTime
0 -> 3
1 -> 3
3 -> 2
4 -> 3
5 -> 4
6 -> 5

Synthesized result:
org.joda.time.Days v1 = new Days(1);
int v2 = v1.getDays();
Instant v3 = v0.toInstant();
org.joda.time.Days v4 = Days.daysBetween(v0, v0);
org.joda.time.LocalDate v4 = v0.toLocalDate();

=========
Node 0: #METHOD_INVOCATION$toLocalDate
Node 1: #METHOD_INVOCATION$toLocalDate
Node 2: #OP$RETURN
Node 3: #METHOD_INVOCATION$getDays
Node 4: #METHOD_INVOCATION$daysBetween
Node 5: #DATA$Days
0 -> 4
1 -> 4
3 -> 2
4 -> 3
5 -> 4

Synthesized result:
org.joda.time.Days v1 = new Days(1);
int v2 = v1.getDays();
Instant v3 = v0.toInstant();
org.joda.time.Days v4 = Days.daysBetween(v0, v0);
org.joda.time.LocalDate v4 = v0.toLocalDate();

=========
Node 0: #DATA$System
Node 1: #FIELD_ACCESS$out
Node 2: #METHOD_INVOCATION$println
Node 3: #METHOD_INVOCATION$getDays
Node 4: #METHOD_INVOCATION$daysBetween
Node 5: #DATA$Days
0 -> 1
1 -> 2
3 -> 2
4 -> 3
5 -> 4

Synthesized result:
Instant v1 = v0.toInstant();
org.joda.time.Days v2 = Days.daysBetween(v0, v0);
int v3 = v2.getDays();

==========
Synthesis costs: 1.797s
```