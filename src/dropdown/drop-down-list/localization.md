---
title: "Drop-down list Localization"
component: "DropDownList"
description: "This section explains the localization support of the Syncfusion angular drop-down list component."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/drop-down-list/#norecordstemplate) and [actionFailureTemplate](../api/drop-down-list/#actionfailuretemplate)
 &nbsp;properties according to the culture currently assigned to the DropDownList.

| Locale key | en-US (default)  |
|------|------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use load function of the **L10n** class.

In the following sample, French culture is set to the DropDownList and no data is loaded. Hence,
the [`noRecordsTemplate`](../api/drop-down-list/#norecordstemplate) property displays its text in French culture initially, and if the sample is
run offline, the [`actionFailureTemplate`](../api/drop-down-list/#actionfailuretemplate) property displays its text appropriately.

{% tab template="dropdownlist/getting-started", sourceFiles="app/**/*.ts" %}

```typescript
import { Component, OnInit } from '@angular/core';
import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';
import { L10n } from '@syncfusion/ej2-base';

@Component({
    selector: 'app-root',
    // specifies the template string for the DropDownList component
    template: `<ejs-dropdownlist id='ddlelement' #samples [dataSource]='data' [query]='query' [fields]='fields' [placeholder]='text' [locale]='locale'></ejs-dropdownlist>`
})
export class AppComponent implements onInit {
    constructor() {
    }
    //set the placeholder text in french to DropDownList input
    public text: string = "Sélectionnez un élément";
    // bind remotedata to showcase actionFailureTemplate in offline
    public data: DataManager = new DataManager({
        url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
        adaptor: new ODataV4Adaptor,
        crossDomain: true
    });
    // map appropriate column
    public fields: Object = { text: 'ContactName', value: 'CustomerID' },
    // take 0 item to showcase noRecordsTemplate property
    public query: Query = new Query().select(['ContactName', 'CustomerID']).take(0);
    //set culture to DropDownList component
    public locale: string = 'fr-BE';
    ngOnInit(): void {
        L10n.load({
            'fr-BE': {
            'dropdowns': {
                    'noRecordsTemplate': "Aucun enregistrement trouvé",
                    'actionFailureTemplate': "Modèle d'échec d'action"
                }
            }
        });
    }
}
```

{% endtab %}

## See Also

* [Accessibility](./accessibility/)
* [How to bind the data to the combobox](./data-binding/)