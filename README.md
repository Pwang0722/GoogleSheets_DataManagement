<h2 align="center">Google Sheets: Efficient Data Management with Apps Script and Formulas</h1>
</div>

### Spreadsheet Examples
- [Asia Content](https://danielpw.page.link/AsiaContent)
- [English Content](https://danielpw.page.link/EnglishContent)
---

### Outline
An example of using the FILTER function to auto-fill similar inputs across multiple worksheets and reformatting them with Apps Script.

---

### Ｍethod 
Take spreadsheet [Asia Content](https://danielpw.page.link/AsiaContent) as an example:
- Fill in the data under columns A to M in the sheet titled "TITLE LIST". Based on the data you have filled in, a code will be generated from a formula in column N.
- There is a formula in cell B19 in the sheets titled from "1B. ###" to "13A. ###", which retrieves the codes from column N in the "TITLE LIST" sheet and automatically fills in the data based on different requirements in each sheet.

Formula example:
  ```bash
  =iferror(FILTER(List,('TITLE LIST'!N:N="ANIMAXCANTO FM00")+('TITLE LIST'!N:N="ANIMAXSOT ONLY00")))
  ```
 - Lastly, running the Apps Script to tidy up multiple sheets, including hiding and deleting unnecessary columns, rows, and data.

  Apps Script example:
  ```bash
  function HideAndDelete() {
  var spreadsheet = SpreadsheetApp.getActive();
  ["1B.NTV-HD","1C.TVB-HD","2A.MAC-SD","3A.TRV-HD & SD","3C.Triple T-SD","4B.AST-HD","4D.AST-DIGITAL","4E.TMNet-HD","5A.ME-HD","5B.SH-HD","5E.ST-HD","5F.PPCTV-SD","5G.WEW-HD","6A.MNC-HD","6C.FIM-HD","6D.TNV-HD","6J.DensTV-HD","6K.NEX-P","7A.SKC-SD","7C.PHP-GEN-SD","7D.CIGNAL-SD","8A.Media-HD","8B.Dhiraagu-HD","11A.Canal+ -HD"].forEach(function (s){
  spreadsheet.setActiveSheet(spreadsheet.getSheetByName(s), true);
  spreadsheet.getRange('A18:L55').activate();
  spreadsheet.getRange('A18:L55').copyTo(spreadsheet.getActiveRange(), SpreadsheetApp.CopyPasteType.PASTE_VALUES, false);
  spreadsheet.getRange('G:G').activate();
  spreadsheet.getActiveSheet().hideColumns(spreadsheet.getActiveRange().getColumn(), spreadsheet.getActiveRange().getNumColumns());
  spreadsheet.getRange('A:A').activate();
  spreadsheet.getActiveSheet().hideColumns(spreadsheet.getActiveRange().getColumn(), spreadsheet.getActiveRange().getNumColumns());
  spreadsheet.getRange('5:16').activate();
  spreadsheet.getActiveSheet().hideRows(spreadsheet.getActiveRange().getRow(), spreadsheet.getActiveRange().getNumRows());
  spreadsheet.getRange('2:2').activate();
  spreadsheet.getActiveSheet().hideRows(spreadsheet.getActiveRange().getRow(), spreadsheet.getActiveRange().getNumRows());
  spreadsheet.getRange('K3:L4').activate();
  spreadsheet.getActiveRangeList().clear({contentsOnly: true, skipFilteredRows: true});
    
})
};


function HideRow() {
  var ss = SpreadsheetApp.getActive();
  ["1B.NTV-HD","1C.TVB-HD","2A.MAC-SD","3A.TRV-HD & SD","3C.Triple T-SD","4B.AST-HD","4D.AST-DIGITAL","4E.TMNet-HD","5A.ME-HD","5B.SH-HD","5E.ST-HD","5F.PPCTV-SD","5G.WEW-HD","6A.MNC-HD","6C.FIM-HD","6D.TNV-HD","6J.DensTV-HD","6K.NEX-P","7A.SKC-SD","7C.PHP-GEN-SD","7D.CIGNAL-SD","8A.Media-HD","8B.Dhiraagu-HD","11A.Canal+ -HD"].forEach(function (s){
  var sheet = ss.getSheetByName(s);
  var values=sheet.getRange(1,1,45,12).getValues();
  values.forEach(function(r,i){
    if(r[0]=='') {
      sheet.hideRows(i+1)
    }
  });
  })
}
  ```
---
