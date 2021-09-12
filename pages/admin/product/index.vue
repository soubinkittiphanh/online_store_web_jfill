<template>
  <div class="text-center">
    <!-- <ImageDialog :imagePreviewURL="imagePreviewURL" :pdialog="dialog" /> -->
    <v-dialog v-model="dialog" width="500">
      <v-card>
        <v-img
          v-if="imagePreviewURL"
          :src="imagePreviewURL"
          max-height="100%"
          max-width="100%"
        ></v-img>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="dialog = false"> ປິດ </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-select
        v-model="select"
        :items="items"
        :rules="[(v) => !!v || 'Item is required']"
        label="ປະເພດສິນຄ້າ"
        required
      ></v-select>
      <v-text-field
        v-model="name"
        :counter="10"
        :rules="nameRules"
        label="ໄອດີສິນຄ້າ"
        required
      ></v-text-field>
      <v-text-field
        v-model="name"
        :counter="10"
        :rules="nameRules"
        label="ຊື້ສິນຄ້າ"
        required
      ></v-text-field>
      <v-text-field
        v-model="name"
        :counter="10"
        :rules="nameRules"
        label="ລາຄາ"
        required
      ></v-text-field>
      <v-textarea
        outlined
        name="input-7-4"
        counter="5"
        label="ຄຳອະທິບາຍ"
        value="The Woodman set to work at once, and so sharp was his axe that the tree was soon chopped nearly through."
      ></v-textarea>
      <v-file-input
        :rules="rules"
        accept="image/png, image/jpeg, image/bmp"
        placeholder="Pick an avatar"
        prepend-icon="mdi-camera"
        label="Avatar"
        @change="onFileChange"
      ></v-file-input>
      <v-img
        v-if="imagePreviewURL"
        :src="imagePreviewURL"
        max-height="150"
        max-width="250"
        @click="dialog = true"
      ></v-img>
      <v-text-field
        v-model="name"
        :counter="10"
        :rules="nameRules"
        label="ສະຖານະ"
        required
      ></v-text-field>

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

      <v-checkbox
        v-model="checkbox"
        :rules="[(v) => !!v || 'You must agree to continue!']"
        label="Do you agree?"
        required
      ></v-checkbox>

      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        ກວດສອບຂໍ້ມູນ
      </v-btn>

      <v-btn color="error" class="mr-4" @click="reset"> ລ້າງຂໍ້ມູນ </v-btn>

      <v-btn color="warning" @click="resetValidation"> ບັນທຶກ </v-btn>
    </v-form>
  </div>
</template>
<script>
import ImagePreviewMixin from './mixins/ImagePreviewMixin.vue'
export default {

  mixins: [ImagePreviewMixin],
  data: () => ({
    dialog: false,
    valid: true,
    name: '',
    nameRules: [
      (v) => !!v || 'Name is required',
      (v) => (v && v.length <= 10) || 'Name must be less than 10 characters',
    ],
    email: '',
    emailRules: [
      (v) => !!v || 'E-mail is required',
      (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
    rules: [
      (value) =>
        !value ||
        value.size < 2000000 ||
        'Avatar size should be less than 2 MB!',
    ],
    select: null,
    items: [
      'ບັດເກມ GARINA FREEFIRE',
      'ບັດເກມ PUBG',
      'ເຄື່ອງໃຊ້ທົ່ວໄປ',
      'ເຄື່ອງດື່ມ',
    ],
    checkbox: false,
  }),

  methods: {
    validate() {
      this.$refs.form.validate()
    },
    reset() {
      this.$refs.form.reset()
    },
    resetValidation() {
      this.$refs.form.resetValidation()
    },
  },
}
</script>

<style scoped>
.text-h5,.grey{
  font-family: "Noto Sans Lao";
}
</style>