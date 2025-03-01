---
title: "XML Schema Support"
url: /refguide9/xml-schema-support/
---

## Introduction

Mendix derives the input/output formats for XML import/export and for calling SOAP/XML web services by interpreting XML Schema Definition (XSD) files. When you import an XML schema (.xsd file) or web service definition (.wsdl file) using Mendix Studio Pro, you might get a dialog that contains warning messages about unsupported constructs. This is because currently Mendix does not support the entire XSD standard. The mapping in Mendix is based on entities and attributes, and some XSD constructs do not lend themselves easily for this format. The following table shows which XSD constructs are supported in Mendix.

| XSD Construct | Is Supported |
| --- | --- |
| group | Yes |
| sequence | Only if it occurs exactly once |
| choice | Only if the individual options are not sequence elements |
| unique | Yes |
| attributeGroup | Yes |
| all | Only if each child element of the **all** occurs at most once |
| union | Yes |
| any | No |
| anyAttribute | No |
| list | No |

There are two kinds of XML mappings in Mendix: import mapping, which translates XML data to Mendix objects, and export mapping, which does the opposite. Import mappings are used when importing XML files using the 'Import XML' activity in microflows, and for processing the response of a web service call. Export mappings are used for exporting XML files in microflows and for generating the XML for the request of a web service call.

In the mapping editor for import mappings, you can check elements that can occur in the XML according to the XSD and then define a mapping to Mendix objects for those elements. It does not matter much how often or in which order elements occur; whenever an element occurs, the corresponding mapping for that element is applied.

### XSD Constraints

* If the XSD contains any of the unsupported constructs then they will be highlighted in the mapping editor with this warning icon: {{< figure src="/attachments/refguide9/modeling/integration/xml-schemas/xml-schema-support/16843903.png" class="no-border" >}}

* This will be next to each unsupported element or attribute. Checking any of such elements or attributes will result in consistency errors. 

* XML generated using export mappings must strictly adhere to the XSD specification. This means that the XML tags that are generated by the mapping must be in the exact order that the XSD specifies.

* When importing or exporting an [XML schema](/refguide9/xml-schema-support/), the XSD file needs to be in your app. If the XML refers to an XSD file that is not in your app, a runtime error will be thrown. Add the XSD file manually to resolve this error.

## Elements and Types

XSD defines elements that correspond to tags in XML. Elements have types that define their contents, for example, a primitive value or a list of child elements. Elements can have either a simple type or a complex type, while a complex type can have either simple or complex content. For both simple types and complex types with simple content, the content of the element is a primitive value, such as an integer or string value. For complex types with complex content, the content of the element can consist of several child elements. Complex types can also define attributes that can occur within the XML tag.

The following example shows an XML schema and an XML instance that adheres to the schema. The schema defines a 'customer' element with a complex type with complex content, namely a sequence of the elements 'name' and 'shoesize'. The 'name' element has a simple type, namely 'string'. The 'shoesize' element has a complex type with simple content; it extends the simple type 'integer' by adding a 'country' attribute.

**Example XML schema**

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema targetNamespace="http://www.example.com/" elementFormDefault="qualified" xmlns:tns="http://www.example.com/" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="customer">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="name" type="xs:string"/>
        <xs:element name="shoesize" type="tns:shoesizeType"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:complexType name="shoesizeType">
    <xs:simpleContent>
      <xs:extension base="xs:integer">
        <xs:attribute name="country" type="xs:string"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>

```

**Example XML instance**

```xml
<?xml version="1.0" encoding="utf-8"?>
<customer xmlns="http://www.example.com/">
  <name>John Doe</name>
  <shoesize country="GB">8</shoesize>
</customer>

```

As XML mappings in Mendix are based on the domain model, which consists of entities, attributes and associations, the XSD elements are translated to a sort of object model when you create a mapping. Elements that have complex types or occur more than once are translated to so-called 'object elements' that are mapped to an entity. Elements that have a simple type and occur at most once are translated to 'value elements' that are mapped to an attribute of the entity of their containing object element. XML attributes of complex types are also translated to value elements.

The following image shows how the XML schema of the previous example is translated to a mapping in Mendix. It is an XML-to-domain mapping for the 'customer' element of the example. The 'customer' element is translated to an object element (gray rectangle), while the 'name' and 'shoesize' elements and the 'country' attribute of the 'shoesize' element are translated to value elements in the mapping.

## Attributes

Complex types can specify attributes that can occur within the XML tag. These attributes always have a simple type and can occur at most once. Attributes are fully supported in both mapping types. Attributes are translated to value elements in the mapping and can therefore be mapped to an attribute of an entity.

## Simple Types and Complex Types with Simple Content

Mendix fully supports elements with primitive content, as in, simple types or complex types with simple content. However, Mendix currently does not take restrictions of simple types into account, such as limiting a string to a finite set of possibilities or limiting the range of an integer. In those cases, all possible values of the base type (for example, string) are allowed.

Usually, elements with primitive content are translated to value elements in the mapping. If for some reason an element with primitive content is translated to an object element in the mapping, for instance because it occurs more than once, or because it has a complex type that also defines attributes, the contents of the element are translated to an extra value element called '(Contents)'.

{{% alert color="info" %}}
The hex binary type is recognized as a string, so operations on binary types are not applicable for a hex binary (for example, MTOM attachment).
{{% /alert %}}

## Complex Types with Complex Content

For elements having a complex type with complex content, the content of the element can consist of several child elements, of which the order and multiplicity is defined by one or more grouping constructs such as choice and sequence. 

## Mixed Content

Complex types can define their content to be mixed. This means that an element has both text and child elements as contents. Mixed content is commonly found in document data such as (X)HTML, and less commonly in structured data. Currently, mixed content is not supported in Mendix.
