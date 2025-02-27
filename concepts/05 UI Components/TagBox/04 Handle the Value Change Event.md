To process new TagBox values, you need to handle the value change event. If the handling function is not going to be changed during the lifetime of the UI component, assign it to the [onValueChanged](/api-reference/10%20UI%20Components/dxTagBox/1%20Configuration/onValueChanged.md '/Documentation/ApiReference/UI_Components/dxTagBox/Configuration/#onValueChanged') property when you configure the UI component.

---
##### jQuery

    <!--JavaScript-->
    $(function() {
        $("#tagBoxContainer").dxTagBox({
            onValueChanged: function (e) {
                const previousValues = e.previousValue;
                const newValues = e.value;
                // Event handling commands go here
            }
        });
    });

##### Angular

    <!--HTML-->
    <dx-tag-box ...
        (onValueChanged)="onValueChanged($event)">
    </dx-tag-box>

    <!--TypeScript-->
    import { DxTagBoxModule } from "devextreme-angular";
    // ...
    export class AppComponent {
        onValueChanged (e) {
            const previousValue = e.previousValue;
            const newValue = e.value;
            // Event handling commands go here
        }
    }
    @NgModule({
         imports: [
             // ...
             DxTagBoxModule
         ],
         // ...
     })

##### Vue

    <template>
        <DxTagBox ...
            @value-changed="onValueChanged"
        />
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';

    import { DxTagBox } from 'devextreme-vue/tag-box';

    export default {
        components: {
            DxTagBox
        },
        methods: {
            onValueChanged(e) {
                const previousValues = e.previousValue;
                const newValues = e.value;
                // Event handling commands go here
            }
        }
    }
    </script>

##### React

    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import { TagBox } from 'devextreme-react/tag-box';

    class App extends React.Component {
        constructor(props) {
            super(props);

            this.onValueChanged = this.onValueChanged.bind(this);
        }

        onValueChanged(e) {
            const previousValues = e.previousValue;
            const newValues = e.value;
            // Event handling commands go here
        }

        render() {
            return (
                <TagBox ...
                    onValueChanged={this.onValueChanged}
                />
            );
        }
    }

    export default App;

---

[note]The `previousValue` and `newValue` fields are _arrays_ that contain values taken from the [valueExpr](/api-reference/10%20UI%20Components/dxSelectBox/1%20Configuration/valueExpr.md '/Documentation/ApiReference/UI_Components/dxTagBox/Configuration/#valueExpr') data field.

If you are going to change event handlers at runtime, or if you need to attach several handlers to the value change event, subscribe to this event using the [on(eventName, eventHandler)](/api-reference/10%20UI%20Components/Component/3%20Methods/on(eventName_eventHandler).md '/Documentation/ApiReference/UI_Components/dxTagBox/Methods/#oneventName_eventHandler') method. This approach is more typical of jQuery.

    <!--JavaScript-->
    const valueChangedHandler1 = function (e) {
        const previousValues = e.previousValue;
        const newValues = e.value;
        // First handler of the "valueChanged" event
    };

    const valueChangedHandler2 = function (e) {
        const previousValues = e.previousValue;
        const newValues = e.value;
        // Second handler of the "valueChanged" event
    };

    $("#tagBoxContainer").dxTagBox("instance")
        .on("valueChanged", valueChangedHandler1)
        .on("valueChanged", valueChangedHandler2);

#####See Also#####
#include common-link-handleevents
- [TagBox - Control the Behavior](/concepts/05%20UI%20Components/TagBox/03%20Control%20the%20Behavior.md '/Documentation/Guide/UI_Components/TagBox/Control_the_Behavior/')
- [TagBox - Configure Search Parameters](/concepts/05%20UI%20Components/TagBox/10%20Configure%20Search%20Parameters.md '/Documentation/Guide/UI_Components/TagBox/Configure_Search_Parameters/')
- [TagBox - Create a User-Defined Item](/concepts/05%20UI%20Components/TagBox/15%20Create%20a%20User-Defined%20Item.md '/Documentation/Guide/UI_Components/TagBox/Create_a_User-Defined_Item/')
- [TagBox API Reference](/api-reference/10%20UI%20Components/dxTagBox '/Documentation/ApiReference/UI_Components/dxTagBox/')
- [TagBox Demos](https://js.devexpress.com/Demos/WidgetsGallery/Demo/TagBox/Overview)

[tags]tagBox, tag box, editor, get value, set value, change value, valueChanged