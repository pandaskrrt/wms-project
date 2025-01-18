<script>
    import { BatteryFull, LucideSearch, TriangleAlert } from 'lucide-svelte';
  
    let isStarted = false; 
  
    function toggleStart() {
      isStarted = !isStarted; 
    }

    let searchQuery = '';
    const items = ['Barang A', 'Barang B', 'Barang C'];

    $: filteredItems = items.filter((item) =>
        item.toLowerCase().includes(searchQuery.toLowerCase())
    );

    
  </script>
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@500;600&display=swap');
  
    .title {
      font-family: 'Poppins', sans-serif;
      font-size: 2.5rem;
      font-weight: 600;
      color: black;
      text-align: center;
      margin-bottom: 2rem;
    }
  
    .container {
      display: flex;
      justify-content: space-between;
      gap: 20px;
    }
  
    .left-section {
      flex: 3;
      padding: 20px;
      border-radius: 8px;
     
    }
    .right-section {
    flex: 1;
    display: flex; 
    flex-direction: column;
    background-color: #f4f4f4; 
    padding: 20px;
    border-radius: 8px;
}

.button-section {
    display: flex;
    justify-content: center;
    gap: 15px; 
    margin-top: auto; 
}
    .search-container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background-color: #ffffff; 
        border-radius: 8px;
        padding: 10px 15px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        margin-bottom: 20px; 
    }

    .search-input {
        border: none;
        outline: none;
        font-size: 1rem;
        color: #333;
        width: 80%; 
    }

    .search-icon {
        font-size: 1.5rem;
        color: #388e3c; 
        cursor: pointer;
    }

    .item-list {
        list-style: none; 
        padding: 0;
        margin: 0;
    }

    .item {
        background-color: #ffffff;
        padding: 10px 15px;
        border-radius: 8px;
        box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
        margin-bottom: 10px;
        font-size: 1rem;
        color: #333;
    }
  
    .button {
      display: flex;
      align-items: center;
      justify-content: center; 
      padding: 10px 20px; 
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1.1rem;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
      min-width: 120px; 
      height: 60px; 
    }
  
    .battery-button {
      background: linear-gradient(135deg, #66bb6a, #388e3c);
      border: 2px solid #388e3c;
    }
  
    .battery-button:hover {
      background: linear-gradient(135deg, #388e3c, #66bb6a);
      transform: scale(1.05);
    }
  
    /* Button kedua - Status Run */
    .status-run-button {
      background: linear-gradient(135deg, #ff7e5f, #feb47b);
      border: 2px solid #ff7e5f; 
    }
  
    .status-run-button:hover {
      background: linear-gradient(135deg, #feb47b, #ff7e5f);
      transform: scale(1.05);
    }
  
    /* Button ketiga - Start/Stop */
    .start-button {
      background: linear-gradient(135deg, #6a11cb, #2575fc); 
      border: 2px solid #6a11cb; 
    }
  
    .start-button:hover {
      background: linear-gradient(135deg, #2575fc, #6a11cb);
      transform: scale(1.05);
    }
  
    .start-button.stop {
      background: linear-gradient(135deg, #f44336, #d32f2f); 
      border: 2px solid #d32f2f; 
    }
  
    .start-button.stop:hover {
      background: linear-gradient(135deg, #d32f2f, #f44336); 
    }

    .alert-button {
      background: linear-gradient(135deg, #ffeb3b, #fbc02d);
      border: 2px solid #fbc02d;
      color: black; 
    }
  
    .alert-button:hover {
      background: linear-gradient(135deg, #fbc02d, #ffeb3b);
      transform: scale(1.05); 
    }
  
    .visualization-box {
    background-color: #ffffff;
    border-radius: 8px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    padding: 40px 20px; 
    margin-top: 30px; 
    text-align: center;
    font-size: 1.2rem;
    font-weight: 600;
    color: #333;
    border: 2px solid #ddd; 
    height: 600px;
    }

    .change-button {
      background-color: #f44336;
      border: none;
      color: white;
      padding: 10px 20px;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
    }

    .change-button:hover {
      background-color: #d32f2f;
      transform: scale(1.05);
    }

  .order-button {
      background: linear-gradient(135deg, #8bc34a, #689f38);
      border: 2px solid #689f38;
  }

  .order-button:hover {
      background: linear-gradient(135deg, #689f38, #8bc34a);
      transform: scale(1.05);
  }
  </style>
  
  <h1 class="title">Warehouse Management System</h1>
  
  
  <div class="container">
    <div class="left-section">
        <div class="button-section">
            <button class="button battery-button">
                <BatteryFull class="icon" />
                Baterai 75%
            </button>
            <button class="button status-run-button">
                Status Run
            </button>
            <button class="button start-button {isStarted ? 'stop' : ''}" on:click={toggleStart}>
                {isStarted ? 'Stop' : 'Start'}
            </button>
            <button class="button alert-button">
                <TriangleAlert class="icon" />
            </button>
        </div>

        <div class="visualization-box">
            <p>Tampilan Visualisasi 3D Gudang Dan Robot Posisi</p>
        </div>
    </div>

    <div class="right-section">
        <div class="search-container">
            <input
                type="text"
                class="search-input"
                bind:value={searchQuery}
                placeholder="Search barang..."
            />
            <button class="search-icon">
                <LucideSearch />
            </button>
        </div>

        <ul class="item-list">
            {#if filteredItems.length > 0}
                {#each filteredItems as item}
                    <li class="item">{item}</li>
                {/each}
            {:else}
                <li class="item">Barang tidak ditemukan</li>
            {/if}
        </ul>

        <div class="button-section">
            <button class="button change-button">Change</button>
            <button class="button order-button">Order</button>
        </div>
    </div>
</div>