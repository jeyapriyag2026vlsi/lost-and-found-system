
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Campus Lost & Found</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f4f7fb;
            color: #26344a;
        }

        /* Navigation */

        nav {
            background: #2457a7;
            color: white;
            padding: 20px 8%;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        nav h2 {
            font-size: 23px;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin-left: 20px;
        }

        /* Home */

        .home {
            text-align: center;
            padding: 65px 20px;
            background: #e3edff;
        }

        .home h1 {
            font-size: 36px;
            margin-bottom: 15px;
            color: #2457a7;
        }

        .home p {
            color: #555;
            margin-bottom: 25px;
        }

        .home button {
            background: #2457a7;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 5px;
            cursor: pointer;
        }

        /* Statistics */

        .stats {
            display: flex;
            justify-content: center;
            gap: 30px;
            padding: 25px;
            flex-wrap: wrap;
        }

        .stat-box {
            background: white;
            padding: 20px 40px;
            text-align: center;
            border-radius: 8px;
            box-shadow: 0 2px 8px #ddd;
        }

        .stat-box h2 {
            color: #2457a7;
            margin-bottom: 8px;
        }

        /* Sections */

        section {
            padding: 40px 8%;
        }

        section h2 {
            margin-bottom: 20px;
            text-align: center;
        }

        /* Form */

        .form-container {
            max-width: 550px;
            margin: auto;
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 2px 10px #ddd;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        textarea {
            height: 90px;
            resize: vertical;
        }

        .submit-btn {
            width: 100%;
            background: #2457a7;
            color: white;
            padding: 13px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        /* Search */

        .search-box {
            max-width: 550px;
            margin: 0 auto 25px;
        }

        /* Items */

        .items {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
        }

        .card {
            background: white;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 8px #ddd;
        }

        .card img {
            width: 100%;
            height: 150px;
            object-fit: cover;
            border-radius: 5px;
            margin-bottom: 12px;
        }

        .card h3 {
            margin: 10px 0;
        }

        .card p {
            margin: 7px 0;
            color: #555;
            font-size: 14px;
        }

        .lost {
            color: #d33;
            font-weight: bold;
        }

        .found {
            color: green;
            font-weight: bold;
        }

        /* Footer */

        footer {
            background: #2457a7;
            color: white;
            text-align: center;
            padding: 20px;
        }

        @media(max-width: 600px) {
            nav {
                flex-direction: column;
                gap: 15px;
            }

            nav a {
                margin: 0 7px;
                font-size: 13px;
            }

            .home h1 {
                font-size: 27px;
            }

            .stats {
                gap: 12px;
            }

            .stat-box {
                padding: 15px 22px;
            }
        }
    </style>
</head>

<body>

    <!-- Navigation -->

    <nav>
        <h2>CampusFind</h2>

        <div>
            <a href="#home">Home</a>
            <a href="#report">Report</a>
            <a href="#items">Browse Items</a>
        </div>
    </nav>


    <!-- Home Section -->

    <div class="home" id="home">

        <h1>Lost Something? Find It Here!</h1>

        <p>
            Helping students find their lost belongings
            and return found items.
        </p>

        <button onclick="document.getElementById('report').scrollIntoView({behavior:'smooth'})">
            Report an Item
        </button>

    </div>


    <!-- Statistics -->

    <div class="stats">

        <div class="stat-box">
            <h2 id="total">0</h2>
            <p>Total Items</p>
        </div>

        <div class="stat-box">
            <h2 id="lostCount">0</h2>
            <p>Lost Items</p>
        </div>

        <div class="stat-box">
            <h2 id="foundCount">0</h2>
            <p>Found Items</p>
        </div>

    </div>


    <!-- Report Form -->

    <section id="report">

        <h2>Report Lost / Found Item</h2>

        <div class="form-container">

            <form id="itemForm">

                <label>Report Type</label>

                <select id="type" required>
                    <option value="Lost">Lost Item</option>
                    <option value="Found">Found Item</option>
                </select>

                <label>Item Name</label>

                <input type="text" id="name"
                    placeholder="Enter item name" required>

                <label>Category</label>

                <select id="category" required>
                    <option value="">Select Category</option>
                    <option>Electronics</option>
                    <option>Books</option>
                    <option>Accessories</option>
                    <option>ID Cards</option>
                    <option>Others</option>
                </select>

                <label>Location</label>

                <input type="text" id="location"
                    placeholder="Enter location" required>

                <label>Description</label>

                <textarea id="description"
                    placeholder="Describe the item" required></textarea>

                <label>Upload Image</label>

                <input type="file" id="image" accept="image/*">

                <button class="submit-btn" type="submit">
                    Submit Report
                </button>

            </form>

        </div>

    </section>


    <!-- Browse Items -->

    <section id="items">

        <h2>Recently Reported Items</h2>

        <div class="search-box">

            <input type="text" id="search"
                placeholder="Search for an item..."
                oninput="displayItems()">

            <select id="filter" onchange="displayItems()">
                <option value="All">All Items</option>
                <option value="Lost">Lost Items</option>
                <option value="Found">Found Items</option>
            </select>

        </div>

        <div class="items" id="itemList"></div>

    </section>


    <!-- Footer -->

    <footer>

        <h3>CampusFind</h3>

        <p>Bringing lost belongings back to their owners.</p>

        <p>© 2026 CampusFind | Student Project</p>

    </footer>


    <!-- JavaScript -->

    <script>

        let items = JSON.parse(
            localStorage.getItem("campusItems") || "[]"
        );

        // Display Items

        function displayItems() {

            let list = document.getElementById("itemList");

            let search = document.getElementById("search")
                .value.toLowerCase();

            let filter = document.getElementById("filter").value;

            list.innerHTML = "";

            let filteredItems = items.filter(item => {

                let matchName = item.name.toLowerCase()
                    .includes(search);

                let matchType = filter === "All" ||
                    item.type === filter;

                return matchName && matchType;

            });

            filteredItems.forEach(item => {

                let card = document.createElement("div");

                card.className = "card";

                let title = document.createElement("h3");
                title.textContent = item.name;

                let status = document.createElement("p");
                status.textContent = item.type;
                status.className = item.type.toLowerCase();

                let category = document.createElement("p");
                category.textContent = "Category: " + item.category;

                let location = document.createElement("p");
                location.textContent = "Location: " + item.location;

                let description = document.createElement("p");
                description.textContent = item.description;

                card.append(status, title);

                if (item.image) {
                    let img = document.createElement("img");
                    img.src = item.image;
                    img.alt = item.name;
                    card.insertBefore(img, status);
                }

                card.append(category, location, description);

                list.appendChild(card);

            });

            updateStats();

        }


        // Update Statistics

        function updateStats() {

            document.getElementById("total").textContent =
                items.length;

            document.getElementById("lostCount").textContent =
                items.filter(item => item.type === "Lost").length;

            document.getElementById("foundCount").textContent =
                items.filter(item => item.type === "Found").length;

        }


        // Submit Form

        document.getElementById("itemForm")
            .addEventListener("submit", function(event) {

                event.preventDefault();

                let file = document.getElementById("image").files[0];

                function saveItem(imageData = "") {

                    let newItem = {

                        type: document.getElementById("type").value,

                        name: document.getElementById("name").value.trim(),

                        category: document.getElementById("category").value,

                        location: document.getElementById("location").value.trim(),

                        description: document.getElementById("description").value.trim(),

                        image: imageData

                    };

                    items.unshift(newItem);

                    try {
                        localStorage.setItem(
                            "campusItems",
                            JSON.stringify(items)
                        );
                    } catch (error) {
                        items.shift();
                        alert("Storage is full. Please try a smaller image.");
                        return;
                    }

                    displayItems();

                    document.getElementById("itemForm").reset();

                    alert("Item reported successfully!");

                }

                if (file) {

                    if (!file.type.startsWith("image/") ||
                        file.size > 1024 * 1024) {
                        alert("Please select an image smaller than 1 MB.");
                        return;
                    }

                    let reader = new FileReader();

                    reader.onload = function(e) {
                        saveItem(e.target.result);
                    };

                    reader.onerror = function() {
                        alert("Unable to read image.");
                    };

                    reader.readAsDataURL(file);

                } else {

                    saveItem();

                }

            });


        // Initial Display

        displayItems();

    </script>

</body>
</html>
