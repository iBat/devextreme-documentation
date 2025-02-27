The MultiView is a UI component that contains several views. An end user navigates through the views by swiping them in the horizontal direction. The UI component is often used along with the [Tabs](/api-reference/10%20UI%20Components/dxTabs '/Documentation/ApiReference/UI_Components/dxTabs/') UI component.

#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/MultiView/Overview/"
}

In the most simple case, the MultiView UI component requires only the [dataSource](/api-reference/10%20UI%20Components/dxMultiView/1%20Configuration/dataSource.md '/Documentation/ApiReference/UI_Components/dxMultiView/Configuration/#dataSource') property to be configured. Note that in such a case, data source items should have a structure described in the **dataSource** section. The following code adds the MultiView to your page.

---

##### jQuery

    <!--JavaScript-->
    var multiViewItems = [
        { text: "Personal Data" },
        { text: "Contacts" },
        { text: "Address" }
    ];

    $(function() {
        $("#multiViewContainer").dxMultiView({
            dataSource: multiViewItems
        });
    });

    <!--HTML-->
    <div id="multiViewContainer">

##### Angular

    <!--HTML-->
    <dx-multi-view
        [dataSource]="multiViewItems">
    </dx-multi-view>

    <!--TypeScript-->
    import { DxMultiViewModule } from 'devextreme-angular';
    // ...
    export class AppComponent {
        multiViewItems = [
            { text: 'Personal Data' },
            { text: 'Contacts' },
            { text: 'Address' }
        ];
    }
    @NgModule({
        imports: [
            // ...
            DxMultiViewModule
        ],
        // ...
    })

##### Vue

    <!--tab: App.vue-->
    <template>
        <DxMultiView
            :data-source="multiViewItems"
        />
    </template>
    <script>
    import 'devextreme/dist/css/dx.light.css';

    import DxMultiView from 'devextreme-vue/multi-view';

    export default {
        components: {
            DxMultiView
        },
        data() {
            return {
                multiViewItems: [
                    { text: 'Personal Data' },
                    { text: 'Contacts' },
                    { text: 'Address' }
                ]
            };
        }
    };
    </script>

##### React

    <!--tab: App.js-->
    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import { MultiView } from 'devextreme-react/multi-view';

    const multiViewItems = [
        { text: 'Personal Data' },
        { text: 'Contacts' },
        { text: 'Address' }
    ];

    class App extends React.Component {
        render() {
            return (
                <MultiView
                    dataSource={multiViewItems}
                />
            );
        }
    }

    export default App;

---

More often, structure of the data source item differs from the default. For correct rendering of views, specify a [custom template](/concepts/05%20UI%20Components/MultiView/05%20Customize%20Item%20Appearance.md '/Documentation/Guide/UI_Components/MultiView/Customize_Item_Appearance'). 

#####See Also#####
#include common-link-configurewidget
- [MultiView - Customize Item Appearance](/concepts/05%20UI%20Components/MultiView/05%20Customize%20Item%20Appearance.md '/Documentation/Guide/UI_Components/MultiView/Customize_Item_Appearance')
- [MultiView - Switch Between Views](/concepts/05%20UI%20Components/MultiView/10%20Switch%20Between%20Views.md '/Documentation/Guide/UI_Components/MultiView/Switch_Between_Views')
- [MultiView - Loop the Views](/concepts/05%20UI%20Components/MultiView/15%20Loop%20the%20Views.md '/Documentation/Guide/UI_Components/MultiView/Loop_the_Views')
- [MultiView API Reference](/api-reference/10%20UI%20Components/dxMultiView '/Documentation/ApiReference/UI_Components/dxMultiView/')

[tags]dxmultiview, multi view, multiView, collection container, collection UI component, navigation, overview
