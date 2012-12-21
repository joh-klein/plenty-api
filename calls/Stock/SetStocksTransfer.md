# SetStocksTransfer

Mit dem Call werden Artikel von einem Lagerplatz auf einen anderen Lagerplatz umgebucht.

### Einschränkungen
* Pro Call können nicht mehr als 25 Umbuchungen vorgenommen werden. Hier gab es langezeit einen Fehler, dass man nur einen Artikel pro Call umbuchen konnte. Gefixt in __v107__ (evtl. auch v106)

### Beobachtungen
* 

### PHP-Code
```php
$response = $this->__soapCall('SetStocksTransfer', array(
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
            ),
         )
      )
   )
));
```

### XML
```xml
<soapenv:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="http://plentymarketsdomain/plenty/api/soap/version106/">
   <soapenv:Header/>
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