<template>
  <div id="alert">
    <template v-for="(bind, index) in binds">
      <b-alert
        :key="index"
        :class="bind.color"
        :show="bind.show"
        :fade="bind.fade"
        :dismissible="bind.dismissible"
      >
        <b-avatar class="octa-icon">
          <component
            v-if="bind.icon"
            :is="bind.icon.component"
            :color="bind.icon.color"
          ></component>
        </b-avatar>

        <div class="octa-content">
          <span class="octa-title" v-if="bind.title">
            {{ $t(bind.title) }}
          </span>

          <div class="octa-subtitle">
            <span v-if="bind.subtitle">
              {{ $t(bind.subtitle) }}
            </span>
            <span
              class="octa-tooltip"
              v-if="bind.tooltip"
              v-b-tooltip.bottom
              :title="$t(bind.tooltip.hover)"
            >
              {{ $t(bind.tooltip.title) }}
            </span>
          </div>

          <a
            class="octa-link"
            target="_blank"
            rel="noopener noreferrer"
            v-if="bind.link"
            :href="bind.link.href"
          >
            {{ $t(bind.link.title) }}
          </a>

          <b-button
            class="octa-btn-modal"
            v-if="bind.modal"
            @click="modalShow = !modalShow"
          >
            {{ $t(bind.modal.title) }}
          </b-button>
        </div>
      </b-alert>

      <component
        v-if="bind.modal && modalShow"
        :key="index + bind.modal.component"
        :is="bind.modal.component"
        :params="bind.modal.params"
        :show="modalShow"
      ></component>
    </template>
  </div>
</template>

<script>
export default {
  name: "alert",
  components: {
    InternetDisconnectIcon: () => import("./InternetDisconnectIcon"),
    InternetSuccessIcon: () => import("./InternetSuccessIcon"),
    WhatsAppDisconnectModal: () => import("./WhatsAppDisconnectModal"),
  },
  props: {
    binds: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      modalShow: false,
    };
  },
};
</script>

<style>
.tooltip > .tooltip-inner {
  border-radius: 0.313rem;
}
</style>

<style lang="scss" scoped>
$color-dark: #333333;
$color-white: white;

.alert {
  border: 0px;
  padding: 20px;
  margin: 20px;
  border-radius: 10px;
  max-width: 325px;
  display: flex;
  align-items: center;
  box-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
  font-family: Helvetica, Arial, sans-serif;

  .octa-icon {
    height: 3.5rem;
    width: 3.5rem;
    margin-right: 10px;
  }

  .octa-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;

    .octa-title {
      font-weight: 700;
      font-size: 0.875rem;
    }

    .octa-subtitle {
      font-size: 0.75rem;

      .octa-tooltip {
        text-decoration: underline;
      }
    }

    .octa-link {
      font-size: 0.75rem;
      cursor: pointer;
      text-decoration: underline;
    }

    .octa-btn-modal {
      background-color: transparent;
      border: 0;
      margin: 0;
      padding: 0;
      font-size: 0.75rem;
      cursor: pointer;
      text-decoration: underline;
    }
  }
}

.success {
  color: $color-white;
  background-color: #07E88D;

  .octa-icon {
    background-color: #0CBD76;
  }

  .octa-btn-modal,
  .octa-link {
    color: $color-white;
  }
}

.danger {
  color: $color-white;
  background-color: #EE316B;

  .octa-icon {
    background-color: #D62158;
  }

  .octa-btn-modal,
  .octa-link {
    color: $color-white;
  }
}

.warning {
  color: $color-dark;
  background-color: #FCB54B;

  .octa-icon {
    background-color: #E59B2D;
  }

  .octa-btn-modal,
  .octa-link {
    color: $color-dark;
  }
}
</style>
