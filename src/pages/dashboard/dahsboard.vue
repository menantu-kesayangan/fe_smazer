<template>
  <div class="container">
    <v-row>
      <v-col sm="12" md="12" lg="12" xl="12" class="mt-16 mt-sm-16 ">
        <h1 class="text-center teks">Data Statistik</h1>
      </v-col>

      <div class="col-md-4 ">
        <div class="card border card1">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Suhu Tertinggi
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
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
        <div class="card border card2">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Suhu Rata-rata
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
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
        <div class="card border card3">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Suhu Terendah
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
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
        <div class="card border card4">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Saturasi Oksigen Tertinggi
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
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
        <div class="card border-left card5">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Saturasi Oksigen Rata-rata
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
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
        <div class="card border card6">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Saturasi Oksigen Terendah
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
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
      <div class="col-md-4 ">
        <div class="card border card7">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Jumlah Pengunjung PerHari
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
                  {{ pengunjung_perhari }}
                </div>
              </div>
              <div class="col-auto">
                <feather type="user"></feather>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-md-4">
        <div class="card border card8">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Jumlah Pengunjung PerMinggu
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
                  {{ pengunjung_perminggu }}
                </div>
              </div>
              <div class="col-auto">
                <feather type="user"></feather>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-md-4">
        <div class="card border card9">
          <div class="card-body">
            <div class="row no-gutters align-items-center">
              <div class="col mr-2">
                <div
                  class="text-xs font-weight-bold text-light text-uppercase mb-1"
                >
                  Jumlah Pengunjung Perbulan
                </div>
                <div class="h5 mb-0 font-weight-bold text-light">
                  {{ pengunjung_perbulan }}
                </div>
              </div>
              <div class="col-auto">
                <feather type="user"></feather>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="col-md-12">
        <div class="card card-suhu">
          <div class="widget-feedback card-body">
            <!-- <div class="text-center">chart put here</div> -->
            <center>
              <iframe
                width="490"
                height="260"
                style="border: 0px solid #cccccc;"
                src="https://thingspeak.com/channels/1560641/charts/1?bgcolor=%23ffffff&color=%23d62020&dynamic=true&results=60&title=Suhu&type=line"
              ></iframe>
            </center>
          </div>
        </div>
      </div>
      <div class="col-md-12">
        <div class="card card-saturasi">
          <div class="widget-feedback card-body">
            <!-- <div class="text-center">chart put here</div> -->
            <center>
              <iframe
                width="450"
                height="260"
                style="border: 0px solid #cccccc;"
                src="https://thingspeak.com/channels/1560641/charts/2?bgcolor=%23ffffff&color=%23d62020&dynamic=true&results=60&title=Saturasi+Oksigen&type=line"
              ></iframe>
            </center>
          </div>
        </div>
      </div>
      <div class="col-md-12">
        <div class="card card-pengunjung">
          <div class="widget-feedback card-body">
            <!-- <div class="text-center">chart put here</div> -->
            <center>
              <iframe
                width="450"
                height="260"
                style="border: 0px solid #cccccc;"
                src="https://thingspeak.com/channels/1560641/charts/4?bgcolor=%23ffffff&color=%23d62020&dynamic=true&results=60&title=Data+Pengunjung&type=line"
              ></iframe>
            </center>
          </div>
        </div>
      </div>

      <div class="col-md-12">
        <div class="card card-volume">
          <div class="widget-feedback card-body">
            <div class="feedback-top text-center">
              <h6 class="font-roboto f-w-400">Volume Hand Sanitizer</h6>
            </div>
            <center>
              <iframe
                width="450"
                height="260"
                style="border: 0px solid #cccccc;"
                src="https://thingspeak.com/channels/1560641/widgets/378987"
              ></iframe>
            </center>
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
        if (status == 200 || status == 201) {
          this.suhu_tertinggi = data.data;
          setInterval(() => {
            this.getSuhuTertinggi;
          }, 3000);
        }
      });
    },

    getSuhuTerendah() {
      API.get("/api/minsuhu").then(({ status, data }) => {
        if (status == 200 || status == 201) {
          this.suhu_terendah = data.data;
          setInterval(() => {
            this.getSuhuTerendah;
          }, 3000);
        }
      });
    },
    getSuhuRata() {
      API.get("/api/meansuhu").then(({ status, data }) => {
        if (status == 200 || status == 201) {
          this.suhu_rata = data.data;
          setInterval(() => {
            this.getSuhuRata;
          }, 3000);
        }
      });
    },
    getSaturasiTertinggi() {
      API.get("/api/maxsaturasi").then(({ status, data }) => {
        if (status == 200 || status == 201) {
          this.saturasi_tertinggi = data.data;
          setInterval(() => {
            this.getSaturasiTertinggi;
          }, 3000);
        }
      });
    },
    getSaturasiTerendah() {
      API.get("/api/minsaturasi").then(({ status, data }) => {
        if (status == 200 || status == 201) {
          this.saturasi_terendah = data.data;
          setInterval(() => {
            this.getSaturasiTerendah;
          }, 3000);
        }
      });
    },
    getSaturasiRata() {
      API.get("/api/meansaturasi").then(({ status, data }) => {
        if (status == 200 || status == 201) {
          this.saturasi_rata = data.data;
          setInterval(() => {
            this.getSaturasiRata;
          }, 3000);
        }
      });
    },
  },
};
</script>
<style>
.teks {
  font-family: Georgia, "Times New Roman", Times, serif;
  color: black;
}
.card1 {
  background-color: #f33a3a;
  color: white;
}
.card2 {
  background-color: #ceb546;
  color: white;
}
.card3 {
  background-color: navy;
  color: white;
}
.card4 {
  background-color: #5e96ae;
  color: white;
}
.card5 {
  background-color: #999999;
  color: white;
}
.card6 {
  background-color: #ff7f50;
  color: white;
}
.card7 {
  background-color: #ff6666;

  color: white;
}
.card8 {
  background-color: #ff6666;

  color: white;
}
.card9 {
  background-color: #ff6666;
  color: white;
}
</style>
