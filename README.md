<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard UI</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background: #f4f6f9;
            display: flex;
        }
        .dashboard {
            display: flex;
            width: 100%;
        }
        .sidebar {
            width: 250px;
            background: #2c3e50;
            color: white;
            padding: 20px;
            height: 100vh;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        .sidebar .logo {
            font-size: 30px;
            font-weight: bold;
            text-align: center;
            padding: 10px;
            background: #34495e;
            border-radius: 10px;
        }
        .sidebar p {
            font-size: 18px;
        }
        .menu-item {
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        .menu-item:hover {
            background: #34495e;
        }
        .content {
            flex: 1;
            padding: 20px;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .search-bar input {
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .filter-dropdown {
            padding: 8px;
            border-radius: 5px;
            border: 1px solid #ddd;
            background: white;
        }
        .stats {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }
        .card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            flex: 1;
            text-align: center;
            font-size: 18px;
            font-weight: bold;
        }
        table {
            width: 100%;
            background: white;
            margin-top: 20px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        table th, table td {
            padding: 10px;
            text-align: left;
        }
        table thead {
            background: #34495e;
            color: white;
        }
    </style>
</head>
<body>
    <div class="dashboard">
        <aside class="sidebar">
            <div class="logo">C</div>
            <p>Welcome,<br><strong>CRAFTUI</strong></p>
            <div class="menu-item">Dashboard</div>
            <div class="menu-item">Sales</div>
            <div class="menu-item">Products</div>
            <div class="menu-item">Orders</div>
            <div class="menu-item">Customers</div>
            <div class="menu-item">Reports</div>
            <div class="menu-item">Settings</div>
        </aside>
        <main class="content">
            <header>
                <h2>Dashboard</h2>
                <div class="search-bar">
                    <input type="text" id="searchInput" placeholder="Search...">
                    <select id="filterDropdown" class="filter-dropdown">
                        <option value="">All</option>
                        <option value="Rodney Cannon">Rodney Cannon</option>
                        <option value="Mike Franklin">Mike Franklin</option>
                        <option value="John Doe">John Doe</option>
                        <option value="Jane Smith">Jane Smith</option>
                    </select>
                </div>
            </header>
            <section class="latest-sales">
                <h3>Latest Sales</h3>
                <table id="salesTable">
                    <thead>
                        <tr>
                            <th>Product</th>
                            <th>Customer</th>
                            <th>Delivery</th>
                            <th>Status</th>
                            <th>Total</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Macbook Pro</td>
                            <td>Rodney Cannon</td>
                            <td>United Kingdom</td>
                            <td>Shipped</td>
                            <td>$118.00</td>
                        </tr>
                        <tr>
                            <td>Dell Laptop</td>
                            <td>Mike Franklin</td>
                            <td>United States</td>
                            <td>Processing</td>
                            <td>$208.00</td>
                        </tr>
                        <tr>
                            <td>Smartphone</td>
                            <td>John Doe</td>
                            <td>Canada</td>
                            <td>Shipped</td>
                            <td>$300.00</td>
                        </tr>
                        <tr>
                            <td>Tablet</td>
                            <td>Jane Smith</td>
                            <td>Australia</td>
                            <td>Processing</td>
                            <td>$250.00</td>
                        </tr>
                    </tbody>
                </table>
            </section>
        </main>
    </div>
    <script>
        document.getElementById('searchInput').addEventListener('input', function() {
            let filter = this.value.toLowerCase();
            let rows = document.querySelectorAll('#salesTable tbody tr');
            rows.forEach(row => {
                let text = row.innerText.toLowerCase();
                row.style.display = text.includes(filter) ? '' : 'none';
            });
        });

        document.getElementById('filterDropdown').addEventListener('change', function() {
            let filter = this.value.toLowerCase();
            let rows = document.querySelectorAll('#salesTable tbody tr');
            rows.forEach(row => {
                let customerName = row.cells[1].innerText.toLowerCase();
                row.style.display = filter === '' || customerName.includes(filter) ? '' : 'none';
            });
        });
    </script>
</body>
</html>
