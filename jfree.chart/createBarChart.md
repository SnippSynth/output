query: create bar chart with database using JfreeChart

query source: https://stackoverflow.com/questions/29895005/create-bar-chart-with-database-values-using-jfreechart

core api: createBarChart

manual code:
```
JFreeChart chart = ChartFactory.createBarChart("title", "X", "Y", dataset);
```

test case:
```
boolean test(JFreeChart chart) {
    return chart.getPlot() instanceof CategoryPlot;
}
```

SnippSynth output:
```
concepts in query: [bar, chart]
Iterable pairs: []
Initial context:
1. TYPE:org.jfree.data.category.CategoryDataset NAME:v0
2. TYPE:org.jfree.data.general.PieDataset NAME:v1
3. TYPE:java.io.File NAME:v2

#Data flow graphs: 199
#Pattern: 4
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$PlotOrientation
Node 1: #FIELD_ACCESS$VERTICAL
Node 2: #DATA$ChartFactory
Node 3: #DATA$false
Node 4: #DATA$true
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$createBarChart
Node 7: #DATA$true
0 -> 1
1 -> 6
2 -> 6
3 -> 6
4 -> 6
6 -> 5
7 -> 6

Synthesized result:
org.jfree.chart.JFreeChart v4 = org.jfree.chart.ChartFactory.createBarChart("a", "a", "a", v0);

=========
Node 0: #DATA$dataset
Node 1: #DATA$PlotOrientation
Node 2: #FIELD_ACCESS$VERTICAL
Node 3: #DATA$ChartFactory
Node 4: #DATA$false
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$createBarChart
Node 7: #DATA$true
0 -> 6
1 -> 2
2 -> 6
3 -> 6
4 -> 6
6 -> 5
7 -> 6

Synthesized result:
org.jfree.chart.JFreeChart v4 = org.jfree.chart.ChartFactory.createBarChart("a", "a", "a", v0);

=========
Node 0: #METHOD_INVOCATION$createDataset
Node 1: #DATA$ChartPanel
Node 2: #DATA$Dimension
Node 3: #METHOD_INVOCATION$Dimension::<init>
Node 4: #METHOD_INVOCATION$setPreferredSize
Node 5: #METHOD_INVOCATION$setContentPane
Node 6: #METHOD_INVOCATION$ChartPanel::<init>
Node 7: #METHOD_INVOCATION$createBarChart
0 -> 7
1 -> 6
2 -> 3
3 -> 4
6 -> 4
6 -> 5
7 -> 6

Synthesized result:
org.jfree.data.category.IntervalCategoryDataset v3 = org.jfree.chart.GanttChartTest.createDataset();
org.jfree.chart.JFreeChart v4 = org.jfree.chart.ChartFactory.createBarChart("a", "a", "a", v0);

=========
Node 0: #DATA$data
Node 1: #DATA$PlotOrientation
Node 2: #FIELD_ACCESS$VERTICAL
Node 3: #DATA$ChartFactory
Node 4: #DATA$true
Node 5: #DATA$true
Node 6: #DATA$0.35
Node 7: #METHOD_INVOCATION$setMaximumBarWidth
Node 8: #DATA$67
Node 9: #DATA$208
Node 10: #DATA$165
Node 11: #DATA$Color
Node 12: #METHOD_INVOCATION$Color::<init>
Node 13: #DATA$0
Node 14: #METHOD_INVOCATION$setSeriesPaint
Node 15: #METHOD_INVOCATION$getRenderer
Node 16: #METHOD_INVOCATION$getCategoryPlot
Node 17: #DATA$ChartPanel
Node 18: #DATA$false
Node 19: #DATA$false
Node 20: #DATA$true
Node 21: #DATA$true
Node 22: #DATA$true
Node 23: #DATA$ancho
Node 24: #DATA$alto
Node 25: #METHOD_INVOCATION$setSize
Node 26: #OP$RETURN
Node 27: #METHOD_INVOCATION$ChartPanel::<init>
Node 28: #METHOD_INVOCATION$createBarChart
Node 29: #DATA$true
0 -> 28
1 -> 2
2 -> 28
3 -> 28
4 -> 28
5 -> 28
6 -> 7
15 -> 7
8 -> 12
9 -> 12
10 -> 12
11 -> 12
12 -> 14
13 -> 14
15 -> 14
16 -> 15
28 -> 16
17 -> 27
18 -> 27
19 -> 27
20 -> 27
21 -> 27
22 -> 27
23 -> 25
24 -> 25
27 -> 25
27 -> 26
28 -> 27
29 -> 28

Synthesized result:
org.jfree.chart.JFreeChart v5 = org.jfree.chart.ChartFactory.createBarChart("a", "a", "a", v0);
org.jfree.chart.plot.CategoryPlot v6 = v5.getCategoryPlot();
org.jfree.chart.renderer.category.CategoryItemRenderer v7 = v6.getRenderer();
org.jfree.chart.renderer.category.BoxAndWhiskerRenderer v8 = new BoxAndWhiskerRenderer();
v8.setMaximumBarWidth(0.35);
int v9 = v5.getBackgroundImageAlignment();
java.awt.Paint v10 = v8.getArtifactPaint();
v7.setSeriesPaint(v9, v10);
org.jfree.chart.needle.MeterNeedle v11 = new MeterNeedle(v10, v10, v10);
v11.setSize(v9);

==========
Synthesis costs: 1.471s
```