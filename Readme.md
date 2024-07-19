```markdown
# Custom DataTable with Tailwind CSS v2

This project demonstrates how to configure a custom DataTable using Tailwind CSS v2.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Customization](#customization)
- [JavaScript Functionality](#javascript-functionality)
- [License](#license)

## Installation

To use this custom DataTable configuration, you need to have a basic understanding of HTML, CSS, and JavaScript. Ensure you have Tailwind CSS v2 included in your project.

### Including Tailwind CSS

You can include Tailwind CSS in your project by adding the following CDN link in the `<head>` of your HTML file:

```html
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.0.0/dist/tailwind.min.css" rel="stylesheet">
```

## Usage

1. Create an HTML file and include the Tailwind CSS CDN link as shown above.
2. Copy the following HTML structure into your file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Date Filter</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.0.0/dist/tailwind.min.css" rel="stylesheet">
</head>
<body>
    <div class="absolute top-0">
        <label for="dateFilter">Filter Tanggal: </label>
        <select id="dateFilter" class="px-4 py-2 mx-2 ring-1 ring-gray-300 rounded-md bg-white">
            <option class="" value="7days">7 Hari Terakhir</option>
            <option value="2weeks">2 Minggu Terakhir</option>
            <option value="3weeks">3 Minggu Terakhir</option>
            <option value="1month">1 Bulan Terakhir</option>
            <option value="custom">Custom</option>
        </select>
        <div id="customDate" style="display:none;">
            <label for="startDate">Dari: </label>
            <input type="date" id="startDate">
            <label for="endDate">Sampai: </label>
            <input type="date" id="endDate">
        </div>
    </div>

    <table id="myTable" class="display flex--wrap" style="width: 100%">
        <thead>
            <tr>
                <th rowspan="2">Name</th>
                <th>Position</th>
                <th>Office</th>
                <th>Age</th>
                <th>Start date</th>
                <th>Salary</th>
            </tr>
            <tr>
                <th>Position</th>
                <th>Office</th>
                <th>Age</th>
                <th>Start date</th>
                <th>Salary</th>
            </tr>
        </thead>
        <tbody>
            <!-- Add table rows here -->
        </tbody>
        <tfoot>
            <tr>
                <th>Name</th>
                <th>Position</th>
                <th>Office</th>
                <th>Age</th>
                <th>Start date</th>
                <th>Salary</th>
            </tr>
        </tfoot>
    </table>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const endDateInput = document.getElementById('endDate');
            const today = new Date().toISOString().split('T')[0];
            endDateInput.value = today;
        });

        document.getElementById('dateFilter').addEventListener('change', function() {
            let startDate, endDate = new Date();
            const value = this.value;
            switch (value) {
                case '7days':
                    startDate = new Date();
                    startDate.setDate(endDate.getDate() - 7);
                    break;
                case '2weeks':
                    startDate = new Date();
                    startDate.setDate(endDate.getDate() - 14);
                    break;
                case '3weeks':
                    startDate = new Date();
                    startDate.setDate(endDate.getDate() - 21);
                    break;
                case '1month':
                    startDate = new Date();
                    startDate.setMonth(endDate.getMonth() - 1);
                    break;
                default:
                    startDate = null;
                    endDate = new Date(); // Set endDate to now
            }
            // Implement further logic here to filter the table based on startDate and endDate
        });
    </script>
</body>
</html>
```

## Customization

You can customize the appearance and behavior of the DataTable by modifying the HTML and CSS classes. Tailwind CSS classes provide a lot of flexibility for styling.

### Example Customization

To change the color of the filter dropdown, you can modify the Tailwind CSS classes:

```html
<select id="dateFilter" class="px-4 py-2 mx-2 ring-1 ring-gray-300 rounded-md bg-blue-500 text-white">
```

## JavaScript Functionality

The JavaScript included in the example sets the default value of the `endDate` input to the current date and updates the date range based on the selected filter option.

### Setting the Current Date

The following JavaScript code sets the value of the `endDate` input to the current date when the page loads:

```javascript
document.addEventListener('DOMContentLoaded', function() {
    const endDateInput = document.getElementById('endDate');
    const today = new Date().toISOString().split('T')[0];
    endDateInput.value = today;
});
```

### Handling Filter Changes

The `change` event listener on the `dateFilter` element updates the `startDate` and `endDate` based on the selected filter option:

```javascript
document.getElementById('dateFilter').addEventListener('change', function() {
    let startDate, endDate = new Date();
    const value = this.value;
    switch (value) {
        case '7days':
            startDate = new Date();
            startDate.setDate(endDate.getDate() - 7);
            break;
        case '2weeks':
            startDate = new Date();
            startDate.setDate(endDate.getDate() - 14);
            break;
        case '3weeks':
            startDate = new Date();
            startDate.setDate(endDate.getDate() - 21);
            break;
        case '1month':
            startDate = new Date();
            startDate.setMonth(endDate.getMonth() - 1);
            break;
        default:
            startDate = null;
            endDate = new Date(); // Set endDate to now
    }
    // Implement further logic here to filter the table based on startDate and endDate
});
```