<template>
  <div class="about">
      <div v-show="show(id)">
        <h1>current Team: {{ team.name }}</h1>
        <button @click="counter(team.name)">counter</button>
        <h1>{{ $store.state.sum }}</h1>
        <p>Last team name clicked: {{ $store.state.lastTeam }}</p>
      </div>
    <router-link to="/">戻る</router-link>
  </div>
</template>
<script>
export default {
  props: ['id'],
  data() {
    return {
      teams: [
        {
          id: "c36136ef-552f-4dc9-84b6-65ecb8574e81",
          name: "Team_A",
        },
        {
          id: "ed0459f5-716d-4ef4-99ba-5dc750dfe0d0",
          name: "Team_B",
        },
        {
          id: "60d0d5d5-8ce9-41d9-a65b-13a090c10ae1",
          name: "Team_C",
        },
      ],
      team: ''
    };
  },
  methods: {
    counter(teamName) {
      this.$store.commit('increment');
      this.$store.commit('setLastTeam', teamName);
    },
    show(id) {
      let team = this.teams.find(el => el.id === id);
      this.team = team;
      return team !== null;
    }
  }
};
</script>
