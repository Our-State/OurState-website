<svelte:head>
  <title>OurState - Legislature Archive</title>
  </svelte:head>

<script lang="ts">
  // Function to create a new row and populate it with bill data
  function createBillRow(billData) {
    if (billData.state == undefined) return;
    const newRow = document.createElement("tr");
    newRow.innerHTML = `
        <td>${billData.state}</td>
        <td>${billData.bill_number}</td>
        <td>${billData.bill_id}</td>
        <td>${billData.last_action_date}</td>
        <td>${billData.last_action}</td>
        <td>${billData.title}</td>
        <td><a href='${billData.text_url}' target='_blank'>${billData.text_url}</a></td>
      `;
    return newRow;
  }

  // Function to populate the table with data
  function populateTable(searchResult) {
    const billDataArray = Object.values(searchResult).filter(
      (item) => typeof item === "object"
    );
    const table = document.getElementById("billsTable") as HTMLTableElement;

    // Remove existing rows from the table (excluding the header row)
    while (table.rows.length > 1) {
      table.deleteRow(1);
    }

    // Loop through the search result and add bill rows to the table
    for (let i = 0; i < billDataArray.length; i++) {
      const billData = billDataArray[i];
      const newRow = createBillRow(billData);
      if (newRow) table.appendChild(newRow);
    }
  }

  // Function to perform a full-text search using the LegiScan API
  function searchBills() {
    const billsTable = document.getElementById(
      "billsTable"
    ) as HTMLTableElement;
    const loadingContainer = document.querySelector(
      ".loading-container"
    ) as HTMLDivElement;

    const searchQuery = (
      document.getElementById("searchInput") as HTMLInputElement
    ).value;
    const apiKey = "63420fa619819847e354e0203c6581a5";
    const apiUrl = `https://api.legiscan.com/?key=${apiKey}&op=getSearch&query=${searchQuery}&state=nj`;

    loadingContainer.style.display = "block";
    billsTable.style.display = "none";

    // Make the AJAX request to the LegiScan API
    fetch(apiUrl)
      .then((response) => response.json())
      .then((data) => {
        if (data.status === "OK") {
          const searchResult = Object.values(data.searchresult);
          populateTable(searchResult);
        } else {
          alert("An error occurred while fetching the data.");
        }

        loadingContainer.style.display = "none";
        billsTable.style.display = "table";
      })
      .catch((error) => {
        alert("An error occurred while fetching the data.");
        console.error(error);

        loadingContainer.style.display = "none";
        billsTable.style.display = "table";
      });
  }
</script>

<h1>NJ Bill Search</h1>
<input type="text" id="searchInput" placeholder="Enter Search Query" />
<button on:click={searchBills}>Search</button>
<div class="loading-container">
  <div class="loading" />
  <p>Loading...</p>
</div>
<table id="billsTable">
  <tr>
    <th>State</th>
    <th>Bill Number</th>
    <th>Bill ID</th>
    <th>Last Action Date</th>
    <th>Last Action</th>
    <th>Title</th>
    <th>Link</th>
  </tr>
</table>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Open+Sans&display=swap");

  table {
    border-collapse: collapse;
    width: 100%;
    max-width: flex;
    border: 2px solid #ddd;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 20px;
  }

  .loading-container {
    display: none;
    text-align: center;
    padding: 20px;
  }

  .loading {
    border: 4px solid #f3f3f3;
    border-top: 4px solid #3498db;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    animation: spin 1s linear infinite;
    align-content: center;
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
