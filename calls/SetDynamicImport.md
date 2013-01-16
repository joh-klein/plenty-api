# SetDynamicImport

Mit diesem Call kann ein Dynamischer Import ausgelöst werden

### Einschränkungen
* Jeder Call _muss_ eine Kopfzeile haben
* Pro Call können nur 1000 Datenzeilen + 1 Kopfzeile übertragen werden

### Erklärung
Paramter in *kursiv* sind optional. __Fettgedruckte__ sind pflicht.

'Delimiter' => 3,
'OnlyMatching' => true,

* __Content__
   * 1 Kopfzeile + max. 1000 Datenzeilen
   * Array
* __FormatID__
   * ID des Dynamischen-Export-Formats
   * Int
* *FormatName*
   * Name des Dynamischen-Export-Formats
   * String
* __Delimiter__
	* Spaltentrenner:
		* 1: Tab
		* 2: Punkt (.)
		* 3: Semikolon (;)
   * Int
* __OnlyMatching__
	* Was passiert, wenn beim Abgleich *keine* Übereinstimmung gefunden wird
		* True: Datensatz überspringen
		* False: Datensatz anlegen
   * Boolean


