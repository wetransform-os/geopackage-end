# INSPIRE Good Practice: Encoding of INSPIRE Data using GeoPackages

Authors: Thorsten Reitz (wetransform), Darja Lihtenegger (EEA), Stefania Morrone (Epsion Italia)

## Description of the Good Practice

This Good Practice (GP) describes a mechanism to create INSPIRE data sets encoded using the GeoPackage standard. These data sets are compliant with the INSPIRE Implementing Rules (IR), and technical compliance can be shown through transformation to the Default Encoding. It can thus be used both as an additional and an alternative encoding for INSPIRE-identified data sets.

The process described here focuses on creating GeoPackage models optimised for usability in GIS environments. It can be used on core INSPIRE data specifications, or on extensions, and can also be use-case specific. This means that even for one INSPIRE theme, multiple logical schemas could, over time, become available. 

An example is the European Noise Directive (END) use case. For delivery of reporting data for the END, a conceptual model was developed that builds on INSPIRE data specifications, such as Human Health and Safety and Area Management. The END conceptual modle extends and re-uses feature types from these data specifications and then applies specific model transformation rules to arrive at a logical model optimised for the END. This optimised model is not a generic model for that INSPIRE data specification though.

For any geopackage logical schema to be accepted as an Annex to this GP, the following resources have to be created:

- A description of the logical model, its relevance and expected benefits, its implementations and its limitations compared to the default encoding
- An empty GeoPackage template file
- A formal, executable specification of the UML-to-Geopackage model transformation *or* the GML-to-GeoPackage model transformation that references the rules in the [common model transformation rules repository](https://github.com/INSPIRE-MIF/model-transformation-rules). These rules include rules that have to be applied always, e.g. on encoding of geometries, and rules that can be selected as needed. This specification can be delivered in any form that takes a computer-readable model as input and creates a computer-readable model. These specifications can be programs. They need to be documented in such a way that the mapping is human-readable. Examples can include an annoated ShapeChange configuration, an XSLT, or a hale studio model transformation.
- A formal, executable model for data transformation that allows to transform a data set encoded as GeoPackage to the Default Encoding. This can be delivered as an ETL workbench (e.g. hale studio transformation project, FME workbench), as a standalone program or as a service. In all cases, the executable model must be documented in a human-readable form.
 
The good practice was developed with a focus on maximal interoperability. It does not rely on existing extensions to the GeoPackage standard, such as the [Related Tables](https://docs.opengeospatial.org/is/18-000/18-000.html) extension, or the [GeoPackage Metadata Profiles](https://gitlab.com/imagemattersllc/ogc-tb-16-gpkg/-/blob/master/extensions/7-metadata-profiles.adoc) extension. If these become widely supported later on, this good practice can be adjusted.

## INSPIRE component(s)

This GP describes how data that falls under any INSPIRE Theme can be encoded in GeoPackage in such a way that the abstract requirements from these specifications are met. The GP relies on INSPIRE codelists, and transformation services.

*Note: This document does not describe a formal mechanism to publish data sets as a network service. The default option would be to use a Predefined Download service implemented via OpenSearch/ATOM Feed. Upcoming alternatives, such as STAC or direct file linking from metadata, would also work.*

## References

- [GeoPackage Encoding Standard](https://www.geopackage.org/spec/), v. 1.3.0
- [Common Model Transformation Rules](https://github.com/INSPIRE-MIF/model-transformation-rules)

## Other references

Supporting materials are available:

- The approach it is based on has been developed [here](https://github.com/INSPIRE-MIF/2017.2) and [here](https://github.com/IAAA-Lab/U2G/blob/master/GeoPackage/geopackage-encoding-rule.md).
- The GP has been applied to create the [GeoPackage Encoding Rule for Environmental Noise Directive Reporting Data](https://www.eionet.europa.eu/reportnet/docs/noise/guidelines/geopackage-encoding-rule-end.pdf/view), v. 1.0 (2021-07-30).

## Relevance & expected benefits

The underlying GeoPackage Encoding Standard has been developed by the Open Geospatial Consortium and is built on SQLite. The GeoPackage Encoding Standard defines the schema for a GeoPackage, including table definitions, integrity assertions, format limitations, and content constraints. The required and supported content of a GeoPackage is entirely defined in the standard. 

GeoPackage is well supported by common desktop, mobile and Web GIS platforms, as well as by ETL tools. The transformation rules for GeoPackage templates have been developed for optimal usability and interoperability. They can be visualised and processed directly in any standard GIS environment. It is also possible to derive the data sets in the default encoding (GML) automatically to perform compliance tests.

The main benefits of the Good Practice are thus:

- To Data Providers:
  - The relatively simple data models focus on key values, which simplifies data harmonisation as compared to creating full INSPIRE GML
  - More robust encoding reduces number of schema and encoding errors
- To Data Users:
  - The simplified data model aligns directly with use cases
  - GeoPackage encoded data can be directly used in GIS without any ETL process, with good performance

## Intended Outcome

The expected outcome is that the various communities of INSPIRE implementers create logical data models for GeoPackage for a wide range of INSPIRE themes and use cases. To make sure interoperability and compliance are guaranteed, all these implementers rely on the common process and set of rules described in this good practice.

## Evidence of implementation & support

The good practice does not require any specific tool support beyond basic support for the GeoPackage specification. GeoPackage is supported by all major GIS tools such as ArcGIS and QGIS, ETL tools such as hale studio and FME, and libraries such as GDAL/OGR. Since the good practice is built without dependencies on any extensions, and takes limitations of individual tools (such as maximum attribute name lengths or dependencies on the presence of spatial indexes) into account, it is compatible with these environments.

The Good Practice also requires the submission of formal model transformation and data tranformation rules for each data model. A simple mapping table is not considered sufficent. To create these formal rules, model transformation tools such as ShapeChange as well as data transformation tools such as hale studio and FME can be used. 

### Concrete implementations

The following concrete implementations of the good practice are known:

- EEA END (Extension of Transport Networks, Human Health and Safety, and )
- HaDEA GO-PEG: GO-DEPTH (Extension of Geology) 
- DK: ...

### Support and Governance 

This best practice will be maintained by [wetransform GmbH](https://www.wetransform.to/) and [Epsilon Italia](https://www.epsilon-italia.it/). A contract is in place to ensure sufficient resources for support and governance.

## Limitations

This Good Practice only describes the framework in which specific GeoPackage logical models for INSPIRE-identified data sets are created. The actual logical models are defined in annexes. 

