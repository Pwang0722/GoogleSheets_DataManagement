<h2 align="center">Goolge Apps Script for Multiple Sheets</h1>
</div>

### Example Sheet
- [Asia Content](https://danielpw.page.link/AsiaContent)
- [English Content](https://danielpw.page.link/EnglishContent)
---

### Introduction
Example of using the FILTER function to auto-fill similar inputs across multiple sheets and reformatting them with Apps Script.

---

### Ｍethod 

- Fill in the data under columns A to M in the sheet titled "TITLE LIST". Based on the data you have filled in, a code will be generated from a formula in column N.
- There is a formula in cell B19 in the sheets titled from "1B. ###" to "13A. ###", which retrieves the codes from column N in the "TITLE LIST" sheet and automatically fills in the data based on different requirements in each sheet.

  Formula example:
  ```bash
  =iferror(FILTER(List,('TITLE LIST'!N:N="ANIMAXCANTO FM00")+('TITLE LIST'!N:N="ANIMAXSOT ONLY00")))
  ```
---
