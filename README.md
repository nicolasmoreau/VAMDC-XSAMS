XSAMS Schema design policies

Edit this note if you have something to add.

Please use meaningful commit messages, describing the whole set of changes made.
"git diff" before commit would help in writing such messages.

ID and IDREF tags and references
------------------------------------
	
	* Define ID types in typesAttributes.xsd,
	
	* Always define the ID prefix letter (or several letters, if we run out of them) to avoid collisions between different IDs in instance documents
	
	* Always document the ID and what would be the use of it.
	
	    - In the documentation of an ID type, name the elements/types that are referencing it.
	
	* Never define attributes/elements of type IDREF without specifyng what ID elements they should refer to!
	  Not everyone is as smart as you, so to deny him making stupid things, don't do this.
	  
	* Define IDREF types in typesAttributes.xsd, next to the ID definition.
	
General tips
---------------
	
* Avoid using <attribute ref="attributeName"/> and <element ref="elementName"/>
  Instead define simple type and define attribute as <xs:attribute name="attributeName" type="attributeSpecificType"/>
  This is required to avoid the need to include xsams default namespace name 
  in each of the occurrences of such elements/attributes.

* Create a basic built-in documentation for added types/elements.
  It will enable people to understand what you meant.
  That would also make the output of automatic xsd documentation tools meaningful.

* Put some example instance files to tests/valid and tests/invalid to demonstrate the use of the element.
  