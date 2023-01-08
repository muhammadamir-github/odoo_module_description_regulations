# **Odoo Module Description Regulations**

Rules which must be followed mandatorily when writing the description of an odoo addon/module in its manifest file.

## Terminology
1. **Section**, root/top level *bullet* list.
2. **Object**, name/description of an entity added by the module. 
	- For Example: view/field/report's name/id.
2. **Class**, a classifier for the Objects, some are mentioned in the last rule, can be arbitrarily created.

## Notes

1. Children of a Field List appear to be a **single value** when placed in the same line and that must always be remembered since it can cause confusion when looking at the source of the description.

## Rules

1. Description, by odoo's requirment, must be written using  **reStructuredText**.

2. Everything must be written in/as **lists**.
	1. Each list item (list's child NOT list-item) must be a list or text and will be referred to as **list-item** or **text-item** in this document.

	2. A list-item's type/style must be:
		1. *Field List*, If
			- list-item's children are **Objects not Classes**
			- text of list-item's children is *short* not long **AND**
			- list-item is in the second-last level *viz* list-item's children DON'T have children (children are possibly text-items) **AND**
			- list-item's children are of nature the *list-item or a parent of the list-item* is supposed to categorize/classify.
		2. *Enumerated List*, If
			- list-item's children are **Objects not Classes**
			- list-item's children's text is *long* not short (To be checked only if list-item's children don't have children since it COULD be possible to make it a Field List) **AND**
			- list-item's children are of nature the *list-item or a parent of the list-item* is supposed to categorize/classify.
				- For example, list-item "Fields" having list-items for models: "model1", "model2", which in turn have text-items for fields: "field1", "field2", CAN NOT BE an enumerated list **since it lists models (Classes) and not fields**.
					- Fields
						- model1
							- field1
							- field2
				- But a list-item "Extensions" having text-items for names: "extension.name" *OR* a list-item "Functionality" having text-items for descriptions: "functionality description", CAN BE enumerated **since they list what they are supposed to categorize**.

		3. *Bullet List*, If no other style is applicable.

3. Lists should be of the correct type, the following is to assist:
	- If list's children *have* children
		- If list's chldren are Objects not Classes
			- If list's chldren are of *nature* the *list or a parent of the list* is supposed to classify/categorize
				- Enumerated List
			- Else
				- Bullet List
		- Else
			- Bullet List
	- Else If list's children *DON'T have* children
		- If list's chldren are Objects not Classes
			- If list's chldren are of *nature* the *list or a parent of the list* is supposed to classify/categorize
				- If list's children's text is *long*
					- Enumerated List
				- Else If list's children's text is *short*
					- Field List
			- Else
				- Bullet List
		- Else
			- Bullet List

4. Description can have the following Sections:
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