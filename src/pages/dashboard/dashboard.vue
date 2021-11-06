<template>
  <div class="container">
      <v-row>
        <v-col sm="12" md="12" lg="12" xl="12" class="mt-16 mt-sm-16 ">
          <h1 class="text-center ">Data Statistik Harian</h1>
        </v-col>

        <div class="col-md-4">
          <div class="card border-left-danger">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                      class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Suhu Tertinggi
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    {{ suhu_tertinggi }}
                    <sup>o</sup>C
                  </div>
                </div>
                <div class="col-auto">
                  <feather type="thermometer"></feather>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <div class="card border-left-warning">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                      class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Suhu Rata-rata
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    {{ suhu_rata }}
                    <sup>o</sup>C
                  </div>
                </div>
                <div class="col-auto">
                  <feather type="thermometer"></feather>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <div class="card border-left-success">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                      class="font-weight-bold text-uppercase text-primary mb-1"
                  >
                    Suhu Terendah
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    {{ suhu_terendah }}
                    <sup>o</sup>C
                  </div>
                </div>
                <div class="col-auto">
                  <feather type="thermometer"></feather>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="col-md-4">
          <div class="card border-left-info">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                      class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Saturasi Oksigen Tertinggi
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    {{ saturasi_tertinggi }}
                    &#37;
                  </div>
                </div>
                <div class="col-auto">
                  <feather type="droplet"></feather>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <div class="card border-left-primary">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                      class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Saturasi Oksigen Rata-rata
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    {{ saturasi_rata }} &#37;
                  </div>
                </div>
                <div class="col-auto">
                  <feather type="droplet"></feather>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <div class="card border-left-dark">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                      class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Saturasi Oksigen Terendah
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    {{ saturasi_terendah }} &#37;
                  </div>
                </div>
                <div class="col-auto">
                  <feather type="droplet"></feather>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="col-md-6">
          <div class="card">
            <div class="widget-feedback card-body">
              <div class="feedback-top text-center">
                <h6 class="font-roboto f-w-400">Data Pengunjung</h6>
              </div>
              <!-- <div class="text-center">chart put here</div> -->
              <div id="donutchart">
                <center>
                  <iframe
                      width="300"
                      height="260"
                      style="border: 0px solid #cccccc;"
                      src="https://thingspeak.com/channels/1322668/charts/2?bgcolor=%23ffffff&color=%23d62020&dynamic=true&results=60&type=line&update=15"
                  ></iframe>
                </center>
              </div>
            </div>
          </div>
        </div>

        <div class="col-md-6">
          <div class="card">
            <div class="widget-feedback card-body">
              <div class="feedback-top text-center">
                <h6 class="font-roboto f-w-400">Volume Hand Sanitizer</h6>
              </div>
              <!-- <div class="text-center">chart put here</div> -->
              <div id="donutchart">
                <center>
                  <iframe
                      width="300"
                      height="260"
                      style="border: 0px solid #cccccc;"
                      src="https://thingspeak.com/channels/1322668/widgets/375826"
                  ></iframe>
                </center>
              </div>
            </div>
          </div>
        </div>
      </v-row>
  </div>
</template>

<script>
var primary = localStorage.getItem("primary_color") || "#7366ff";
import API from "@/services/api.service";
export default {
  name: "ChartWidgets",
  data() {
    return {
      suhu_tertinggi: 0,
      suhu_terendah: 0,
      suhu_rata: 0,
      saturasi_tertinggi: 0,
      saturasi_terendah: 0,
      saturasi_rata: 0,
    };
  },
  created() {
    this.getSuhuTertinggi();
    this.getSuhuTerendah();
    this.getSuhuRata();
    this.getSaturasiTertinggi();
    this.getSaturasiTerendah();
    this.getSaturasiRata();
  },
  methods: {
    getSuhuTertinggi() {
      API.get("/api/maxsuhu").then(({ status, data }) => {
        if (status === 200 || status === 201) {
          // if (data.status) {
          //notif berhasil
          console.log(data);
          this.suhu_tertinggi = data.data;
        } else {
          //notif gagal
        }
        // } else {
        //notif gagal
        // }
      });
    },
    getSuhuTerendah() {
      API.get("/api/minsuhu").then(({ status, data }) => {
        if (status === 200 || status === 201) {
          // if (data.status) {
          //notif berhasil
          console.log(data);
          this.suhu_terendah = data.data;
        } else {
          //notif gagal
        }
        // } else {
        //   //notif gagal
        // }
      });
    },
    getSuhuRata() {
      API.get("/api/meansuhu").then(({ status, data }) => {
        if (status === 200 || status === 201) {
          // if (data.status) {
          //notif berhasil
          console.log(data);
          this.suhu_rata = data.data;
        } else {
          //notif gagal
        }
        // } else {
        //   //notif gagal
        // }
      });
    },
    getSaturasiTertinggi() {
      API.get("/api/maxsaturasi").then(({ status, data }) => {
        if (status === 200 || status === 201) {
          // if (data.status) {
          //notif berhasil
          console.log(data);
          this.saturasi_tertinggi = data.data;
        } else {
          //notif gagal
        }
        // } else {
        //   //notif gagal
        // }
      });
    },
    getSaturasiTerendah() {
      API.get("/api/minsaturasi").then(({ status, data }) => {
        if (status === 200 || status === 201) {
          // if (data.status) {
          //notif berhasil
          console.log(data);
          this.saturasi_terendah = data.data;
        } else {
          //notif gagal
        }
        // } else {
        //   //notif gagal
        // }
      });
    },
    getSaturasiRata() {
      API.get("/api/meansaturasi").then(({ status, data }) => {
        if (status === 200 || status === 201) {
          // if (data.status) {
          //notif berhasil
          console.log(data);
          this.saturasi_rata = data.data;
        } else {
          //notif gagal
        }
        // } else {
        //   //notif gagal
        // }
      });
    },
  },
};
</script>
<style>
.paddingatas {
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  color: black;
  padding: 5%;
  padding-bottom: 2%;
}
</style>
