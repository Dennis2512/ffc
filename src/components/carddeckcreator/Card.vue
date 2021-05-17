<template>
  <div>
    <v-card>
      <v-card-actions>
        <v-card-title style="cursor: pointer" @click="show = !show">{{
          id
        }}</v-card-title>
        <v-btn icon @click="show = !show">
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn icon @click="deleteCard">
          <v-icon color="red">mdi-delete</v-icon>
        </v-btn>
      </v-card-actions>
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>
          <div>
            <v-container fluid>
              <!-- Markdown Editors -->
              <v-row style="justify-content: space-Evenly">
                <div>
                  <v-card-title>Question</v-card-title>
                  <editor
                    :ref="card.title + '_q'"
                    :initialValue="card.q"
                    :options="editorOptions"
                    initialEditType="wysiwyg"
                    placeholder="Type in your text..."
                    @change="questionChange"
                  ></editor>
                </div>
                <div>
                  <v-card-title>Answer</v-card-title>
                  <editor
                    :ref="card.title + '_a'"
                    :initialValue="card.a"
                    :options="editorOptions"
                    initialEditType="wysiwyg"
                    placeholder="Type in your text..."
                    @change="answerChange"
                  ></editor>
                </div>
              </v-row>
            </v-container>
          </div>
        </div>
      </v-expand-transition>
    </v-card>
  </div>
</template>
<script>
import 'codemirror/lib/codemirror.css'
import '@toast-ui/editor/dist/toastui-editor.css'
import { Editor } from '@toast-ui/vue-editor'
export default {
  components: {
    editor: Editor,
  },
  props: ['card', 'id'],
  data() {
    return {
      show: false,
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
          'codeblock',
        ],
      },
    }
  },
  methods: {

    deleteCard() {
      this.$emit('delete')
    },
    questionChange() {
      this.$emit(
        'questionChange',
        this.$refs[this.card.title + '_q'].invoke('getHtml')
      )
    },
    answerChange() {
      this.$emit(
        'answerChange',
        this.$refs[this.card.title + '_a'].invoke('getHtml')
      )
    }
  },
}
</script>
<style scoped>
.v-card {
  margin: 10px 0px 10px;
}
</style>
