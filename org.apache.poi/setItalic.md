query: set italic font

query source: http://thinktibits.blogspot.com/2012/12/Java-POI-Excel-Italic-Cell-Font-Example-Program.html

core api: setItalic

manual code:
```
Font font = wb.createFont();
font.setItalic(true);
```

test case:
```
boolean test(Font font) {
    return font.getItalic();
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

#Data flow graphs: 10
#Pattern: 2
Min pattern frequency: 2
Min pattern nodes num: 4
=========
pattern:
Node 0: #DATA$tamanhoFonte
Node 1: #DATA$excelGalderma
Node 2: #DATA$nomeFonte
Node 3: #DATA$true
Node 4: #METHOD_INVOCATION$setBold
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$font
Node 7: #METHOD_INVOCATION$setItalic
Node 8: #DATA$true
0 -> 6
1 -> 6
2 -> 6
3 -> 4
6 -> 4
6 -> 5
6 -> 7
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.Font v4 = v0.createFont();
v4.setBold(true);
v4.setItalic(true);

=========
pattern:
Node 0: #DATA$excelGalderma
Node 1: #DATA$tamanhoFonte
Node 2: #METHOD_INVOCATION$setFontHeightInPoints
Node 3: #OP$RETURN
Node 4: #DATA$false
Node 5: #METHOD_INVOCATION$setItalic
Node 6: #METHOD_INVOCATION$createFont
Node 7: #METHOD_INVOCATION$setFontName
Node 8: #DATA$nomeFonte
0 -> 6
1 -> 2
6 -> 2
6 -> 3
4 -> 5
6 -> 5
6 -> 7
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.Font v4 = v0.createFont();
String v5 = v0.getSheetName(1);
v4.setFontName(v5);
v4.setItalic(false);
short v6 = v2.getFirstCellNum();
v4.setFontHeightInPoints(v6);

==========
Synthesis costs: 0.914s
```