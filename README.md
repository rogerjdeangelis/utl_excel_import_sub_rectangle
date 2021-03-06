# utl_excel_import_sub_rectangle
Import a arbitrary sub rectangle with a spreadsheet using SAS

    ```  %let pgm=utl_xlsx_import_sub_rectangle;  ```
    ```    ```
    ```  How to import an excel file with selected rows containing column name?  ```
    ```    ```
    ```    ```
    ```      WORKING CODE  ```
    ```    ```
    ```           libname xel "d:/xls/have.xlsx";  ```
    ```           set xel.'sheet1$A3:F99'n(firstobs=50);  ```
    ```    ```
    ```  see  ```
    ```  https://goo.gl/kWJ6NV  ```
    ```  https://communities.sas.com/t5/Base-SAS-Programming/  ```
    ```  How-to-import-an-excel-file-with-selected-rows-as-column-name/m-p/392328  ```
    ```    ```
    ```    ```
    ```    ```
    ```  HAVE  ```
    ```  ====  ```
    ```    ```
    ```  d:/xls/have.xlsx  ```
    ```    ```
    ```      |-----------------------------------------------------------+  ```
    ```  1   |   A     |   B     |   C     |   D     |   E     |    F    |  ```
    ```      |---------+---------+---------+---------+---------+---------|  ```
    ```  2   |MASTERC  |A        |B        |C        |D        |E        |  ```
    ```      |---------+---------+---------+---------+---------+---------|  ```
    ```  3   |Months   |Jan-17   |Feb-17   |Mar-17   |Apr-17   |May-17   | Use this row for column names  ```
    ```      |---------+---------+---------+---------+---------+---------+  ```
    ```  4   |Loss     |1        |2        |3        |4        |5        |  ```
    ```      |---------+---------+---------+---------+---------+---------+  ----+  ```
    ```  5   |Recov    |6        |7        |8        |9        |10       |      |  ```
    ```      |---------+---------+---------+---------+---------+---------+      |  ```
    ```  6   |Recov    |6        |7        |8        |9        |10       |      |  ```
    ```      |---------+---------+---------+---------+---------+---------+      |  ```
    ```  7   |Recov    |6        |7        |8        |9        |10       |      | Want just these rows  ```
    ```      |---------+---------+---------+---------+---------+---------+      |  ```
    ```  8   |Recov    |6        |7        |8        |9        |10       |      |  ```
    ```      |---------+---------+---------+---------+---------+---------+      |  ```
    ```  9   |Recov    |6        |7        |8        |9        |10       |      |  ```
    ```      ------------------------------------------------------------- -----+  ```
    ```    ```
    ```      .....  ```
    ```    ```
    ```    ```
    ```  WANT  (skip over Loss row)  ```
    ```    ```
    ```  Up to 40 obs WORK.WANT total obs=5  ```
    ```    ```
    ```  Obs    MONTHS    JAN_17    FEB_17    MAR_17    APR_17    MAY_17  ```
    ```    ```
    ```   1     Recov       6         7         8         9         10  ```
    ```   2     Recov       6         7         8         9         10  ```
    ```   3     Recov       6         7         8         9         10  ```
    ```   4     Recov       6         7         8         9         10  ```
    ```   5     Recov       6         7         8         9         10  ```
    ```    ```
    ```    ```
    ```  *                _              _       _  ```
    ```   _ __ ___   __ _| | _____    __| | __ _| |_ __ _  ```
    ```  | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |  ```
    ```  | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |  ```
    ```  |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|  ```
    ```    ```
    ```  ;  ```
    ```    ```
    ```  %utlfkil(d:/xls/have.xlsx);      * just in case it exists;  ```
    ```    ```
    ```  libname xel "d:/xls/have.xlsx";  ```
    ```    ```
    ```  data xel.have;  ```
    ```  informat MasterC A B C D E $12.;  ```
    ```  input  MasterC A B C D E;  ```
    ```  output;  ```
    ```  if _n_> 3 then do;  ```
    ```    do rec=1 to 5;  ```
    ```      output;  ```
    ```    end;  ```
    ```  end;  ```
    ```  cards4;  ```
    ```  Calen . . . . .  ```
    ```  Months Jan-17 Feb-17 Mar-17 Apr-17 May-17  ```
    ```  Loss 1 2 3 4 5  ```
    ```  Recov 6 7 8 9 10  ```
    ```  ;;;;  ```
    ```  run;quit;  ```
    ```    ```
    ```  libname xel clear;  ```
    ```    ```
    ```  *          _       _   _  ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __  ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \  ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |  ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|  ```
    ```    ```
    ```  ;  ```
    ```    ```
    ```  libname xel "d:/xls/have.xlsx";  ```
    ```    ```
    ```  data want;  ```
    ```     set xel.'have$A3:F99'n(firstobs=3);  ```
    ```  run;quit;  ```
    ```    ```
    ```  libname xel clear;  ```
    ```    ```
    ```    ```
    ```    ```
    ```    ```
    ```    ```
    ```    ```
