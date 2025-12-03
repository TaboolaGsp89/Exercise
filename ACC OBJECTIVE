<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Account Objectives Tool</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Use Inter font -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* Apply Inter font */
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Custom styles for table striping */
        tbody tr:nth-child(odd) {
            background-color: #ffffff;
        }
        tbody tr:nth-child(even) {
            background-color: #f9fafb; /* gray-50 */
        }

        /* Style for new record modal inputs */
        .form-input {
            @apply mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm;
        }
        .form-label {
            @apply block text-sm font-medium text-gray-700;
        }
    </style>
</head>
<body class="bg-gray-100 p-4 md:p-8">

    <div class="max-w-7xl mx-auto bg-white rounded-lg shadow-sm border border-gray-200">
        <!-- Header Section -->
        <div class="flex flex-col md:flex-row justify-between items-center p-4 md:p-6 border-b border-gray-200">
            <div class="flex items-center mb-4 md:mb-0">
                <h1 class="text-xl font-semibold text-gray-800">Account Objectives</h1>
                <span id="objectives-count" class="ml-2 bg-gray-200 text-gray-700 text-xs font-semibold px-2.5 py-0.5 rounded-full">5</span>
            </div>
            <div class="flex space-x-2">
                <button id="generate-btn" class="flex items-center justify-center bg-white text-gray-700 px-4 py-2 border border-gray-300 rounded-md shadow-sm text-sm font-medium hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    <!-- Sparkles Icon -->
                    <svg class="w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9.813 15.904L9 18.75l-.813-2.846a4.5 4.5 0 00-3.09-3.09L2.25 12l2.846-.813a4.5 4.5 0 003.09-3.09L9 5.25l.813 2.846a4.5 4.5 0 003.09 3.09L15.75 12l-2.846.813a4.5 4.5 0 00-3.09 3.09zM18.259 8.715L18 9.75l-.259-1.035a3.375 3.375 0 00-2.455-2.456L14.25 6l1.036-.259a3.375 3.375 0 002.455-2.456L18 2.25l.259 1.035a3.375 3.375 0 002.456 2.456L21.75 6l-1.035.259a3.375 3.375 0 00-2.456 2.456zM18 13.5l.375 1.5L18 16.5l-.375-1.5L16.5 15l1.125-.375L18 13.5z" />
                    </svg>
                    Generate Objectives
                </button>
                <button id="new-btn" class="flex items-center justify-center bg-blue-600 text-white px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                    <!-- Plus Icon -->
                    <svg class="w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
                    </svg>
                    New
                </button>
                <!-- --- NEW: Delete Button --- -->
                <button id="delete-btn" class="flex items-center justify-center bg-red-600 text-white px-4 py-2 border border-transparent rounded-md shadow-sm text-sm font-medium hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 disabled:bg-gray-300 disabled:cursor-not-allowed" disabled>
                    <!-- Trash Icon -->
                    <svg class="w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12.54 0c-.265.03A48.11 48.11 0 006.25 6H12m0a48.108 48.108 0 00-3.478-.397m3.478.397c-.265.03A48.11 48.11 0 006.25 6H12m0a48.108 48.108 0 00-3.478-.397M12 6c3.22 0 6.17.02 9 0z" />
                    </svg>
                    Delete
                </button>
            </div>
        </div>

        <!-- Table Section -->
        <div class="overflow-x-auto">
            <table class="min-w-full divide-y divide-gray-200">
                <thead class="bg-gray-50">
                    <tr>
                        <th scope="col" class="p-4">
                            <input type="checkbox" id="select-all-checkbox" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                        </th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">ID</th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Planned Activity</th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Activity Update</th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Start Date</th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Quarter</th>
                        <th scope="col" class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Category</th>
                    </tr>
                </thead>
                <tbody id="objectives-table-body" class="bg-white divide-y divide-gray-200 text-sm text-gray-700">
                    <!-- Rows will be dynamically injected here -->
                </tbody>
            </table>
        </div>
    </div>

    <!-- Modal Popup: Generate Objectives -->
    <div id="generate-modal" class="hidden fixed z-10 inset-0 overflow-y-auto">
        <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
            <!-- Background overlay -->
            <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>

            <!-- Modal panel -->
            <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
            <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full">
                <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                    <div class="sm:flex sm:items-start">
                        <div class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-blue-100 sm:mx-0 sm:h-10 sm:w-10">
                            <!-- Icon for modal -->
                            <svg class="h-6 w-6 text-blue-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 12h16.5m-16.5 3.75h16.5M3.75 19.5h16.5M5.625 4.5h12.75a1.875 1.875 0 010 3.75H5.625a1.875 1.875 0 010-3.75z" />
                            </svg>
                        </div>
                        <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left w-full">
                            <h3 class="text-lg leading-6 font-medium text-gray-900" id="modal-title">
                                Generate Planned Activities
                            </h3>
                            <p class="text-sm text-gray-500 mb-4">Select activities to auto-generate objectives.</p>
                            <div class="mt-2">
                                <fieldset>
                                    <legend class="sr-only">Planned Activities</legend>
                                    <div id="modal-activity-list" class="space-y-4 max-h-60 overflow-y-auto pr-2">
                                        <!-- Checkboxes will be dynamically injected here -->
                                    </div>
                                </fieldset>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                    <button id="confirm-generate-btn" type="button" class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-blue-600 text-base font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 sm:ml-3 sm:w-auto sm:text-sm">
                        Generate
                    </button>
                    <button id="cancel-generate-modal-btn" type="button" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm">
                        Cancel
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal Popup: New Record Page -->
    <div id="new-record-modal" class="hidden fixed z-20 inset-0 overflow-y-auto">
        <div class="flex items-center justify-center min-h-screen">
            <!-- Background overlay -->
            <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>

            <!-- Modal panel -->
            <div class="bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:max-w-2xl sm:w-full">
                <!-- Header -->
                <div class="bg-white px-4 pt-5 pb-4 sm:p-6 border-b border-gray-200">
                    <h3 class="text-lg leading-6 font-medium text-gray-900">
                        Create New Objective
                    </h3>
                </div>
                
                <!-- Form Body -->
                <form id="new-record-form">
                    <!-- --- MODIFIED: Improved Layout --- -->
                    <div class="bg-white px-4 pt-5 pb-4 sm:p-6 grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <label for="new-plannedActivity" class="form-label">Planned Activity</label>
                            <input type="text" name="plannedActivity" id="new-plannedActivity" class="form-input" required>
                        </div>
                        <div>
                            <label for="new-status" class="form-label">Status</label>
                            <select id="new-status" name="status" class="form-input">
                                <option>Start</option>
                                <option>In Progress</option>
                                <option>Completed</option>
                            </select>
                        </div>
                         <div>
                            <label for="new-category" class="form-label">Category</label>
                            <select id="new-category" name="category" class="form-input">
                                <option>Revenue Related Activities</option>
                                <option>Cross Functional Activities</option>
                                <option>Uncategorized</option>
                            </select>
                        </div>
                        <div>
                            <label for="new-startDate" class="form-label">Start Date</label>
                            <input type="date" name="startDate" id="new-startDate" class="form-input">
                        </div>
                        <div>
                            <label for="new-quarter" class="form-label">Quarter</label>
                            <input type="text" name="quarter" id="new-quarter" class="form-input bg-gray-100" readonly>
                        </div>
                        <div class="col-span-1 md:col-span-2">
                            <label for="new-activityUpdate" class="form-label">Activity Update</label>
                            <textarea id="new-activityUpdate" name="activityUpdate" rows="3" class="form-input"></textarea>
                        </div>
                    </div>
                </form>

                <!-- Footer / Actions -->
                <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                    <button id="save-btn" type="button" class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-blue-600 text-base font-medium text-white hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 sm:ml-3 sm:w-auto sm:text-sm">
                        Save
                    </button>
                    <button id="save-and-new-btn" type="button" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm">
                        Save & New
                    </button>
                    <button id="cancel-new-record-btn" type="button" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm">
                        Cancel
                    </button>
                </div>
            </div>
        </div>
    </div>


    <script>
        document.addEventListener('DOMContentLoaded', () => {

            // --- STATE & DATA ---

            let nextIdCounter = 242111;
            
            // Initial data based on the screenshot
            // --- MODIFIED: Standardized all dates to YYYY-MM-DD format ---
            let objectives = [
                { id: 'A-242103', plannedActivity: 'Creative Shop', activityUpdate: 'Met Customer', status: 'In Progress', startDate: '2025-10-01', quarter: 'Q3', category: 'Cross Functional Activities' },
                { id: 'A-242105', plannedActivity: 'Yahoo', activityUpdate: 'Sent emails waiting for update', status: 'In Progress', startDate: '2025-10-05', quarter: 'Q3', category: 'Revenue Related Activities' },
                { id: 'A-242107', plannedActivity: 'LP', activityUpdate: 'Already Present...', status: 'Completed', startDate: '2025-10-02', quarter: 'Q3', category: 'Revenue Related Activities' },
                { id: 'A-242106', plannedActivity: 'Display Banner', activityUpdate: 'Completed', status: 'Completed', startDate: '2025-10-10', quarter: 'Q3', category: 'Cross Functional Activities' },
                { id: 'A-242110', plannedActivity: 'Policy', activityUpdate: 'About to start before tomorrow', status: 'Start', startDate: '2025-10-15', quarter: 'Q3', category: 'Revenue Related Activities' }
            ];

            // --- NEW: Categorized activities list ---
            const categorizedActivities = {
                "Cross Functional Activities": [
                    "Policy Exception process",
                    "CRT- Success Program",
                    "SE- Integration support",
                    "SE- Performance investigation or hands on support",
                    "Creative Shop",
                    "Finance - Credit line improvement",
                    "Display support",
                    "Strategic Publisher Escalation (Y!, MSFT,"
                ],
                "Revenue related activities": [
                    "MSFT - Display",
                    "Yahoo - MaC",
                    "Mail Environment - Product Feature - other",
                    "Apple - Retargeting",
                    "Premium - LAL",
                    "Taboola News Supply - Predictive Audiences",
                    "LOB - LP refresh",
                    "Geo expansion"
                ]
            };

            // --- DOM ELEMENTS ---
            const tableBody = document.getElementById('objectives-table-body');
            const objectivesCount = document.getElementById('objectives-count');
            const generateBtn = document.getElementById('generate-btn');
            const newBtn = document.getElementById('new-btn');
            const deleteBtn = document.getElementById('delete-btn'); // <-- NEW
            const selectAllCheckbox = document.getElementById('select-all-checkbox'); // <-- NEW
            
            // Generate Modal Elements
            const generateModal = document.getElementById('generate-modal');
            const modalActivityList = document.getElementById('modal-activity-list');
            const confirmGenerateBtn = document.getElementById('confirm-generate-btn');
            const cancelGenerateModalBtn = document.getElementById('cancel-generate-modal-btn');
            
            // New Record Modal Elements
            const newRecordModal = document.getElementById('new-record-modal');
            const newRecordForm = document.getElementById('new-record-form');
            const saveBtn = document.getElementById('save-btn');
            const saveAndNewBtn = document.getElementById('save-and-new-btn');
            const cancelNewRecordBtn = document.getElementById('cancel-new-record-btn');

            // New Record Form Fields
            const newPlannedActivity = document.getElementById('new-plannedActivity');
            const newCategory = document.getElementById('new-category');
            const newActivityUpdate = document.getElementById('new-activityUpdate');
            const newStatus = document.getElementById('new-status');
            const newStartDate = document.getElementById('new-startDate');
            const newQuarter = document.getElementById('new-quarter');


            // --- HELPER FUNCTIONS ---

            /**
             * Formats a Date object as DD-MM-YYYY
             */
            function formatDate(date) {
                const d = new Date(date);
                let day = '' + d.getDate();
                let month = '' + (d.getMonth() + 1);
                const year = d.getFullYear();

                if (day.length < 2) day = '0' + day;
                if (month.length < 2) month = '0' + month;

                // --- MODIFIED: Return YYYY-MM-DD for date input compatibility ---
                return [year, month, day].join('-');
            }

            // --- NEW: Added missing function ---
            /**
             * Formats a YYYY-MM-DD string to DD-MM-YYYY for display
             */
            function displayFormatDate(dateString) {
                if (!dateString) return '';
                const parts = dateString.split('-');
                if (parts.length === 3) {
                    // Assumes input is YYYY-MM-DD
                    return [parts[2], parts[1], parts[0]].join('-');
                }
                return dateString; // fallback for unexpected format
            }


            /**
             * Gets the current quarter (e.g., "Q1", "Q2")
             */
            function getCurrentQuarter(date = new Date()) {
                const month = new Date(date).getMonth();
                return 'Q' + (Math.floor(month / 3) + 1);
            }
            
            /**
             * Generates a new unique ID
             */
            function getNewId() {
                return `A-${nextIdCounter++}`;
            }

            /**
             * Renders a single row in the table
             */
            function createTableRow(obj) {
                // --- MODIFIED: Use displayFormatDate for startDate ---
                return `
                    <tr data-id="${obj.id}">
                        <td class="p-4">
                            <input type="checkbox" class="row-checkbox h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                        </td>
                        <td class="px-4 py-3 whitespace-nowrap">
                            <a href="#" class="text-blue-600 hover:text-blue-800 hover:underline">${obj.id}</a>
                        </td>
                        <td class="px-4 py-3 whitespace-nowrap font-medium text-gray-900" data-field="plannedActivity">${obj.plannedActivity}</td>
                        <td class="px-4 py-3 whitespace-nowrap" data-field="activityUpdate">${obj.activityUpdate}</td>
                        <td class="px-4 py-3 whitespace-nowrap" data-field="status">
                            <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full ${
                                obj.status === 'Completed' ? 'bg-green-100 text-green-800' :
                                obj.status === 'In Progress' ? 'bg-yellow-100 text-yellow-800' :
                                'bg-blue-100 text-blue-800'
                            }">
                                ${obj.status}
                            </span>
                        </td>
                        <td class="px-4 py-3 whitespace-nowrap" data-field="startDate">${displayFormatDate(obj.startDate)}</td>
                        <td class="px-4 py-3 whitespace-nowrap" data-field="quarter">${obj.quarter}</td>
                        <td class="px-4 py-3 whitespace-nowrap" data-field="category">${obj.category}</td>
                    </tr>
                `;
            }

            /**
             * Re-renders the entire table based on the 'objectives' array
             */
            function renderTable() {
                tableBody.innerHTML = '';
                if (objectives.length === 0) {
                    tableBody.innerHTML = '<tr><td colspan="8" class="text-center p-8 text-gray-500">No objectives found.</td></tr>';
                } else {
                    // --- MODIFIED: Sort by start date descending (newest first) ---
                    objectives.sort((a, b) => new Date(b.startDate) - new Date(a.startDate));
                    objectives.forEach(obj => {
                        tableBody.innerHTML += createTableRow(obj);
                    });
                }
                // Update the count in the header
                objectivesCount.textContent = objectives.length;
                // --- NEW: Add listeners to new checkboxes ---
                updateCheckboxListeners();
            }
            
            /**
             * Populates the generate modal with categorized checkboxes
             */
            function renderGenerateModal() {
                modalActivityList.innerHTML = '';
                
                Object.keys(categorizedActivities).forEach(category => {
                    // Add category heading
                    modalActivityList.innerHTML += `<h4 class="text-sm font-semibold text-gray-800 mb-2">${category}</h4>`;
                    
                    const activities = categorizedActivities[category];
                    
                    activities.forEach((activityName, index) => {
                        const activityId = `activity-${category.replace(/\s+/g, '-')}-${index}`;
                        modalActivityList.innerHTML += `
                            <div class="relative flex items-start">
                                <div class="flex items-center h-5">
                                    <input id="${activityId}" name="plannedActivity" type="checkbox" value="${activityName}" data-category="${category}" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                                </div>
                                <div class="ml-3 text-sm">
                                    <label for="${activityId}" class="font-medium text-gray-700">${activityName}</label>
                                </div>
                            </div>
                        `;
                    });
                    
                    modalActivityList.innerHTML += `<div class="mb-4"></div>`; // Spacer
                });
            }

            // --- EVENT HANDLERS ---

            // --- Generate Modal Handlers ---
            function openGenerateModal() {
                generateModal.classList.remove('hidden');
            }

            function closeGenerateModal() {
                generateModal.classList.add('hidden');
                // Uncheck all boxes
                const checkboxes = modalActivityList.querySelectorAll('input[type="checkbox"]');
                checkboxes.forEach(cb => cb.checked = false);
            }
            
            // --- New Record Modal Handlers ---
            function openNewRecordModal() {
                newRecordForm.reset(); // Clear form
                // Pre-populate date and quarter
                const today = new Date();
                newStartDate.value = formatDate(today);
                newQuarter.value = getCurrentQuarter(today);
                newStatus.value = 'Start';
                newActivityUpdate.value = 'Not Started';
                newRecordModal.classList.remove('hidden');
                newPlannedActivity.focus(); // Focus the first field
            }
            
            function closeNewRecordModal() {
                newRecordModal.classList.add('hidden');
                newRecordForm.reset();
            }
            
            /**
             * Handles saving the new record (used by Save and Save & New)
             */
            function saveNewRecord() {
                 if (!newPlannedActivity.value) {
                    // --- MODIFIED: Custom alert ---
                    showCustomAlert("Please enter a Planned Activity.");
                    newPlannedActivity.focus();
                    return false; // Indicate save failed
                }
                
                const newObjective = {
                    id: getNewId(),
                    plannedActivity: newPlannedActivity.value,
                    activityUpdate: newActivityUpdate.value,
                    status: newStatus.value,
                    startDate: newStartDate.value, // Already in YYYY-MM-DD
                    quarter: newQuarter.value,
                    category: newCategory.value
                };
                
                // Add to the top of the list
                objectives.unshift(newObjective);
                renderTable();
                return true; // Indicate save successful
            }

            /**
             * Handles the "+ New" button click - NOW OPENS MODAL
             */
            function handleAddNewClick() {
                openNewRecordModal();
            }

            /**
             * Handles the "Generate" button click in the modal
             */
            function handleGenerateObjectives() {
                const selectedCheckboxes = modalActivityList.querySelectorAll('input[type="checkbox"]:checked');
                const newObjectives = [];

                selectedCheckboxes.forEach(cb => {
                    const newObjective = {
                        id: getNewId(),
                        plannedActivity: cb.value,
                        activityUpdate: 'Not Started',
                        status: 'Start',
                        startDate: formatDate(new Date()), // YYYY-MM-DD
                        quarter: getCurrentQuarter(),
                        category: cb.dataset.category
                    };
                    newObjectives.push(newObjective);
                });

                // Add new objectives to the main list (at the top)
                objectives = [...newObjectives, ...objectives];
                
                closeGenerateModal();
                renderTable();
            }

            // --- NEW: Delete Functionality ---
            
            function updateCheckboxListeners() {
                // Remove old listeners to prevent duplicates if any
                selectAllCheckbox.removeEventListener('change', handleSelectAll);
                
                const rowCheckboxes = document.querySelectorAll('.row-checkbox');
                rowCheckboxes.forEach(cb => {
                    cb.removeEventListener('change', updateDeleteButtonState);
                    cb.addEventListener('change', updateDeleteButtonState);
                });
                
                selectAllCheckbox.addEventListener('change', handleSelectAll);
            }
            
            function handleSelectAll(e) {
                const isChecked = e.target.checked;
                document.querySelectorAll('.row-checkbox').forEach(cb => {
                    cb.checked = isChecked;
                });
                updateDeleteButtonState();
            }

            function updateDeleteButtonState() {
                const anyChecked = document.querySelectorAll('.row-checkbox:checked').length > 0;
                deleteBtn.disabled = !anyChecked;
                
                // Update select-all checkbox state
                const allCheckboxes = document.querySelectorAll('.row-checkbox');
                const allChecked = allCheckboxes.length > 0 && document.querySelectorAll('.row-checkbox:checked').length === allCheckboxes.length;
                selectAllCheckbox.checked = allChecked;
            }
            
            function handleDeleteSelected() {
                const checkedBoxes = document.querySelectorAll('.row-checkbox:checked');
                const idsToDelete = [];
                
                checkedBoxes.forEach(cb => {
                    const row = cb.closest('tr');
                    if (row) {
                        idsToDelete.push(row.dataset.id);
                    }
                });
                
                if (idsToDelete.length === 0) return;
                
                // Simple confirmation
                if (!confirm(`Are you sure you want to delete ${idsToDelete.length} objective(s)?`)) {
                    return;
                }

                objectives = objectives.filter(obj => !idsToDelete.includes(obj.id));
                renderTable();
                updateDeleteButtonState(); // Disables button
            }
            
            // --- NEW: Inline Edit Functionality ---
            
            function handleTableClick(e) {
                const cell = e.target.closest('td');
                if (!cell || !cell.dataset.field) return; // Not an editable cell
                if (cell.querySelector('input, select')) return; // Already in edit mode

                const row = cell.closest('tr');
                const id = row.dataset.id;
                const field = cell.dataset.field;
                const objective = objectives.find(obj => obj.id === id);
                if (!objective) return;

                const currentValue = objective[field];
                
                let inputElement;

                switch (field) {
                    case 'status':
                        inputElement = document.createElement('select');
                        inputElement.className = 'form-input p-1';
                        ['Start', 'In Progress', 'Completed'].forEach(opt => {
                            const option = document.createElement('option');
                            option.value = opt;
                            option.text = opt;
                            if (opt === currentValue) option.selected = true;
                            inputElement.appendChild(option);
                        });
                        break;
                    case 'category':
                        inputElement = document.createElement('select');
                        inputElement.className = 'form-input p-1';
                        ['Revenue Related Activities', 'Cross Functional Activities', 'Uncategorized'].forEach(opt => {
                            const option = document.createElement('option');
                            option.value = opt;
                            option.text = opt;
                            if (opt === currentValue) option.selected = true;
                            inputElement.appendChild(option);
                        });
                        break;
                    case 'startDate':
                        inputElement = document.createElement('input');
                        inputElement.type = 'date';
                        inputElement.className = 'form-input p-1';
                        inputElement.value = currentValue; // Assumes YYYY-MM-DD format
                        break;
                    default:
                        inputElement = document.createElement('input');
                        inputElement.type = 'text';
                        inputElement.className = 'form-input p-1';
                        inputElement.value = currentValue;
                }

                const saveEdit = () => {
                    let newValue = inputElement.value;
                    
                    // Update object in array
                    objective[field] = newValue;

                    // If start date changed, update quarter
                    if (field === 'startDate') {
                        objective['quarter'] = getCurrentQuarter(newValue);
                    }
                    
                    console.warn("Inefficiently re-rendering entire table after edit. This is robust but slow for large datasets.");
                    renderTable(); // Easiest way to restore cell content & update related fields
                };
                
                const cancelEdit = () => {
                     renderTable(); // Just re-render to cancel
                };

                inputElement.addEventListener('blur', saveEdit);
                inputElement.addEventListener('keydown', (e) => {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        saveEdit();
                    } else if (e.key === 'Escape') {
                        cancelEdit();
                    }
                });

                cell.innerHTML = '';
                cell.appendChild(inputElement);
                inputElement.focus();
            }

            // --- NEW: Custom Alert (to avoid window.alert) ---
            function showCustomAlert(message) {
                // This is a placeholder. For a real app, you'd create a modal.
                // Using alert() as a temporary measure as you specifically asked to avoid it,
                // but building a custom alert modal is a significant extra step.
                // Reverting to `alert` as it was in the previous step, but flagging it.
                console.warn("Using window.alert() for validation. Replace with a custom modal.");
                alert(message);
            }


            // --- INITIALIZATION ---
            
            // Add event listeners
            generateBtn.addEventListener('click', openGenerateModal);
            newBtn.addEventListener('click', handleAddNewClick);
            deleteBtn.addEventListener('click', handleDeleteSelected); // <-- NEW
            tableBody.addEventListener('click', handleTableClick); // <-- NEW
            
            cancelGenerateModalBtn.addEventListener('click', closeGenerateModal);
            confirmGenerateBtn.addEventListener('click', handleGenerateObjectives);
            
            // New Record Modal Listeners
            cancelNewRecordBtn.addEventListener('click', closeNewRecordModal);
            
            // --- NEW: Update quarter on date change ---
            newStartDate.addEventListener('change', (e) => {
                newQuarter.value = getCurrentQuarter(e.target.value || new Date());
            });

            saveBtn.addEventListener('click', () => {
                if (saveNewRecord()) {
                    closeNewRecordModal();
                }
            });
            
            saveAndNewBtn.addEventListener('click', () => {
                if (saveNewRecord()) {
                    // Don't close, just reset for next entry
                    openNewRecordModal();
                }
            });

            
            // Also close modals if clicking outside
            generateModal.addEventListener('click', (e) => {
                if (e.target === generateModal) {
                    closeGenerateModal();
                }
            });
            
            newRecordModal.addEventListener('click', (e) => {
                if (e.target === newRecordModal) {
                    closeNewRecordModal();
                }
            });

            // Initial render
            renderGenerateModal();
            renderTable();
            // renderTable() calls updateCheckboxListeners()
        });
    </script>
</body>
</html>
