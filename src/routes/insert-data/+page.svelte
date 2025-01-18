<script lang="ts">
  import * as Table from "$lib/components/ui/table";

  const data = [
    {
      namaBarang: "Produk A",
      alamat1: "Jl. Raya No. 1",
      alamat2: "Kompleks ABC",
    },
    {
      namaBarang: "Produk B",
      alamat1: "Jl. Pahlawan No. 2",
      alamat2: "Perumahan XYZ",
    },
    {
      namaBarang: "Produk C",
      alamat1: "Jl. Merdeka No. 3",
      alamat2: "Perumahan ABC",
    },
  ];
</script>

<div class="container">
  <div class="title">Insert Data</div>
  <div class="form-row">
    <div class="form-group">
      <label for="nama-barang">Nama Barang</label>
      <input type="text" id="nama-barang" placeholder="Masukkan nama barang" />
    </div>
    <div class="form-group">
      <label for="alamat-1">Alamat 1</label>
      <input type="text" id="alamat-1" placeholder="Masukkan alamat pertama" />
    </div>
    <div class="form-group">
      <label for="alamat-2">Alamat 2</label>
      <input type="text" id="alamat-2" placeholder="Masukkan alamat kedua" />
    </div>
  </div>
  <div class="submit-btn-container">
    <button class="submit-btn">Submit Data</button>
  </div>
  >
  <div class="separator"></div>

  <div class="title">Data List</div>
  <Table.Root>
    <Table.Caption>A list of your recent data.</Table.Caption>
    <Table.Header>
      <Table.Row>
        <Table.Head class="w-[150px]">Nama Barang</Table.Head>
        <Table.Head>Alamat 1</Table.Head>
        <Table.Head>Alamat 2</Table.Head>
      </Table.Row>
    </Table.Header>
    <Table.Body>
      {#each data as { namaBarang, alamat1, alamat2 }}
        <Table.Row>
          <Table.Cell class="font-medium">{namaBarang}</Table.Cell>
          <Table.Cell>{alamat1}</Table.Cell>
          <Table.Cell>{alamat2}</Table.Cell>
        </Table.Row>
      {/each}
    </Table.Body>
  </Table.Root>
</div>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap");

  .container {
    font-family: "Poppins", sans-serif;
    max-width: 1000px;
    margin: 2rem auto;
    padding: 1rem;
  }

  .title {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 1rem;
  }

  .form-row {
    display: flex;
    gap: 2rem;
    margin-bottom: 1.5rem;
  }

  .form-group {
    flex: 1;
    display: flex;
    flex-direction: column;
    min-width: 250px;
  }

  label {
    font-size: 0.9rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
  }

  input {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
    font-family: "Poppins", sans-serif;
  }

  input:focus {
    outline: none;
    border-color: #007bff;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
  }

  .submit-btn-container {
    display: flex;
    justify-content: flex-end;
    margin-top: 1.5rem;
  }

  .submit-btn {
    padding: 0.75rem 1.5rem;
    background: linear-gradient(45deg, #28a745, #218838);
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 1rem;
    font-family: "Poppins", sans-serif;
    cursor: pointer;
    transition: background 0.3s;
  }

  .submit-btn:hover {
    background: linear-gradient(45deg, #218838, #28a745);
  }

  .separator {
    height: 2px;
    background: linear-gradient(to right, #dcdcdc, rgba(220, 220, 220, 0));
    margin: 2rem 0;
  }
</style>
