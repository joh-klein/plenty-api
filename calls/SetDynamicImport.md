# SetDynamicImport

Mit diesem Call kann ein Dynamischer Import ausgelöst werden

### Einschränkungen
* Jeder Call _muss_ eine Kopfzeile haben
* Pro Call können nur 1000 Datenzeilen + 1 Kopfzeile übertragen werden

### Erklärung
Paramter in *kursiv* sind optional. __Fettgedruckte__ sind pflicht.

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


### PHP-Code
```php
$response = $this->__soapCall(
	'SetDynamicImport', array(
		array(
			'Content' => array(
				array(
					'Value' => 'ItemID;ItemPosition'
				), array(
					'Value' => '1234;3'
				), array(
					'Value' => '5678;5'
				)
			),
			'FormatID' => 60,
			'Delimiter' => 3,
			'OnlyMatching' => true,
		)            
 	)
);
```

### XML
```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="http://plentymarketsdomain/plenty/api/soap/version106/">
	<soapenv:Header>
		<ns2:verifyingToken>
			<UserID>1</UserID>
			<Token>abc</Token>
		</ns2:verifyingToken>
	</soapenv:Header>
   <soapenv:Body>
      <ver:SetDynamicImport soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <oPlentySoapRequest_SetDynamicImport xsi:type="ver:PlentySoapRequest_SetDynamicImport">
            <!--You may enter the following 5 items in any order-->
            <FormatID xsi:type="xsd:int">?</FormatID>
            <FormatName xsi:type="xsd:string">?</FormatName>
            <Delimiter xsi:type="xsd:int">?</Delimiter>
            <OnlyMatching xsi:type="xsd:boolean">?</OnlyMatching>
            <Content xsi:type="ver:ArrayOfPlentysoapobject_string">
               <!--Zero or more repetitions:-->
               <item xsi:type="ver:PlentySoapObject_String">
                  <Value xsi:type="xsd:string">?</Value>
               </item>
            </Content>
         </oPlentySoapRequest_SetDynamicImport>
      </ver:SetDynamicImport>
   </soapenv:Body>
</soapenv:Envelope>
```