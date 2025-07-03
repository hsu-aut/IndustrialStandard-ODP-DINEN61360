# DIN EN 61360 Ontology-Design-Pattern

## Introduction

The development of software functionalities, or applications in general, that monitor and analyze manufacturing related data in order to improve, support or automate processes, is becoming increasingly important in industry. These applications require several information from different data sources in their context. An application that is planning a maintenance workers daily schedule for instance, requires several information about machine statuses, production plans and inventory, which resides in different systems likes Programmable Logical Controllers (PLC) or Structured Query Language (SQL) databases. Furthermore, manufacturing companies usually run machines and software systems from different vendors or of different ages. The schemata used in such systems do therefore not follow a certain standard, i.e. they are very heterogeneous in their semantics. When building such applications, accessing, searching and understanding the data sources is becoming a very time intensive, manual and error prone procedure that is repeated for every newly build application and for every newly introduced data source. To allow for an eased access, searching and understanding of these heterogeneous data sources, an ontology can be used to integrate all heterogeneous data sources in one schemata. 

This repository contains an ontology of DIN EN 61360 which is a standard to describe properties. We maintain a whole list of standard-based ontologies, check out these links:
 - [VDI 2206](https://github.com/hsu-aut/IndustrialStandard-ODP-VDI2206)
 - [VDI 2860](https://github.com/hsu-aut/IndustrialStandard-ODP-VDI2860)
 - [VDI 3682](https://github.com/hsu-aut/IndustrialStandard-ODP-VDI3682)
 - [DIN 8580](https://github.com/hsu-aut/IndustrialStandard-ODP-DIN8580)
 - [ISA 88](https://github.com/hsu-aut/IndustrialStandard-ODP-ISA88)
 - [WADL](https://github.com/hsu-aut/IndustrialStandard-ODP-WADL)
 - [DIN EN 62264-2](https://github.com/hsu-aut/IndustrialStandard-ODP-DINEN62264-2)
 - [OPC UA](https://github.com/hsu-aut/IndustrialStandard-ODP-OPC-UA)
 - [ISO 22400-2](https://github.com/hsu-aut/IndustrialStandard-ODP-ISO22400-2)


## DIN EN 61360

The DIN EN 61360 [1] defines concepts to describe properties of technical systems. The properties are described as "data elements"
(e.g. lot size, filling level, error codes, live values, ...) and can be used to characterize a technical system.

Data elements can be described by a type description and an instance description. This brings the benefit of a uniform meta description that distinguishes between type descriptions, used to classify possible properties 
or characteristics in general, and instances that can be used to express certain values of a property (e.g. lot size = 4). 
The type description represents the characteristics of a physical or logical object that can be used to describe this object 
(e.g. unit of measure for the lot size). According to [1] the attributes of a type description can be classified as follows: 
-	Identifying attributes: e.g. ID, preferred name, version number
-	Semantic attributes: e.g. definition, source document for definition of the data element type, formula 
-	Value related attributes: e.g. data type, unit of measure, value list
-	Relational attributes: e.g. superordinate classes of the data element type

</br>
Please note, that all descriptions of attributes behind these four classes can be found in detail in [1].

Whenever a data element is instantiated, this data element receives an additional 
instance de-scription. The instance description complements the type description with further details, e.g. a measured value 
(e.g. lot size = “4”). In order to describe the data elements in a machine-interpretable way, attributes have to be used to further 
describe a type or an instance of a data element. 

With respect to [2], the attributes that represent the instance description of a data element are subsequently explained. The “Value” represents a measurable value of the instance. The attribute “Interpretation Logic” can be used to indicate a 
logical interpretation of the value, e.g. less than/ greater than / equal / not equal. The quality indicates the quality of the value, in means of quality of measure. The “Expression Goal” is used to indicate whether a data element represents:
-	**Requirements** expression: the data element is used to describe a requirement (e.g. an order requires the lot size “4”)
-	**Assurance** expression: the data element is used to describe an assurance (e.g. a machine asssures to produce with lot size “4”)
-	**Actual_Value**: the data element is used to describe a measured value (e.g. the actual produce lot size was “3”)
-	**Variable**: The data element doesn't have a value yet and this value may be calculated during planning or set during execution

![](./pictures/DINEN61360_LWO.png?raw=true "DIN EN 61360 LWO")<br></br>
Figure 1: Type and instance description of data elements according to DIN EN 61360

Exemplary Competency Questions that could be answered with this ODP:<br></br>
Table 1: Example Competency Questions
![](./pictures/DINEN61360_exCQ.png?raw=true "exampleCQ")

[1]: DIN EN 61360-1. Standard data element types with associated classification scheme Part 1: Definitions - Principles and methods, 
06.2018 <br></br>
[2]: EPPLE, Ulrich: Merkmale als Grundlage der Interoperabilität technischer Systeme. 
In: at - Automa-tisierungstechnik 59 (2011), Nr. 7, S. 440–450 <br></br>


## Usage
If you want to this ontology design pattern, the easiest way is to directly import it into your ontology via `owl:imports` statements. Simply use the ontology IRI (W3ID) to import and make sure to reference a fixed release version so that you can't get surprised by future changes. Simply take the latest release or pick a specific version in case you don't need the latest updates. To import the latest version, you would import `http://www.w3id.org/hsu-aut/DINEN61360/2.0.0`. You can use this IRI in an `owl:imports` statement of your ontology. If you're having trouble using this IRI in a tool like Protégé, try opening your ontology with a text editor and simply inserting your imports manually.
An example of an imports section looks like this:

```xml
<owl:Ontology rdf:about="http://www.hsu-ifa.de/ontologies/capability-model#">
    <owl:versionIRI rdf:resource="http://www.hsu-ifa.de/ontologies/capability-model/1.0.0#"/>
    <owl:imports rdf:resource="https://w3id.org/hsu-aut/DINEN61360/2.0.0"/>
</owl:Ontology>
```
Of course you can also clone or download this repository and import an ODP from a local copy. The advantage of the first approach is that tools like Protégé or TopBraid Composer will directly use the ontologies from the internet and you can simply increase the version number in case you want to use a newer version of our ODPs.

## Tool Support
In case you want to make creating individuals from these TBoxes a lot easier, check out our 'Lightweight Industrial Ontology Design Support Tool' (LiOnS). It is designed to create RDF models using the Ontology Design Patterns of this repository. This enables users to:
- Semi-automatically design RDF models (only variable parts of the graph have to be defined)
- Consistent modelling, without being an ontology expert
- Downloading Turtle serialized models or SPARQL INSERTs

For more information, see https://github.com/hsu-aut/lion.

## Further reading:
- C. Hildebrandt, A. Köcher, C. Kustner, C.-M. Lopez-Enriquez, A.W. Muller, B. Caesar, C.S. Gundlach, A. Fay: Ontology Building for Cyber-Physical Systems: Application in the Manufacturing Domain. IEEE Transactions on Automation Science and Engineering, 2020, S. 1–17.
- C. Hildebrandt, S. Törsleff, T. Bandyszak, B. Caesar, A. Ludewig, A. Fay: Ontology Engineering for Collaborative Embedded Systems – Requirements and Initial Approach. In: Schäfer, Karagiannis (Hrsg.): Fachtagung Modellierung, 2018.
- C. Hildebrandt, S. Törsleff, B. Caesar, A. Fay: Ontology Building for Cyber-Physical Systems: A domain expert centric approach. In: 2018 14th IEEE Conference on Automation Science and Engineering (CASE 2018), 2018.
- C. Hildebrandt, A. Scholz, A. Fay, T. Schröder, T. Hadlich, C. Diedrich, M. Dubovy, C. Eck, R. Wiegand: Semantic Modeling for Collaboration and Cooperation of Systems in the production domain. In: 22nd IEEE Emerging Technology and Factory Automation (ETFA), 2017.
