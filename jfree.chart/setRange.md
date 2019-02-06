query: set range for bar chart axis

query source: https://stackoverflow.com/questions/7231824/setting-range-for-x-y-axis-jfreechart

core api: setRange

manual code:
```
JFreeChart jfreechart = ChartFactory.createBarChart(
            title, "X", "Y", dataset);
CategoryPlot plot = jfreechart.getCategoryPlot();
ValueAxis range = plot.getRangeAxis();
range.setRange(0.0, 1.0);
```

test case:
```
boolean test(JFreeChart chart) {
    return !chart.getCategoryPlot().getRangeAxis().isAutoRange();
}
```

SnippSynth output:
```
concepts in query: [range, bar, chart, axis]
Iterable pairs: []
Initial context:
1. TYPE:org.jfree.data.category.CategoryDataset NAME:v0

#Data flow graphs: 81
#Pattern: 1
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$"Category"
Node 1: #DATA$"Score (%)"
Node 2: #DATA$PlotOrientation
Node 3: #FIELD_ACCESS$HORIZONTAL
Node 4: #DATA$ChartFactory
Node 5: #DATA$false
Node 6: #DATA$100.0
Node 7: #DATA$0.0
Node 8: #METHOD_INVOCATION$setRange
Node 9: #METHOD_INVOCATION$getRangeAxis
Node 10: #METHOD_INVOCATION$getCategoryPlot
Node 11: #METHOD_INVOCATION$createBarChart
Node 12: #DATA$true
0 -> 11
1 -> 11
2 -> 3
3 -> 11
4 -> 11
5 -> 11
6 -> 8
7 -> 8
9 -> 8
10 -> 9
11 -> 10
12 -> 11

Synthesized result:
org.jfree.chart.JFreeChart v3 = org.jfree.chart.ChartFactory.createBarChart("a", "a", "a", v0);
org.jfree.chart.plot.CategoryPlot v5 = v3.getCategoryPlot();
org.jfree.chart.axis.ValueAxis v6 = v5.getRangeAxis();
v6.setRange(0.0, 100.0);

==========
Synthesis costs: 1.175s
```