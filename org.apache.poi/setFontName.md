query: set the font name to "Verdana"

query source: http://thinktibits.blogspot.com/2012/12/Java-POI-XLS-XLSX-Change-Cell-Font-Name-Example.html

core api: setFontName

manual code:
```
Font font = wb.createFont();
font.setFontName("Verdana");
CellStyle style = wb.createCellStyle();
style.setFont(font);
```

test case:
```
boolean test(Font font) {
    return font.getFontName().equals("Verdana");
}
```

SnippSynth output:
```
concepts in query: [font]
Iterable pairs: []
Initial context:
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2
4. TYPE:java.io.OutputStream NAME:v3

#Data flow graphs: 51
#Pattern: 4
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$200
Node 1: #METHOD_INVOCATION$setFontHeight
Node 2: #DATA$wb
Node 3: #DATA$HSSFCellStyle
Node 4: #FIELD_ACCESS$ALIGN_LEFT
Node 5: #METHOD_INVOCATION$setAlignment
Node 6: #OP$RETURN
Node 7: #METHOD_INVOCATION$getBaseStyle
Node 8: #METHOD_INVOCATION$setFont
Node 9: #DATA$"Verdana"
Node 10: #METHOD_INVOCATION$setFontName
Node 11: #METHOD_INVOCATION$createFont
Node 12: #DATA$wb
0 -> 1
11 -> 1
2 -> 7
3 -> 4
4 -> 5
7 -> 5
7 -> 6
7 -> 8
11 -> 8
9 -> 10
11 -> 10
12 -> 11

Synthesized result:
org.apache.poi.hwpf.model.StyleDescription v6 = new StyleDescription();
int v7 = v6.getBaseStyle();
org.apache.poi.ss.usermodel.CellStyle v8 = v2.getRowStyle();
v8.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
org.apache.poi.ss.usermodel.Font v10 = v0.createFont();
v10.setFontName("Verdana");
short v11 = v2.getHeight();
v10.setFontHeight(v11);
v8.setFont(v10);

=========
Node 0: #DATA$workbook
Node 1: #DATA$workbook
Node 2: #DATA$VerticalAlignment
Node 3: #FIELD_ACCESS$CENTER
Node 4: #METHOD_INVOCATION$setVerticalAlignment
Node 5: #METHOD_INVOCATION$setAlignment
Node 6: #OP$RETURN
Node 7: #METHOD_INVOCATION$createCellStyle
Node 8: #METHOD_INVOCATION$setFont
Node 9: #DATA$fontName
Node 10: #METHOD_INVOCATION$setFontName
Node 11: #METHOD_INVOCATION$createFont
0 -> 11
1 -> 7
2 -> 3
3 -> 4
7 -> 4
7 -> 5
7 -> 6
7 -> 8
11 -> 8
9 -> 10
11 -> 10

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v7 = v0.createCellStyle();
org.apache.poi.ss.usermodel.Font v8 = v0.createFont();
v8.setFontName("Verdana");
v7.setFont(v8);
v7.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.CENTER);
v7.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);


=========
Node 0: #DATA$workbook
Node 1: #DATA$workbook
Node 2: #DATA$HorizontalAlignment
Node 3: #FIELD_ACCESS$CENTER
Node 4: #METHOD_INVOCATION$setAlignment
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$createCellStyle
Node 7: #METHOD_INVOCATION$setFont
Node 8: #METHOD_INVOCATION$setFontName
Node 9: #METHOD_INVOCATION$createFont
0 -> 9
1 -> 6
2 -> 3
3 -> 4
6 -> 4
6 -> 5
6 -> 7
9 -> 7
9 -> 8

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v7 = v0.createCellStyle();
org.apache.poi.ss.usermodel.Font v8 = v0.createFont();
v8.setFontName("Verdana");
v7.setFont(v8);
v7.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.CENTER);

=========
Node 0: #METHOD_INVOCATION$setFontHeight
Node 1: #DATA$HSSFFont
Node 2: #FIELD_ACCESS$BOLDWEIGHT_BOLD
Node 3: #METHOD_INVOCATION$setBoldweight
Node 4: #METHOD_INVOCATION$setFontName
Node 5: #METHOD_INVOCATION$createFont
5 -> 0
1 -> 2
2 -> 3
5 -> 3
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.Font v6 = v0.createFont();
v6.setFontName("Verdana");
short v7 = v2.getHeight();
v6.setFontHeight(v7);

==========
Synthesis costs: 1.505s
```