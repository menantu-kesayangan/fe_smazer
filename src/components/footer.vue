<template>
  <footer class="main-footer">
    <div class="row">
      <div class="col-md-12 footer-copyright text-center">
        <p class="mb-0">
          Copyright 2021 © PT Azki Inovasi Nusantara
        </p>
      </div>
    </div>
  </footer>
</template>

<script>
import json from "../data/menu";
export default {
  name: "footerpage",
  data() {
    return {
      customizer: false,
      data:
        "data:text/json;charset=utf-8," +
        encodeURIComponent(JSON.stringify(json)),
    };
  },
};
</script>
<style>
.main-footer {
  background-color: #fff;
  -webkit-box-shadow: 0 0 20px rgba(89, 102, 122, 0.1);
  box-shadow: 0 0 20px rgba(89, 102, 122, 0.1);
  /* padding: 15px; */
  bottom: 0;
  left: 0;
  /* margin-left: 280px; */
  -webkit-transition: 0.5s;
  transition: 0.5s;
}
</style>
