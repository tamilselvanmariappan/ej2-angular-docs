---
title: " Chart How To | Angular "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Create footer and watermark for chart

By using `annotation`, you can place any html elements to chart in a desired view.

To create footer and watermark for chart, follow the given steps:

**Step 1**:

Initialize the custom elements by using the `annotation` property.

By using the `content` option of the annotation object, you can specify the id of the element that needs
to be displayed in the chart area as follow,

{% tab template= "chart/how-to" , sourceFiles="app/**/*.ts" %}

```typescript
import { Component, OnInit } from '@angular/core';
import { IPointRenderEventArgs } from '@syncfusion/ej2-angular-charts';

@Component({
    selector: 'app-container',
    template:
    `<ejs-chart id="chart-container" [primaryXAxis]='primaryXAxis'[primaryYAxis]='primaryYAxis' [title]='title'>
         <e-annotations>
            <e-annotation  content='<div id="chart_cloud" style="font-size:450%; opacity: 0.3;" >syncfusion</div>'
            x='Wed' y= 20 coordinateUnits= 'Point' horizontalAlignment='Center'>
            </e-annotation>
            <e-annotation  content='<div id="chart" > <a href="https://www.syncfusion.com" target="_blank">www.syncfusion.com</a></div>'
            x=400 y=440 coordinateUnits='Pixel' horizontalAlignment='Center'>
            </e-annotation>
        </e-annotations>
        <e-series-collection>
            <e-series [dataSource]='chartData' type='Spline' xName='x' yName='y' name='Max Temp' width=2 [marker]='marker'></e-series>
        </e-series-collection>
    </ejs-chart>`
})
export class AppComponent implements OnInit {
    public primaryXAxis: Object;
    public chartData: Object[];
    public title: string;
    public marker: Object;
    public primaryYAxis: Object;
    ngOnInit(): void {
        this.chartData =[
                    { x: 'Sun', y: 15 }, { x: 'Mon', y: 5 },{ x: 'Tue', y: 32 },
                    { x: 'Wed', y: 15 },{ x: 'Thu', y: 29 }, { x: 'Fri', y: 24 },
                    { x: 'Sat', y: 18 },
                ];
        this.primaryXAxis = {
          valueType: 'Category',
            interval: 1, majorGridLines: { width: 0 },
            labelIntersectAction: 'Rotate90'
        };
        this.primaryYAxis = {
             minimum: 0,
            maximum: 40,
            interval: 10,
        };
        this.marker = { visible: true};
        this.title =  'NC Weather Report - 2016';
    }
}
```

{% endtab %}