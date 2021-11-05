<template>
  <v-card flat :dark="theme">
    <v-card-title>
      <v-btn
        data-testid="button"
        v-show="!hideadd"
        @click="$emit('add', true)"
        color="primary"
        >{{ "tambah" }}</v-btn
      >
      <v-btn
        class="ml-4"
        data-testid="button"
        v-show="!hidesimpan"
        @click="$emit('simpan', true)"
        color="primary"
        >{{ "simpan" }}</v-btn
      >

      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        :label="$t('Search')"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>

    <v-data-table flat :headers="headers" :items="items" :search="search">
      <template v-slot:[`item.jk`]="{ item }">
        {{ getJK(item.jk) }}
      </template>
      <template v-slot:[`item.status_pengajuan`]="{ item }">
        {{ getStatusConfirmation(item.status_pengajuan) }}
      </template>

      <template v-slot:[`item.no`]="{ index }">
        {{ index + 1 }}
      </template>
      <template v-slot:[`item.total_donasi`]="{ item }">
        Rp {{ formatCurrency(item.total_donasi) }}
      </template>
      <template v-slot:[`item.jumlah_pengajuan`]="{ item }">
        Rp {{ formatCurrency(item.jumlah_pengajuan) }}
      </template>
      <template v-slot:[`item.jumlah_realisasi`]="{ item }">
        Rp {{ formatCurrency(item.jumlah_realisasi) }}
      </template>

      <template v-slot:[`item.asnaf`]="{ item }">
        {{ getAsnaf(item.asnaf) }}
      </template>
      <template v-slot:[`item.status_pengguna`]="{ item }">
        {{ item.status_pengguna == 1 ? "Aktif" : "Tidak Aktif" }}
      </template>
      <template v-slot:[`item.kategori`]="{ item }">
        {{ getKategori(item.kategori) }}
      </template>

      <template v-slot:[`item.leveluser`]="{ item }">{{
        getLevel(item.leveluser)
      }}</template>
      <template v-slot:[`item.kategori_mustahik`]="{ item }">
        {{ getKetgoriMustahik(item.kategori_mustahik) }}
      </template>
      <template v-slot:[`item.npwz`]="{ item }">
        <a :class="{ 'text-color': link }" @click="cekHalaman(item)">{{
          item.npwz
        }}</a>
      </template>
      <template v-slot:[`item.nama_akun`]="{ item }">
        <a :class="{ 'text-color': link }" @click="getNamaAkun(item)">{{
          item.nama_akun
        }}</a>
      </template>
      <template v-slot:[`item.nama_sub_akun`]="{ item }">
        <a :class="{ 'text-color': link }" @click="getNamaSubAkun(item)">{{
          item.nama_sub_akun
        }}</a>
      </template>
      <template v-slot:[`item.nama_sub_akun_program`]="{ item }">
        <a
          :class="{ 'text-color': link }"
          @click="getNamaSubAkunProgram(item)"
          >{{ item.nama_sub_akun_program }}</a
        >
      </template>

      <template v-slot:[`item.action`]="{ item }">
        <b-button-toolbar
          aria-label="Toolbar with button groups and dropdown menu"
        >
          <b-button-group class="mx-1">
            <v-btn
              v-show="!hideupdate"
              @click="$emit('edit', item)"
              outlined
              small
              >{{ $t("Edit") }}</v-btn
            >
            <v-btn
              v-show="!hidedelete"
              @click="$emit('delete', item)"
              outlined
              small
              >{{ $t("Delete") }}</v-btn
            >
            <v-btn
              v-show="!hidekonfirm"
              @click="$emit('konfirmasi', item)"
              outlined
              small
              :disabled="getStatusProses(item.status_pengajuan)"
              >{{ $t("Konfirmasi") }}</v-btn
            >
            <v-btn
              v-show="!hidedetail"
              @click="$emit('detail', item)"
              outlined
              small
              >{{ $t("Detail") }}</v-btn
            >
            <v-btn
              v-show="!hidecetak"
              @click="$emit('cetak', item)"
              outlined
              small
              >{{ $t("Cetak") }}</v-btn
            >
          </b-button-group>
        </b-button-toolbar>
      </template>
    </v-data-table>
  </v-card>
</template>
<script>
import { mapState } from "vuex";
export default {
  props: [
    "items",
    "headers",
    "hideadd",
    "hidedelete",
    "hideupdate",
    "hidesimpan",
    "hidecetak",
    "hidekonfirm",
    "hidedetail",
  ],
  data() {
    return {
      search: "",
      link: "blue",
    };
  },
  computed: {
    ...mapState({
      theme: (state) => state.layout.isDark,
    }),
  },
  created() {},
  methods: {
    getAsnaf(val) {
      if (val == 1) return "fakir miskin";
      if (val == 2) return "Riqob";
      if (val == 3) return "Ibnu Sabil";
      if (val == 4) return "Ghorimin";
      if (val == 5) return "Amil";
      if (val == 6) return "Fisabilillah";
      if (val == 7) return "Amil";
      if (val == 8) return "Muallaf";
      if (val == 9) return "Lain-lain";
    },
    getKategori(val) {
      if (val == 1) return "Aset Lancar";
      if (val == 2) return "Aset Tidak Lancar";
      if (val == 3) return "Liabilitas";
      if (val == 4) return "Saldo Pendanaan";
      if (val == 5) return "Penerimaan Dana";
      if (val == 6) return "Penyaluran Dana";
      if (val == 7) return "Biaya Pengelolaan";
    },

    getJK(val) {
      console.log(val);
      if (val == 1) return "Laki-Laki";
      if (val == 2) return "Perempuan";
    },
    getLevel(level) {
      if (level == 1) return "Direktur";
      if (level == 2) return "Akuntan";
      if (level == 3) return "Program";
      if (level == 4) return "ZISR";
      if (level == 5) return "Front Office";
      if (level == 6) return "Admin";
    },

    getKetgoriMustahik(cat) {
      if (cat == 1) return "Perorangan";
      if (cat == 2) return "Lembaga";
    },
    getDetailDonasi(donasi) {
      return `/main/datadonasi/detail/${donasi.npwz}`;
    },

    getStatusConfirmation(val) {
      if (val == 1) return "Proses";
      if (val == 2) return "Diterima";
      if (val == 3) return "Ditolak";
      if (val == 4) return "Selesai";
    },

    getStatusProses(status) {
      if (status == 1) return true;
      if (status == 2) return false;
      if (status == 3) return true;
      if (status == 4) return true;
    },

    formatCurrency(total) {
      if (total) {
        const parse = parseFloat(total);
        return parse.toFixed(2).replace(/./g, function(c, i, a) {
          return i > 0 && c !== "." && (a.length - i) % 3 === 0 ? "," + c : c;
        });
      }
      return "0,00.00";
    },
    cekHalaman(data) {
      if (this.$router.currentRoute.path == "/main/muzaki") {
        this.link = "black";
        return;
      }
      return this.$router.push({ path: this.getDetailDonasi(data) });
    },
    getNamaAkun(data) {
      this.$router.push({ path: `/main/program/subakun/${data.id_akun}` });
    },
    getNamaSubAkun(data) {
      this.$router.push({
        path: `/main/program/subsubakun/${data.id_sub_akun}`,
      });
    },
    getNamaSubAkunProgram(data) {
      this.$router.push({
        path: `/main/program/dataprogram/${data.id_sub_akun_program}`,
      });
    },
  },
};
</script>
