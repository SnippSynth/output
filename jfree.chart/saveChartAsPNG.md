query: how to save current chart in ChartPanel as PNG programmatically

query source: https://stackoverflow.com/questions/34836338/how-to-save-current-chart-in-chartpanel-as-png-programmatically

core api: saveChartAsPNG

manual code:
```
try {
    File file = new File("1.png");
    JfreeChart chart = org.jfree.chart.ChartFactory.createPieChart("title", dataset);
    int width = 10, height = 10;
    org.jfree.chart.ChartUtils.saveChartAsPNG(file, chart, width, height);
} catch(IOException e) {
    e.printStackTrace();
}
```

test case:
```
side effect code, judged manually
```

SnippSynth output:
```
concepts in query: [chart]
Iterable pairs: []
Initial context:
1. TYPE:org.jfree.data.category.CategoryDataset NAME:v0
2. TYPE:org.jfree.data.general.PieDataset NAME:v1
3. TYPE:java.io.File NAME:v2

#Data flow graphs: 106
#Pattern: 1
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$DefaultPieDataset
Node 1: #METHOD_INVOCATION$setValue
Node 2: #METHOD_INVOCATION$setValue
Node 3: #METHOD_INVOCATION$setValue
Node 4: #METHOD_INVOCATION$setValue
Node 5: #METHOD_INVOCATION$DefaultPieDataset::<init>
Node 6: #DATA$ChartFactory
Node 7: #DATA$true
Node 8: #DATA$false
Node 9: #METHOD_INVOCATION$createPieChart
Node 10: #DATA$ChartUtilities
Node 11: #METHOD_INVOCATION$saveChartAsPNG
Node 12: #METHOD_INVOCATION$File::<init>
Node 13: #DATA$File
0 -> 5
5 -> 1
5 -> 2
5 -> 3
5 -> 4
5 -> 9
6 -> 9
7 -> 9
8 -> 9
9 -> 11
10 -> 11
12 -> 11
13 -> 12

Synthesized result:
Comparable v3 = v1.getKey(1);
Number v4 = v1.getValue(1);
v1.setValue(v3, v4);
org.jfree.chart.JFreeChart v5 = org.jfree.chart.ChartFactory.createPieChart("a", v1);
int v6 = v1.getIndex(v3);
try {
org.jfree.chart.ChartUtils.saveChartAsPNG(v2, v5, v6, v6);
} catch(Exception e) {
e.printStackTrace();
}

=========
Synthesis costs: 0.872s
```