<template>
    <editor :options="editorOptions" initialEditType="wysiwyg" placeholder="Type in your text..."></editor>
</template>

<script>
import 'codemirror/lib/codemirror.css';
import '@toast-ui/editor/dist/toastui-editor.css';

import {Editor} from '@toast-ui/vue-editor';

export default {
    data() {
        return {
            editorOptions: {
                minHeight: '200px',
                language: 'en-US',
                useCommandShortcut: true,
                useDefaultHTMLSanitizer: false,
                usageStatistics: false,
                hideModeSwitch: true,
                toolbarItems: [
                    'heading',
                    'bold',
                    'italic',
                    'strike',
                    'divider',
                    'hr',
                    'quote',
                    'divider',
                    'ul',
                    'ol',
                    'task',
                    'indent',
                    'outdent',
                    'divider',
                    'table',
                    'image',
                    'link',
                    'divider',
                    'code',
                    'codeblock'
                ]
            }
        }
    },
    components: {
        editor: Editor
    }
}

</script>