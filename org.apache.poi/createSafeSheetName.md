query: create excel sheet name with valid characters for "safe/?*name"

query source: https://stackoverflow.com/questions/451452/valid-characters-for-excel-sheet-names

core api: createSafeSheetName

manual code:
```
Sheet sheet = wb.createSheet();
sheet.setSheetName(WorkbookUtil.createSafeSheetName("safe/?*name"));
```

test case:
```
boolean test(Sheet sheet) {
    return sheet.getSheetName.equals("safe   name");
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

#Data flow graphs: 75
#Pattern: 5
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$"second sheet"
Node 1: #OP$ASSIGNMENT
Node 2: #DATA$WorkbookUtil
Node 3: #DATA$1
Node 4: #DATA$HSSFWorkbook
Node 5: #DATA$"workbook.xls"
Node 6: #DATA$FileOutputStream
Node 7: #METHOD_INVOCATION$close
Node 8: #METHOD_INVOCATION$FileOutputStream::<init>
Node 9: #METHOD_INVOCATION$write
Node 10: #METHOD_INVOCATION$createSheet
Node 11: #DATA$"new sheet"
Node 12: #METHOD_INVOCATION$createSheet
Node 13: #METHOD_INVOCATION$HSSFWorkbook::<init>
Node 14: #METHOD_INVOCATION$setSheetName
Node 15: #METHOD_INVOCATION$createSafeSheetName
0 -> 1
1 -> 15
2 -> 15
3 -> 14
4 -> 13
5 -> 8
6 -> 8
8 -> 7
8 -> 9
13 -> 9
13 -> 10
11 -> 12
13 -> 12
13 -> 14
15 -> 14

Synthesized result:
org.apache.poi.ss.usermodel.Sheet v6 = v0.createSheet();
String v7 = org.apache.poi.ss.util.WorkbookUtil.createSafeSheetName("safe/?*name");
v0.setSheetName(0, v7);
try {
v0.write(v3);
v0.close();
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$"[O'Brien's sales*?]"
Node 1: #DATA$WorkbookUtil
Node 2: #DATA$HSSFWorkbook
Node 3: #DATA$"workbook.xls"
Node 4: #DATA$FileOutputStream
Node 5: #METHOD_INVOCATION$close
Node 6: #METHOD_INVOCATION$FileOutputStream::<init>
Node 7: #METHOD_INVOCATION$write
Node 8: #DATA$"second sheet"
Node 9: #METHOD_INVOCATION$createSheet
Node 10: #DATA$"new sheet"
Node 11: #METHOD_INVOCATION$createSheet
Node 12: #METHOD_INVOCATION$HSSFWorkbook::<init>
Node 13: #METHOD_INVOCATION$createSheet
Node 14: #METHOD_INVOCATION$createSafeSheetName
0 -> 14
1 -> 14
2 -> 12
3 -> 6
4 -> 6
6 -> 5
6 -> 7
12 -> 7
8 -> 9
12 -> 9
10 -> 11
12 -> 11
12 -> 13
14 -> 13
Synthesized result:
org.apache.poi.ss.usermodel.Sheet v6 = v0.createSheet();
String v6 = org.apache.poi.ss.util.WorkbookUtil.createSafeSheetName(v6);
try {
v0.write(v3);
v0.close();
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$"[O'Brien's sales*?]"
Node 1: #DATA$WorkbookUtil
Node 2: #DATA$XSSFWorkbook
Node 3: #DATA$FileOutputStream
Node 4: #METHOD_INVOCATION$close
Node 5: #METHOD_INVOCATION$FileOutputStream::<init>
Node 6: #METHOD_INVOCATION$write
Node 7: #DATA$"second sheet"
Node 8: #METHOD_INVOCATION$createSheet
Node 9: #DATA$"new sheet"
Node 10: #METHOD_INVOCATION$createSheet
Node 11: #METHOD_INVOCATION$XSSFWorkbook::<init>
Node 12: #METHOD_INVOCATION$createSheet
Node 13: #METHOD_INVOCATION$createSafeSheetName
0 -> 13
1 -> 13
2 -> 11
3 -> 5
5 -> 4
5 -> 6
11 -> 6
7 -> 8
11 -> 8
9 -> 10
11 -> 10
11 -> 12
13 -> 12

Synthesized result:
v0.close();
org.apache.poi.ss.usermodel.Sheet v6 = v0.createSheet();
String v6 = org.apache.poi.ss.util.WorkbookUtil.createSafeSheetName(v6);
try {
v0.write(v3);
} catch(Exception e) {
e.printStackTrace();
}

=========
Node 0: #DATA$WorkbookUtil
Node 1: #METHOD_INVOCATION$createSafeSheetName
Node 2: #METHOD_INVOCATION$setCellValue
Node 3: #METHOD_INVOCATION$createCell
Node 4: #DATA$0
Node 5: #METHOD_INVOCATION$setCellValue
Node 6: #METHOD_INVOCATION$createCell
Node 7: #METHOD_INVOCATION$createRow
Node 8: #METHOD_INVOCATION$createSheet
0 -> 1
1 -> 8
3 -> 2
7 -> 3
4 -> 6
6 -> 5
7 -> 6
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.Sheet v6 = v0.createSheet();
String v6 = org.apache.poi.ss.util.WorkbookUtil.createSafeSheetName(v6);
org.apache.poi.ss.usermodel.Row v7 = v6.createRow(v6);
org.apache.poi.ss.usermodel.Cell v7 = v7.createCell(v6);
v7.setCellValue(v6);
org.apache.poi.ss.usermodel.Cell v8 = v7.createCell(v6);

=========
Node 0: #DATA$WorkbookUtil
Node 1: #DATA$HSSFWorkbook
Node 2: #BINARY$+
Node 3: #DATA$FileOutputStream
Node 4: #METHOD_INVOCATION$FileOutputStream::<init>
Node 5: #METHOD_INVOCATION$write
Node 6: #METHOD_INVOCATION$HSSFWorkbook::<init>
Node 7: #METHOD_INVOCATION$createSheet
Node 8: #METHOD_INVOCATION$createSafeSheetName
0 -> 8
1 -> 6
2 -> 4
3 -> 4
4 -> 5
6 -> 5
6 -> 7
8 -> 7

Synthesized result:
String v6 = org.apache.poi.ss.util.WorkbookUtil.createSafeSheetName(v6);
org.apache.poi.ss.usermodel.Sheet v6 = v0.createSheet();
try {
v0.write(v3);
} catch(Exception e) {
e.printStackTrace();
}

==========
Synthesis costs: 1.596s
```