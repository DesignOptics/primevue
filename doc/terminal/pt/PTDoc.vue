<template>
    <DocSectionText v-bind="$attrs" :level="2" />
    <div class="card">
        <p>Enter "<strong>date</strong>" to display the current date, "<strong>greet {0}</strong>" for a message and "<strong>random</strong>" to get a random number.</p>
        <Terminal
            welcomeMessage="Welcome to PrimeVue"
            prompt="primevue $"
            :pt="{
                root: { class: 'surface-900 text-white' },
                command: { class: 'text-blue-500' },
                prompt: { class: 'text-yellow-500' },
                response: { class: 'text-purple-500' }
            }"
        />
    </div>
    <DocSectionCode :code="code" />
</template>

<script>
import TerminalService from 'primevue/terminalservice';

export default {
    data() {
        return {
            code: {
                basic: `
<Terminal
    welcomeMessage="Welcome to PrimeVue"
    prompt="primevue $"
    :pt="{
        root: { class: 'surface-900 text-white' },
        command: { class: 'text-blue-500' },
        prompt: { class: 'text-yellow-500' },
        response: { class: 'text-purple-500' }
    }"
/>`,
                options: `
<template>
    <div>
        <p>Enter "date" to display the current date, "greet {0}" for a message and "random" to get a random number.</p>
        <Terminal
            welcomeMessage="Welcome to PrimeVue"
            prompt="primevue $"
            :pt="{
                root: { class: 'surface-900 text-white' },
                command: { class: 'text-blue-500' },
                prompt: { class: 'text-yellow-500' },
                response: { class: 'text-purple-500' }
            }"
        />
    </div>
</template>

<script>
import TerminalService from "primevue/terminalservice";

export default {
    methods: {
        commandHandler(text) {
            let response;
            let argsIndex = text.indexOf(' ');
            let command = argsIndex !== -1 ? text.substring(0, argsIndex) : text;

            switch(command) {
                case "date":
                    response = 'Today is ' + new Date().toDateString();
                    break;

                case "greet":
                    response = 'Hola ' + text.substring(argsIndex + 1);
                    break;

                case "random":
                    response = Math.floor(Math.random() * 100);
                    break;

                default:
                    response = "Unknown command: " + command;
            }
            
            TerminalService.emit('response', response);
        }
    },
    mounted() {
        TerminalService.on('command', this.commandHandler);
    },
    beforeUnmount() {
        TerminalService.off('command', this.commandHandler);
    }
}
<\/script>`,
                composition: `
<template>
    <div>
        <p>Enter "date" to display the current date, "greet {0}" for a message and "random" to get a random number.</p>
        <Terminal
            welcomeMessage="Welcome to PrimeVue"
            prompt="primevue $"
            :pt="{
                root: { class: 'surface-900 text-white' },
                command: { class: 'text-blue-500' },
                prompt: { class: 'text-yellow-500' },
                response: { class: 'text-purple-500' }
            }"
        />
    </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue';
import TerminalService from "primevue/terminalservice";

onMounted(() => {
    TerminalService.on('command', commandHandler);
})

onBeforeUnmount(() => {
    TerminalService.off('command', commandHandler);
})

const commandHandler = (text) => {
    let response;
    let argsIndex = text.indexOf(' ');
    let command = argsIndex !== -1 ? text.substring(0, argsIndex) : text;

    switch(command) {
        case "date":
            response = 'Today is ' + new Date().toDateString();
            break;

        case "greet":
            response = 'Hola ' + text.substring(argsIndex + 1);
            break;

        case "random":
            response = Math.floor(Math.random() * 100);
            break;

        default:
            response = "Unknown command: " + command;
    }
    
    TerminalService.emit('response', response);
}
<\/script>`
            }
        };
    },
    mounted() {
        TerminalService.on('command', this.commandHandler);
    },
    beforeUnmount() {
        TerminalService.off('command', this.commandHandler);
    },
    methods: {
        commandHandler(text) {
            let response;
            let argsIndex = text.indexOf(' ');
            let command = argsIndex !== -1 ? text.substring(0, argsIndex) : text;

            switch (command) {
                case 'date':
                    response = 'Today is ' + new Date().toDateString();
                    break;

                case 'greet':
                    response = 'Hola ' + text.substring(argsIndex + 1);
                    break;

                case 'random':
                    response = Math.floor(Math.random() * 100);
                    break;

                default:
                    response = 'Unknown command: ' + command;
            }

            TerminalService.emit('response', response);
        }
    }
};
</script>
