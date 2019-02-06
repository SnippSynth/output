query: how to set cell comments

query source: https://poi.apache.org/components/spreadsheet/quick-guide.html#CellComments

core api: setCellComment

manual code:
```
CreationHelper helper = wb.getCreationHelper();
Drawing drawing = sheet.createDrawingPatriarch();
ClientAnchor anchor = helper.createClientAnchor();
Comment comment1 = drawing.createCellComment(anchor);
RichTextString str1 = helper.createRichTextString("example comment");
comment1.setString(str1);
comment1.setAuthor("xxx");
Cell cell = sheet.createCell(0, 0);
cell.setCellComment(comment1);
```

test case:
```
boolean test(Cell cell) {
    return cell.getCellComment().getString().getString().equals("example comment");
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
4. TYPE:java.io.OutputStream NAME:v3

#Data flow graphs: 292
#Pattern: 4
Min pattern frequency: 4
Min pattern nodes num: 6
=========
Node 0: #DATA$"Apache POI"
Node 1: #METHOD_INVOCATION$setAuthor
Node 2: #METHOD_INVOCATION$createClientAnchor
Node 3: #METHOD_INVOCATION$getCreationHelper
Node 4: #METHOD_INVOCATION$createRichTextString
Node 5: #METHOD_INVOCATION$setString
Node 6: #METHOD_INVOCATION$setCellComment
Node 7: #METHOD_INVOCATION$createCellComment
Node 8: #METHOD_INVOCATION$createDrawingPatriarch
0 -> 1
7 -> 1
2 -> 7
3 -> 2
3 -> 4
4 -> 5
7 -> 5
7 -> 6
8 -> 7

Synthesized result:
org.apache.poi.ss.usermodel.CreationHelper v7 = v0.getCreationHelper();
org.apache.poi.ss.usermodel.Drawing v8 = v1.createDrawingPatriarch();
org.apache.poi.ss.usermodel.ClientAnchor v9 = v7.createClientAnchor();
org.apache.poi.ss.usermodel.Comment v10 = v8.createCellComment(v9);
org.apache.poi.ss.usermodel.RichTextString v11 = v7.createRichTextString("example comment");
v10.setString(v11);
v10.setAuthor("Apache POI");
org.apache.poi.ss.usermodel.Cell v12 = v2.createCell(1, 1);
v12.setCellComment(v10);

=========
Node 0: #METHOD_INVOCATION$createDrawingPatriarch
Node 1: #METHOD_INVOCATION$setAuthor
Node 2: #METHOD_INVOCATION$getCreationHelper
Node 3: #METHOD_INVOCATION$createRichTextString
Node 4: #METHOD_INVOCATION$setString
Node 5: #METHOD_INVOCATION$createCellComment
Node 6: #METHOD_INVOCATION$setCellComment
Node 7: #DATA$cell
0 -> 5
5 -> 1
2 -> 3
3 -> 4
5 -> 4
5 -> 6
7 -> 6

Synthesized result:
org.apache.poi.ss.usermodel.Drawing v7 = v1.createDrawingPatriarch();
org.apache.poi.ss.usermodel.CreationHelper v8 = v0.getCreationHelper();
org.apache.poi.ss.usermodel.ClientAnchor v9 = v8.createClientAnchor();
org.apache.poi.ss.usermodel.Comment v10 = v7.createCellComment(v9);
org.apache.poi.ss.usermodel.RichTextString v11 = v8.createRichTextString("example comment");
v10.setString(v11);
v10.setAuthor("example comment");
org.apache.poi.ss.usermodel.Cell v12 = v2.createCell(1, 1);
v12.setCellComment(v10);

=========
Node 0: #DATA$XSSFWorkbook
Node 1: #METHOD_INVOCATION$XSSFWorkbook::<init>
Node 2: #METHOD_INVOCATION$createSheet
Node 3: #DATA$5
Node 4: #METHOD_INVOCATION$setCellComment
Node 5: #METHOD_INVOCATION$createCell
Node 6: #METHOD_INVOCATION$createRow
Node 7: #DATA$3
0 -> 1
1 -> 2
2 -> 6
3 -> 5
5 -> 4
6 -> 5
7 -> 6

Synthesized result:
org.apache.poi.ss.usermodel.Sheet v7 = v0.createSheet();
int v7 = v0.getNumCellStyles();
org.apache.poi.ss.usermodel.Row v8 = v7.createRow(v7);
org.apache.poi.ss.usermodel.Cell v8 = v8.createCell(v7);
org.apache.poi.ss.usermodel.Comment v9 = v8.getCellComment();
v8.setCellComment(v9);

=========
Node 0: #DATA$commentText
Node 1: #METHOD_INVOCATION$createRichTextString
Node 2: #METHOD_INVOCATION$setString
Node 3: #METHOD_INVOCATION$createCellComment
Node 4: #METHOD_INVOCATION$setCellComment
Node 5: #DATA$cell
0 -> 1
1 -> 2
3 -> 2
3 -> 4
5 -> 4

Synthesized result:
org.apache.poi.ss.usermodel.Drawing v7 = v1.getDrawingPatriarch();
org.apache.poi.ss.usermodel.ClientAnchor v8 = v7.createAnchor(1, 1, 1, 1, 1, 1, 1, 1);
org.apache.poi.ss.usermodel.Comment v9 = v7.createCellComment(v8);
org.apache.poi.ss.usermodel.CreationHelper v10 = v0.getCreationHelper();
org.apache.poi.ss.usermodel.RichTextString v11 = v10.createRichTextString("example comment");
v9.setString(v11);
org.apache.poi.ss.usermodel.Cell v12 = v2.createCell(1, 1);
v12.setCellComment(v9);

==========
Synthesis costs: 4.979s
```