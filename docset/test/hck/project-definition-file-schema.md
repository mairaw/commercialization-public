---
author: joshbax-msft
title: Project Definition File schema
description: Project Definition File schema
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dc385635-ce0c-45fd-a35a-889ea829bd82
---

# Project Definition File schema


The format for the Project Definition File is described below:

## Schema definition


``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:attribute name="User" type="xsd:string"/>
<xsd:attribute name="Controller" type="xsd:string"/>
<xsd:attribute name="Timeout" type="xsd:nonNegativeInteger"/>
<xsd:attribute name="Database" type="xsd:string"/>
<xsd:attribute name="Name" type="xsd:string"/>
<xsd:attribute name="TestCollectionReadLocation" type="xsd:string"/>
<xsd:attribute name="TestCollectionStatusLocation" type="xsd:string"/>
<xsd:attribute name="OsPlatform" type="xsd:string"/>
<xsd:attribute name="MachinePool" type="xsd:string"/>
<xsd:attribute name="TargetType">
<xsd:simpleType>
<xsd:restriction base="xsd:NMTOKEN">
<xsd:pattern value="((S|s)(Y|y)(S|s)(T|t)(E|e)(M|m))|((D|d)(E|e)(V|v)(I|i)(C|c)(E|e))|((T|t)(A|a)(R|r)(G|g)(E|e)(T|t)(C|c)(O|o)(L|l)(L|l)(E|e)(C|c)(T|t)(I|i)(O|o)(N|n))"/>
</xsd:restriction>
</xsd:simpleType>
</xsd:attribute>
<xsd:attribute name="Id" type="xsd:string"/>
<xsd:attribute name="Role">
<xsd:simpleType>
<xsd:restriction base="xsd:NMTOKEN">
<xsd:pattern value="((S|s)(U|u)(T|t))|((C|c)(L|l)(I|i)(E|e)(N|n)(T|t))"/>
</xsd:restriction>
</xsd:simpleType>
</xsd:attribute>
<xsd:attribute name="Path" type="xsd:string"/>
<xsd:element name="ProjectDefinitionData">
<xsd:complexType>
<xsd:sequence>
<xsd:element ref="Project" minOccurs="1"  maxOccurs="unbounded"/>
</xsd:sequence>
<xsd:attribute ref="User" use="optional"/>
<xsd:attribute ref="Controller" use="required"/>
<xsd:attribute ref="Timeout" use="optional" default="120"/>
<xsd:attribute ref="Database" use="optional" default="DTMJobs"/>
</xsd:complexType>
</xsd:element>
<xsd:element name="Project">
<xsd:complexType>
<xsd:sequence>
                        <xsd:element ref="SchedulerType" minOccurs="0" maxOccurs="1"/>
<xsd:element ref="MultiDeviceTestGroup" minOccurs="0" maxOccurs="1"/>
<xsd:element ref="TestStatusToSkip" minOccurs="0" maxOccurs="1"/>
<xsd:element ref="Product" minOccurs="1" maxOccurs="unbounded"/>
<xsd:element ref="Packages" minOccurs="1" maxOccurs="1"/>
</xsd:sequence>
<xsd:attribute ref="Name" use="required"/>
<xsd:attribute ref="TestCollectionReadLocation" use="optional"/>
<xsd:attribute ref="TestCollectionStatusLocation" use="optional"/>
</xsd:complexType>
</xsd:element>
                <xsd:element name="SchedulerType">
                                <xsd:simpleType>
                                                <xsd:restriction base="xsd:NMTOKEN">
                                                                <xsd:pattern value="((A|a)(D|d)(A|a)(P|p)(T|t)(I|i)(V|v)(E|e)(O|o)(R|r)(D|d)(E|e)(R|r)(O|o)(P|p)(T|t)(I|i)(M|m)(I|i)(Z|z)(E|e)(D|d))|((A|a)(D|d)(A|a)(P|p)(T|t)(I|i)(V|v)(E|e)(R|r)(E|e)(S|s)(O|o)(U|u)(R|r)(C|c)(E|e)(O|o)(P|p)(T|t)(I|i)(M|m)(I|i)(Z|z)(E|e)(D|d))"/>
                                                </xsd:restriction>
                                </xsd:simpleType>
                </xsd:element>
<xsd:element name="MultiDeviceTestGroup" type="xsd:boolean"/>
<xsd:element name="TestStatusToSkip">
<xsd:simpleType>
<xsd:restriction base="xsd:NMTOKEN">
<xsd:pattern value="((P|p)(A|a)(S|s)(S|s))|((F|f)(A|a)(I|i)(L|l))|((N|n)(O|o)(D|d)(A|a)(T|t)(A|a))"/>
</xsd:restriction>
</xsd:simpleType>
</xsd:element>
<xsd:element name="Product">
<xsd:complexType>
<xsd:sequence>
<xsd:element ref="Family" minOccurs="1" maxOccurs="unbounded"/>
<xsd:element ref="Machine" minOccurs="0" maxOccurs="unbounded"/>
</xsd:sequence>
<xsd:attribute ref="Name" use="required"/>
<xsd:attribute ref="OsPlatform" use="required"/>
<xsd:attribute ref="MachinePool" use="optional"/>
</xsd:complexType>
</xsd:element>
<xsd:element name="Family">
<xsd:complexType>
<xsd:sequence>
<xsd:element ref="Target" minOccurs="1" maxOccurs="unbounded"/>
</xsd:sequence>
<xsd:attribute ref="Name" use="optional"/>
</xsd:complexType>
</xsd:element>
<xsd:element name="Target">
<xsd:complexType>
<xsd:attribute ref="TargetType" use="required"/>
<xsd:attribute ref="Id" use="required"/>
</xsd:complexType>
</xsd:element>
<xsd:element name="Machine">
<xsd:complexType>
<xsd:attribute ref="Name" use="required"/>
<xsd:attribute ref="Role" use="optional"/>
</xsd:complexType>
</xsd:element>
<xsd:element name="Packages" type="xsd:string"/>
</xsd:schema>
```

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Project%20Definition%20File%20schema%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



