<template>
  <div>
    <div class="row">
      <div class="col-sm-12">
        <px-card :actions="false">
          <div slot="with-padding">
            <b-form class="needs-validation" @submit.prevent="onsubmit">
              <div class="form-row">
                <div class="col-md-12 mb-3">
                  <label for="c_form_alamat">Judul</label>
                  <b-form-textarea
                    placeholder="Deskripsi"
                    rows="3"
                    no-resize
                  ></b-form-textarea>
                </div>
              </div>
              <div class="form-row">
                <div class="col-md-12 ">
                  <label>Gambar Produk</label>
                  <b-form-file
                    placeholder="Pilih File"
                    drop-placeholder="Pilih File"
                    @change="onPilihFile"
                  ></b-form-file>
                </div>
              </div>

              <b-button type="submit" variant="primary">Simpan</b-button>
              <b-button class="ml-3" type="submit" variant="primary"
                >Simpan</b-button
              >
            </b-form>
          </div>
        </px-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["isEdit", "body"],
  data() {
    return {
      form: {},
    };
  },

  methods: {
    onsubmit() {
      console.log(this.form);
      this.$emit("submit", this.form);
    },
  },
};
</script>
