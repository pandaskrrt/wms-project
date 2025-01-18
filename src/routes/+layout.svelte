<script lang="ts">
  import { page } from "$app/stores";
  import "../app.css";
  import { ChevronsUpDown, Warehouse } from "lucide-svelte";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu";
  let { children } = $props();
</script>

<div class="wrapper">
  <nav class="sidebar">
    <div class="sidebar-top">
      <div class="logo-section">
        <Warehouse class="logo-icon mr-3" />
        <h1 class="sidebar-title">WMS</h1>
      </div>
      <ul class="menu mt-10 ml-5">
        <li class="menu-item">
          <a href="/" class={$page.url.pathname === "/" ? "active" : ""}
            >Dashboard</a
          >
        </li>
        <li class="menu-item">
          <a
            href="/insert-data"
            class={$page.url.pathname === "/insert-data" ? "active" : ""}
            >Insert Data</a
          >
        </li>
        <li class="menu-item">
          <a
            href="/barang-keluar"
            class={$page.url.pathname === "/barang-keluar" ? "active" : ""}
            >Barang Keluar</a
          >
        </li>
      </ul>
    </div>
    <div class="sidebar-account">
      <DropdownMenu.Root>
        <DropdownMenu.Trigger>
          <button class="account-button">
            <img
              src="https://github.com/shadcn.png"
              alt="User Avatar"
              class="avatar"
            />
            <div class="account-info">
              <p class="username">John Doe</p>
              <span class="role">Developer</span>
            </div>
            <ChevronsUpDown class="arrow ml-3" />
          </button>
        </DropdownMenu.Trigger>
        <DropdownMenu.Content>
          <DropdownMenu.Group>
            <DropdownMenu.Label>My Account</DropdownMenu.Label>
            <DropdownMenu.Separator />
            <DropdownMenu.Item>Logout</DropdownMenu.Item>
          </DropdownMenu.Group>
        </DropdownMenu.Content>
      </DropdownMenu.Root>
    </div>
  </nav>

  <main class="content">
    {@render children()}
  </main>
</div>

<style>
  .wrapper {
    display: flex;
  }

  .sidebar {
    background-color: #2c2c2c;
    color: #fff;
    font-family: "Poppins", sans-serif;
    width: 250px;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 20px;
  }

  .logo-section {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    margin-right: 15px;
  }

  .sidebar-title {
    font-size: 1.5rem;
    margin: 0;
    font-weight: bold;
  }

  .menu {
    list-style: none;
    padding: 0;
  }

  .menu-item {
    margin: 15px 0;
    font-weight: 500;
    cursor: pointer;
    border-radius: 4px;
    padding: 8px 10px;
  }

  .menu-item.text-muted {
    color: #b0b0b0;
    cursor: default;
  }

  .menu-item a {
    text-decoration: none;
    color: #fff;
  }

  .menu-item a:hover {
    color: #1abc9c;
  }

  .menu-item a.active {
    color: #1abc9c;
    font-weight: bold;
  }

  .sidebar-account {
    margin-top: 20px;
  }

  .account-button {
    background: none;
    border: none;
    color: #fff;
    padding: 10px;
    width: 100%;
    display: flex;
    align-items: center;
    cursor: pointer;
    transition: background-color 0.3s;
    border-radius: 8px;
  }

  .account-button:hover {
    background-color: #3a3a3a;
  }

  .avatar {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    margin-right: 15px;
  }

  .account-info {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .username {
    font-size: 1rem;
    font-weight: 600;
    margin: 0;
  }

  .role {
    font-size: 0.9rem;
    color: #ccc;
  }

  .content {
    flex-grow: 1;
    padding: 20px;
    font-family: "Poppins", sans-serif;
  }
</style>
