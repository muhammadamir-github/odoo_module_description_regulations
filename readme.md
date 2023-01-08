# **Odoo Module Description Regulations**

Rules which must be followed mandatorily when writing the description of an odoo addon/module in its manifest file.

## Terminology
1. **Section**, root level lists viz first lists.

## Rules

1. Description, by odoo's requirment, must be written using  **reStructuredText**.

2. Everything must be written in/as **lists**.
	1. Each list item must be a list or text and will be referred to as **list-item** or **text-item** in this document.

	2. A list-item's type/style must be:
		1. *Field List*, If
			- list-item is in the second-last level *viz* list-item's children have no children (is possibly a text-item) **AND**
			- text of list-item's children is *short* and not long **AND**
			- list-item's children are of nature the list-item is supposed to categorize/classify.
		2. *Enumerated List*, If
			- list-item's children have no children BUT their text is *long* and not short **AND**
			- list-item's children are of nature the list-item is supposed to categorize/classify.
				- For example, list-item "Fields" having list-items for models: "model1", "model2", which in turn have text-items for fields: "field1", "field2", CAN NOT BE an enumerated list **since it lists models and not fields**.
					- Fields
						- model1
							- field1
							- field2
				- But a list-item "Extensions" having text-items for names: "extension.name" *OR* a list-item "Functionality" having text-items for descriptions: "functionality description", CAN BE enumerated **since they list what they are supposed to categorize**.

		3. *Bullet List*, If no other style is applicable.

3. Lists should be of the correct type, the following is to assist:
	- If list's children *have* children
		- If list's chldren's are of *nature* the list is supposed to classify/categorize
			- Enumerated List
		- Else
			- Bullet List
	- Else If list's children *DONT have* children
		- If list's chldren's are of *nature* the list is supposed to classify/categorize
			- If list's children's text is *long*
				- Enumerated List
			- Else If list's children's text is *short*
				- Field List
		- Else
			- Bullet List

4. Description can have the following Sections:
	- **Requirements**, which should list the required *Fields* and *Functions* added by other modules classified by their model names.

	- **Adds**, which should list the following entities added by the addon:
		- *Functionality*.
		- *Fields*, classified by their model names.
		- *Views*, classified by their types (New, Extensions).
		- *Templates*, classified by their types (Reports, Extensions).
			- Reports, templates belonging to reports, classified by their reports.
				- main.template/report.name (Containing other templates for the report classified by their types (New, Extensions))
					- New, templates created for the report.
					- Extensions, templates extended for the report.
			- Extensions, templates extended but not for reports.
		- *Actions*, classified by their types.
		- *Paper Formats*