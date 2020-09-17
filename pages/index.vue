<template>
  <div class="container">
    <textarea v-model="context"></textarea>
    <button @click="getText">GET</button>
  </div>
</template>

<script>
export default {
  head: {
    script: [
      { src: 'https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js' },
      { src: 'https://cdnjs.cloudflare.com/ajax/libs/tinymce/5.0.5/tinymce.min.js' }
    ]
  },
  data() {
    return {
      context: 'test'
    }
  },
  mounted() {
    setTimeout(() => {
      tinymce.init({
        selector: "textarea",
        plugins: "lists advlist autolink autoresize charmap code emoticons hr image insertdatetime link media paste preview searchreplace table textpattern toc visualblocks visualchars wordcount quickbars",
        toolbar: "fontsizeselect | bold italic underline strikethrough backcolor | subscript superscript | numlist bullist | alignleft aligncenter alignright alignjustify | outdent indent | paste searchreplace | toc link image media charmap insertdatetime emoticons hr | table tabledelete | tableprops tablerowprops tablecellprops | tableinsertrowbefore tableinsertrowafter tabledeleterow | tableinsertcolbefore tableinsertcolafter tabledeletecol | removeformat",
        insertdatetime_element: true,
        media_scripts: [
        {filter: 'platform.twitter.com'},
        {filter: 's.imgur.com'},
        {filter: 'instagram.com'},
        {filter: 'https://platform.twitter.com/widgets.js'},
      ],
        browser_spellcheck: true,
        contextmenu: false,
      });
    }, 100);
  },
  methods: {
    getText() {
      var conconet = tinymce.activeEditor.getContent()
      console.log(conconet)
    }
  }
}
</script>