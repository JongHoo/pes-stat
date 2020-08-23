<script>
  import { onMount } from 'svelte'
  let players = []

  onMount(() => {
    players = [
      {
        name: '우리형',
        win: 3,
        draw: 2,
        lose: 1,
        total: 6,
        percentage: 50
      },
      {
        name: '호동생',
        win: 1,
        draw: 2,
        lose: 3,
        total: 6,
        percentage: 16.7
      }
    ]
  })
</script>

<main>
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
          <td>{player.percentage.toFixed(1)}%</td>
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
