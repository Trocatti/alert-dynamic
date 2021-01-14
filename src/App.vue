<template>
  <div id="app">
    <Alert :binds="notifications" />
  </div>
</template>

<script>
import Alert from "./components/Alert";

export default {
  name: "app",
  components: {
    Alert,
  },
  data() {
    return {
      notifications: [
        {
          color: "warning",
          title: "alert.internetDisconnect.title",
          subtitle: "alert.internetDisconnect.subtitle",
          icon: {
            component: "InternetDisconnectIcon",
          },
          dismissible: false,
          fade: true,
          show: true,
          link: {
            href: "http://google.com",
            title: "alert.internetDisconnect.resolve",
          },
        },
        {
          color: "success",
          title: "alert.internetSuccess.title",
          icon: {
            component: "InternetSuccessIcon",
          },
          dismissible: true,
          fade: true,
          show: true,
        },
        {
          color: "danger",
          title: "alert.internetDisconnect.title",
          subtitle: "alert.internetDisconnect.subtitle",
          icon: {
            component: "InternetSuccessIcon",
          },
          dismissible: false,
          fade: true,
          show: true,
          tooltip: {
            hover: "991074224, 99153214",
            title: "alert.internetDisconnect.tooltip",
          },
        },
        {
          color: "danger",
          title: "alert.internetDisconnect.title",
          subtitle: "alert.internetDisconnect.subtitle",
          icon: {
            component: "InternetDisconnectIcon",
            color: "white",
          },
          dismissible: false,
          fade: true,
          show: true,
          modal: {
            title: "alert.internetDisconnect.resolve",
            component: "WhatsAppDisconnectModal",
            params: {
              numbers: [
                {
                  name: "Financeiro",
                  number: "991074224",
                },
                {
                  name: "Vendas",
                  number: "991074224",
                },
                {
                  name: "Suporte",
                  number: "991074224",
                },
              ],
            },
          },
        },
      ],
    };
  },
};
</script>
