The TextArea raises four keyboard events: [keyDown](/api-reference/10%20UI%20Components/dxTextEditor/4%20Events/keyDown.md '/Documentation/ApiReference/UI_Components/dxTextArea/Events/#keyDown'), [keyUp](/api-reference/10%20UI%20Components/dxTextEditor/4%20Events/keyUp.md '/Documentation/ApiReference/UI_Components/dxTextArea/Events/#keyUp') and [enterKey](/api-reference/10%20UI%20Components/dxTextEditor/4%20Events/enterKey.md '/Documentation/ApiReference/UI_Components/dxTextArea/Events/#enterKey'). Within the functions that handle them, you can access the original keyboard events. If you are _not_ going to change the functions during the lifetime of the UI component, assign them to the respective UI component properties.

---
##### jQuery

    <!--JavaScript-->$(function() {
        $("#textAreaContainer").dxTextArea({
            onKeyDown: function (e) {
                const keyCode = e.event.key;
                // Event handling commands go here
            },
            onKeyUp: function (e) {
                const keyCode = e.event.key;
                // Event handling commands go here
            },
            onEnterKey: function (e) {
                // Event handling commands go here
            }
        });
    });

##### Angular

    <!--HTML-->
    <dx-text-area
        (onKeyDown)="onKeyDown($event)"
        (onKeyUp)="onKeyUp($event)"
        (onEnterKey)="onEnterKey($event)">
    </dx-text-area>

    <!--TypeScript-->
    import { DxTextAreaModule } from "devextreme-angular";
    // ...
    export class AppComponent {
        onKeyDown (e) {
            const keyCode = e.event.key;
            // Event handling commands go here
        }
        onKeyUp (e) {
            const keyCode = e.event.key;
            // Event handling commands go here
        }
        onEnterKey (e) {
            // Event handling commands go here
        }
    }
    @NgModule({
         imports: [
             // ...
             DxTextAreaModule
         ],
         // ...
     })

##### Vue

    <template>
        <DxTextArea
            @key-down="onKeyDown"
            @key-up="onKeyUp"
            @enter-key="onEnterKey"
        />
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';
    import { DxTextArea } from 'devextreme-vue/text-area';

    export default {
        components: {
            DxTextArea
        },
        methods: {
            onKeyDown(e) {
                const keyCode = e.event.key;
                // Event handling commands go here
            },
            onKeyUp(e) {
                const keyCode = e.event.key;
                // Event handling commands go here
            },
            onEnterKey(e) {
                // Event handling commands go here
            }
        }
    }
    </script>

##### React

    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import { TextArea } from 'devextreme-react/text-area';

    class App extends React.Component {
        render() {
            return (
                <TextArea
                    onKeyDown={this.onKeyDown}
                    onKeyUp={this.onKeyUp}
                    onEnterKey={this.onEnterKey}
                />
            );
        }

        onKeyDown(e) {
            const keyCode = e.event.key;
            // Event handling commands go here
        }
        onKeyUp(e) {
            const keyCode = e.event.key;
            // Event handling commands go here
        }
        onEnterKey(e) {
            // Event handling commands go here
        }
    }

    export default App;

---

If you are going to change the handling functions at runtime, or if you need to attach several functions to a single event, use the [on(eventName, eventHandler)](/api-reference/10%20UI%20Components/Component/3%20Methods/on(eventName_eventHandler).md '/Documentation/ApiReference/UI_Components/dxTextArea/Methods/#oneventName_eventHandler') method. This approach is more typical of jQuery.

    <!--JavaScript-->
    const keyDownHandler1 = function (e) {
        const keyCode = e.event.key;
        // First handler of the "keyDown" event
    };

    const keyDownHandler2 = function (e) {
        const keyCode = e.event.key;
        // Second handler of the "keyDown" event
    };

    $("#textAreaContainer").dxTextArea("instance")
        .on("keyDown", keyDownHandler1)
        .on("keyDown", keyDownHandler2);

#include common-code-register-key-handler

#####See Also#####
#include common-link-handleevents
#include common-link-callmethods
- [TextArea - Handle the Value Change Event](/concepts/05%20UI%20Components/TextArea/10%20Handle%20the%20Value%20Change%20Event.md '/Documentation/Guide/UI_Components/TextArea/Handle_the_Value_Change_Event/')
- [TextArea Demos](https://js.devexpress.com/Demos/WidgetsGallery/Demo/TextArea/Overview)

[tags]textArea, text area, editor, keyboard events, keyup, keydown, keypress, enterkey
