---
id: dxDrawer.Options.template
type: template
default: 'panel'
---
---
##### shortDescription
Specifies the drawer's content.

##### param(Element): DxElement
The container for the content. It is an <a href="https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement" target="_blank">HTML Element</a> or a <a href="http://api.jquery.com/Types/#jQuery" target="_blank">jQuery Element</a> when you use jQuery.

##### return: any
A template name or container.

---
![DevExtreme HTML5 JavaScript Drawer](/images/UiWidgets/drawer.png)

This property specifies the drawer's content. To specify the view's content, nest it inside the Drawer's markup element as shown in the code below.

[important] Always specify a fixed width for the drawer's content because this is used to calculate the drawer's width. If the drawer is [positioned](/api-reference/10%20UI%20Components/dxDrawer/1%20Configuration/position.md '/Documentation/ApiReference/UI_Components/dxDrawer/Configuration/#position') on the y-axis, specify a fixed height for the drawer's content because it determines the drawer's height.

---
##### jQuery

    <!-- tab: index.js -->
    $(function() {
        $("#drawerContainer").dxDrawer({
            template: function() {
                const $drawerContent = $("<div>").width(200);
                // ...
                // Specify the drawer's content here
                // ...
                return $drawerContent;
            }
        });
    });

<!---->

    <!-- tab: index.html -->
    <div id="drawerContainer">
        <!-- Declare the view's content here -->
    </div>

##### Angular

    <!-- tab: app.component.html -->
    <dx-drawer
        template="drawer-content">
        <div *dxTemplate="let data of 'drawer-content'" style="width:200px;">
            <!-- Declare the drawer's content here -->
        </div>
        <!-- Declare the view's content here -->
    </dx-drawer>

##### Vue

    <!-- tab: App.vue -->
    <template>
        <DxDrawer
            template="drawer-content">
            <template #drawer-content="{ data }" style="width:200px;">
                <!-- Declare the drawer's content here -->
            </template>
            <!-- Declare the view's content here -->
        </DxDrawer>
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';

    import DxDrawer from 'devextreme-vue/drawer';

    export default {
        components: {
            DxDrawer
        }
    }
    </script>

##### React

    <!-- tab: App.js -->
    import React from 'react';

    import 'devextreme/dist/css/dx.light.css';

    import Drawer from 'devextreme-react/drawer';

    function DrawerContent() {
        return (
            <div style={{ width: 200 }}>
                {/* Declare the drawer's content here */}
            </div>
        )
    }

    export default function App() {
        return (
            <Drawer
                render={DrawerContent}>
                {/* Declare the view's content here */}
            </Drawer>
        );
    }

---

[note]The Drawer UI component is not designed to contain another Drawer. Do not use nested Drawers to avoid possible issues in your application.

#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/Drawer/LeftOrRightPosition/"
}

#####See Also#####
- [Custom Templates](/concepts/05%20UI%20Components/zz%20Common/30%20Templates/10%20Custom%20Templates.md '/Documentation/Guide/UI_Components/Common/Templates/#Custom_Templates')
