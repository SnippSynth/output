query: set cell alignment as GENERAL

query source: http://thinktibits.blogspot.com/2012/12/Excel-Horizontal-Vertical-Cell-Alignment-Java-POI-Example-Program.html

core api: setAlignment

manual code:
```
CellStyle titleStyle = wb.createCellStyle();
titleStyle.setAlignment(HorizontalAlignment.GENERAL);
```

test case:
```
boolean test(CellStyle style) {
    return style.getAlignmentEnum().getCode() == HorizontalAlignment.GENERAL.getCode();
}
```

SnippSynth output:
```
concepts in query: [cell]
Iterable pairs: []
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2

#Data flow graphs: 217
#Pattern: 4
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$1
Node 1: #METHOD_INVOCATION$setVerticalAlignment
Node 2: #DATA$2
Node 3: #METHOD_INVOCATION$setAlignment
Node 4: #OP$RETURN
Node 5: #METHOD_INVOCATION$createCellStyle
0 -> 1
5 -> 1
2 -> 3
5 -> 3
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v4 = v0.createCellStyle();
v4.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
v4.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);

=========
Node 0: #DATA$true
Node 1: #METHOD_INVOCATION$setWrapText
Node 2: #METHOD_INVOCATION$setVerticalAlignment
Node 3: #METHOD_INVOCATION$setAlignment
Node 4: #OP$RETURN
Node 5: #METHOD_INVOCATION$createCellStyle
0 -> 1
5 -> 1
5 -> 2
5 -> 3
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
v5.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);
v5.setWrapText(true);

=========
Node 0: #METHOD_INVOCATION$setBoldweight
Node 1: #METHOD_INVOCATION$createFont
Node 2: #METHOD_INVOCATION$setFont
Node 3: #FIELD_ACCESS$ALIGN_CENTER
Node 4: #METHOD_INVOCATION$setAlignment
Node 5: #METHOD_INVOCATION$createCellStyle
1 -> 0
1 -> 2
5 -> 2
3 -> 4
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v4 = v0.createCellStyle();
org.apache.poi.ss.usermodel.Font v5 = v0.createFont();
v4.setFont(v5);
v4.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);

=========
Node 0: #METHOD_INVOCATION$setVerticalAlignment
Node 1: #METHOD_INVOCATION$setFontName
Node 2: #METHOD_INVOCATION$createFont
Node 3: #METHOD_INVOCATION$setFont
Node 4: #METHOD_INVOCATION$setAlignment
Node 5: #METHOD_INVOCATION$createCellStyle
5 -> 0
2 -> 1
2 -> 3
5 -> 3
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v4 = v0.createCellStyle();
org.apache.poi.ss.usermodel.Font v5 = v0.createFont();
String v6 = v0.getSheetName(1);
v5.setFontName(v6);
v4.setFont(v5);
v4.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
v4.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);

==========
Synthesis costs: 4.372s
```