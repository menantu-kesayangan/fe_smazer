<template>
  <div class="container">
    <div>
      <div class="paddingatas">
        <h1 class="text-center ">Data Statistik Harian</h1>
      </div>
      <div class="row">
        <div class="col-md-4">
          <div class="card border-left-primary">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                    class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Suhu Tertinggi
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    30
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
          <div class="card border-left-primary">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                    class="font-weight-bold text-uppercase text-primary  mb-1"
                  >
                    Suhu Terendah
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">50</div>
                </div>
                <div class="col-auto">
                  <feather type="thermometer"></feather>
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
                    Suhu Rata-rata
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    30
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
          <div class="card border-left-primary">
            <div class="card-body">
              <div class="row no-gutters align-items-center">
                <div class="col mr-2">
                  <div
                    class="text-xs font-weight-bold text-primary text-uppercase mb-1"
                  >
                    Saturasi Oksigen Tertinggi
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">
                    30%
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
                    class="font-weight-bold text-uppercase text-primary  mb-1"
                  >
                    Saturasi Oksigen Terendah
                  </div>
                  <div class="h5 mb-0 font-weight-bold text-gray-800">50</div>
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
                    30
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
      </div>
    </div>
  </div>
</template>

<script>
var primary = localStorage.getItem("primary_color") || "#7366ff";
export default {
  name: "ChartWidgets",
  data() {
    return {};
  },
};
</script>
<style>
.paddingatas {
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  color: black;
  padding: 6%;
}
</style>
