<script lang="ts">
 function createBillRow(billData) {
      const newRow = document.createElement('tr');
      newRow.innerHTML = `
        <td>${billData.state}</td>
        <td>${billData.bill_number}</td>
        <td>${billData.last_action_date}</td>
        <td>${billData.last_action}</td>
        <td>${billData.title}</td>
        <td><a href='${billData.text_url}' target='_blank'>Link</a></td>
      `;
      return newRow;
    }

    function populateTable(searchResult) {
      const tableBody = document.getElementById('tableBody');
      tableBody.innerHTML = '';

      for (const key in searchResult) {
        if (Object.prototype.hasOwnProperty.call(searchResult, key)) {
          const billData = searchResult[key];
          const newRow = createBillRow(billData);
          tableBody.appendChild(newRow);
        }
      }
    }

    const apiUrl = 'https://api.legiscan.com/?key=63420fa619819847e354e0203c6581a5&op=getSearch&query=status:passed&state=NJ'; // Replace 'YOUR_API_ENDPOINT' with the actual LegiScan API URL

    fetch(apiUrl)
      .then(response => response.json())
      .then(data => {
        if (data.status === 'OK') {
          populateTable(data.searchresult);
        } else {
          console.error('An error occurred while fetching data:', data.status);
        }
      })
      .catch(error => {
        console.error('Error fetching data:', error);
      });
</script>

<svelte:head>
  <title>OurState - Recent Bills</title>
</svelte:head>
<body>
<div id="space">
  <div id="format">
  <h1>Recent Bills</h1>
  <table id="billsTable">
    <thead>
      <tr>
        <th>State</th>
        <th>Bill Number</th>
        <th>Last Action Date</th>
        <th>Last Action</th>
        <th>Title</th>
        <th>Link</th>
      </tr>
    </thead>
    <tbody id="tableBody"></tbody>
  </table>
  </div>
</body>

<style>

table {
    border-collapse: collapse;
    width: 97%;
    max-width: flex;
    border: 2px solid #00000030;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 20px;
    margin-left: 0.5rem;
  }

  body {
    font-family: 'Titillium Web', sans-serif;
    background: #fffff4;
    height: 100%;
    text-align: center;
  }

</style>