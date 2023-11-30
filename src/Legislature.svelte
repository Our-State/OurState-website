<script lang="ts">
  let loadingContainer: HTMLDivElement,
    searchInput: HTMLInputElement,
    billRows: BillData[] = [];

  type BillData = {
    state: string;
    bill_number: string;
    last_action_date: string;
    last_action: string;
    title: string;
    text_url: string;
  };

  function searchBills() {
    const searchQuery = searchInput.value,
      apiKey = "63420fa619819847e354e0203c6581a5",
      apiUrl = `https://api.legiscan.com/?key=${apiKey}&op=getSearch&query=${searchQuery}&state=nj`;

    loadingContainer.style.display = "block";

    // Make the AJAX request to the LegiScan API
    fetch(apiUrl)
      .then((response) => response.json())
      .then((data) => {
        if (data.status === "OK") {
          const searchResult = Object.values(data.searchresult);
          billRows = Object.values(searchResult)
            .filter((data) => typeof data === "object")
            .filter((data: Object) => "state" in data) as unknown as BillData[];
        } else {
          alert("An error occurred while fetching the data.");
        }

        loadingContainer.style.display = "none";
      })
      .catch((error) => {
        alert("An error occurred while fetching the data.");
        console.error(error);

        loadingContainer.style.display = "none";
      });
  }
</script>

<svelte:head>
  <title>OurState - Legislature Archive</title>
</svelte:head>

<center>
  <h1>NJ Bill Search</h1>
  <input type="text" bind:this={searchInput} placeholder="Enter Search Query" />
  <button on:click={searchBills}>Search</button>

  <table>
    <tr>
      <th>State</th>
      <th>Bill Number</th>
      <th>Last Action Date</th>
      <th>Last Action</th>
      <th>Title/Synopsis</th>
      <th>Link</th>
    </tr>
    {#each billRows as billData (billData.bill_number)}
      <tr>
        <td>{billData.state}</td>
        <td>{billData.bill_number}</td>
        <td>{billData.last_action_date}</td>
        <td>{billData.last_action}</td>
        <td>{billData.title}</td>
        <td>
          <a href={billData.text_url} target="_blank">
            {billData.text_url}
          </a>
        </td>
      </tr>
    {/each}
  </table>
</center>

<div class="loading" bind:this={loadingContainer} />

<style>
  button {
    padding-left: 1rem;
    padding-right: 1rem;
    font-size: 1rem;
    border: none;
    background-color: var(--blue);
    color: var(--bg);
    cursor: pointer;
    height: 2rem;
    border-radius: 1rem;
  }

  button:hover {
    background-color: var(--dim-bg);
    color: var(--fg);
    border-radius: 0.5rem;
  }

  table {
    margin-top: 2rem;
    border-collapse: collapse;
    width: min(80vw, 1600px);
    max-width: flex;
    border: 2px solid #00000030;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }

  td {
    padding-left: 1rem;
    padding-right: 1rem;
  }

  th {
    background-color: var(--blue);
    color: var(--bg);
    padding-left: 2rem;
    padding-right: 2rem;
  }

  .loading {
    display: none;
    border: 4px solid color-mix(in srgb, var(--blue) 20%, var(--bg));
    border-top: 4px solid var(--blue);
    border-radius: 50%;
    width: min(8vw, 8vh);
    height: min(8vw, 8vh);
    animation: spin 1s linear infinite;
    align-content: center;
    position: absolute;
    top: 50vh;
    left: 50vw;
    transform: translate(-50%, -50%);
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
