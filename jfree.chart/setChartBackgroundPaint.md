query: set the chart background paint

query source: https://stackoverflow.com/questions/36389172/difficulty-changing-background-colour-of-jfreechart

api: setChartBackgroundColor

manual code:
```
StandardChartTheme chartTheme = new StandardChartTheme("name", true);
chartTheme.setChartBackgroundPaint(new Color(0, 0, 0));
```

test case:
```
boolean test(StandardChartTheme theme, Paint paint) {
    return theme.getChartBackgroundPaint().equals(paint);
}
```

SnippSynth output:
```
concepts in query: [chart, paint]
Iterable pairs: []
Initial context:
1. TYPE:org.jfree.data.category.CategoryDataset NAME:v0
2. TYPE:org.jfree.data.general.PieDataset NAME:v1
3. TYPE:java.io.File NAME:v2
4. TYPE:java.awt.Paint NAME:v3

#Data flow graphs: 296
#Pattern: 1
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #METHOD_INVOCATION$setChartBackgroundPaint
Node 1: #METHOD_INVOCATION$setPlotBackgroundPaint
Node 2: #METHOD_INVOCATION$StandardChartTheme::<init>
Node 3: #DATA$StandardChartTheme
Node 4: #DATA$true
Node 5: #DATA$""
2 -> 0
2 -> 1
3 -> 2
4 -> 2
5 -> 2

Synthesized result:
org.jfree.chart.StandardChartTheme v5 = new StandardChartTheme("a", true);
v5.setChartBackgroundPaint(v3);
v5.setPlotBackgroundPaint(v3);

==========
Synthesis costs: 2.401s
```