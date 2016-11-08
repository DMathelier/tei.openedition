08/04/2013

Les modifications suivantes sont � faire sur le sch�ma W3C fourni par Roma pour le rendre valide et fonctionnel.



Dans le fichier principal (tei.openedition.1.0.xsd) :

1. Supprimer tous les " form=unqualified" en les rempla�ant par "" (cha�ne vide). Il y a 24 occurences.



2. Dans la d�finition de l'�l�ment 'list', dans la d�finition de son attribut 'type', supprimer la cha�ne 'default="simple"'

<xs:element name="list">
  <xs:annotation>
    <xs:documentation> (liste) contient une suite d'items ordonn�s dans une liste. [3.7. ]</xs:documentation>
  </xs:annotation>
  <xs:complexType>
    <xs:group maxOccurs="unbounded" ref="ns1:item"/>
    <xs:attributeGroup ref="ns1:att.global.attribute.xmlid"/>
    <xs:attributeGroup ref="ns1:att.global.attribute.rend"/>
    <xs:attributeGroup ref="ns1:att.global.attribute.rendition"/>
    <xs:attribute name="type" default="simple">                        <!-- // ICI \\ -->
      <xs:annotation>
        <xs:documentation>d�crit la forme de la liste.</xs:documentation>
      </xs:annotation>
      <xs:simpleType>
        <xs:restriction base="xs:token">
          <xs:enumeration value="ordered"/>
          <xs:enumeration value="unordered"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
</xs:element>



3. En t�te de fichier, supprimer la ligne suivante :
<xs:import namespace="http://www.isocat.org/ns/dcr" schemaLocation="dcr.xsd"/>

Une erreur de validation apparait, li�e � la disparition de l'espace de nom "dcr".



4. Supprimer la s�quence suivante qui utilise l'espace de nom dcr :

<xs:attributeGroup name="att.datcat.attribute.datcat">
    <xs:attribute ref="dcr:datcat"/>
</xs:attributeGroup>
<xs:attributeGroup name="att.datcat.attribute.valueDatcat">
    <xs:attribute ref="dcr:valueDatcat"/>
</xs:attributeGroup>



5. Supprimer la d�claration de l'espace de nom dcr dans la balise racine :
xmlns:dcr="http://www.isocat.org/ns/dcr"



6. En t�te de fichier, remplacer la ligne suivante : 
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="xml.xsd"/>
Par celle-ci :
<xs:import namespace="http://www.w3.org/XML/1998/namespace" schemaLocation="http://www.w3.org/2001/xml.xsd"/>



7. Supprimer les fichiers dcr.xsd et xml.xsd