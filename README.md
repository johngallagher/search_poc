
Sparql Query Notes
==================

This lists unique district administratives for all schools

PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?node ?label WHERE {
  ?school <http://education.data.gov.uk/def/school/districtAdministrative> ?node .
  ?node rdfs:label ?label .
}


To list all towns of schools


PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX school: <http://education.data.gov.uk/def/school/>

SELECT DISTINCT ?town
WHERE {
?item rdf:type school:School .
?item school:address ?address .
?address school:town ?town
} 


List all types of establishments

SELECT ?item
WHERE {
 ?item a <http://education.data.gov.uk/def/school/TypeOfEstablishment_TERM> . 
}


List all types of types of establishments

PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?item ?label
WHERE {
?item a <http://education.data.gov.uk/def/school/TypeOfEstablishment_TERM> . 
?item rdfs:label ?label
}



PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX school: <http://education.data.gov.uk/def/school/>
SELECT ?name ?item
WHERE {
?___establishmentStatus_1 rdfs:label "Open" .
?item school:establishmentStatus ?___establishmentStatus_1 .
?item rdf:type school:School .
?item rdfs:label ?name
}  OFFSET 0 LIMIT 10

For those in a district add:
?___districtAdministrative_0 rdfs:label "Bristol, City of" .
?item school:districtAdministrative ?___districtAdministrative_0 .

For those in primary education
?___phaseOfEducation_2 rdfs:label "Primary" .
?item school:phaseOfEducation ?___phaseOfEducation_2 .

