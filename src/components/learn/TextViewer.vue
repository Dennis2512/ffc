<template>
    <viewer :initialValue="text" style="background-color: white"></viewer>
</template>

<script>
import 'codemirror/lib/codemirror.css';
import '@toast-ui/editor/dist/toastui-editor-viewer.css';

import {Viewer} from '@toast-ui/vue-editor';

export default {
    props: [
        "text"
    ],
    // Test if Component is loaded
    created() {
        console.log("This Component gets loaded.")
    },
    data() {
        return {
            // editorOptions: {
            //     minHeight: '200px'
            // }
        }
    },
    components: {
        viewer: Viewer
    }
}

</script>