<template>
    <div class="federation-cabinet container-fluid">
        <div class="row">
            <div class="col-sm-12 col-md-12 col-lg-2">
                <div class="sidebar__cabinet">
                    <div class="list-group" v-for="item of menu">
                        <button @click="toggleMenuItem(item.title)"
                                class="list-group-item list-group-item-action"
                                v-bind:class="{'list-group-item-success': activeItem === item.title}">
                            {{item.title}}
                        </button>
                    </div>
                </div>
            </div>
            <div class="col-sm-12 col-md-12 col-lg-10">
                <tournaments v-if="activeItem === 'Tournaments'"></tournaments>
                <sportsmen v-else-if="activeItem === 'Sportsmen'"></sportsmen>
                <news v-else-if="activeItem === 'News'"></news>
                <settings class="col-10" v-else-if="activeItem === 'Settings'"></settings>
            </div>
        </div>
    </div>
</template>

<script>
import Tournaments from "../components/privateCabinet/tournamentsCabinet.vue";
import Sportsmen from "../components/privateCabinet/federationSportsmenCabinet.vue";
import News from "../components/privateCabinet/newsCabinet.vue";
import Settings from "../components/privateCabinet/settingsCabinet.vue";

export default {
  name: "federation-cabinet",
  components: {
    Tournaments,
    Sportsmen,
    News,
    Settings
  },
  data: function() {
    return {
      activeItem: "Tournaments",
      menu: [
        {
          title: "Tournaments"
        },
        {
          title: "Sportsmen"
        },
        {
          title: "News"
        },
        {
          title: "Settings"
        }
      ]
    };
  },
  methods: {
    toggleMenuItem(item) {
      this.activeItem = item;
    }
  },
  mounted() {}
};
</script>

<style scoped lang="scss">
.federation-cabinet {
  margin-bottom: 30px;
}

.list-group-item {
    cursor: pointer;
}

@media (max-width: 992px) {
    .list-group {
        width: 50%;
        display: inline-block;
    }
    .list-group-item {
        font-size: 1.5rem;
    }

}
@media (max-width: 576px) {
    .list-group {
        width: 100%;
        display: block;
    }
}
</style>
