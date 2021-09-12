<script>
import ImagePreviewMixin from './mixins/ImagePreviewMixin.vue'

export default {
  mixins: [ImagePreviewMixin],
}
</script>

<template>
  <div>
    Using Vuetify
    <v-file-input
      v-model="avatarImage"
      label="Image"
      required
      @change="onFileChange"
    ></v-file-input>
    <img
      v-if="imagePreviewURL"
      :src="imagePreviewURL"
      alt=""
      style="max-width: 100%; width: 250px; object-fit: cover"
    />
  </div>
</template>