 ------""------- Proof of Concept: Add missing fields to records from XML source using XSD ------""------- 

This simple pipeline demonstrates how to compare records pulled from an XML document via a SFTP origin with an XSD schema file for that XML source and add missing fields with a default NULL text value.

This pipeline depends on the JSch 0.1.55 Java SFTP client. The pipeline contains a Groovy Evaluator stage that connects to the same SFTP server, downloads the XSD schema file, and then reads it using a Groovy XmlParser object. All of the field names from the XSD schema are stored in a list in the state variable.

In its current iteration, the XSD file is downloaded every time. This can be optimized by checking to see if the file is there, checking the SFTP server for an updated version of the file, and only download if the files are out of sync. This could improve performance for large XSD files.

Ideally, the Groovy Evaluator stage should use an XmlSlurper Groovy object instead of an XmlParser object. Unfortunately, with the version of Groovy used with recent versions of the Data Collector, the XmlSlurper object doesn't read from the XSD file. 


                                                                    Updated on : 15-Apr-2020
