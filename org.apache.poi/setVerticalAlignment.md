query: cell vertical top alignment using poi

query source: https://stackoverflow.com/questions/7992807/cell-vertical-top-alignment-using-poi

core api: setVerticalAlignment

manual code:
```
CellStyle style = wb.createCellStyle();
style.setVerticalAlignment(VerticalAlignment.TOP);
```

test case:
```
boolean test(CellStyle style) {
    return style.getVerticalAlignmentEnum().getCode() == VerticalAlignment.TOP.getCode();
}
```

SnippSynth output:
```
concepts in query: [cell]
Iterable pairs: []
Initial context:
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2

#Data flow graphs: 263
#Pattern: 9
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$wb
Node 1: #DATA$HSSFCellStyle
Node 2: #FIELD_ACCESS$VERTICAL_CENTER
Node 3: #METHOD_INVOCATION$setVerticalAlignment
Node 4: #OP$RETURN
Node 5: #METHOD_INVOCATION$createCellStyle
0 -> 5
1 -> 2
2 -> 3
5 -> 3
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);

=========
Node 0: #METHOD_INVOCATION$setWrapText
Node 1: #DATA$HSSFCellStyle
Node 2: #FIELD_ACCESS$ALIGN_CENTER
Node 3: #METHOD_INVOCATION$setAlignment
Node 4: #METHOD_INVOCATION$setVerticalAlignment
Node 5: #OP$RETURN
Node 6: #METHOD_INVOCATION$createCellStyle
6 -> 0
1 -> 2
2 -> 3
6 -> 3
6 -> 4
6 -> 5

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
v5.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);
boolean v8 = v2.isFormatted();
v5.setWrapText(v8);

=========
Node 0: #DATA$workbook
Node 1: #DATA$BuiltinFormats
Node 2: #METHOD_INVOCATION$getBuiltinFormat
Node 3: #METHOD_INVOCATION$setDataFormat
Node 4: #METHOD_INVOCATION$setAlignment
Node 5: #METHOD_INVOCATION$setVerticalAlignment
Node 6: #METHOD_INVOCATION$createCellStyle
0 -> 6
1 -> 2
2 -> 3
6 -> 3
6 -> 4
6 -> 5

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v5 = v0.createCellStyle();
v5.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);
short v7 = v2.getFirstCellNum();
v5.setDataFormat(v7);
int v8 = v0.getNumCellStyles();
String v9 = org.apache.poi.ss.usermodel.BuiltinFormats.getBuiltinFormat(v8);
v5.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);

=========
Node 0: #METHOD_INVOCATION$setFillForegroundColor
Node 1: #DATA$FillPatternType
Node 2: #FIELD_ACCESS$SOLID_FOREGROUND
Node 3: #METHOD_INVOCATION$setFillPattern
Node 4: #METHOD_INVOCATION$setAlignment
Node 5: #METHOD_INVOCATION$setVerticalAlignment
Node 6: #METHOD_INVOCATION$createCellStyle
6 -> 0
1 -> 2
2 -> 3
6 -> 3
6 -> 4
6 -> 5

Synthesized result:
org.apache.poi.ss.usermodel.CellStyle v6 = v0.createCellStyle();
v6.setAlignment(org.apache.poi.ss.usermodel.HorizontalAlignment.GENERAL);
v6.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);
v6.setFillPattern(org.apache.poi.ss.usermodel.FillPatternType.SOLID_FOREGROUND);
short v9 = v2.getFirstCellNum();
v6.setFillForegroundColor(v9);

=========
Node 0: #DATA$HSSFRichTextString
Node 1: #METHOD_INVOCATION$HSSFRichTextString::<init>
Node 2: #METHOD_INVOCATION$setCellValue
Node 3: #METHOD_INVOCATION$createCell
Node 4: #METHOD_INVOCATION$setCellStyle
Node 5: #METHOD_INVOCATION$setVerticalAlignment
Node 6: #METHOD_INVOCATION$createCellStyle
0 -> 1
1 -> 2
3 -> 2
3 -> 4
6 -> 4
6 -> 5

Synthesized result:
int v5 = v0.getNumCellStyles();
org.apache.poi.ss.usermodel.Cell v6 = v2.createCell(v5);
boolean v7 = v2.isFormatted();
v6.setCellValue(v7);
org.apache.poi.ss.usermodel.CellStyle v8 = v0.createCellStyle();
v8.setVerticalAlignment(org.apache.poi.ss.usermodel.VerticalAlignment.TOP);
v6.setCellStyle(v8);

==========
Synthesis costs: 9.651s
```