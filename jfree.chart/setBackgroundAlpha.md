query: set transparency of chart background

query source: http://www.jfree.org/jfreechart/api/javadoc/org/jfree/chart/plot/Plot.html#setBackgroundAlpha-float-

core api: setBackgroundAlpha

manual code:
```
JFreeChart jfreechart = ChartFactory.createPieChart(
    "title", pieDataset);
CategoryPlot plot = jfreechart.getPlot();
plot.setBackgroundAlpha(0.5);
```

test case:
```
boolean test(JFreeChart chart) {
    // 1.0 is the default value of alpha
    return chart.getPlot().getBackgroundAlpha() != 1.0;
}
```

SnippSynth output:
```
concepts in query: []
Iterable pairs: []
Initial context:
TYPE:org.jfree.data.category.CategoryDataset NAME:v0
TYPE:org.jfree.data.general.PieDataset NAME:v1

#Data flow graphs: 645
#Pattern: 3
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$PlotOrientation
Node 1: #FIELD_ACCESS$VERTICAL
Node 2: #DATA$ChartFactory
Node 3: #DATA$false
Node 4: #DATA$0.5
Node 5: #METHOD_INVOCATION$setForegroundAlpha
Node 6: #DATA$0.5
Node 7: #METHOD_INVOCATION$setBackgroundAlpha
Node 8: #METHOD_INVOCATION$getPlot
Node 9: #OP$RETURN
Node 10: #METHOD_INVOCATION$createLineChart
Node 11: #DATA$true
0 -> 1
1 -> 10
2 -> 10
3 -> 10
4 -> 5
8 -> 5
6 -> 7
8 -> 7
10 -> 8
10 -> 9
11 -> 10

Synthesized result:
String v5 = org.jfree.chart.ui.Layer.BACKGROUND.toString();
org.jfree.chart.JFreeChart v6 = org.jfree.chart.ChartFactory.createLineChart(v5, v5, v5, v0);
org.jfree.chart.plot.Plot v7 = v6.getPlot();
v7.setBackgroundAlpha(0.0);
v7.setForegroundAlpha(0.0);

=========
Node 0: #DATA$ChartFactory
Node 1: #DATA$0.5
Node 2: #METHOD_INVOCATION$setForegroundAlpha
Node 3: #METHOD_INVOCATION$setBackgroundAlpha
Node 4: #METHOD_INVOCATION$getPlot
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$createPieChart3D
Node 7: #DATA$true
0 -> 6
1 -> 2
4 -> 2
4 -> 3
6 -> 4
6 -> 5
7 -> 6

Synthesized result:
String v5 = org.jfree.chart.ui.Layer.BACKGROUND.toString();
org.jfree.chart.JFreeChart v6 = org.jfree.chart.ChartFactory.createPieChart3D(v5, v1);
org.jfree.chart.plot.Plot v7 = v6.getPlot();
v7.setBackgroundAlpha(0.0);
v7.setForegroundAlpha(0.0);

=========
Node 0: #DATA$ChartFactory
Node 1: #DATA$false
Node 2: #METHOD_INVOCATION$setBackgroundAlpha
Node 3: #METHOD_INVOCATION$getPlot
Node 4: #METHOD_INVOCATION$createPieChart
Node 5: #DATA$true
0 -> 4
1 -> 4
3 -> 2
4 -> 3
5 -> 4

Synthesized result:
String v4 = org.jfree.chart.ui.Layer.BACKGROUND.toString();
org.jfree.chart.JFreeChart v5 = org.jfree.chart.ChartFactory.createPieChart(v4, v1);
org.jfree.chart.plot.Plot v6 = v5.getPlot();
v6.setBackgroundAlpha(0.0);

==========
Synthesis costs: 8.369s
```