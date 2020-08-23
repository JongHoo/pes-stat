<script>
  import { Router, Route, Link, navigate } from 'svelte-routing'
  import Ranking from './containers/Ranking.svelte'
  import Dashboard from './containers/Dashboard.svelte'
  export let url = ''
  const moveHome = () => {
    navigate(`/`)
  }
  const moveRanking = () => {
    navigate(`/ranking`)
  }
</script>

<main>
  <Router url="{url}">
    <div class="header">
      <span class="main-logo" on:click={moveHome}>PES STAT PAGE</span>
    </div>
    <div class="menu-bar">
      <span class="menu" on:click={moveRanking}>RANKING</span>
    </div>
    <div>
      <Route path="ranking" component="{Ranking}"/>
      <Route path="/" component="{Dashboard}"/>
    </div>
  </Router>
</main>

<style lang="less">
  main {
    .header {
      display: flex;
      justify-content: center;
      margin-bottom: 20px;
      & .main-logo {
        font-weight: bold;
        font-size: 60px;
        cursor: pointer;
      }
    }
    .menu-bar {
      display: flex;
      justify-content: center;
      margin-bottom: 50px;
      .menu {
        font-weight: bold;
        cursor: pointer;
      }
    }
  }
</style>
