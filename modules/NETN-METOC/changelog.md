## Changelog NETN-METOC

### v1.0 - Initial version developed by MSG-163. Release included in NETN FOM v3.0



### v2.0 - Updates developed by MSG-191 and included in NETN FOM v4.0

* Replaced `Service` object class with `METOC_Service` 
* Replaced `EnvironmentCondition` object class with `METOC_EnvironmentCondition` 
* Replaced `EnvironmentCondition` attribute `ServiceId` with `METOC_EnvironmentCondition` attribute `Service` 
* Replaced `EnvironmentCondition` attribute `GeoReference` with `METOC_EnvironmentCondition` attribute `GeoReference` 
* Replaced `METOC_Root` attribute `UniqueId` with HLA-BASE `HLAobjectRoot` attribute `UniqueId` 
* Replaced `METOC_Root` attribute `Name` with `METOC_Service` attribute `Name` 
* Removed object class `METOC_Root` 
 
* Replaced `METOC_Interaction` parameter `EventId` with NETN-BASE `HLAinteractionRoot` parameter `UniqueId` 
* Removed interaction class `METOC_Interaction` 
 
* Replaced `Request` parameter `ServiceId` with `METOC_Request` parameter `Service` 
* Replaced `Request` parameter `GeoReference` with `METOC_Request` parameter `GeoReference` 
* Replaced `Request` parameter `UpdateAsObject` with `METOC_Request` parameter `UpdateAsObject` 
 
* Replaced `Response` parameter `EnvironmentObjectId` with `METOC_Response` parameter `EnvironmentObject` 
* Replaced `Response` parameter `GeoReference` with `METOC_Response` parameter `GeoReference` 
* Replaced `Response` parameter `Status` with `METOC_Response` parameter `Status` 
* Added `Response` parameter `Request` 
* Added `FederateControlActionEnum` Enumerated datatype. 
* Reamed `WeatherModelTypeEnum32` Enumerated datatype to `EnvironmentConditionModelTypeEnum32`

