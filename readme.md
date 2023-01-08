# **Odoo Module Description Regulations**

Rules which must be followed mandatorily when writing the description of an odoo addon/module in its manifest file.

## Terminology
1. **Section**, root level lists viz first lists.

## Rules

1. Description, by odoo's requirment, must be written using  **reStructuredText**.

2. Everything must be written in **lists**.
	1. Each list item must be a list or text and will be referred to as **list-item** or **text-item** in this document.

	2. A list-item's type/style must be:
		1. *Field List*, if 
			- item is in second-last level viz item's children have no children **AND**
			- text of item's children is *short* and not very long **AND**
			- if item's children are of nature the item is supposed to categorize/classify.
		2. *Enumerated List*, 
			- if item's children have no children BUT their text is *long* and not short **AND**
			- if item's children are of nature the item is supposed to categorize/classify.
				- For example, item "Fields" having items for models "model1", "model2" which in turn have items for fields "field1", "field2", can not be an enumerated list **since it lists models and not fields**.
					- Fields
						- model1
							- field1
							- field2
				- But an item "Extensions" having item "extension.name" or an item "Functionality" having **text-items** "functionality description" can be enumerated **since they list what they are supposed to categorize**.

		3. *Bullet List*, if no other style is applicable.

3. Lists should be of the correct type, the following is to assist:
	- If list's children have children
		- If list's chldren's are of nature the list is supposed to classify/categorize
			- Enumerated List
		- Else
			- Bullet List
	- Else If list's children DONT have children
		- If list's chldren's are of nature the list is supposed to classify/categorize
			- If list's children's text is long
				- Enumerated List
			- Else If list's children's text is short
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
				- main.template/report.name
					- New, templates created for the report.
					- Extensions, templates extended for the report.
			- Extensions, templates extended but not for reports.
		- *Actions*, classified by their types.
		- *Paper Formats*