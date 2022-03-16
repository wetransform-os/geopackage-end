# INSPIRE Good Practice: INSPIRE-compliant Encoding of END Reporting Data using GeoPackages

## Description of the Good Practice

This good practice describes a mechanism to deliver GeoPackage-encoded reporting data for the European Noise Directive in such a way that all requirements of the INSPIRE Implementing Rules for the relevant themes are met.

The good practice includes a total of ten GeoPackage logical data models derived from a set of extended and simplified conceptual models:

- DF1_5 Noise Sources:
    - Major Roads (extends INSPIRE Transport Networks Road `RoadLink`)
    - Major Railways (extends INSPIRE Transport Networks Railways `RailwayLink`)
    - Major Airports (extends INSPIRE Transport Networks Air `AerodromeNode`)
    - Agglomerations (extends INSPIRE Area Management `ManagementRestrictionOrRegulationZone`)
- DF4_8 Noise Exposure:
    - Agglomerations (extends INSPIRE Human Health and Safety `EnvHealthDeterminantMeasure`)
    - Major Airports (extends INSPIRE Human Health and Safety `EnvHealthDeterminantMeasure`)
	- Major Railways (extends INSPIRE Human Health and Safety `EnvHealthDeterminantMeasure`)
	- Major Roads (extends INSPIRE Human Health and Safety `EnvHealthDeterminantMeasure`)
- DF7_10 Noise Plans:
    - Noise Action Plans (extends INSPIRE Area Management `ManagementRestrictionOrRegulationZone`)
	- Quiet Areas (extends INSPIRE Area Management `ManagementRestrictionOrRegulationZone`)

## INSPIRE component(s)

This GP describes how data that falls under several INSPIRE data specifications (Area management, Human Health and Safety, Transport Networks) can be encoded in GeoPackage in such a way that the abstract requirements from these specifications are met.

*Note: This document does not describe a formal mechanism to publish data sets as a network service. The default option would be to use a Predefined Download service implemented via OpenSearch/ATOM Feed. Upcoming alternatives, such as STAC or direct file linking from metadata, would also work.*

## References

- [GeoPackage Encoding Rule for Environmental Noise Directive Reporting Data](https://www.eionet.europa.eu/reportnet/docs/noise/guidelines/geopackage-encoding-rule-end.pdf/view), v. 1.0 (2021-07-30)
- [Environmental Noise Directive - Data model documentation](https://www.eionet.europa.eu/reportnet/docs/noise/data-model-documentation/data_model_24062021.pdf/view), v. 3.0 (2021-06-24)  
- [GeoPackage Encoding Standard](https://www.geopackage.org/spec/), v. 1.3.0
- INSPIRE Transport Networks Data Specification, v. 4.0 
- INSPIRE Area management / restriction / regulation zones & reporting units, v. 4.0 
- INSPIRE Human Health and Safety Data Specification, v. 4.0 

## Other references

Supporting materials are available:
- [Video tutorials](https://www.eionet.europa.eu/reportnet/docs/noise/videos) and other help
- [Presentation at the INSPIRE conference 2021](https://inspire.ec.europa.eu/conference2021/livestream/4)

## Relevance & expected benefits

The Environmental Noise Directive 2002/49/EC (END) defines reporting obligations for assessing and managing environmental noise. The main aim of the END is to identify noise pollution levels and to trigger the necessary action both at Member State and at EU level. To pursue its stated aims the END focuses on the determination of exposure to environmental noise, ensuring information on environmental noise and its effects is made available to the public, and preventing and reducing environmental noise where necessary, preserving environmental noise quality where it is good. 

This Directive applies to noise to which humans are exposed, particularly in built-up areas, in public parks or other quiet areas in an agglomeration, in quiet areas in open country, near schools, hospitals and other noise-sensitive buildings and areas. It does not apply to noise that is caused by the exposed person himself, noise from domestic activities, noise created by neighbours, noise at workplaces or noise inside means of transport or due to military activities in military areas.

The END contains reporting provisions which require Member States (MS) to communicate information to the European Commission (EC) concerning the preparation and publication of strategic noise maps and noise management action plans for:

− All roads, railways, airports, and industrial sites within agglomerations with more than 100.000 inhabitants
− major roads (more than 3 million vehicles a year)
− major railways (more than 30.000 trains a year)
− major airports (more than 50.000 movements a year, including small aircrafts and helicopters).

The END reporting mechanism contains three data flows containing spatial information. These data flows have been developed to completely fulfil the requirements of the European Noise Directive. For each data flow, a data model has been developed that re-uses concepts and types from the matching INSPIRE data specifications. In each model related to spatial information, there is at least one spatial type that inherits from different INSPIRE feature types. For each of these models, a streamlined view has been developed, which is essentially a simplified INSPIRE model. The streamlined models are transformed to a GeoPackage logical schema, using different model transformation rules. 

The underlying GeoPackage Encoding Standard has been developed by the Open Geospatial Consortium and is built on SQLite. The GeoPackage Encoding Standard defines the schema for a GeoPackage, including table definitions, integrity assertions, format limitations, and content constraints. The required and supported content of a GeoPackage is entirely defined in the standard. 

The GeoPackage encoding of European Noise Directive data can thus be used to deliver data that fulfills the following requirements:

- It contains all information required for Noise Reporting
- It contains all necessary information to also derive compliant INSPIRE GML encoded data and thus comply with INSPIRE Implementing Rules

The GeoPackage templates have been developed for optimal usability and interoperability. They can be visualised and processed directly in any standard GIS environment. It is also possible to derive the data sets in the default encoding (GML) automatically to perform compliance tests.

The main benefits of the Good Practice are thus:
- To Data Providers:
  - more robust encoding than Excel/CSV files reduces number of schema and encoding errors
  - relatively simple data model focused on key values simplifies data preparation as compared to creating full INSPIRE GML
- To Data Users:
  - simplified data model aligns directly with use cases
  - GeoPackage encoded data can be directly used in GIS without any ETL process, with good performance

## Intended Outcome

The expected outcome is that the large majority of organisations that need to do noise reporting in the 2022 reporting cycle will use this mechanism to achieve compliance with INSPIRE and the END requirements. An update will be made for later reporting cycles.

## Evidence of implementation & support

The good practice does not require any specific tool support beyond basic support for the GeoPackage specification. GeoPackage is supported by all major GIS tools such as ArcGIS and QGIS, ETL tools such as hale studio and FME, and libraries such as GDAL/OGR. Since the good practice is built without dependencies on any extensions, and takes limitations of individual tools (such as maximum attribute name lengths or dependencies on the presence of spatial indexes) into account, it is compatible with these environments.

The good practice was developed with a focus on maximal interoperability. We thus decided not to use existing extensions to the GeoPackage standard, such as the [Related Tables](https://docs.opengeospatial.org/is/18-000/18-000.html) extension, or the [GeoPackage Metadata Profiles](https://gitlab.com/imagemattersllc/ogc-tb-16-gpkg/-/blob/master/extensions/7-metadata-profiles.adoc) extension. If these become widely supported later on, this good practice can be adjusted.

### Concrete implementations

The following concrete implementations of the good practice are known:

- EEA: EIONET/ReportNet ingests and validates END GeoPackages using FME Server
- RIVM (NL): Uses the geopackage templates directly to collect data from 99 reporting agencies and then aggregates them into 4 big geopackages, using hale connect
- UBA (DE): Uses a translated version of the geopackage schema as a template to collect data and then delivers aggregate GeoPackages, based on hale studio
- UBA (AT): ??

In addition, the GeoPackage templates are available as presets in hale studio since the release of version 4.1.0. There are also example hale studio transformation projects to generate compliant geopackages available in this repository.

### Support and Governance 

This best practice will be maintained by the European Environmental Agency, with technical support from wetransform GmbH and Epsilon Italia. A contract is in place to ensure sufficient resources for support and governance.

## Limitations

This Good Practice does not describe a full GeoPackage Encoding Rule for all kinds of INSPIRE data across all themes. Its applicability is limited to the extended and modified conceptual models specific to the European Noise Directive. Some patterns, such as factoring out contours for LDen and LNight into separate tables, are very specific to how this data is used.

The approach it is based on has been developed [here](https://github.com/INSPIRE-MIF/2017.2) and [here](https://github.com/IAAA-Lab/U2G/blob/master/GeoPackage/geopackage-encoding-rule.md), and can be applied beyond that scope, but needs to be specified in other good practices.