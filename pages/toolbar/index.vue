<template>
    <DocComponent title="Vue Toolbar Component" header="Toolbar" description="Toolbar is a grouping component for buttons and other content." :componentDocs="docs" :apiDocs="['Toolbar']" :ptTabComponent="ptComponent" />
</template>
<script>
import AccessibilityDoc from '@/doc/toolbar/AccessibilityDoc';
import BasicDoc from '@/doc/toolbar/BasicDoc';
import ImportDoc from '@/doc/toolbar/ImportDoc';
import StyleDoc from '@/doc/toolbar/StyleDoc';
import PTComponent from '@/doc/toolbar/pt/index.vue';

export default {
    data() {
        return {
            docs: [
                {
                    id: 'import',
                    label: 'Import',
                    component: ImportDoc
                },
                {
                    id: 'basic',
                    label: 'Basic',
                    component: BasicDoc
                },
                {
                    id: 'style',
                    label: 'Style',
                    component: StyleDoc
                },
                {
                    id: 'accessibility',
                    label: 'Accessibility',
                    component: AccessibilityDoc
                }
            ],
            ptComponent: PTComponent
        };
    }
};
</script>
