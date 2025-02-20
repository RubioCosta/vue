<template>
  <div class="loading-main">
    <div class="first-box"></div>
    <div class="second-box"></div>
  </div>
</template>

<script>
  export default {
    name: 'Loading',
    data() {
      return {

      }
    }
  }
</script>

<style>
  .loading-main {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .first-box, .second-box {
    flex: 1;
    height: 300px;
    margin: 4px;
    animation: animation-loading 5s infinite;
  }

  @keyframes animation-loading {
    0%  {
      background: rgb(222,218,255);
      background: linear-gradient(352deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    5%  {
      background: rgb(222,218,255);
      background: linear-gradient(0deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    10%  {
      background: rgb(222,218,255);
      background: linear-gradient(32deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    20%  {
      background: rgb(222,218,255);
      background: linear-gradient(64deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    30%  {
      background: rgb(222,218,255);
      background: linear-gradient(96deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    40%  {
      background: rgb(222,218,255);
      background: linear-gradient(128deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    50%  {
      background: rgb(222,218,255);
      background: linear-gradient(160deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    60%  {
      background: rgb(222,218,255);
      background: linear-gradient(192deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    70%  {
      background: rgb(222,218,255);
      background: linear-gradient(224deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    80%  {
      background: rgb(222,218,255);
      background: linear-gradient(256deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    90%  {
      background: rgb(222,218,255);
      background: linear-gradient(288deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
    100%  {
      background: rgb(222,218,255);
      background: linear-gradient(320deg ,rgb(222, 222, 223),rgb(191, 192, 192));
    }
  }
</style>