# SetStocksTransfer

Mit diesem Call kann der Warenbestand eines Artikel zwischen zwei Lagerplätzen umgebucht werden.

### Einschränkungen
* Pro Call können nicht mehr als __25 Umbuchungen__ vorgenommen werden. *Hier gab es langezeit einen Fehler, dass nur ein Artikel pro Call umgebucht werden konnte. Gefixt in __v107__ (evtl. auch v106).*

### Erklärung
Paramter in *kursiv* sind optional. __Fettgedruckte__ sind pflicht.

* __SKU__
   * (Stock Keeping Unit) zusammengesetzt aus ArtikelID-PreisID-VariantenID
   * String
* *EAN*
   * String
* __Reason__
   * Umbuchungsgrund (Link zur Tabelle mit möglichen Werten)
   * Integer
* *CreditorID*
   * Lieferant-ID (?)
   * Integer
* __CurrentLocation__
   * aktueller Lagerort
   * Array
   * __StorageLocation__
      * Lagerort
      * String
   * __WarehouseID__
      * Lager-ID
      * Integer
* __NewLocation__
   * neuer Lagerort
   * Array
   * __StorageLocation__
      * Lagerort
      * String
   * __WarehouseID__
      * Lager-ID
      * Integer


### Beobachtungen
* Der "Standard-Lagerort" eines Lagers hat die *StorageLocation* 0.
* *PhysicalStock* akzeptiert auch negative Werte.
* Es heißt *SetStocksTransfer* aber *StockTransfers* …

### PHP-Code
```php
$response = $this->__soapCall(
   'SetStocksTransfer', array(
      array(
         'StockTransfers' => array(
            array(
               'SKU' => '123-123-123',
               'EAN' => '1234567890123',
               'Reason' => 100,
               'CreditorID' => 5,
               'PhysicalStock' => 1,
               'CurrentLocation' => array(
                  'StorageLocation' => '123',
                  'WarehouseID' => 1
               ),
               'NewLocation' => array(
                  'StorageLocation' => '123',
                  'WarehouseID' => 1
               )
            ),
            array(
               'SKU' => '123-123-123',
               'EAN' => '1234567890123',
               'Reason' => 100,
               'CreditorID' => 5,
               'PhysicalStock' => 1,
               'CurrentLocation' => array(
                  'StorageLocation' => '123',
                  'WarehouseID' => 1
               ),
               'NewLocation' => array(
                  'StorageLocation' => '123',
                  'WarehouseID' => 1
               )
            )            
         )
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
      <ver:SetStocksTransfer soapenv:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
         <oPlentySoapRequest_SetStocksTransfer xsi:type="ver:PlentySoapRequest_SetStocksTransfer">
            <StockTransfers xsi:type="ver:ArrayOfPlentysoapobject_setstockstransfer">
               <!--Zero or more repetitions:-->
               <item xsi:type="ver:PlentySoapObject_SetStocksTransfer">
                  <!--You may enter the following 7 items in any order-->
                  <SKU xsi:type="xsd:string">?</SKU>
                  <EAN xsi:type="xsd:string">?</EAN>
                  <Reason xsi:type="xsd:int">?</Reason>
                  <CreditorID xsi:type="xsd:int">?</CreditorID>
                  <PhysicalStock xsi:type="xsd:string">?</PhysicalStock>
                  <CurrentLocation xsi:type="ver:PlentySoapObject_StockLocation">
                     <!--You may enter the following 2 items in any order-->
                     <WarehouseID xsi:type="xsd:int">?</WarehouseID>
                     <StorageLocation xsi:type="xsd:string">?</StorageLocation>
                  </CurrentLocation>
                  <NewLocation xsi:type="ver:PlentySoapObject_StockLocation">
                     <!--You may enter the following 2 items in any order-->
                     <WarehouseID xsi:type="xsd:int">?</WarehouseID>
                     <StorageLocation xsi:type="xsd:string">?</StorageLocation>
                  </NewLocation>
               </item>
            </StockTransfers>
         </oPlentySoapRequest_SetStocksTransfer>
      </ver:SetStocksTransfer>
   </soapenv:Body>
</soapenv:Envelope>
```

### Links
http://man.plentymarkets.eu/soap-api/call-index/setstockstransfer/