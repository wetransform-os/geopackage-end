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

- GeoPackage Encoding Rule for Environmental Noise Directive Reporting Data, v. 1.0 (2021-07-30)
- Environmental Noise Directive - Data model documentation, v. 3.0 (2021-04-07)  
- GeoPackage Encoding Standard version, v. 1.3.0
- INSPIRE Transport Networks Data Specification, v. 4.0 
- INSPIRE Area management / restriction / regulation zones & reporting units, v. 4.0 
- INSPIRE Human Health and Safety Data Specification, v. 4.0 

## Other references

Supporting materials are available:
- Video tutorials and other help
- Presentation at the INSPIRE conference 2021

## Relevance & expected benefits

Describe why the GP was developed. In the description, please explain whether the GP 
•	aims at meeting (some of) the INSPIRE requirements  AND/OR
•	goes beyond the requirements of the IRs and TGs in order to improve the usability / usefulness of the infrastructure (including INSPIRE extensions) AND/OR
•	is using INSPIRE data or services to perform a certain task
and what the expected benefits are for INSPIRE implementers, users or other stakeholders.
A full text description of the problem addressed by the GP may also be provided. It can be any length but is likely to be no more than a few sentences. 

## Intended Outcome

Describe what should be possible to do when following the GP. 

## Evidence of implementation & support

The good practice does not require any specific tool support beyond basic support for the GeoPackage specification. GeoPackage is supported by all major GIS tools such as ArcGIS and QGIS, ETL tools such as hale studio and FME, and libraries such as GDAL/OGR. Since the good practice is built without dependencies on any extensions, and takes limitaitons of individual tools (such as maximum attribute name lengths or dependencies on the presence of spatial indexes) into account, it is compatible with these environments.

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