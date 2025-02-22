<template>
  <div class="loading-main">
    <div class="first-box">
      {{ id }}
    </div>
  </div>
</template>

<script setup>
  const { id } = defineProps(['id']);
</script>

<style>
  .loading-main {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .first-box {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 40px;
    margin: 4px;
    animation: animation-loading .5s ease-in-out infinite;
  }

  @keyframes animation-loading {
    0% {
      background: linear-gradient(352deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    10% {
      background: linear-gradient(32deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    20% {
      background: linear-gradient(64deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    30% {
      background: linear-gradient(96deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    40% {
      background: linear-gradient(128deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    50% {
      background: linear-gradient(160deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    60% {
      background: linear-gradient(192deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    70% {
      background: linear-gradient(224deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    80% {
      background: linear-gradient(256deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    90% {
      background: linear-gradient(288deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
    100% {
      background: linear-gradient(320deg, rgb(222, 222, 223), rgb(191, 192, 192));
    }
  }
</style>