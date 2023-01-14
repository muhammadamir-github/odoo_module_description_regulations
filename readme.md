# **Odoo Module Description Regulations V.1.1**

Rules which must be followed mandatorily when writing the description of an odoo addon/module in its manifest file.

## Terminology
1. **Section**, root/top level *bullet* list.
2. **List-Item**, item of a list, having items of its own.
3. **Text-Item**, item of a list, *not having* items of its own.
2. **Object**, item of a list *(List-Item or Text-Item)*, which refers to an entity **added** by the module by using entity's name/id/description **as its name or text**.
	- Examples
		1. **extension_name**:
			- button
			- field
			- chart
		2. **Description of a functionality.**
2. **Class**, item of a list *(Only List-Item)*, which classifies the Objects and *lists* them. Some are mentioned in the last rule and can be created arbitrarily.

## Notes

1. Every *item* of a list is *at least* either a Class or an Object.
2. **A *Class* is always a *List-Item* and a List-Item is always a Class but can also be an *Object*** 
	- *viz* A Class always lists but can also refer to an entity added by the module through its name (list's name).
	- Example, elements added by extensions are classified by their extensions:
		- **extension_name** (both, an Object and a Class):
			- button
			- field
			- chart
3. Children of a *Field List* appear to be a **single value** when placed in the same line and that must always be remembered to avoid any confusion when looking at the source of the description.
4. *Views and Templates*, in Adds Section, can list elements added/removed by them classified into *Adds* and *Removes* and further classified by *their types which can be created arbitrarily* (Fields, Buttons, Texts, Headings, Tables etc).

## Rules

1. Description, by odoo's requirement, must be written using  **reStructuredText**.

2. Everything must be written in/as **lists**.
	1. A list-item's type/style must be:
		1. *Field List*, If
			- list-item's children are **Objects but not Classes** **AND**
			- text of list-item's children is *short* not long **AND**
			- list-item's children are of nature the *list-item or a parent of the list-item* is supposed to contain/list.
		2. *Enumerated List*, If
			- list-item's children are **Objects** **AND**
			- list-item's children's text is *long* not short *(To be checked only if list-item's children are not Classes in which case it MAY BE possible to make list-item a Field List)* **AND**
			- list-item's children are of nature the *list-item or a parent of the list-item* is supposed to contain/list.
			- Example
				- list-item/Class "*Fields*" having Classes "*model1*" and "*model2*" for models (not added by the module), which in turn have Objects "*field1*" and "*field2*" for fields (added by the module), CAN NOT BE an Enumerated List **since it violates first condition by listing models (Classes) and not fields (Objects)**.
					- Fields
						- model1
							- field1
							- field2
				- But list-items/Classes of models CAN BE *Enumerated/Field* Lists **since they fulfill all conditions**.
		3. *Bullet List*, If no other style is applicable.

3. Use the following to find the correct list style:
	- If list's children are Objects
		- If list's chldren are of *nature* the *list or a parent of the list* is supposed to contain/list
			- If list's children are *ALSO* Classes
				- Enumerated List
			- Else If list's children are *ONLY* Objects
				- If list's children's text is long
					- Enumerated List
				- Else
					- Field List
		- Else
			- Bullet List
	- Else If list's children are *ONLY* Classes
		- Bullet List

4. Description must have the following Sections:
	- **Requirements**, which should list the required *Fields* and *Functions* added by other modules classified by their model/file names.

	- **Adds**, which should list the following entities added by the addon:
		- *Functionality*.
		- *Fields*, classified by their model names.
		- *Views*, classified by their types (New, Extensions).
		- *Templates*, classified by their types (Reports, New, Extensions).
			- Reports, templates belonging to a report, classified by their reports.
				- Example, main-template/report-name: templates created for the report.
			- New, templates not extending and not belonging to a report.
			- Extensions, template extensions.
		- *Actions*, classified by their types.
		- *Paper Formats*

## Example
Description of a custom addon.
```
`Read the Description Regulations <https://github.com/muhammadamir-github/odoo_module_description_regulations/blob/master/readme.md>`_

|

Requirements:
	- Fields:
		- :account.move: ci_tax_by_rcm
Adds:
	- Functionality:
		1. To reserve/lock/restrict payments (account.payment) for invoices (account.move) of a specific sale/purchase order which allows users to record an ADVANCE PAYMENT for a sale/purchase without requiring/recording/creating an/a invoice/bill. These payments act as **Receipt/Refund** vouchers (Credit/Debit notes are issued instead of Receipt/Refund vouchers if an invoice/bill has been issued).
	- Fields:
		- :account.payment: cp_reserved_for, cp_so_reserved_for_id, cp_po_reserved_for_id
		- :purchase.order and sale.order: cp_reserved_payments_count
	- Views:
		- New:
			1. None
		- Extensions:
			1. purchase_order_form_extension extends purchase.purchase_order_form & view_order_form_extension extends sale.view_order_form:
				- Adds:
					- :Buttons: cp_button_create_payment, cp_button_view_payments
			2. view_account_payment_form_extension exnteds account.view_account_payment_form:
				- Adds:
					- :Fields: cp_reserved_for, cp_so_reserved_for_id, cp_po_reserved_for_id
	- Templates:
		- Reports:
			1. :**payment**, a custom report for account.payment with structure and style same as Pocket Journal's documents: content, header, footer, fonts, sharedcss, external_layout
		- New: 
			1. None
		- Extensions: 
			1. None
	- Actions:
		- :Report: payment_action
	- :Paper Formats: paperformat (A4 (custom_payment))
```