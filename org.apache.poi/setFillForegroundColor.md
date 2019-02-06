query: iterate through all the cells in a row to set foreground color blue

query source: https://stackoverflow.com/questions/8424327/how-to-loop-through-all-the-rows-and-cells-in-an-excel-file

core api: setFillForegroundColor

manual code:
```
CellStyle style = wb.createCellStyle();
style.setFillForegroundColor(IndexedColors.BLUE.getIndex());
style.setFillPattern(FillPatternType.SOLID_FOREGROUND);
for (Cell cell: row) {
    cell.setCellStyle(style);
}
```

test case:
```
boolean test(Cell cell) {
    return cell.getCellStyle().getFillForegroundColor() == IndexedColors.BLUE.getIndex();
}
```

SnippSynth output:
```
concepts in query: [cell, row, color]
Iterable pairs: [cell,row]
Initial context:
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2
4. TYPE:java.io.OutputStream NAME:v3

#Data flow graphs: 265
#Pattern: 6
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$HSSFCellStyle
Node 1: #DATA$HSSFFont
Node 2: #FIELD_ACCESS$BOLDWEIGHT_BOLD
Node 3: #DATA$objWB
Node 4: #METHOD_INVOCATION$fuente
Node 5: #DATA$objWB
Node 6: #DATA$HSSFColor
Node 7: #FIELD_ACCESS$GREY_25_PERCENT
Node 8: #FIELD_ACCESS$index
Node 9: #METHOD_INVOCATION$setFillForegroundColor
Node 10: #OP$RETURN
Node 11: #METHOD_INVOCATION$celda
Node 12: #METHOD_INVOCATION$setFillPattern
Node 13: #FIELD_ACCESS$SOLID_FOREGROUND
0 -> 13
1 -> 2
2 -> 4
3 -> 4
4 -> 11
5 -> 11
6 -> 7
7 -> 8
8 -> 9
11 -> 9
11 -> 10
11 -> 12
13 -> 12

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v8 = v2.getRowStyle();
short v9 = v2.getFirstCellNum();
v8.setFillForegroundColor(v9);
v8.setFillPattern(org.apache.poi.ss.usermodel.FillPatternType.SOLID_FOREGROUND);

=========
Node 0: #DATA$workbook
Node 1: #DATA$CellStyle
Node 2: #FIELD_ACCESS$SOLID_FOREGROUND
Node 3: #METHOD_INVOCATION$setFillPattern
Node 4: #DATA$java.awt.Color
Node 5: #METHOD_INVOCATION$java.awt.Color::<init>
Node 6: #DATA$XSSFColor
Node 7: #METHOD_INVOCATION$XSSFColor::<init>
Node 8: #METHOD_INVOCATION$setFillForegroundColor
Node 9: #METHOD_INVOCATION$createCellStyle
Node 10: #METHOD_INVOCATION$setCellStyle
Node 11: #DATA$cell
0 -> 9
1 -> 2
2 -> 3
9 -> 3
4 -> 5
5 -> 7
6 -> 7
7 -> 8
9 -> 8
9 -> 10
11 -> 10

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v8 = v0.createCellStyle();
short v9 = org.apache.poi.ss.usermodel.IndexedColors.BLUE.getIndex();
v8.setFillForegroundColor(v9);
v8.setFillPattern(org.apache.poi.ss.usermodel.FillPatternType.SOLID_FOREGROUND);
for (org.apache.poi.ss.usermodel.Cell v10: v2) {
v10.setCellStyle(v8);
}

=========
Node 0: #DATA$workbook
Node 1: #DATA$workbook
Node 2: #METHOD_INVOCATION$fillWhiteTextCell
Node 3: #DATA$CellStyle
Node 4: #FIELD_ACCESS$SOLID_FOREGROUND
Node 5: #METHOD_INVOCATION$setFillPattern
Node 6: #DATA$XSSFColor
Node 7: #METHOD_INVOCATION$XSSFColor::<init>
Node 8: #METHOD_INVOCATION$setFillForegroundColor
Node 9: #METHOD_INVOCATION$createCellStyle
Node 10: #METHOD_INVOCATION$setCellStyle
Node 11: #DATA$cell
0 -> 9
1 -> 2
9 -> 2
3 -> 4
4 -> 5
9 -> 5
6 -> 7
7 -> 8
9 -> 8
9 -> 10
11 -> 10

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v8 = v0.createCellStyle();
short v9 = org.apache.poi.ss.usermodel.IndexedColors.BLUE.getIndex();
v8.setFillForegroundColor(v9);
v8.setFillPattern(org.apache.poi.ss.usermodel.FillPatternType.SOLID_FOREGROUND);
for (org.apache.poi.ss.usermodel.Cell v10: v2) {
v10.setCellStyle(v8);
}

=========
Node 0: #DATA$HSSFCellStyle
Node 1: #DATA$8
Node 2: #DATA$objWB
Node 3: #METHOD_INVOCATION$fuente
Node 4: #DATA$objWB
Node 5: #FIELD_ACCESS$index
Node 6: #METHOD_INVOCATION$setFillForegroundColor
Node 7: #OP$RETURN
Node 8: #METHOD_INVOCATION$celda
Node 9: #METHOD_INVOCATION$setFillPattern
Node 10: #FIELD_ACCESS$SOLID_FOREGROUND
0 -> 10
1 -> 3
2 -> 3
3 -> 8
4 -> 8
5 -> 6
8 -> 6
8 -> 7
8 -> 9
10 -> 9

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v8 = v2.getRowStyle();
short v9 = org.apache.poi.ss.usermodel.IndexedColors.BLUE.getIndex();
v8.setFillForegroundColor(v9);
v8.setFillPattern(org.apache.poi.ss.usermodel.FillPatternType.SOLID_FOREGROUND);

=========
Node 0: #DATA$fg
Node 1: #DATA$HSSFColor
Node 2: #METHOD_INVOCATION$setFillForegroundColor
Node 3: #METHOD_INVOCATION$getIndex
Node 4: #METHOD_INVOCATION$toHSSFColor
Node 5: #BINARY$==
Node 6: #DATA$null
0 -> 4
1 -> 4
3 -> 2
4 -> 3
4 -> 5
6 -> 5

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v7 = v2.getRowStyle();
org.apache.poi.ss.usermodel.Color v8 = v7.getFillForegroundColorColor();
org.apache.poi.hssf.util.HSSFColor v9 = org.apache.poi.hssf.util.HSSFColor.toHSSFColor(v8);
short v10 = org.apache.poi.ss.usermodel.IndexedColors.BLUE.getIndex();
v7.setFillForegroundColor(v10);
short v11 = org.apache.poi.ss.usermodel.IndexedColors.BLUE.getIndex();

==========
Synthesis costs: 2.788s
```