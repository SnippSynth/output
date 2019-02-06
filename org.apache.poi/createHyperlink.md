query: create hyperlink to local file \"E:/1.png\" using Apache POI and Java

query source: https://stackoverflow.com/questions/48282807/how-to-create-hyperlink-using-apache-poi-and-java

core api: createHyperlink

manual code:
```
CreationHelper helper = wb.getCreationHelper();
Hyperlink link = helper.createHyperlink(HyperlinkType.FILE);
link.setAddress("E:/1.png");
cell.setHyperlink(v13);
```

test case:
```
boolean test(Cell cell) {
    return cell.getHyperlink().getAddress().equals("E:/1.png");
}
```

SnippSynth output:
```
concepts in query: [file]
Iterable pairs: []
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2
4. TYPE:java.io.OutputStream NAME:v3

#Data flow graphs: 127
#Pattern: 1
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$XSSFWorkbook
Node 1: #DATA$0
Node 2: #METHOD_INVOCATION$createRow
Node 3: #METHOD_INVOCATION$createSheet
Node 4: #METHOD_INVOCATION$getCreationHelper
Node 5: #DATA$FileOutputStream
Node 6: #METHOD_INVOCATION$close
Node 7: #METHOD_INVOCATION$FileOutputStream::<init>
Node 8: #METHOD_INVOCATION$write
Node 9: #METHOD_INVOCATION$XSSFWorkbook::<init>
Node 10: #FIELD_ACCESS$U_SINGLE
Node 11: #METHOD_INVOCATION$setUnderline
Node 12: #METHOD_INVOCATION$createFont
Node 13: #METHOD_INVOCATION$setFont
Node 14: #METHOD_INVOCATION$createCellStyle
Node 15: #METHOD_INVOCATION$setCellStyle
Node 16: #METHOD_INVOCATION$setCellValue
Node 17: #METHOD_INVOCATION$createCell
Node 18: #METHOD_INVOCATION$setHyperlink
Node 19: #METHOD_INVOCATION$setAddress
Node 20: #METHOD_INVOCATION$createHyperlink
0 -> 9
1 -> 2
2 -> 17
3 -> 2
9 -> 3
4 -> 20
9 -> 4
5 -> 7
7 -> 6
7 -> 8
9 -> 8
9 -> 14
9 -> 12
10 -> 11
12 -> 11
12 -> 13
14 -> 13
14 -> 15
17 -> 15
17 -> 16
17 -> 18
20 -> 18
20 -> 19

Synthesized result:
org.apache.poi.ss.usermodel.CreationHelper v6 = v0.getCreationHelper();
org.apache.poi.ss.usermodel.CellStyle v7 = v0.createCellStyle();
org.apache.poi.ss.usermodel.Font v8 = v0.createFont();
byte v9 = v8.getUnderline();
v8.setUnderline(v9);
v7.setFont(v8);
org.apache.poi.ss.usermodel.Sheet v10 = v0.createSheet();
org.apache.poi.ss.usermodel.Row v11 = v10.createRow(0);
org.apache.poi.ss.usermodel.Cell v12 = v11.createCell(0);
v12.setCellValue("E:/1.png");
org.apache.poi.ss.usermodel.Hyperlink v13 = v6.createHyperlink(org.apache.poi.common.usermodel.HyperlinkType.FILE);
v13.setAddress("E:/1.png");
v12.setHyperlink(v13);
v12.setCellStyle(v7);

==========
Synthesis costs: 7.242s
```