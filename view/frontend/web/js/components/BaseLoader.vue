<template>
  <div class="block" :class="{ show: show }">
    <svg class="spinner"
         width="44px"
         height="44px"
         viewBox="0 0 44 44"
    >
      <circle class="path"
              fill="none"
              stroke-width="4"
              stroke-linecap="round"
              cx="22"
              cy="22"
              r="20"
      >
      </circle>
    </svg>
  </div>
</template>

<style lang="scss">
.block {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.5);
    z-index: 999;
    display: none;

    &.show {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    &.animation {
        animation-duration: 2s;
        animation-fill-mode: forwards;
        animation-iteration-count: infinite;
        animation-name: placeholderAnimation;
        animation-timing-function: linear;
        background: rgba(255, 255, 255, 0.5);
        background: linear-gradient(to right, transparent 10%, #EEEEEE 20%, transparent 30%);
        background-size: 200%;
        background-repeat: no-repeat;
    }

    .spinner {
        animation: rotate 1.5s linear infinite;
        animation-play-state: running;

        .path {
            stroke: #47b784;
            stroke-dasharray: 16;
            stroke-dashoffset: 0;
            transform-origin: center;
            animation: dash 1.5s ease-in-out infinite;
        }
    }
}

@keyframes rotate {
    0% {
        transform: scale(0.5) rotate(0deg);
    }

    100% {
        transform: scale(0.5) rotate(270deg);
    }
}

@keyframes dash {
    0% {
        stroke-dashoffset: 126;
    }

    50% {
        stroke-dashoffset: 32;
        transform: rotate(135deg);
    }

    100% {
        stroke-dashoffset: 126;
        transform: rotate(450deg);
    }
}

@keyframes placeholderAnimation{
    0%, 50%{
        background-position: -800px 0
    }
    50%, 100%{
        background-position: 800px 0
    }
}
</style>

<script>
export default {
  computed: {
    show() {
      if (this.$store.state.loader) {
        return true;
      }
      else {
        return false;
      }
    },
  }
}
</script>
