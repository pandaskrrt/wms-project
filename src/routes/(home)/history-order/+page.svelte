<script lang="ts">
  import * as Table from "$lib/components/ui/table";

  const orders = [
    { namaBarang: "Produk A", waktuOrder: "2025-01-18 08:30" },
    { namaBarang: "Produk B", waktuOrder: "2025-01-18 09:15" },
    { namaBarang: "Produk C", waktuOrder: "2025-01-17 14:45" },
    { namaBarang: "Produk D", waktuOrder: "2025-01-17 16:00" },
    { namaBarang: "Produk E", waktuOrder: "2025-01-16 10:30" },
  ];
</script>

<div class="container">
  <div class="title">Riwayat Order</div>

  <Table.Root>
    <Table.Caption>A list of your recent orders.</Table.Caption>
    <Table.Header>
      <Table.Row>
        <Table.Head class="w-[150px]">Nama Barang</Table.Head>
        <Table.Head class="w-[200px]">Jam Waktu Order</Table.Head>
      </Table.Row>
    </Table.Header>
    <Table.Body>
      {#each orders as { namaBarang, waktuOrder }}
        <Table.Row>
          <Table.Cell class="font-medium">{namaBarang}</Table.Cell>
          <Table.Cell>{waktuOrder}</Table.Cell>
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
</style>
