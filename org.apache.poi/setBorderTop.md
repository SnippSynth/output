query: set thin border on specific cell

query source: https://stackoverflow.com/questions/51044288/java-apache-poi-excel-set-border-on-specific-cell-and-set-currency-cell-format

core api: setBorderTop

manual code:
```
CellStyle style = wb.createCellStyle();
style.setBorderBottom(BorderStyle.THIN);
style.setBorderLeft(BorderStyle.THIN);
style.setBorderRight(BorderStyle.THIN);
style.setBorderTop(BorderStyle.THIN);
cell.setCellStyle(cell);
```

test case:
```
boolean test(CellStyle style) {
    return style.getBorderBottomEnum().equals(BorderStyle.THIN) ||
            style.getBorderLeftEnum().equals(BorderStyle.THIN) ||
            style.getBorderTopEnum().equals(BorderStyle.THIN) ||
            style.getBorderRightEnum().equals(BorderStyle.THIN);
}
```

SnippSynth output:
```
concepts in query: [border, cell]
Iterable pairs: []
Initial context:
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2

#Data flow graphs: 301
#Pattern: 10
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #METHOD_INVOCATION$setFontName
Node 1: #METHOD_INVOCATION$setFontHeightInPoints
Node 2: #METHOD_INVOCATION$setAlignment
Node 3: #METHOD_INVOCATION$setBorderLeft
Node 4: #METHOD_INVOCATION$setBorderRight
Node 5: #METHOD_INVOCATION$setBorderBottom
Node 6: #METHOD_INVOCATION$setBorderTop
Node 7: #METHOD_INVOCATION$createCellStyle
Node 8: #METHOD_INVOCATION$setFont
Node 9: #METHOD_INVOCATION$createFont
9 -> 0
9 -> 1
7 -> 2
7 -> 3
7 -> 4
7 -> 5
7 -> 6
7 -> 8
9 -> 8

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
org.apache.poi.ss.usermodel.Font v7 = v0.createFont();
short v8 = org.apache.poi.ss.usermodel.BorderStyle.THIN.getCode();
v7.setFontHeightInPoints(v8);
String v9 = v0.getSheetName(1);
v7.setFontName(v9);
v5.setFont(v7);
v5.setBorderBottom(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderLeft(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderTop(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderRight(org.apache.poi.ss.usermodel.BorderStyle.THIN);

=========
Node 0: #METHOD_INVOCATION$setCellStyle
Node 1: #FIELD_ACCESS$BORDER_THIN
Node 2: #METHOD_INVOCATION$setBorderLeft
Node 3: #FIELD_ACCESS$BORDER_THIN
Node 4: #METHOD_INVOCATION$setBorderRight
Node 5: #METHOD_INVOCATION$setBorderTop
Node 6: #METHOD_INVOCATION$createCellStyle
Node 7: #METHOD_INVOCATION$setBorderBottom
Node 8: #FIELD_ACCESS$BORDER_THIN
6 -> 0
1 -> 2
6 -> 2
3 -> 4
6 -> 4
6 -> 5
6 -> 7
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setBorderBottom(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderTop(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderRight(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderLeft(org.apache.poi.ss.usermodel.BorderStyle.THIN);
org.apache.poi.ss.usermodel.Cell v6 = v2.createCell(1, 1);
v6.setCellStyle(v5);

=========
Node 0: #DATA$BorderStyle
Node 1: #FIELD_ACCESS$THICK
Node 2: #METHOD_INVOCATION$setBorderBottom
Node 3: #DATA$BorderStyle
Node 4: #FIELD_ACCESS$THICK
Node 5: #METHOD_INVOCATION$setBorderTop
Node 6: #OP$RETURN
Node 7: #METHOD_INVOCATION$createCellStyle
Node 8: #DATA$workbook
0 -> 1
1 -> 2
7 -> 2
3 -> 4
4 -> 5
7 -> 5
7 -> 6
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setBorderTop(org.apache.poi.ss.usermodel.BorderStyle.THICK);
v5.setBorderBottom(org.apache.poi.ss.usermodel.BorderStyle.THICK);

=========
Node 0: #METHOD_INVOCATION$setFontName
Node 1: #METHOD_INVOCATION$setColor
Node 2: #METHOD_INVOCATION$setBorderLeft
Node 3: #METHOD_INVOCATION$setBorderRight
Node 4: #METHOD_INVOCATION$setBorderBottom
Node 5: #METHOD_INVOCATION$setBorderTop
Node 6: #METHOD_INVOCATION$createCellStyle
Node 7: #METHOD_INVOCATION$setFont
Node 8: #METHOD_INVOCATION$createFont
8 -> 0
8 -> 1
6 -> 2
6 -> 3
6 -> 4
6 -> 5
6 -> 7
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setBorderBottom(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderLeft(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderRight(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderTop(org.apache.poi.ss.usermodel.BorderStyle.THIN);
org.apache.poi.ss.usermodel.Font v6 = v0.createFont();
String v7 = v0.getSheetName(1);
v6.setFontName(v7);
short v8 = org.apache.poi.ss.usermodel.BorderStyle.THIN.getCode();
v6.setColor(v8);
v5.setFont(v6);

=========
Node 0: #DATA$baseExcel
Node 1: #METHOD_INVOCATION$setAlignment
Node 2: #METHOD_INVOCATION$setBorderLeft
Node 3: #METHOD_INVOCATION$setBorderRight
Node 4: #METHOD_INVOCATION$setBorderBottom
Node 5: #METHOD_INVOCATION$setBorderTop
Node 6: #OP$RETURN
Node 7: #METHOD_INVOCATION$createCellStyle
0 -> 7
7 -> 1
7 -> 2
7 -> 3
7 -> 4
7 -> 5
7 -> 6

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
v5.setBorderBottom(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderLeft(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderRight(org.apache.poi.ss.usermodel.BorderStyle.THIN);
v5.setBorderTop(org.apache.poi.ss.usermodel.BorderStyle.THIN);

==========
Synthesis costs: 9.279s
```