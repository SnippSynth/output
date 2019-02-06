query: Converting "14/02/2018 13:14" to a DateTime object using Joda Time library

query source: https://stackoverflow.com/questions/6252678/converting-a-date-string-to-a-datetime-object-using-joda-time-library

core api: parseDateTime

manual code:
```
DateTimeFormatter formatter = DateTimeFormat.forPattern("dd/MM/yyyy HH:mm");
DateTime dt = formatter.parseDateTime("14/02/2018 13:14");
```

test case:
```
boolean test(DateTime dt) {
    boolean d = dt.getDayOfMonth() == 14;
    boolean m = dt.getMonthOfYear() == 2;
    boolean y = dt.getYear() == 2018;
    boolean h = dt.getHourOfDay() == 13;
    boolean min = dt.getMinuteOfHour() == 14;
    return d && m && y && h && min;
}
```

SnippSynth output:
```
concepts in query: [day, date]
Iterable pairs: []
Initial context:
1. TYPE:org.joda.time.DateTime NAME:v0

#Data flow graphs: 161
#Pattern: 2
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$stringDateTime
Node 1: #DATA$"dd/MM/yyyy HH:mm"
Node 2: #DATA$DateTimeFormat
Node 3: #METHOD_INVOCATION$forPattern
Node 4: #OP$RETURN
Node 5: #METHOD_INVOCATION$parseDateTime
0 -> 5
1 -> 3
2 -> 3
3 -> 5
5 -> 4

Synthesized result:
org.joda.time.format.DateTimeFormatter v1 = DateTimeFormat.forPattern("dd/MM/yyyy HH:mm")
v0 = v1.parseDateTime("14/02/2018 13:14");

=========
Node 0: #DATA$DateTimeFormat
Node 1: #METHOD_INVOCATION$forPattern
Node 2: #DATA$System
Node 3: #FIELD_ACCESS$out
Node 4: #METHOD_INVOCATION$println
Node 5: #METHOD_INVOCATION$parseDateTime
0 -> 1
1 -> 5
2 -> 3
3 -> 4
5 -> 4

Synthesized result:
org.joda.time.format.DateTimeFormatter v1 = DateTimeFormat.forPattern("14/02/2018 13:14");
v0 = v1.parseDateTime("14/02/2018 13:14");
org.joda.time.format.DateTimeFormatter v3 = org.joda.time.format.DateTimeFormat.forPattern("14/02/2018 13:14");

==========
Synthesis costs: 5.9s
```