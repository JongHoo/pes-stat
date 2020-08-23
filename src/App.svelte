<script>
  import { Router, Route, Link, navigate } from 'svelte-routing'
  import Ranking from './containers/Ranking.svelte'
  import Dashboard from './containers/Dashboard.svelte'
  import HeadToHead from './containers/Headtohead.svelte'
  export let url = ''
  const moveHome = () => {
    navigate(`/`)
  }
  const moveRanking = () => {
    navigate(`/ranking`)
  }
  const moveHeadToHead = () => {
    navigate(`/headtohead`)
  }
</script>

<main>
  <Router url="{url}">
    <div class="header">
      <span class="main-logo" on:click={moveHome}>PES STAT</span>
    </div>
    <div class="menu-bar">
      <span class="menu" on:click={moveRanking}>랭킹</span>
      <span class="menu" on:click={moveHeadToHead}>상대전적</span>
    </div>
    <div>
      <Route path="ranking" component="{Ranking}"/>
      <Route path="/" component="{Dashboard}"/>
      <Route path="/headtohead" component="{HeadToHead}"/>
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
        margin: auto 10px;
      }
    }
  }
</style>
