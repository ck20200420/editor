<template>
  <div class="container">
    <editor
        v-model="content"
        api-key="csbjkrxgrzjz43jwb0eem0uxkpwdqnrmfgjpkul70yxcp2tg"
        :init="init"
     />
     <input name="image" type="file" id="upload" class="hidden" onchange="">
  </div>
</template>

<script>
import $ from 'jquery'
import Editor from '@tinymce/tinymce-vue'
export default {
  data() {
    return {
      content: 'test',
      init: {
        language: 'zh_TW',
        menubar: false,
        plugins: [
          'lists advlist autolink autoresize charmap emoticons image insertdatetime link paste textpattern toc visualblocks',
        ],
        toolbar: 'fontsizeselect forecolor backcolor bold italic underline strikethrough | numlist bullist | aligncenter alignleft alignright | link image emoticons',
        paste_data_images: false,
        image_advtab: true,
        file_picker_callback: function(callback, value, meta) {
          if (meta.filetype == 'image') {
            $('#upload').trigger('click');
            $('#upload').on('change', function() {
              var file = this.files[0];
              var reader = new FileReader();
              reader.onload = function(e) {
                console.log(e)
                callback(e.target.result, {
                  alt: ''
                });
              };
              reader.readAsDataURL(file);
            });
          }
        }
      }
    }
  },
  components: {
    'editor': Editor
  }
}
</script>