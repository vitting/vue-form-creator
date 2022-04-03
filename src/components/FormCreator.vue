<template>
    <div>
        <v-container grid-list-xs>
            <v-row>
                <v-col cols="3">
                    <h1>test1</h1>
                    <draggable
                        :list="list1"
                        :group="{ name: 'people', pull: 'clone', put: false }"
                        @change="log"
                        item-key="id"
                        :clone="cloneElement"
                        :sort="false"
                    >
                        <template #item="{ element }">
                            <div>
                                <TextComponent
                                    v-if="element.component === 'TextComponent'"
                                    :label="element.label"
                                    :type="element.type"
                                    :disabled="true"
                                ></TextComponent>
                                <TextAreaComponent
                                    v-if="element.component === 'TextAreaComponent'"
                                    :label="element.label"
                                ></TextAreaComponent>
                                <SwitchComponent
                                    v-if="element.component === 'SwitchComponent'"
                                    :label="element.label"
                                ></SwitchComponent>
                                <CheckboxComponent
                                    v-if="element.component === 'CheckboxComponent'"
                                    :label="element.label"
                                ></CheckboxComponent>
                            </div>
                        </template>
                    </draggable>
                </v-col>
                <v-col cols="3">
                    <h1>test2</h1>
                    <draggable
                        :list="list2"
                        group="people"
                        @change="log"
                        item-key="id"
                        class="area"
                    >
                        <template #item="{ element }">
                            <div>
                                <TextComponent
                                    v-if="element.component === 'TextComponent'"
                                    :label="element.label"
                                    :type="element.type"
                                ></TextComponent>
                                <TextAreaComponent
                                    v-if="element.component === 'TextAreaComponent'"
                                    :label="element.label"
                                ></TextAreaComponent>
                                <SwitchComponent
                                    v-if="element.component === 'SwitchComponent'"
                                    :label="element.label"
                                ></SwitchComponent>
                                <CheckboxComponent
                                    v-if="element.component === 'CheckboxComponent'"
                                    :label="element.label"
                                ></CheckboxComponent>
                            </div>
                        </template>
                    </draggable>
                </v-col>
                <v-col cols="3">
                    <RawDisplayer :value="list1" title="List 1" />
                </v-col>
                <v-col cols="3">
                    <RawDisplayer :value="list2" title="List 2" />
                </v-col>
            </v-row>
        </v-container>
        <v-dialog v-model="dialog">
            <v-card>
                <v-card-title>
                    <span class="text-h5">User Profile</span>
                </v-card-title>
                <v-card-text>
                    <v-container>
                        <v-row>
                            <v-col cols="12">
                                
                            </v-col>
                        </v-row>
                    </v-container>
                </v-card-text>
                <v-card-actions>
                    <v-btn color="primary" block @click="dialog = false">Close Dialog</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </div>
</template>

<script setup lang="ts">
import { uid } from 'uid';
import { reactive, ref } from "vue";
import draggable from "vuedraggable";
import RawDisplayer from "./RawDisplayer.vue";
import TextComponent from "./form-components/TextComponent.vue";
import TextAreaComponent from "./form-components/TextAreaComponent.vue";
import SwitchComponent from "./form-components/SwitchComponent.vue";
import CheckboxComponent from "./form-components/CheckboxComponent.vue";

interface ElementInteface {
    label: string;
    id: string;
    type: string;
    component: string;
}

const dialog = ref(false);

const list1 = reactive([
    { type: "text", label: "Text", id: uid(), component: "TextComponent" },
    { type: "number", label: "Number", id: uid(), component: "TextComponent" },
    { type: "email", label: "Email", id: uid(), component: "TextComponent" },
    { type: "date", label: "Date", id: uid(), component: "TextComponent" },
    { type: "password", label: "Password", id: uid(), component: "TextComponent" },
    { type: "textarea", label: "Textarea", id: uid(), component: "TextAreaComponent" },
    { type: "switch", label: "Switch", id: uid(), component: "SwitchComponent" },
    { type: "Checkbox", label: "Checkbox", id: uid(), component: "CheckboxComponent" }
] as ElementInteface[]);

const list2 = reactive([

] as ElementInteface[]);

const log = (evt: Event) => {
    console.log(evt);
}

const cloneElement = (element: ElementInteface) => {
    return {
        label: `element clone ${element.label}`,
        id: uid(),
        type: element.type,
        component: element.component
    }
}


</script>

<style scoped>
.area {
    background-color: rgb(250, 250, 250);
    min-height: 4em;
}
</style>