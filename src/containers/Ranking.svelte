<script>
  import { onMount } from 'svelte'
  import CONSTANTS from '../constants/Constants'
  let players = []

  onMount(() => {
    players = CONSTANTS.TEMP_PLAYER_INFO_LIST.sort((a, b) => {
      return (b.win / b.total) - (a.win / a.total)
    })
  })
</script>

<main>
  <div class="title">
    랭킹
  </div>
  <div class="table-area">
    <table>
      <thead>
        <th>순위</th><th style="width: 80px;">이름</th><th>경기수</th><th>승</th><th>무</th><th>패</th><th>승률</th>
      </thead>
      <tbody>
      {#each players as player, index}
        <tr>
          <td>{index + 1}</td>
          <td>{player.name}</td>
          <td>{player.total}</td>
          <td>{player.win}</td>
          <td>{player.draw}</td>
          <td>{player.lose}</td>
          <td>{(player.win / player.total * 100).toFixed(1)}%</td>
        </tr>
      {:else}
        <tr><td colspan="6">No Data</td></tr>
      {/each}
      </tbody>
    </table>
  </div>
</main>

<style lang="less">
  main {
    & > .title {
      display: flex;
      justify-content: center;
      margin: 10px auto;
      font-weight: bold;
      font-size: 25px;
    }
    & > .table-area {
      display: flex;
      justify-content: center;
      & > table {
        text-align: center;
        & th {
          width: 50px;
        }
      }
    }
  }
</style>
