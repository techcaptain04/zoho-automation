
# how-to-get-subform-in-widget

You can not get subform data for all records request in ZOHO SDK. So to get the subfrom data while calling all data inside a widget you can do the following:






- Create a multiline field. **Remeber to select large text**

- Create a standalone function to get all subform data inside an array, then convert it into a text and then populate the multiline field


Now you can get the subform data for all records inside the widget.






## Usage/Examples

```javascript
all_module_records = zoho.crm.getRecords("module_name");
upd_list = List();
for each  record in all_module_records
{
	record_resp = zoho.crm.getRecordById("module_name",record.get("id"));
	subform_list = {record_resp.get("subform")};
	upd_list.add({"id":record_resp.get("id"),"multiline_field":subform_list.toText()});
}
info zoho.crm.bulkUpdate("module_name",upd_list);
return "";
```

