query: create a simple 3d pie chart using jfreechart

query source: https://stackoverflow.com/questions/25042070/how-to-convert-plot-to-pieplot3d-for-creating-a-3d-pie-chart-using-jfreechart

core api: createPieChart3D

manual code:
```
JFreeChart chart = ChartFactory.createBarChart("title", dataset);
```

test case:
```
boolean test(JFreeChart chart) {
    return chart.getPlot() instanceof PiePlot3D;
}
```

SnippSynth output:
```
concepts in query: [chart]
Iterable pairs: []
Initial context:
1. TYPE:org.jfree.data.category.CategoryDataset NAME:v0
2. TYPE:org.jfree.data.general.PieDataset NAME:v1
3. TYPE:java.io.File NAME:v2

#Data flow graphs: 536
#Pattern: 2
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$"Section 3"
Node 1: #DATA$DefaultPieDataset
Node 2: #DATA$BufferedImage
Node 3: #FIELD_ACCESS$TYPE_INT_RGB
Node 4: #DATA$BufferedImage
Node 5: #DATA$200
Node 6: #DATA$100
Node 7: #METHOD_INVOCATION$BufferedImage::<init>
Node 8: #METHOD_INVOCATION$dispose
Node 9: #METHOD_INVOCATION$createGraphics
Node 10: #DATA$Rectangle2D.Double
Node 11: #DATA$200
Node 12: #DATA$100
Node 13: #DATA$0
Node 14: #DATA$0
Node 15: #METHOD_INVOCATION$Rectangle2D.Double::<init>
Node 16: #DATA$null
Node 17: #DATA$null
Node 18: #METHOD_INVOCATION$draw
Node 19: #METHOD_INVOCATION$createPieChart3D
Node 20: #DATA$"Section 1"
Node 21: #DATA$10.0
Node 22: #METHOD_INVOCATION$setValue
Node 23: #DATA$"Section 2"
Node 24: #DATA$11.0
Node 25: #METHOD_INVOCATION$setValue
Node 26: #METHOD_INVOCATION$DefaultPieDataset::<init>
Node 27: #METHOD_INVOCATION$setValue
Node 28: #DATA$null
0 -> 27
1 -> 26
2 -> 3
3 -> 7
4 -> 7
5 -> 7
6 -> 7
7 -> 9
9 -> 8
9 -> 18
10 -> 15
11 -> 15
12 -> 15
13 -> 15
14 -> 15
15 -> 18
16 -> 18
17 -> 18
19 -> 18
26 -> 19
20 -> 22
21 -> 22
26 -> 22
23 -> 25
24 -> 25
26 -> 25
26 -> 27
28 -> 27

Synthesized result:
org.jfree.data.category.DefaultCategoryDataset v4 = new DefaultCategoryDataset();
Comparable v5 = v4.getRowKey(1);
v4.setValue(11.0, v5, v5);
org.jfree.chart.JFreeChart v6 = org.jfree.chart.ChartFactory.createPieChart3D("a", v1);
BAD SYNTHESIS

=========
Node 0: #DATA$"Pie Chart"
Node 1: #DATA$dataset
Node 2: #DATA$false
Node 3: #DATA$ChartFactory
Node 4: #DATA$true
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$createPieChart3D
Node 7: #DATA$true
0 -> 6
1 -> 6
2 -> 6
3 -> 6
4 -> 6
6 -> 5
7 -> 6

Synthesized result:
org.jfree.chart.JFreeChart v4 = org.jfree.chart.ChartFactory.createPieChart3D("a", v1);

==========
Synthesis costs: 2.698s
```