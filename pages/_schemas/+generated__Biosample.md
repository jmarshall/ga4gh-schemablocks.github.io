---
title: 'Biosample'
layout: default
permalink: "/schemas/blocks/Biosample.html"
excerpt_separator: <!--more-->
category:
  - schemas
tags:
  - code
---
## Biosample

#### Status: __proposed__

<!--more-->

  
<h4>Properties of the <i>Biosample</i> class</h4>

<table>
  <tr>
    <th>Property</th>
    <th>Type</th>
    <th>Format</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>age_at_collection</td>
    <td></td>
    <td></td>
    <td>The age of the individual at time of biosample collection, as Age object.
</td>
  </tr>
  <tr>
    <td>biocharacteristics</td>
    <td>array</td>
    <td></td>
    <td>biocharacteristics represents a wrapper list of "Phenotype" objects with properly prefixed term ids, describing features of the biosample.
Examples would be phenotypes, disease codes or other ontology classes specific to this biosample. In a complete data model (variants - (callsets) - biosamples - individuals), characteristics applying to the individual (e.g. sex, most phenotypes) should be annotated there.
</td>
  </tr>
  <tr>
    <td>created</td>
    <td>timestamp</td>
    <td></td>
    <td>The creation time of this record, in ISO8601
</td>
  </tr>
  <tr>
    <td>data_use_conditions</td>
    <td></td>
    <td></td>
    <td>Data use conditions applying to data from this biosample, as ontology object (e.g. DUO).
</td>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td></td>
    <td>A free text description of the biosample. This should not contain any structured data.</td>
  </tr>
  <tr>
    <td>external_references</td>
    <td>array</td>
    <td></td>
    <td>list of reference_class objects with properly (e.g. identifiers.org) prefixed external identifiers and a term describing the relationship
</td>
  </tr>
  <tr>
    <td>geo_provenance</td>
    <td></td>
    <td></td>
    <td>This geo_class attribute ideally describes the geographic location of where the sample was extracted.
Frequently this value may reflect either the place of the laboratory where the analysis was performed, or correspond to the corresponding author's institution.
</td>
  </tr>
  <tr>
    <td>id</td>
    <td>string</td>
    <td></td>
    <td>The local-unique identifier of this biosample (referenced as "biosample_id"). This is unique in the context of the server instance.</td>
  </tr>
  <tr>
    <td>individual_id</td>
    <td>string</td>
    <td></td>
    <td>In a complete data model "individual_id" points to the "id" of the individual ("donor") this <i>biosample</i> was derived from.
In a local context this could be the <code>id</code> attribute in a corresponding "individuals" collection.
</td>
  </tr>
  <tr>
    <td>info</td>
    <td></td>
    <td></td>
    <td>This is a wrapper for objects without further specification in the schema.
</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td></td>
    <td>A short descriptive name for sample which should be sufficient to distinguish it from other samples in the project or collection. This is a label or symbolic identifier for the biosample.
</td>
  </tr>
  <tr>
    <td>project_id</td>
    <td>string</td>
    <td></td>
    <td>The id attribute of the project that this biosample was collected in.
</td>
  </tr>
  <tr>
    <td>updated</td>
    <td>timestamp</td>
    <td></td>
    <td>The time of the last edit of this record, in ISO8601
</td>
  </tr>

</table>A Biosample refers to a unit of biological material from which the substrate molecules (e.g. genomic DNA, RNA, proteins) for molecular analyses (e.g. sequencing, array hybridisation, mass-spectrometry) are extracted.
Examples would be a tissue biopsy, a single cell from a culture for single cell genome sequencing or a protein fraction from a gradient centrifugation. Several instances (e.g. technical replicates) or types of experiments (e.g. genomic array as well as RNA-seq experiments) may refer to the same Biosample. FHIR mapping: Specimen (http://www.hl7.org/fhir/specimen.html).



#### Examples

```
{
   "id" : "AM_BS__NCBISKYCGH-1993",
   "biocharacteristics" : [
      {
         "description" : "Pancreatic Adenocarcinoma",
         "type" : {
            "id" : "icdot:C25.9",
            "label" : "Pancreas, NOS"
         }
      }
   ],
   "name" : "Sample BRCA-00429, 2nd replicate",
   "geo_provenance" : {
      "altitude" : 94,
      "city" : "Timisoara",
      "label" : "Str Marasesti 5, 300077 Timisoara, Romania",
      "longitude" : 21.23,
      "country" : "Romania",
      "latitude" : 45.75
   },
   "data_use_conditions" : {
      "id" : "DUO:0000004",
      "label" : "no restriction"
   },
   "individual_id" : "ind-cnhl-1293347-004",
   "description" : "Burkitt lymphoma, cell line Namalwa",
   "age_at_collection" : {
      "age" : "P56Y",
      "age_class" : {
         "id" : "HP:0003621",
         "label" : "Juvenile onset"
      }
   },
   "project_id" : "ind-cnhl-1293347-004",
   "created" : "2017-10-25T07:06:03Z",
   "updated" : "2017-10-25T07:06:03Z",
   "external_references" : [
      {
         "description" : "Cellosaurus cell line identifier",
         "relation" : "provenance",
         "type" : {
            "label" : "HOS",
            "id" : "cellosaurus:CVCL_0312"
         }
      }
   ],
   "info" : {
      "death" : 1,
      "followup_time" : "P14M"
   }
}
```
--------------------------------------------------------------------------------

<h4>Notes and examples on the <i>Biosample</i> properties</h4>

##### age_at_collection

* The age of the individual at time of biosample collection, as Age object.

* example:

```
'age_at_collection' : {
  'age_class' => {
                   'label' => 'Juvenile onset',
                   'id' => 'HP:0003621'
                 },
  'age' => 'P56Y'
}
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### biocharacteristics

* biocharacteristics represents a wrapper list of "Phenotype" objects with properly prefixed term ids, describing features of the biosample.
Examples would be phenotypes, disease codes or other ontology classes specific to this biosample. In a complete data model (variants - (callsets) - biosamples - individuals), characteristics applying to the individual (e.g. sex, most phenotypes) should be annotated there.

* example:

```
'biocharacteristics' : [
  {
    'description' => 'Pancreatic Adenocarcinoma',
    'type' => {
                'id' => 'icdot:C25.9',
                'label' => 'Pancreas, NOS'
              }
  },
  {
    'type' => {
                'label' => 'Adenocarcinoma, NOS',
                'id' => 'icdom:81403'
              },
    'description' => 'Pancreatic Adenocarcinoma'
  },
  {
    'description' => 'Pancreatic Adenocarcinoma',
    'type' => {
                'label' => 'Pancreatic Adenocarcinoma',
                'id' => 'ncit:C8294'
              }
  }
]
```

* Queries:  The query will return all biosamples with an (exact) class.id of "icdom:81403" in their "biocharacteristics" object list.

```
db.biosamples.find( { "biocharacteristics.type.id" : "icdom:81403" } )
```
This call to the distinct funcion will return *all* bioterms ids for samples having some ncit id; to retrive only the ncit ids, this has to be followed by a regex filter (/^ncit/).

```
db.biosamples.distinct( "biocharacteristics.type.id", { "biocharacteristics.type.id" : { $regex : /ncit/ } } )
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### created

* The creation time of this record, in ISO8601

* example:

```
'created' : "2017-10-25T07:06:03Z"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### data_use_conditions

* Data use conditions applying to data from this biosample, as ontology object (e.g. DUO).

* example:

```
'data_use_conditions' : {
  'id' => 'DUO:0000004',
  'label' => 'no restriction'
}
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### description

* A free text description of the biosample. This should not contain any structured data.
* example:

```
'description' : "Burkitt lymphoma, cell line Namalwa"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### external_references

* list of reference_class objects with properly (e.g. identifiers.org) prefixed external identifiers and a term describing the relationship

* example:

```
'external_references' : [
  {
    'type' => {
                'label' => 'HOS',
                'id' => 'cellosaurus:CVCL_0312'
              },
    'relation' => 'provenance',
    'description' => 'Cellosaurus cell line identifier'
  },
  {
    'relation' => 'report',
    'description' => 'PubMed reference',
    'type' => {
                'id' => 'pubmed:2823272',
                'label' => 'Rearrangement of the p53 gene in human osteogenic sarcomas.'
              }
  }
]
```

* Queries:  The query will return all biosamples reported in this publication

```
db.biosamples.find( { "external_references.type.id" : "pubmed:17440070" } )
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### geo_provenance

* This geo_class attribute ideally describes the geographic location of where the sample was extracted.
Frequently this value may reflect either the place of the laboratory where the analysis was performed, or correspond to the corresponding author's institution.

* example:

```
'geo_provenance' : {
  'latitude' => '45.75',
  'country' => 'Romania',
  'longitude' => '21.23',
  'label' => 'Str Marasesti 5, 300077 Timisoara, Romania',
  'city' => 'Timisoara',
  'altitude' => 94
}
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### id

* The local-unique identifier of this biosample (referenced as "biosample_id"). This is unique in the context of the server instance.
* example:

```
'id' : "AM_BS__NCBISKYCGH-1993"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### individual_id

* In a complete data model "individual_id" points to the "id" of the individual ("donor") this <i>biosample</i> was derived from.
In a local context this could be the <code>id</code> attribute in a corresponding "individuals" collection.

* example:

```
'individual_id' : "ind-cnhl-1293347-004"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### info

* This is a wrapper for objects without further specification in the schema.

* example:

```
'info' : {
  'followup_time' => 'P14M',
  'death' => 1
}
```

* Queries:  This query retrieves biosamples with an ISO8601 period value for "followup_time" and a boolean "true" for death.

```
db.biosamples.find( {"info" : { $elemMatch: { "followup_time.value" : { $regex : /\P/ }, "death.value" : true } } } )
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### name

* A short descriptive name for sample which should be sufficient to distinguish it from other samples in the project or collection. This is a label or symbolic identifier for the biosample.

* example:

```
'name' : "Sample BRCA-00429, 2nd replicate"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### project_id

* The id attribute of the project that this biosample was collected in.

* example:

```
'project_id' : "ind-cnhl-1293347-004"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).
##### updated

* The time of the last edit of this record, in ISO8601

* example:

```
'updated' : "2022-11-11T09:45:13Z"
```
  
The original schema definitions are provided in the [YAML file](https://github.com/ga4gh-schemablocks/blocks/blob/master/src/yaml/biosample.yaml).