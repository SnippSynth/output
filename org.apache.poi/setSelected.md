query: set a sheet as selected

query source: https://poi.apache.org/components/spreadsheet/quick-guide.html#SelectSheet

core api: setSelected

manual code:
```
sheet.setSelected(true);
```

test case:
```
boolean test(Sheet sheet) {
    return sheet.isSelected();
}
```

SnippSynth output:
```
concepts in query: [sheet]
Iterable pairs: []
Initial context:
1. TYPE:org.apache.poi.ss.usermodel.Workbook NAME:v0
2. TYPE:org.apache.poi.ss.usermodel.Sheet NAME:v1
3. TYPE:org.apache.poi.ss.usermodel.Row NAME:v2
4. TYPE:java.io.OutputStream NAME:v3

#Data flow graphs: 22
#Pattern: 1
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$"new sheet"
Node 1: #DATA$HSSFWorkbook
Node 2: #DATA$"workbook.xls"
Node 3: #DATA$FileOutputStream
Node 4: #METHOD_INVOCATION$close
Node 5: #METHOD_INVOCATION$FileOutputStream::<init>
Node 6: #METHOD_INVOCATION$write
Node 7: #DATA$"row sheet"
Node 8: #DATA$true
Node 9: #METHOD_INVOCATION$setSelected
Node 10: #METHOD_INVOCATION$createSheet
Node 11: #METHOD_INVOCATION$HSSFWorkbook::<init>
Node 12: #DATA$CellRangeAddress
Node 13: #DATA$5
Node 14: #DATA$2
Node 15: #DATA$2
Node 16: #DATA$2
Node 17: #METHOD_INVOCATION$CellRangeAddress::<init>
Node 18: #METHOD_INVOCATION$addMergedRegion
Node 19: #METHOD_INVOCATION$createSheet
Node 20: #DATA$1
Node 21: #DATA$"This is a test of merging"
Node 22: #METHOD_INVOCATION$setCellValue
Node 23: #METHOD_INVOCATION$createCell
Node 24: #METHOD_INVOCATION$createRow
Node 25: #DATA$1
0 -> 19
1 -> 11
2 -> 5
3 -> 5
5 -> 4
5 -> 6
11 -> 6
7 -> 10
8 -> 9
10 -> 9
11 -> 10
11 -> 19
12 -> 17
13 -> 17
14 -> 17
15 -> 17
16 -> 17
17 -> 18
19 -> 18
19 -> 24
20 -> 23
21 -> 22
23 -> 22
24 -> 23
25 -> 24
Pattern Code:
HSSFWorkbook wb = new HSSFWorkbook();
HSSFSheet sheet = wb.createSheet(new sheet);
HSSFRow row = sheet.createRow((short)1);
HSSFCell cell = row.createCell(1);
cell.setCellValue(This is a test of merging);
    sheet.addMergedRegion(new CellRangeAddress(2, 2, 2, 5));
HSSFSheet sheet1 = wb.createSheet(row sheet);
sheet1.setSelected(true);
FileOutputStream fileOut = new FileOutputStream(workbook.xls);
wb.write(fileOut);
fileOut.close();

Synthesized result:
org.apache.poi.ss.usermodel.Cell v6 = v2.createCell(0);
v6.setCellValue(true);
org.apache.poi.ss.util.CellRangeAddress v7 = v6.getArrayFormulaRange();
int v8 = v1.addMergedRegion(v7);
v1.setSelected(true);

==========
Synthesis costs: 1.485s
```