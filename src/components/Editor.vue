<script setup lang="ts">
import {useEditor, EditorContent} from "@tiptap/vue-3";
import * as Y from "yjs"
import Collaboration from "@tiptap/extension-collaboration"
import CollaborationCursor from "@tiptap/extension-collaboration-cursor";

import { WebrtcProvider } from "y-webrtc";
import StarterKit from "@tiptap/starter-kit";
const doc = new Y.Doc();
const provider = new WebrtcProvider("text-editor",doc);
const editor= useEditor({
  content:"<p>Hello world!</p>",
  extensions: [StarterKit, 
  Collaboration.configure({
document: doc,
  }),
  CollaborationCursor.configure({
    provider: provider,
    user: {
      name: "Suman Bhardwaj",
      color: "purple",
    },
  }),
]
});
</script>

<template>
  <EditorContent :editor="editor" />
  
</template>