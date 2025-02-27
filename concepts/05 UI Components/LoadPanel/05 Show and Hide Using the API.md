[note] In this article, the [Button](/api-reference/10%20UI%20Components/dxButton '/Documentation/ApiReference/UI_Components/dxButton/') UI component is used to demonstrate how to show and hide the LoadPanel. This choice is made for purely demonstrational purposes, and you can do the same operations using another UI component following the same guidelines.

To show or hide the LoadPanel programmatically, call the [show()](/api-reference/10%20UI%20Components/dxLoadPanel/3%20Methods/show().md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Methods/#show') or [hide()](/api-reference/10%20UI%20Components/dxOverlay/3%20Methods/hide().md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Methods/#hide') method. The same thing can be done using the [toggle(showing)](/api-reference/10%20UI%20Components/dxLoadPanel/3%20Methods/toggle(showing).md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Methods/#toggleshowing') method. Pass **true** or **false** to this method to show or hide the LoadPanel, respectively.

---
##### jQuery

    <!--JavaScript-->
    $(function() {
        $("#loadPanelContainer").dxLoadPanel({
            hideOnOutsideClick: true
        });
        $("#buttonContainer").dxButton({
            text: "Show the Load Panel", 
            onClick: function () {
                $("#loadPanelContainer").dxLoadPanel("show");
                // ==== or ====
                $("#loadPanelContainer").dxLoadPanel("toggle", true);
            } 
        });
    });

##### ASP.NET MVC Controls

    <!--Razor C#-->
    @(Html.DevExtreme().LoadPanel()
        .ID("loadPanel")
        .HideOnOutsideClick(true)
    )

    @(Html.DevExtreme().Button()
        .ID("button")
        .Text("Show the Load Panel")
        .OnClick(@<text>
            function () {
                $("#loadPanel").dxLoadPanel("show");
                // ==== or ====
                $("#loadPanel").dxLoadPanel("toggle", true);
            } 
        </text>)
    )

    <!--Razor VB-->
    @(Html.DevExtreme().LoadPanel() _
        .ID("loadPanel") _
        .HideOnOutsideClick(True)
    )

    @(Html.DevExtreme().Button() _
        .ID("button") _
        .Text("Show the Load Panel") _
        .OnClick("button_click")
    )

    <script>
        function button_click() {
            $("#loadPanel").dxLoadPanel("show");
            // ==== or ====
            $("#loadPanel").dxLoadPanel("toggle", true);
        }
    </script>

---

With Angular, Vue, or React, use a different technique. Bind the [visible](/api-reference/10%20UI%20Components/dxLoadPanel/1%20Configuration/visible.md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Configuration/#visible') property of the LoadPanel UI component to a component property. After that, change this property, and the LoadPanel will appear or disappear.

---
##### Angular

    <!--HTML-->
    <dx-load-panel
        [hideOnOutsideClick]="true"
        [(visible)]="isLoadPanelVisible">
    </dx-load-panel>
    <dx-button
        text="Show the Load Panel"
        (onClick)="isLoadPanelVisible = true">
    </dx-button>

    <!--TypeScript-->
    import { DxLoadPanelModule, DxButtonModule } from "devextreme-angular";
    // ...
    export class AppComponent {
        isLoadPanelVisible: boolean = false;
    }
    @NgModule({
        imports: [
            // ...
            DxLoadPanelModule,
            DxButtonModule
        ],
        // ...
    })

##### Vue

    <template>
        <div>
            <DxLoadPanel
                :hide-on-outside-click="true"
                v-model:visible="isLoadPanelVisible"
            />
            <DxButton
                text="Show the Load Panel"
                @click="handleClick"
            />
        </div>
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';

    import { DxLoadPanel } from 'devextreme-vue/load-panel';
    import { DxButton } from 'devextreme-vue/button';

    export default {
        components: {
            DxLoadPanel,
            DxButton
        },
        data() {
            return {
                isLoadPanelVisible: false
            }
        },
        methods: {
            handleClick() {
                this.isLoadPanelVisible = true;
            }
        }
    }
    </script>

##### React

    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import { LoadPanel } from 'devextreme-react/load-panel';
    import { Button } from 'devextreme-react/button';

    class App extends React.Component {
        constructor(props) {
            super(props);

            this.state = {
                isLoadPanelVisible: false
            };

            this.handleClick = this.handleClick.bind(this);
            this.handleHide = this.handleHide.bind(this);
        }

        handleClick() {
            this.setState({
                isLoadPanelVisible: true
            });
        }

        handleHide() {
            this.setState({
                isLoadPanelVisible: false
            });
        }

        render() {
            return (
                <div>
                    <LoadPanel
                        hideOnOutsideClick={true}
                        visible={this.state.isLoadPanelVisible}
                        onHidden={this.handleHide}
                    />
                    <Button
                        text="Show the Load Panel"
                        onClick={this.handleClick}
                    />
                </div>
            );
        }
    }

    export default App;

---

To execute certain commands before or after the LoadPanel is shown/hidden, handle the [showing](/api-reference/10%20UI%20Components/dxOverlay/4%20Events/showing.md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Events/#showing'), [shown](/api-reference/10%20UI%20Components/dxOverlay/4%20Events/shown.md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Events/#shown'), [hiding](/api-reference/10%20UI%20Components/dxOverlay/4%20Events/hiding.md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Events/#hiding') or [hidden](/api-reference/10%20UI%20Components/dxOverlay/4%20Events/hidden.md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Events/#hidden') event. If the event handling function is not going to be changed during the lifetime of the UI component, assign it to the corresponding **on*EventName*** property. For example, in the following code, a handler of the **shown** event is assigned to the [onShown](/api-reference/10%20UI%20Components/dxOverlay/1%20Configuration/onShown.md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Configuration/#onShown') property. This handler hides the LoadPanel three seconds after it was shown.

---
##### jQuery

    <!--JavaScript-->$(function() {
		$("#loadPanelContainer").dxLoadPanel({
            onShown: function (e) {
                setTimeout(function () { 
                    e.component.hide();          
                }, 3000);
            }
        });

        $("#buttonContainer").dxButton({
            text: "Show the Load Panel", 
            onClick: function () {
                $("#loadPanelContainer").dxLoadPanel("show");
            } 
        });
    });

##### Angular

    <!--HTML-->
    <dx-load-panel
        [(visible)]="isLoadPanelVisible"
        (onShown)="hideLoadPanel($event)">
    </dx-load-panel>
    <dx-button
        text="Show the Load Panel"
        (onClick)="isLoadPanelVisible = true">
    </dx-button>

    <!--TypeScript-->
    import { DxLoadPanelModule, DxButtonModule } from "devextreme-angular";
    // ...
    export class AppComponent {
        isLoadPanelVisible: boolean = false;
        hideLoadPanel (e) {
            setTimeout(() => { 
                e.component.hide();          
            }, 3000);
        }
    }
    @NgModule({
        imports: [
            // ...
            DxLoadPanelModule,
            DxButtonModule
        ],
        // ...
    })

##### Vue

    <template>
        <div>
            <DxLoadPanel
                :hide-on-outside-click="true"
                v-model:visible="isLoadPanelVisible"
                @shown="hideLoadPanel"
            />
            <DxButton
                text="Show the Load Panel"
                @click="handleClick"
            />
        </div>
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';

    import { DxLoadPanel } from 'devextreme-vue/load-panel';
    import { DxButton } from 'devextreme-vue/button';

    export default {
        components: {
            DxLoadPanel,
            DxButton
        },
        data() {
            return {
                isLoadPanelVisible: false
            }
        },
        methods: {
            handleClick() {
                this.isLoadPanelVisible = true;
            },
            hideLoadPanel(e) {
                setTimeout(() => { 
                    e.component.hide();          
                }, 3000);
            }
        }
    }
    </script>

##### React

    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import { LoadPanel } from 'devextreme-react/load-panel';
    import { Button } from 'devextreme-react/button';

    class App extends React.Component {
        constructor(props) {
            super(props);

            this.state = {
                isLoadPanelVisible: false
            };

            this.handleClick = this.handleClick.bind(this);
            this.hideLoadPanel = this.hideLoadPanel.bind(this);
        }

        handleClick() {
            this.setState({
                isLoadPanelVisible: true
            });
        }

        hideLoadPanel(e) {
            setTimeout(() => { 
                this.setState({
                    isLoadPanelVisible: false
                });          
            }, 3000);
        }

        render() {
            return (
                <div>
                    <LoadPanel
                        hideOnOutsideClick={true}
                        visible={this.state.isLoadPanelVisible}
                        onShown={this.hideLoadPanel}
                    />
                    <Button
                        text="Show the Load Panel"
                        onClick={this.handleClick}
                    />
                </div>
            );
        }
    }

    export default App;

---

If you are going to change event handlers at runtime, or if you need to attach several handlers to a single event, subscribe to the events using the [on(eventName, eventHandler)](/api-reference/10%20UI%20Components/Component/3%20Methods/on(eventName_eventHandler).md '/Documentation/ApiReference/UI_Components/dxLoadPanel/Methods/#oneventName_eventHandler') method. This approach is more typical of jQuery.

    <!--JavaScript-->
    const shownEventHandler1 = function (e) {
        // First handler of the "shown" event
    };

    const shownEventHandler2 = function (e) {
        // Second handler of the "shown" event
    };

    $("#loadPanelContainer").dxLoadPanel("instance")
        .on("shown", shownEventHandler1)
        .on("shown", shownEventHandler2);

#####See Also#####
#include common-link-handleevents
- [LoadPanel - Customize the Appearance](/concepts/05%20UI%20Components/LoadPanel/10%20Customize%20the%20Appearance/10%20Customize%20the%20Loading%20Indicator.md '/Documentation/Guide/UI_Components/LoadPanel/Customize_the_Appearance/')
- [LoadPanel - Resize and Relocate](/concepts/05%20UI%20Components/LoadPanel/15%20Resize%20and%20Relocate.md '/Documentation/Guide/UI_Components/LoadPanel/Resize_and_Relocate/')
- [LoadPanel Demos](https://js.devexpress.com/Demos/WidgetsGallery/Demo/LoadPanel/Overview)
- [LoadPanel API Reference](/api-reference/10%20UI%20Components/dxLoadPanel '/Documentation/ApiReference/UI_Components/dxLoadPanel/')

[tags]loadPanel, load panel, overlay, show, hide, open, close, showing, shown, hiding, hidden