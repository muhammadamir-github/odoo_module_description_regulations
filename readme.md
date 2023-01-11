# **Odoo Module Description Regulations**

Rules which must be followed mandatorily when writing the description of an odoo addon/module in its manifest file.

## Terminology
1. **Section**, root/top level *bullet* list.
2. **List-Item**, item of a list, having items of its own.
3. **Text-Item**, item of a list, *not having* items of its own.
2. **Object**, item of a list *(List-Item or Text-Item)*, which refers to an entity **added** by the module using its name **as its name or text**.
	- Examples
		1. **extension_name**:
			- button
			- field
			- chart
		2. **Description of a functionality.**
2. **Class**, item of a list *(Only List-Item)*, which classifies the Objects and *lists* them. Some are mentioned in the last rule and can be created arbitrarily.

## Notes

1. Every item of a list is either a Class or an Object.
2. **A *Class* is always a *List-Item* but can also be an *Object*** *viz* A Class always lists but can also refer to an entity added through its name (list's name).
	- Example, elements added by extensions are classified by their extensions:
		- **extension_name** (both, an Object and a Class):
			- button
			- field
			- chart
3. Children of a Field List appear to be a **single value** when placed in the same line and that must always be remembered to avoid any confusion when looking at the source of the description.

## Rules

1. Description, by odoo's requirement, must be written using  **reStructuredText**.

2. Everything must be written in/as **lists**.
	1. A list-item's type/style must be:
		1. *Field List*, If
			- list-item's children are **Objects  but not Classes** **AND**
			- text of list-item's children is *short* not long **AND**
			- list-item's children are of nature the *list-item or a parent of the list-item* is supposed to contain/list.
		2. *Enumerated List*, If
			- list-item's children are **Objects** **AND**
			- list-item's children's text is *long* not short *(To be checked only if list-item's children are not Classes in which case it MAY BE possible to make it a Field List)* **AND**
			- list-item's children are of nature the *list-item or a parent of the list-item* is supposed to contain/list.
			- Example
				- list-item/Class "*Fields*" having Classes "*model1*" and "*model2*" for models (not added by the module), which in turn have Objects "*field1*" and "*field2*" for fields (added by the module), CAN NOT BE an Enumerated List **since it violates first condition by listing models (Classes) and not fields (Objects)**.
					- Fields
						- model1
							- field1
							- field2
				- But list-items/Classes for models CAN BE *Enumerated/Field* Lists **since they fulfill all conditions**.
		3. *Bullet List*, If no other style is applicable.

3. The following is for assistance in finding the correct list style:
	- If list's children are Objects
		- If list's chldren are of *nature* the *list or a parent of the list* is supposed to contain/list
			- If list's children's text is long
				- Enumerated List
			- Else
				- If list's children are *ALSO* Classes
					- Bullet List
				- Else
					- Field List
		- Else
			- Bullet List
	- Else If list's children are *ONLY* Classes
		- Bullet List

4. Description must have the following Sections:
	- **Requirements**, which should list the required *Fields* and *Functions* added by other modules classified by their model names.

	- **Adds**, which should list the following entities added by the addon:
		- *Functionality*.
		- *Fields*, classified by their model names.
		- *Views*, classified by their types (New, Extensions).
		- *Templates*, classified by their types (Reports, Extensions).
			- Reports, templates belonging to reports, classified by their reports and their types (New, Extensions).
				- main-template/report-name
					- New, templates created for the report.
					- Extensions, template extensions for the report.
			- Extensions, template extensions but not for reports.
		- *Actions*, classified by their types.
		- *Paper Formats*