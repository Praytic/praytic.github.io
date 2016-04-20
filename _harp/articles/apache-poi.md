# Apache POI

### 1. Общее

1. **Apache POI** - опенсорсное API, позволяющее создавать, модифицировать и отображать документы Microsoft Office используя Java код. <sup>[\[3.9\]][apache-poi-3.9]</sup>

### 2. Компоненты

1. **POIFS (Poor Obfuscation Implementation File System)** - базовый управляющий компонент для всех POI элементов. Он используется для явного чтения различных файлов.

1. **HSSF (Horrible Spreadsheet Format)** - компонент, который используется для чтения и записи формата .xls MS-Excel файлов. <sup>[\[3.9\]][hssf-3.9]</sup>

1. **XSSF (XML Spreadsheet Format)** - компонент, который используется для чтения и записи формата .xlsx MS-Excel файлов. <sup>[\[3.9\]][xssf-3.9]</sup>

1. **HPSF (Horrible Property Set Format)** - компонент, который используется для извлечения пропертей из MS-Office файлов. <sup>[\[3.9\]][hpsf-3.9]</sup>

1. **HWPF (Horrible Word Processor Format)** - компонент, который используется для чтения и записи формата .doc MS-Word файлов. <sup>[\[3.9\]][hwpf-3.9]</sup>

1. **XWPF (XML Word Processor Format)** - компонент, который используется для чтения и записи формата .docx MS-Word файлов. <sup>[\[3.9\]][xwpf-3.9]</sup>

1. **HSLF (Horrible Slide Layout Format)** - компонент, который используется для чтения и записи MS-PowerPoint файлов. <sup>[\[3.9\]][hslf-3.9]</sup>

1. **HDGF (Horrible DiaGram Format)** - компонент, который используется для чтения и записи MS-Visio файлов. <sup>[\[3.9\]][hdgf-3.9]</sup>

1. **HPBF (Horrible PuBlisher Format)** - компонент, который используется для чтения и записи MS-Publisher файлов. <sup>[\[3.9\]][hpbf-3.9]</sup>

### 3. Классы и интерфейсы

1. **`Workbook`** - базовый интерфейс для всех классов, которые создают или обрабатывают Excel документы.
  - Он находится в `org.apache.poi.ss.usermodel` пакете. <sup>[\[3.9\]][workbook-3.9]</sup>
  - Его реализуют следующие классы:
    + **`HSSFWorkbook`** - класс для чтения и записи файлов .xls формата. Поддерживает 1997-2003 версии MS-Office. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFWorkbook`** - класс для чтения и записи файлов .xlsx формата. Поддерживает 2007+ версии MS-Office. Он находится в `org.apache.poi.xssf.usermodel` пакете.

1. **`Sheet`** - базовый интерфейс для всех классов, которые создают таблицы произвольного типа. Наиболее распространенной таблицей является worksheet, которая представлена сеткой ячеек. <sup>[\[3.9\]][sheet-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFSheet`** - класс для создания excel таблиц и редактирования данных и стилей этих таблиц. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFSheet`** - класс для создания excel таблиц и редактирования данных и стилей этих таблиц. Он находится в `org.apache.poi.xssf.usermodel` пакете.
  
1. **`Row`** - базовый интерфейс для всех классов, которые представляют строку таблицы. <sup>[\[3.9\]][row-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`XSSFRow`** - класс для представления строк в таблице. Он находится в `org.apache.poi.xssf.usermodel` пакете.
    
1. **`Cell`** - базовый интерфейс для всех классов, которые представляют ячейки в строках таблицы. <sup>[\[3.9\]][cell-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`XSSFCell`** - класс для представления ячеек в таблице. Он находится в `org.apache.poi.xssf.usermodel` пакете.
    + **`XSSFCell`** - класс для представления ячеек в таблице. Он находится в `org.apache.poi.xssf.usermodel` пакете.

1. **`CellStyle`** - базовый интерфейс для всех классов, которые представляют собой стиль ячейки. <sup>[\[3.9\]][cellstyle-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFCellStyle`** - класс для представления ячеек в таблице. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFCellStyle`** - класс для представления ячеек в таблице. Он находится в `org.apache.poi.xssf.usermodel` пакете.
  
1. **`Color`** - базовый интерфейс для всех классов, которые представляют цвет ячейки. <sup>[\[3.9\]][color-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFColor`** - класс для регулирования цвета ячеек в таблице. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFColor`** - класс для регулирования цвета ячеек в таблице. Он находится в `org.apache.poi.xssf.usermodel` пакете.
    
1. **`Font`** - базовый интерфейс для всех классов, которые представляют шрифт текста ячейки. <sup>[\[3.9\]][font-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFColor`** - класс для регулирования шрифта текста ячеек в таблице. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFColor`** - класс для регулирования шрифта текста ячеек в таблице. Он находится в `org.apache.poi.xssf.usermodel` пакете.
    
1. **`Hyperlink`** - базовый интерфейс для всех классов, которые представляют гиперссылку. <sup>[\[3.9\]][hyperlink-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFColor`** - класс для представления гиперссылки. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFColor`** - класс для представления гиперссылки. Он находится в `org.apache.poi.xssf.usermodel` пакете.
    
1. **`CreationHelper`** - базовый интерфейс для всех классов, которые являются используются при вычислении формулы ячейки и для создания гиперссылок. <sup>[\[3.9\]][creationhelper-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFCreationHelper`** - класс для вычисления формулы ячейки и для создания гиперссылок. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFCreationHelper`** - класс для вычисления формулы ячейки и для создания гиперссылок. Он находится в `org.apache.poi.xssf.usermodel` пакете.
    
1. **`PrintSetup`** - базовый интерфейс для всех классов, которые регулируют размер, область, параметры распечатываемой страницы. <sup>[\[3.9\]][printsetup-3.9]</sup>
  - Он находится в `org.apache.poi.ss.usermodel` пакете.
  - Его реализуют следующие классы:
    + **`HSSFColor`** - класс для регулирования размера, области, параметров распечатываемой страницы. Он находится в `org.apache.poi.hssf.usermodel` пакете.
    + **`XSSFColor`** - класс для регулирования размера, области, параметров распечатываемой страницы. Он находится в `org.apache.poi.xssf.usermodel` пакете.

[printsetup-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[creationhelper-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[hyperlink-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[font-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[color-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[cellstyle-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[cell-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[row-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[sheet-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[workbook-3.9]: www.tutorialspoint.com/apache_poi/apache_poi_core_classes.htm
[hssf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[xssf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[hpsf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[hwpf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[xwpf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[hslf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[hdgf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[hpbf-3.9]: http://www.tutorialspoint.com/apache_poi/apache_poi_overview.htm
[apache-poi-3.9]: http://www.tutorialspoint.com/apache_poi/index.htm
