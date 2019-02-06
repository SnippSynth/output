query: set "example title" as chart title

query source: http://thinktibits.blogspot.com/2012/11/JFreeChart-Chart-Title-setTitle-Example-Program.html

core api: setTitle

manual code:
```
JFreeChart chart = ChartFactory.createPieChart("title", dataset);
chart.setTitle("example title");
```

test case:
```
boolean test(JFreeChart chart) {
    System.out.println(chart.getTitle().getText());
    return chart.getTitle().getText().equals("example title");
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

#Data flow graphs: 1351
#Pattern: 1
Min pattern frequency: 10
Min pattern nodes num: 6
=========
Node 0: #METHOD_INVOCATION$setTitle
Node 1: #METHOD_INVOCATION$assertFalse
Node 2: #METHOD_INVOCATION$isBorderVisible
Node 3: #METHOD_INVOCATION$assertTrue
Node 4: #METHOD_INVOCATION$isNotify
Node 5: #METHOD_INVOCATION$JFreeChart::<init>
Node 6: #DATA$JFreeChart
5 -> 0
2 -> 1
5 -> 2
4 -> 3
5 -> 4
6 -> 5

Synthesized result:
org.jfree.chart.plot.Plot v4 = new PiePlot();
org.jfree.chart.JFreeChart v5 = new JFreeChart("example title", v4);
v5.setTitle("example title");
boolean v6 = v5.isNotify();
boolean v7 = v5.isBorderVisible();

==========
Synthesis costs: 18.252s
```