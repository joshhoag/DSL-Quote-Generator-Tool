[DSL_Rate_Manager_12_1.html](https://github.com/user-attachments/files/31524429/DSL_Rate_Manager_12_1.html)
[DSL_Quote_Generator_20.html](https://github.com/user-attachments/files/31524421/DSL_Quote_Generator_20.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DSL Logistics Quote Generator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: Calibri, Arial, sans-serif;
            background-color: #f9f9f9;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        
        h1 {
            text-align: center;
            margin-bottom: 40px;
            color: #000;
            font-size: 28px;
        }
        
        .main-content {
            display: grid;
            grid-template-columns: 380px 1fr;
            gap: 40px;
            align-items: start;
        }
        
        .form-container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            height: fit-content;
            max-height: 90vh;
            overflow-y: auto;
        }
        
        .form-section {
            margin-bottom: 25px;
            padding-bottom: 20px;
            border-bottom: 1px solid #f0f0f0;
        }
        
        .form-section:last-of-type {
            border-bottom: none;
        }
        
        .form-section h2 {
            font-size: 12px;
            font-weight: 700;
            color: #000;
            margin-bottom: 12px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            border-bottom: 1px solid #FFD700;
            padding-bottom: 8px;
        }
        
        .form-group {
            margin-bottom: 12px;
        }
        
        label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            color: #333;
            margin-bottom: 4px;
        }
        
        input[type="text"],
        input[type="number"],
        textarea,
        select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-family: Calibri, Arial, sans-serif;
            font-size: 13px;
        }
        
        select:disabled {
            background-color: #eee;
            color: #999;
            cursor: not-allowed;
        }

        input[type="text"]:focus,
        input[type="number"]:focus,
        textarea:focus,
        select:focus {
            outline: none;
            border-color: #FFD700;
            box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.15);
        }
        
        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 8px;
        }
        
        input[type="checkbox"] {
            width: 16px;
            height: 16px;
            cursor: pointer;
        }
        
        .checkbox-group label {
            margin: 0;
            font-weight: 400;
            cursor: pointer;
        }
        
        .form-group-with-toggle {
            display: flex;
            gap: 8px;
            align-items: flex-end;
        }
        
        .form-group-with-toggle > div {
            flex: 1;
        }
        
        .form-group-with-toggle label {
            margin-bottom: 4px;
        }
        
        .toggle-btn {
            background-color: #ddd;
            color: #333;
            border: none;
            padding: 8px 12px;
            border-radius: 4px;
            font-size: 11px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s;
            font-family: Calibri, Arial, sans-serif;
        }
        
        .toggle-btn.active {
            background-color: #FFD700;
            color: #000;
        }
        
        .toggle-btn:hover {
            opacity: 0.9;
        }
        
        .custom-fields-container {
            background-color: #f9f9f9;
            border: 1px solid #e0e0e0;
            border-radius: 4px;
            padding: 12px;
            margin-bottom: 12px;
        }
        
        .custom-field-item {
            display: flex;
            gap: 8px;
            margin-bottom: 8px;
            align-items: center;
            font-size: 12px;
        }
        
        .custom-field-item:last-child {
            margin-bottom: 0;
        }
        
        .custom-field-label {
            font-weight: 600;
            min-width: 80px;
            word-break: break-word;
        }
        
        .custom-field-value {
            flex: 1;
            word-break: break-word;
        }
        
        .btn-remove-field {
            background: none;
            border: none;
            color: #d97757;
            cursor: pointer;
            font-size: 12px;
            font-weight: 600;
            padding: 2px 6px;
        }
        
        .btn-remove-field:hover {
            color: #a5523a;
        }
        
        .add-custom-section {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        
        .add-custom-inputs {
            display: flex;
            gap: 8px;
            font-size: 12px;
        }
        
        .add-custom-inputs input {
            flex: 1;
            padding: 6px;
            font-size: 12px;
        }
        
        .btn-add-field {
            background-color: #333;
            color: white;
            border: none;
            padding: 6px 12px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 11px;
            font-weight: 600;
        }
        
        .btn-add-field:hover {
            background-color: #555;
        }
        
        .button-group {
            display: flex;
            gap: 10px;
            margin-top: 25px;
        }
        
        button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 4px;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            font-family: Calibri, Arial, sans-serif;
            transition: background-color 0.3s;
        }
        
        .btn-generate {
            background-color: #FFD700;
            color: #000;
        }
        
        .btn-generate:hover {
            background-color: #E6C200;
        }
        
        .btn-copy {
            background-color: #333;
            color: white;
            grid-column: 1 / -1;
            margin-bottom: 15px;
        }
        
        .btn-copy:hover {
            background-color: #555;
        }
        
        .btn-copy.copied {
            background-color: #4CAF50;
        }
        
        .preview-container {
            background: white;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            display: none;
        }
        
        .preview-container.show {
            display: block;
        }
        
        .quote-display {
            font-family: Calibri, Arial, sans-serif;
            line-height: 1.6;
            color: #333;
        }
        
        .quote-header {
            text-align: center;
            margin-bottom: 24px;
        }
        
        .quote-title {
            font-size: 22px;
            font-weight: bold;
            color: #000;
            margin-bottom: 4px;
        }
        
        .divider {
            border-bottom: 2px solid #FFD700;
            margin: 24px 0;
            font-size: 1px;
            line-height: 1px;
        }
        
        .quote-heading {
            font-size: 19px;
            color: #555;
            margin: 0 0 24px 0;
        }
        
        .quote-heading-container {
            margin-bottom: 24px;
        }

        .quote-heading-title {
            font-size: 19px;
            color: #555;
            margin: 0 0 20px 0;
        }

        .quote-heading-customer {
            font-size: 16px;
            color: #333;
            font-weight: 600;
            margin: 0;
        }
        
        .route-info {
            margin-bottom: 24px;
        }
        
        .route-from-to {
            font-size: 17px;
            font-weight: bold;
            color: #000;
            margin-bottom: 8px;
        }
        
        .route-type {
            font-size: 14px;
            color: #666;
            margin-bottom: 24px;
        }
        
        .quote-table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 24px;
            font-size: 15px;
        }
        
        .quote-table thead {
            background-color: #f5f5f5;
            border-bottom: 2px solid #FFD700;
        }
        
        .quote-table th {
            padding: 12px;
            text-align: left;
            font-weight: bold;
            font-size: 16px;
        }
        
        .quote-table th:last-child {
            text-align: right;
        }
        
        .quote-table td {
            padding: 10px 12px;
            border-bottom: 1px solid #e0e0e0;
        }
        
        .quote-table td:last-child {
            text-align: right;
            font-weight: bold;
        }
        
        .service-desc {
            font-size: 13px;
            color: #888;
        }
        
        .services-section {
            margin-bottom: 24px;
        }
        
        .services-title {
            font-size: 15px;
            font-weight: bold;
            color: #000;
            margin-bottom: 8px;
        }
        
        .services-list {
            margin-bottom: 24px;
            font-size: 15px;
            line-height: 1.6;
        }

        .menu-quote {
            margin: 8px 0 20px;
            font-size: 15px;
            line-height: 1.6;
        }
        .menu-lead { margin: 0 0 16px; }
        .menu-cond { margin: 14px 0 3px; }
        .menu-rate { margin: 0 0 4px; font-weight: 700; }
        .menu-section { margin: 20px 0 4px; }
        .menu-fee { margin: 0; }
        .menu-divider { border-top: 1px solid #ddd; margin: 16px 0; font-size: 1px; line-height: 1px; }
        
        .service-item {
            margin: 6px 0;
            font-size: 15px;
        }
        
        .custom-section {
            margin-bottom: 24px;
        }
        
        .custom-title {
            font-size: 15px;
            font-weight: bold;
            color: #000;
            margin-bottom: 8px;
        }
        
        .custom-item {
            margin: 6px 0;
            font-size: 15px;
        }
        
        .note {
            font-size: 13px;
            color: #888;
            font-style: italic;
            margin: 24px 0 0 0;
        }
        
        .footer {
            border-top: 2px solid #FFD700;
            margin-top: 24px;
            padding-top: 12px;
            text-align: center;
        }
        
        .footer-text {
            font-size: 13px;
            color: #888;
            margin: 0;
        }

        .footer-cta {
            font-size: 13px;
            color: #333;
            margin: 0 0 6px;
        }

        .footer-cta a {
            color: #000;
            font-weight: 600;
            text-decoration: underline;
        }

        .copy-feedback {
            text-align: center;
            margin-top: 10px;
            font-size: 13px;
            color: #4CAF50;
            font-weight: 600;
            display: none;
        }
        
        .copy-feedback.show {
            display: block;
        }

        .btn-load-rate {
            background-color: #FFD700;
            color: #000;
            font-size: 12px;
            padding: 10px 12px;
            margin-bottom: 10px;
            width: 100%;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            font-family: Calibri, Arial, sans-serif;
        }
        
        .btn-load-rate:hover {
            background-color: #E6C200;
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.4);
        }
        
        .modal.show {
            display: block;
        }
        
        .modal-content {
            background-color: white;
            margin: 10% auto;
            padding: 0;
            border-radius: 8px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }
        
        .modal-header {
            background-color: #000;
            color: #FFD700;
            padding: 15px 20px;
            border-radius: 8px 8px 0 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-header h2 {
            margin: 0;
            font-size: 16px;
        }
        
        .modal-close {
            background: none;
            border: none;
            color: #FFD700;
            font-size: 24px;
            cursor: pointer;
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .modal-form-group {
            margin-bottom: 15px;
        }
        
        .modal-form-group label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            color: #333;
            margin-bottom: 6px;
            text-transform: uppercase;
        }
        
        .modal-form-group input,
        .modal-form-group select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-family: Calibri, Arial, sans-serif;
            font-size: 13px;
        }
        
        .modal-form-group input:focus,
        .modal-form-group select:focus {
            outline: none;
            border-color: #FFD700;
            box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.15);
        }
        
        .rate-result {
            background-color: #f9f9f9;
            border: 1px solid #e0e0e0;
            border-radius: 4px;
            padding: 12px;
            margin-top: 15px;
            display: none;
        }
        
        .rate-result.show {
            display: block;
        }
        
        .rate-result-row {
            display: flex;
            justify-content: space-between;
            padding: 6px 0;
            font-size: 12px;
        }
        
        .rate-result-label {
            font-weight: 600;
            color: #666;
        }
        
        .rate-result-value {
            font-weight: 700;
            color: #000;
        }
        
        .modal-buttons {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .modal-buttons button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 600;
            cursor: pointer;
            font-family: Calibri, Arial, sans-serif;
        }
        
        .btn-apply {
            background-color: #FFD700;
            color: #000;
        }
        
        .btn-apply:hover {
            background-color: #E6C200;
        }
        
        .btn-cancel {
            background-color: #ddd;
            color: #333;
        }
        
        .btn-cancel:hover {
            background-color: #bbb;
        }
        
        .autocomplete-list {
            background: white;
            border: 1px solid #ddd;
            border-top: none;
            border-radius: 0 0 4px 4px;
            max-height: 200px;
            overflow-y: auto;
            position: absolute;
            width: 100%;
            z-index: 10;
            display: none;
        }
        
        .autocomplete-item {
            padding: 10px;
            border-bottom: 1px solid #e0e0e0;
            cursor: pointer;
            font-size: 13px;
            transition: background-color 0.2s;
        }
        
        .autocomplete-item:hover {
            background-color: #f9f9f9;
        }
        
        .destination-wrapper {
            position: relative;
        }

        .btn-add-lane {
            background-color: #000;
            color: #FFD700;
            font-size: 12px;
            padding: 10px 12px;
            margin-top: 4px;
            width: 100%;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 700;
            font-family: Calibri, Arial, sans-serif;
        }

        .btn-add-lane:hover {
            background-color: #333;
        }

        .lane-section {
            background-color: #fafafa;
            border: 1px solid #e0e0e0;
            border-left: 3px solid #FFD700;
            border-radius: 4px;
            padding: 14px;
            margin-bottom: 12px;
        }

        .lane-section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .lane-section-title {
            font-size: 12px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: #000;
        }

        .btn-remove-lane {
            background: none;
            border: none;
            color: #d97757;
            cursor: pointer;
            font-size: 11px;
            font-weight: 700;
            padding: 2px 6px;
        }

        .btn-remove-lane:hover {
            color: #a5523a;
        }

        .lane-quote-separator {
            border-top: 2px dashed #ccc;
            margin: 40px 0;
            font-size: 1px;
            line-height: 1px;
        }

        @media print {
            .lane-quote-separator {
                border: none;
                margin: 0;
                page-break-before: always;
            }
        }

        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>DSL Logistics Quote Generator</h1>
        
        <div class="main-content">
            <!-- Form Section -->
            <div class="form-container">
                <div class="form-section">
                    <h2>Quote Type</h2>
                    <div style="display: flex; gap: 10px; margin-bottom: 10px;">
                        <button class="toggle-btn active" id="importBtn" onclick="switchMode('import')" style="flex: 1; padding: 12px;">IMPORT</button>
                        <button class="toggle-btn" id="railBtn" onclick="switchMode('rail')" style="flex: 1; padding: 12px;">RAIL IMPORT</button>
                        <button class="toggle-btn" id="localBtn" onclick="switchMode('local')" style="flex: 1; padding: 12px;">LOCAL</button>
                    </div>
                    <div style="display: flex; gap: 10px; margin-bottom: 10px;">
                        <button class="toggle-btn" id="exportBtn" onclick="switchMode('export')" style="flex: 1; padding: 12px;">EXPORT</button>
                        <button class="toggle-btn" id="railExportBtn" onclick="switchMode('railExport')" style="flex: 1; padding: 12px;">RAIL EXPORT</button>
                        <button class="toggle-btn" id="railRampExportBtn" onclick="switchMode('railRampExport')" style="flex: 1; padding: 12px;">RAIL LOCAL EXPORT</button>
                    </div>
                </div>
                
                <div class="form-section">
                    <h2>Customer Info</h2>
                    <div class="form-group">
                        <label>Customer Name</label>
                        <input type="text" id="customerName" placeholder="Enter customer name">
                    </div>
                </div>
                
                <div class="form-section">
                    <h2>Route Details</h2>
                    <div class="form-group">
                        <label>From</label>
                        <select id="fromLocation" onchange="updateChassisFromLocation()">
                            <option value="los_angeles">Port of Los Angeles/Long Beach</option>
                            <option value="other">Other Location</option>
                        </select>
                    </div>
                    <div class="form-group" id="customLocationGroup" style="display: none;">
                        <label>Custom Location</label>
                        <input type="text" id="customLocation" placeholder="Enter custom location" onchange="generateQuote()">
                    </div>
                    <div class="form-group">
                        <label>To</label>
                        <div class="destination-wrapper">
                            <input type="text" id="toLocation" placeholder="Delivery location" autocomplete="off">
                            <div class="autocomplete-list" id="toLocationAutocompleteList"></div>
                        </div>
                    </div>
                </div>
                
                <div class="form-section">
                    <h2>Rates</h2>
                    <button class="btn-load-rate" onclick="openRateModal()">📊 Load Rate from Manager</button>
                    <div class="form-group" id="tieredMenuRow" style="display:none;">
                        <label style="display:flex; align-items:center; gap:8px; cursor:pointer; font-weight:700;">
                            <input type="checkbox" id="tieredMenuMode" onchange="generateQuote()" style="width:auto; margin:0;">
                            Tiered menu quote (all container tiers)
                        </label>
                        <small style="color:#666; display:block; margin-top:4px;">Outputs the full 40′ / 20′-45′ / reefer pricing menu — use when the container type or steamship line isn't known yet.</small>
                    </div>
                    <input type="hidden" id="importSteamshipLine" value="">
                    <input type="hidden" id="importContainerType" value="">
                    <div class="form-group">
                        <label>Transport ($)</label>
                        <input type="number" id="transportRate" value="0.00" step="0.01">
                    </div>
                    <div class="form-group">
                        <label>Fuel Surcharge (%)</label>
                        <input type="number" id="fuelSurcharge" value="57" step="0.1">
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Chassis Fee ($)</label>
                            <input type="number" id="chassisRate" value="50.00" step="0.01">
                        </div>
                        <button class="toggle-btn active" id="chassisToggleBtn" onclick="toggleChassisFee()">ON</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Hazmat ($)</label>
                            <input type="number" id="hazmatSurcharge" placeholder="$325" step="0.01">
                        </div>
                        <button class="toggle-btn" id="hazmatToggleBtn" onclick="toggleHazmatSurcharge()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Tanker Surcharge ($)</label>
                            <input type="number" id="tankerSurcharge" placeholder="$225" step="0.01">
                        </div>
                        <button class="toggle-btn" id="tankerToggleBtn" onclick="toggleTankerSurcharge()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Triaxle ($)</label>
                            <input type="number" id="triaxleSurcharge" placeholder="$150" step="0.01">
                        </div>
                        <button class="toggle-btn" id="triaxleToggleBtn" onclick="toggleTriaxleSurcharge()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Split Chassis ($)</label>
                            <input type="number" id="splitChassisFee" placeholder="$150" step="0.01">
                        </div>
                        <button class="toggle-btn" id="splitChassisToggleBtn" onclick="toggleSplitChassisFee()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Residential Delivery ($)</label>
                            <input type="number" id="residentialDelivery" placeholder="$250" step="0.01">
                        </div>
                        <button class="toggle-btn" id="residentialToggleBtn" onclick="toggleResidentialDelivery()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Reefer ($)</label>
                            <input type="number" id="reeferSurcharge" placeholder="$300" step="0.01">
                        </div>
                        <button class="toggle-btn" id="reeferToggleBtn" onclick="toggleReefer()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>GenSet ($)</label>
                            <input type="number" id="gensetSurcharge" placeholder="$225" step="0.01">
                        </div>
                        <button class="toggle-btn" id="gensetToggleBtn" onclick="toggleGenSet()">OFF</button>
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Scale Ticket Fee ($)</label>
                            <input type="number" id="scaleTicketFee" placeholder="$175" step="0.01">
                        </div>
                        <button class="toggle-btn" id="scaleTicketToggleBtn" onclick="toggleScaleTicketFee()">OFF</button>
                    </div>
                </div>

                <div class="form-section">
                    <h2>Additional Lanes</h2>
                    <div id="additionalLanesContainer"></div>
                    <button class="btn-add-lane" onclick="addLane()">+ Add Another Lane</button>
                </div>
                
                <div class="form-section">
                    <h2>Services</h2>
                    <div class="form-group">
                        <label>Drop/Pick ZIP</label>
                        <input type="text" id="dropLocation" value="85032">
                    </div>
                    <div class="form-group-with-toggle">
                        <div>
                            <label>Max Cargo Weight Allowed in Pounds</label>
                            <input type="number" id="maxCargoWeight" placeholder="LBS" step="1">
                        </div>
                        <button class="toggle-btn" id="maxCargoToggleBtn" onclick="toggleMaxCargoWeight()">OFF</button>
                    </div>
                    <div class="checkbox-group">
                        <input type="checkbox" id="includeStorage" checked>
                        <label for="includeStorage">Include Free Storage</label>
                    </div>
                    <div class="form-group" id="storageDaysGroup">
                        <label>Storage Days</label>
                        <input type="text" id="storageDays" value="4">
                    </div>
                    <div class="checkbox-group">
                        <input type="checkbox" id="includeNoChassis" checked>
                        <label for="includeNoChassis">No Chassis Split Note</label>
                    </div>
                    <div class="form-group">
                        <label>Live Unload ($/hr)</label>
                        <input type="number" id="liveUnloadRate" value="97.50" step="0.01">
                    </div>
                </div>

                <div class="form-section">
                    <h2>Custom Fields</h2>
                    <div id="customFieldsList" class="custom-fields-container" style="display: none;"></div>
                    <div class="add-custom-section">
                        <div class="add-custom-inputs">
                            <input type="text" id="customFieldName" placeholder="Field name">
                            <input type="text" id="customFieldValue" placeholder="Value">
                            <button class="btn-add-field" onclick="addCustomField()">Add</button>
                        </div>
                    </div>
                </div>
                
                <div class="button-group">
                    <button class="btn-generate" onclick="generateQuote()">Generate Quote</button>
                </div>
            </div>
            
            <!-- Preview Section -->
            <div class="preview-container" id="previewContainer">
                <button class="btn-copy" id="copyBtn" onclick="copyQuote()">Copy to Clipboard</button>
                <div class="copy-feedback" id="copyFeedback">✓ Copied! Now paste into your Outlook email</div>
                
                <div class="quote-display" id="quoteContent">
                    <!-- Quote will be generated here -->
                </div>
            </div>
        </div>
    </div>

    <!-- Rate Loading Modal -->
    <div id="rateModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Load Rate from Manager</h2>
                <button class="modal-close" onclick="closeRateModal()">&times;</button>
            </div>
            <div class="modal-body">
                <div class="modal-form-group">
                    <label id="modalDestinationLabel">Pick Up</label>
                    <div class="destination-wrapper">
                        <input type="text" id="modalDestination" placeholder="Type pick up location..." autocomplete="off">
                        <div class="autocomplete-list" id="modalAutocompleteList"></div>
                    </div>
                </div>
                
                <div class="modal-form-group" id="railRampGroup" style="display: none;">
                    <label>Rail Ramp</label>
                    <select id="modalRailRamp">
                        <option value="">Select ramp...</option>
                        <option value="Laveen Yard/Phoenix RR">Laveen Yard/Phoenix RR</option>
                        <option value="Tucson Rail">Tucson Rail</option>
                        <option value="BNSF Rail">BNSF Rail</option>
                    </select>
                </div>

                <div class="modal-form-group" id="containerTypeGroup">
                    <label>Container Type</label>
                    <select id="modalContainerType" onchange="updateSteamshipLineAvailability()">
                        <option value="">Select type...</option>
                        <option value="40ST_HC">40' Standard & 40' HC</option>
                        <option value="20_45">(20' / 45')</option>
                        <option value="NOR_REEFER">RT (NOR / Reefer)</option>
                    </select>
                </div>
                
                <div class="modal-form-group" id="steamshipLineGroup">
                    <label>Steamship Line</label>
                    <select id="modalSteamshipLine">
                        <option value="">Select line type...</option>
                        <option value="ssl">Premium Lines (SSL)</option>
                        <option value="other">Other Lines (+$480)</option>
                    </select>
                </div>
                
                <button class="btn-apply" onclick="lookupModalRate()" style="width: 100%; margin-top: 15px;">Get Rate</button>
                
                <!-- Custom Quote Section -->
                <div style="margin-top: 20px; padding-top: 20px; border-top: 1px solid #ddd;">
                    <button class="btn-apply" onclick="toggleCustomQuote()" style="width: 100%; background-color: #000000; color: #FFD700; font-weight: bold;">Custom Quote</button>
                    <div id="customQuoteSection" style="display: none; margin-top: 15px;">
                        <div class="modal-form-group">
                            <label>Delivery Location (Optional)</label>
                            <div class="destination-wrapper">
                                <input type="text" id="customQuoteDelivery" placeholder="Type delivery location..." autocomplete="off">
                            </div>
                        </div>
                        
                        <div class="modal-form-group">
                            <label>Container Type (Optional)</label>
                            <select id="customQuoteContainerType">
                                <option value="">Select type...</option>
                                <option value="40ST_HC">40' Standard & 40' HC</option>
                                <option value="20_45">(20' / 45')</option>
                                <option value="NOR_REEFER">RT (NOR / Reefer)</option>
                            </select>
                        </div>
                        
                        <div class="modal-form-group">
                            <label>Shipment Line (Optional)</label>
                            <select id="customQuoteShipmentLine">
                                <option value="">Select line type...</option>
                                <option value="ssl">Premium Lines (SSL)</option>
                                <option value="other">Other Lines</option>
                            </select>
                        </div>
                        
                        <div class="modal-form-group">
                            <label for="customAmount">Add Dollar Amount</label>
                            <input type="number" id="customAmount" placeholder="Enter dollar amount..." step="0.01" value="">
                        </div>
                        <small style="color: #666; display: block; margin-top: 5px;">All fields optional - Enter dollar amount to add to transport rate</small>
                    </div>
                </div>
                
                <div class="rate-result" id="modalRateResult">
                    <div id="modalRateResultContent"></div>
                    <div class="modal-buttons">
                        <button class="btn-apply" onclick="applyModalRate()">Apply Rate</button>
                        <button class="btn-cancel" onclick="closeRateModal()">Cancel</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        let customFields = [];
        let rateData = {};
        let tankerActive = false;
        let triaxleActive = false;
        let customQuoteMode = false;
        let lanes = [];            // ids of additional lanes, in display order
        let laneCounter = 0;       // ever-increasing id source
        let rateModalTarget = null; // null = main form; otherwise a lane id
        let laneStoredChassis = {}; // per-lane chassis stashed while triaxle is ON
        
        const SURCHARGES = {
            tanker: 225.00,
            triaxlePhoenix: 250.00,
            triaxleLosAngeles: 250.00
        };

        // Display labels for the container type codes picked in the rate modal,
        // used to prefix the "Loaded Container" line in generated Import quotes.
        const IMPORT_CONTAINER_LABELS = {
            '40ST_HC': "40' Standard & 40' HC",
            '20_45': "20' / 45'",
            'NOR_REEFER': 'RT (NOR / Reefer)'
        };
        const RAIL_CONTAINER_LABELS = {
            '40_45': "40' / 45'",
            '20': "20'"
        };
        
        const DESTINATIONS = [
            "Phoenix, AZ",
            "Tempe, AZ",
            "Mesa, AZ",
            "Scottsdale, AZ",
            "Chandler, AZ",
            "Gilbert, AZ",
            "Glendale, AZ",
            "Peoria, AZ",
            "Avondale, AZ",
            "Goodyear, AZ",
            "Maricopa, AZ",
            "Tucson, AZ",
            "Nogales, AZ",
            "Eloy, AZ",
            "Casa Grande, AZ",
            "Douglas, AZ",
            "Naco, AZ",
            "Sedona, AZ",
            "Flagstaff, AZ",
            "Willcox, AZ",
            "Safford, AZ",
            "Prescott, AZ",
            "Yuma, AZ",
            "Lake Havasu, AZ",
            "Coolidge, AZ",
            "Albuquerque, NM",
            "Santa Fe, NM",
            "Las Cruces, NM",
            "El Paso, TX",
            "Dallas, TX",
            "Houston, TX",
            "Austin, TX",
            "San Antonio, TX",
            "Fort Worth, TX",
            "Corpus Christi, TX",
            "Denver, CO",
            "Boulder, CO",
            "Colorado Springs, CO",
            "Salt Lake City, UT",
            "Ogden, UT",
            "Provo, UT",
            "Washington, UT",
            "St George, UT",
            "Hurricane, UT",
            "Las Vegas, NV",
            "Reno, NV",
            "Los Angeles, CA",
            "Long Beach, CA",
            "San Diego, CA",
            "San Francisco, CA",
            "Sacramento, CA",
            "Fresno, CA",
            "Bakersfield, CA"
        ];
        
        let currentMode = 'import'; // Track current mode (import or export)
        
        const EXPORT_DESTINATIONS = []; // Will be populated from Rate Manager
        const RAIL_EXPORT_DESTINATIONS = []; // Will be populated from Rate Manager (rateData.exportRail)
        const RAIL_RAMP_EXPORT_PICKUPS = []; // Will be populated from Rate Manager (rateData.railRampExport)

        // Fixed set of rail ramps a Rail Ramp Export pickup can price to; maps display name -> data field
        const RAIL_RAMPS = {
            'Laveen Yard/Phoenix RR': 'laveenYard',
            'Tucson Rail': 'tucsonRail',
            'BNSF Rail': 'bnsfRail'
        };

        let modalRateInfo = null;

        function switchMode(mode) {
            currentMode = mode;
            
            // Update button styles
            const importBtn = document.getElementById('importBtn');
            const exportBtn = document.getElementById('exportBtn');
            const localBtn = document.getElementById('localBtn');
            const railBtn = document.getElementById('railBtn');
            const railExportBtn = document.getElementById('railExportBtn');
            const railRampExportBtn = document.getElementById('railRampExportBtn');

            importBtn.classList.remove('active');
            exportBtn.classList.remove('active');
            localBtn.classList.remove('active');
            if (railBtn) railBtn.classList.remove('active');
            if (railExportBtn) railExportBtn.classList.remove('active');
            if (railRampExportBtn) railRampExportBtn.classList.remove('active');

            if (mode === 'import') {
                importBtn.classList.add('active');
            } else if (mode === 'export') {
                exportBtn.classList.add('active');
            } else if (mode === 'local') {
                localBtn.classList.add('active');
            } else if (mode === 'rail') {
                if (railBtn) railBtn.classList.add('active');
            } else if (mode === 'railExport') {
                if (railExportBtn) railExportBtn.classList.add('active');
            } else if (mode === 'railRampExport') {
                if (railRampExportBtn) railRampExportBtn.classList.add('active');
            }
            
            // Update form visibility
            updateFormForMode();
            
            // Reset fields
            document.getElementById('toLocation').value = '';
            document.getElementById('fuelSurcharge').value = '57';
            document.getElementById('importSteamshipLine').value = '';
            document.getElementById('importContainerType').value = '';
            
            // Set transport rate based on mode
            if (mode === 'import') {
                document.getElementById('transportRate').value = '0.00';
            } else {
                document.getElementById('transportRate').value = '0.00';
            }
            
            // Chassis Fee - set default based on mode
            if (currentMode === 'local' || currentMode === 'rail' || currentMode === 'railExport' || currentMode === 'railRampExport') {
                document.getElementById('chassisRate').value = '50.00';
            } else if (currentMode === 'export') {
                document.getElementById('chassisRate').value = '110.00';
            } else {
                // Import mode
                document.getElementById('chassisRate').value = '195.00';
            }
            document.getElementById('chassisToggleBtn').classList.add('active');
            document.getElementById('chassisToggleBtn').textContent = 'ON';
            
            document.getElementById('hazmatSurcharge').value = '';
            
            // Reset hazmat toggle to OFF
            document.getElementById('hazmatToggleBtn').classList.remove('active');
            document.getElementById('hazmatToggleBtn').textContent = 'OFF';
            
            // Reset tanker toggle to OFF
            document.getElementById('tankerSurcharge').value = '';
            document.getElementById('tankerToggleBtn').classList.remove('active');
            document.getElementById('tankerToggleBtn').textContent = 'OFF';
            
            // Reset triaxle toggle to OFF
            document.getElementById('triaxleSurcharge').value = '';
            document.getElementById('triaxleToggleBtn').classList.remove('active');
            document.getElementById('triaxleToggleBtn').textContent = 'OFF';
            
            // Reset residential delivery toggle to OFF
            document.getElementById('residentialDelivery').value = '';
            document.getElementById('residentialToggleBtn').classList.remove('active');
            document.getElementById('residentialToggleBtn').textContent = 'OFF';
            
            // Reset reefer toggle to OFF
            document.getElementById('reeferSurcharge').value = '';
            document.getElementById('reeferToggleBtn').classList.remove('active');
            document.getElementById('reeferToggleBtn').textContent = 'OFF';
            
            // Reset genset toggle to OFF
            document.getElementById('gensetSurcharge').value = '';
            document.getElementById('gensetToggleBtn').classList.remove('active');
            document.getElementById('gensetToggleBtn').textContent = 'OFF';

            // Reset scale ticket fee toggle to OFF
            document.getElementById('scaleTicketFee').value = '';
            document.getElementById('scaleTicketToggleBtn').classList.remove('active');
            document.getElementById('scaleTicketToggleBtn').textContent = 'OFF';

            // Update triaxle placeholder based on mode
            const triaxleInput = document.getElementById('triaxleSurcharge');
            if (mode === 'import' || mode === 'rail') {
                triaxleInput.placeholder = '$250';
            } else if (mode === 'export' || mode === 'railExport') {
                triaxleInput.placeholder = '$150';
            } else {
                // LOCAL
                triaxleInput.placeholder = '$100';
            }

            // The generic reset above blanks toLocation/transportRate; re-derive them here so
            // each mode's locked/auto-picked destination and rate survive the mode switch.
            if (mode === 'export') {
                document.getElementById('toLocation').value = 'Port of Los Angeles/Long Beach';
                updateExportRate();
            } else if (mode === 'railExport') {
                document.getElementById('toLocation').value = 'Port of Los Angeles/Long Beach RAIL';
                updateRailExportRate();
            } else if (mode === 'railRampExport') {
                updateRailRampExportRate();
            }

            updateLaneLabels();
            generateQuote();
        }

        function updateFormForMode() {
            const fromLocation = document.getElementById('fromLocation');
            const toLocation = document.getElementById('toLocation');
            const toLocationWrapper = toLocation.parentElement;
            const customLocationGroup = document.getElementById('customLocationGroup');
            
            // Tiered menu option is import-only (runs on load and on every mode change)
            const tieredRow = document.getElementById('tieredMenuRow');
            if (tieredRow) {
                if (currentMode === 'import') {
                    tieredRow.style.display = 'block';
                } else {
                    tieredRow.style.display = 'none';
                    const mb = document.getElementById('tieredMenuMode');
                    if (mb) mb.checked = false;
                }
            }
            
            // Get the surcharge containers more accurately
            const liveUnloadInput = document.getElementById('liveUnloadRate');
            
            const liveUnloadContainer = liveUnloadInput ? liveUnloadInput.closest('.form-group') : null;
            
            if (currentMode === 'export') {
                // Export mode - From field shows all export cities, To is locked
                fromLocation.innerHTML = EXPORT_DESTINATIONS.map(dest => 
                    `<option value="${dest.city}">${dest.city}</option>`
                ).join('');
                fromLocation.value = 'Phoenix, AZ';
                fromLocation.disabled = false;
                fromLocation.style.backgroundColor = 'white';
                fromLocation.style.cursor = 'auto';
                fromLocation.onchange = function() { 
                    updateExportRate(); 
                    generateQuote();
                };
                
                // Hide custom location
                if (customLocationGroup) customLocationGroup.style.display = 'none';
                
                // Lock To field as LA/LB - make it readonly and disabled
                toLocationWrapper.style.display = 'block';
                toLocation.value = 'Port of Los Angeles/Long Beach';
                toLocation.disabled = true;
                toLocation.readOnly = true;
                toLocation.style.backgroundColor = '#f0f0f0';
                toLocation.style.cursor = 'not-allowed';
                
                // Hide liveUnload in export mode
                if (liveUnloadContainer) liveUnloadContainer.style.display = 'none';
                
                // Load export rate for default city
                updateExportRate();
            } else if (currentMode === 'local') {
                // Local mode - From offers our CY (default) or our RR; To shows local cities
                fromLocation.innerHTML = `
                    <option value="phoenix_cy">Phoenix, AZ (Our CY)</option>
                    <option value="phoenix_rr">Phoenix, AZ (Our RR)</option>
                `;
                fromLocation.value = 'phoenix_cy';
                fromLocation.disabled = false;
                fromLocation.style.backgroundColor = '';
                fromLocation.style.cursor = '';
                fromLocation.onchange = generateQuote;
                
                // Hide custom location
                if (customLocationGroup) customLocationGroup.style.display = 'none';
                
                // Show To field - populate with local cities from Rate Manager
                toLocationWrapper.style.display = 'block';
                toLocation.disabled = false;
                toLocation.readOnly = false;
                toLocation.value = '';
                toLocation.style.backgroundColor = 'white';
                toLocation.style.cursor = 'auto';
                
                // Populate toLocation with local cities
                if (rateData.local && rateData.local.rates) {
                    toLocation.innerHTML = rateData.local.rates.map(rate =>
                        `<option value="${rate.destination}">${rate.destination}</option>`
                    ).join('');
                    toLocation.onchange = function() {
                        updateLocalRate();
                        generateQuote();
                    };
                }
                
                // Show liveUnload in local mode
                if (liveUnloadContainer) liveUnloadContainer.style.display = 'block';
                
                // Set fuel surcharge to 57% for LOCAL mode
                document.getElementById('fuelSurcharge').value = '57';
                
                // Set default chassis fee to $50 for LOCAL mode
                document.getElementById('chassisRate').value = '50.00';
                document.getElementById('chassisToggleBtn').classList.add('active');
                document.getElementById('chassisToggleBtn').textContent = 'ON';
                
                // Load local rate for default city
                updateLocalRate();
            } else if (currentMode === 'rail') {
                // Import Rail mode - From shows the LA/LB RAIL ramp origin
                fromLocation.innerHTML = `
                    <option value="los_angeles_rail">Port of Los Angeles/Long Beach RAIL</option>
                    <option value="other">Other Location</option>
                `;
                fromLocation.value = 'los_angeles_rail';
                fromLocation.disabled = false;
                fromLocation.style.backgroundColor = 'white';
                fromLocation.style.cursor = 'auto';
                fromLocation.onchange = updateChassisFromLocation;

                updateChassisFromLocation();

                toLocationWrapper.style.display = 'block';
                toLocation.disabled = false;
                toLocation.readOnly = false;
                toLocation.value = '';
                toLocation.style.backgroundColor = 'white';
                toLocation.style.cursor = 'auto';

                if (liveUnloadContainer) liveUnloadContainer.style.display = 'block';

                document.getElementById('chassisRate').value = '50.00';
                document.getElementById('chassisToggleBtn').classList.add('active');
                document.getElementById('chassisToggleBtn').textContent = 'ON';
            } else if (currentMode === 'railExport') {
                // Rail Export mode - From shows all rail-export pickup cities, To is locked to LA/LB RAIL
                fromLocation.innerHTML = RAIL_EXPORT_DESTINATIONS.map(dest =>
                    `<option value="${dest.city}">${dest.city}</option>`
                ).join('');
                if (RAIL_EXPORT_DESTINATIONS.length > 0) {
                    fromLocation.value = RAIL_EXPORT_DESTINATIONS[0].city;
                }
                fromLocation.disabled = false;
                fromLocation.style.backgroundColor = 'white';
                fromLocation.style.cursor = 'auto';
                fromLocation.onchange = function() {
                    updateRailExportRate();
                    generateQuote();
                };

                // Hide custom location
                if (customLocationGroup) customLocationGroup.style.display = 'none';

                // Lock To field as LA/LB RAIL
                toLocationWrapper.style.display = 'block';
                toLocation.value = 'Port of Los Angeles/Long Beach RAIL';
                toLocation.disabled = true;
                toLocation.readOnly = true;
                toLocation.style.backgroundColor = '#f0f0f0';
                toLocation.style.cursor = 'not-allowed';

                // Hide liveUnload in rail export mode
                if (liveUnloadContainer) liveUnloadContainer.style.display = 'none';

                // Load rail export rate for default city
                updateRailExportRate();
            } else if (currentMode === 'railRampExport') {
                // Rail Ramp Export mode - From shows pickup cities; To is the chosen rail ramp (not locked)
                fromLocation.innerHTML = RAIL_RAMP_EXPORT_PICKUPS.map(dest =>
                    `<option value="${dest.city}">${dest.city}</option>`
                ).join('');
                if (RAIL_RAMP_EXPORT_PICKUPS.length > 0) {
                    fromLocation.value = RAIL_RAMP_EXPORT_PICKUPS[0].city;
                }
                fromLocation.disabled = false;
                fromLocation.style.backgroundColor = 'white';
                fromLocation.style.cursor = 'auto';
                fromLocation.onchange = function() {
                    updateRailRampExportRate();
                    generateQuote();
                };

                // Hide custom location
                if (customLocationGroup) customLocationGroup.style.display = 'none';

                // To field holds the chosen ramp - editable via autocomplete, not locked
                toLocationWrapper.style.display = 'block';
                toLocation.disabled = false;
                toLocation.readOnly = false;
                toLocation.value = '';
                toLocation.style.backgroundColor = 'white';
                toLocation.style.cursor = 'auto';

                // Hide liveUnload in rail ramp export mode
                if (liveUnloadContainer) liveUnloadContainer.style.display = 'none';

                // Load rate for default pickup, auto-picking its first valid ramp
                updateRailRampExportRate();
            } else {
                // Import mode
                fromLocation.innerHTML = `
                    <option value="los_angeles">Port of Los Angeles/Long Beach</option>
                    <option value="other">Other Location</option>
                `;
                fromLocation.value = 'los_angeles';
                fromLocation.disabled = false;
                fromLocation.style.backgroundColor = 'white';
                fromLocation.style.cursor = 'auto';
                fromLocation.onchange = updateChassisFromLocation;
                
                // Show/hide custom location based on selection
                updateChassisFromLocation();
                
                // Show To field normally - unlock it
                toLocationWrapper.style.display = 'block';
                toLocation.disabled = false;
                toLocation.readOnly = false;
                toLocation.value = '';
                toLocation.style.backgroundColor = 'white';
                toLocation.style.cursor = 'auto';
                
                // Show liveUnload in import mode
                if (liveUnloadContainer) liveUnloadContainer.style.display = 'block';
                
                // Set Chassis Fee to ON for import mode with LA/LB default ($195)
                document.getElementById('chassisRate').value = '195.00';
                document.getElementById('chassisToggleBtn').classList.add('active');
                document.getElementById('chassisToggleBtn').textContent = 'ON';
            }
        }

        function updateExportRate() {
            const fromCity = document.getElementById('fromLocation').value;
            const exportDest = EXPORT_DESTINATIONS.find(d => d.city === fromCity);
            
            if (exportDest) {
                document.getElementById('transportRate').value = exportDest.baseRate.toFixed(2);
                document.getElementById('fuelSurcharge').value = exportDest.fuelSurcharge;
            }
        }

        function updateRailExportRate() {
            const fromCity = document.getElementById('fromLocation').value;
            const railDest = RAIL_EXPORT_DESTINATIONS.find(d => d.city === fromCity);
            
            if (railDest) {
                document.getElementById('transportRate').value = railDest.baseRate.toFixed(2);
                document.getElementById('fuelSurcharge').value = railDest.fuelSurcharge;
            }
        }

        // Picks the rate for the currently selected pickup + ramp. If the current ramp isn't
        // valid (or wasn't served, i.e. $0) for this pickup, auto-selects the first ramp that is.
        function updateRailRampExportRate() {
            const pickup = document.getElementById('fromLocation').value;
            const toLocation = document.getElementById('toLocation');
            const pickupRow = RAIL_RAMP_EXPORT_PICKUPS.find(d => d.city === pickup);
            if (!pickupRow) return;

            const currentRampField = RAIL_RAMPS[toLocation.value];
            let rampName = (currentRampField && pickupRow[currentRampField]) ? toLocation.value : '';

            if (!rampName) {
                rampName = Object.keys(RAIL_RAMPS).find(name => pickupRow[RAIL_RAMPS[name]]) || '';
            }

            toLocation.value = rampName;
            const rate = rampName ? pickupRow[RAIL_RAMPS[rampName]] : 0;
            document.getElementById('transportRate').value = (rate || 0).toFixed(2);
            document.getElementById('fuelSurcharge').value = pickupRow.fuelSurcharge;
        }

        function updateLocalRate() {
            const toCity = document.getElementById('toLocation').value;
            if (!rateData.local || !rateData.local.rates) return;
            
            const localRate = rateData.local.rates.find(r => r.destination === toCity);
            if (localRate) {
                document.getElementById('transportRate').value = localRate.baseRate.toFixed(2);
                document.getElementById('fuelSurcharge').value = localRate.fuelSurcharge;
                
                // Set chassis fee based on destination
                const chassisRateField = document.getElementById('chassisRate');
                const chassisToggleBtn = document.getElementById('chassisToggleBtn');
                
                if (toCity === 'Albuquerque, NM / Belen, NM / El Paso, TX') {
                    // Albuquerque/Belen/El Paso = $195 chassis fee
                    chassisRateField.value = '195.00';
                } else {
                    // All other LOCAL destinations = $50 chassis fee
                    chassisRateField.value = '50.00';
                }
                
                // Always turn ON chassis fee for LOCAL mode
                chassisToggleBtn.classList.add('active');
                chassisToggleBtn.textContent = 'ON';
            }
        }

        // Load rates from Rate Manager
        function loadRatesFromManager() {
            try {
                const stored = localStorage.getItem('dsl_rates');
                
                // Load existing data from localStorage
                if (stored) {
                    rateData = JSON.parse(stored);
                } else {
                    rateData = {};
                }
                
                // Populate EXPORT_DESTINATIONS from Rate Manager
                if (rateData.export && rateData.export.rates && rateData.export.rates.length > 0) {
                    EXPORT_DESTINATIONS.length = 0; // Clear array
                    rateData.export.rates.forEach(rate => {
                        EXPORT_DESTINATIONS.push({
                            city: rate.destination,
                            baseRate: rate.baseRate,
                            fuelSurcharge: rate.fuelSurcharge
                        });
                    });
                    console.log(`✅ Loaded ${EXPORT_DESTINATIONS.length} EXPORT destinations from Rate Manager`);
                }
                
                // Populate RAIL_EXPORT_DESTINATIONS from Rate Manager (rateData.exportRail)
                if (rateData.exportRail && rateData.exportRail.rates && rateData.exportRail.rates.length > 0) {
                    RAIL_EXPORT_DESTINATIONS.length = 0; // Clear array
                    rateData.exportRail.rates.forEach(rate => {
                        RAIL_EXPORT_DESTINATIONS.push({
                            city: rate.destination,
                            baseRate: rate.baseRate,
                            fuelSurcharge: rate.fuelSurcharge
                        });
                    });
                    console.log(`✅ Loaded ${RAIL_EXPORT_DESTINATIONS.length} RAIL EXPORT destinations from Rate Manager`);
                }

                // Populate RAIL_RAMP_EXPORT_PICKUPS from Rate Manager (rateData.railRampExport)
                if (rateData.railRampExport && rateData.railRampExport.rates && rateData.railRampExport.rates.length > 0) {
                    RAIL_RAMP_EXPORT_PICKUPS.length = 0; // Clear array
                    rateData.railRampExport.rates.forEach(rate => {
                        RAIL_RAMP_EXPORT_PICKUPS.push({
                            city: rate.pickupLocation,
                            laveenYard: rate.laveenYard,
                            tucsonRail: rate.tucsonRail,
                            bnsfRail: rate.bnsfRail,
                            fuelSurcharge: rate.fuelSurcharge
                        });
                    });
                    console.log(`✅ Loaded ${RAIL_RAMP_EXPORT_PICKUPS.length} RAIL RAMP EXPORT pickups from Rate Manager`);
                }

                // ONLY initialize LOCAL if it doesn't exist
                // NEVER touch IMPORT/EXPORT - those come from Rate Manager
                if (!rateData.local) {
                    rateData.local = {
                        description: "Local Shipments (Phoenix CY to Local Destinations)",
                        rates: [
                            { destination: "Phoenix, AZ", baseRate: 250.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 392.50 },
                            { destination: "Chandler/Mesa/Tempe/Gilbert, AZ", baseRate: 295.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 463.15 },
                            { destination: "Tucson, AZ", baseRate: 785.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1232.45 },
                            { destination: "Nogales, AZ", baseRate: 1160.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1821.20 },
                            { destination: "Albuquerque, NM / Belen, NM / El Paso, TX", baseRate: 2095.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 3289.15 },
                            { destination: "Casa Grande, AZ", baseRate: 595.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 934.15 },
                            { destination: "Maricopa, AZ", baseRate: 475.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 745.75 },
                            { destination: "Eloy, AZ", baseRate: 595.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 934.15 },
                            { destination: "Prescott, AZ", baseRate: 785.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1232.45 }
                        ]
                    };
                    localStorage.setItem('dsl_rates', JSON.stringify(rateData));
                }
                
            } catch (error) {
                console.error('Error loading rates:', error);
            }
        }

        // Ramps valid (nonzero rate) for whichever pickup is currently selected in Rail Ramp Export mode
        function validRampsForCurrentPickup() {
            const pickup = document.getElementById('fromLocation').value;
            const pickupRow = RAIL_RAMP_EXPORT_PICKUPS.find(d => d.city === pickup);
            if (!pickupRow) return [];
            return Object.keys(RAIL_RAMPS).filter(name => pickupRow[RAIL_RAMPS[name]]);
        }

        function setupToLocationAutocomplete() {
            const input = document.getElementById('toLocation');
            const showRampList = function() {
                const list = document.getElementById('toLocationAutocompleteList');
                const ramps = validRampsForCurrentPickup();
                if (ramps.length === 0) {
                    list.style.display = 'none';
                    return;
                }
                list.innerHTML = ramps.map(ramp => `
                    <div class="autocomplete-item" onclick="selectToLocation('${ramp}')">${ramp}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.addEventListener('input', function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('toLocationAutocompleteList');

                if (currentMode === 'railRampExport') {
                    showRampList();
                    return;
                }

                // Show autocomplete in import and rail modes
                if (currentMode !== 'import' && currentMode !== 'rail') {
                    list.style.display = 'none';
                    return;
                }

                if (value.length === 0) {
                    list.style.display = 'none';
                    return;
                }

                const sourceList = (currentMode === 'rail')
                    ? ((rateData.importRail && rateData.importRail.rates) ? rateData.importRail.rates.map(r => r.destination) : [])
                    : DESTINATIONS;
                const filtered = sourceList.filter(destination =>
                    destination.toLowerCase().includes(value)
                );

                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }

                list.innerHTML = filtered.map(destination => `
                    <div class="autocomplete-item" onclick="selectToLocation('${destination}')">${destination}</div>
                `).join('');
                list.style.display = 'block';
            });
            input.addEventListener('focus', function() {
                if (currentMode === 'railRampExport') showRampList();
            });
            input.addEventListener('blur', function() {
                applyImportChassisForDestination();
            });
        }

        function selectToLocation(destination) {
            document.getElementById('toLocation').value = destination;
            document.getElementById('toLocationAutocompleteList').style.display = 'none';
            if (currentMode === 'railRampExport') {
                updateRailRampExportRate();
            } else {
                applyImportChassisForDestination();
            }
            generateQuote();
        }

        // NV delivery locations get a $110 chassis fee, CA delivery locations get $90,
        // instead of the standard $195 LA/LB default
        function applyImportChassisForDestination() {
            if (currentMode !== 'import') return;
            if (document.getElementById('fromLocation').value !== 'los_angeles') return;
            const toLoc = document.getElementById('toLocation').value;
            let chassisFee = '195.00';
            if (/,\s*(NV|Nevada)\b/i.test(toLoc)) {
                chassisFee = '110.00';
            } else if (/,\s*(CA|California)\b/i.test(toLoc)) {
                chassisFee = '90.00';
            }
            document.getElementById('chassisRate').value = chassisFee;
        }

        function updateChassisFromLocation() {
            const fromLocationDropdown = document.getElementById('fromLocation').value;
            const customLocationGroup = document.getElementById('customLocationGroup');
            const chassisInput = document.getElementById('chassisRate');
            
            // Show/hide custom location field
            if (fromLocationDropdown === 'other') {
                customLocationGroup.style.display = 'block';
            } else {
                customLocationGroup.style.display = 'none';
            }
            
            // Set chassis fee based on selection
            if (fromLocationDropdown === 'los_angeles') {
                chassisInput.value = '195.00';
            } else if (fromLocationDropdown === 'los_angeles_rail') {
                chassisInput.value = '50.00';
            } else if (fromLocationDropdown === 'phoenix') {
                chassisInput.value = '50.00';
            }
            applyImportChassisForDestination();

            // Update Triaxle price based on origin if it's active
            if (triaxleActive) {
                const triaxleInput = document.getElementById('triaxleSurcharge');
                if (fromLocationDropdown === 'los_angeles') {
                    triaxleInput.value = SURCHARGES.triaxleLosAngeles.toFixed(2);
                } else if (fromLocationDropdown === 'phoenix') {
                    triaxleInput.value = SURCHARGES.triaxlePhoenix.toFixed(2);
                }
            }
            
            generateQuote();
        }

        function toggleChassisFee() {
            const chassisInput = document.getElementById('chassisRate');
            const chassisBtn = document.getElementById('chassisToggleBtn');
            
            const isActive = chassisBtn.classList.contains('active');
            
            if (isActive) {
                // Turn OFF - set to $0
                chassisInput.value = '0.00';
                chassisBtn.classList.remove('active');
                chassisBtn.textContent = 'OFF';
            } else {
                // Turn ON - default to $195
                chassisInput.value = '195.00';
                chassisBtn.classList.add('active');
                chassisBtn.textContent = 'ON';
            }
            
            generateQuote();
        }

        function toggleHazmatSurcharge() {
            const hazmatInput = document.getElementById('hazmatSurcharge');
            const hazmatBtn = document.getElementById('hazmatToggleBtn');
            
            const isActive = hazmatBtn.classList.contains('active');
            
            if (isActive) {
                // Turn OFF - set to empty
                hazmatInput.value = '';
                hazmatBtn.classList.remove('active');
                hazmatBtn.textContent = 'OFF';
            } else {
                // Turn ON - set to $325
                hazmatInput.value = '325.00';
                hazmatBtn.classList.add('active');
                hazmatBtn.textContent = 'ON';
            }
            
            generateQuote();
        }

        function toggleTankerSurcharge() {
            const tankerInput = document.getElementById('tankerSurcharge');
            const tankerBtn = document.getElementById('tankerToggleBtn');
            
            const isActive = tankerBtn.classList.contains('active');
            
            if (isActive) {
                // Turn OFF - set to empty
                tankerInput.value = '';
                tankerBtn.classList.remove('active');
                tankerBtn.textContent = 'OFF';
            } else {
                // Turn ON - set to $225
                tankerInput.value = '225.00';
                tankerBtn.classList.add('active');
                tankerBtn.textContent = 'ON';
            }
            
            generateQuote();
        }

        function toggleTriaxleSurcharge() {
            const triaxleInput = document.getElementById('triaxleSurcharge');
            const triaxleBtn = document.getElementById('triaxleToggleBtn');
            const fromLocationDropdown = document.getElementById('fromLocation').value;
            const chassisInput = document.getElementById('chassisRate');
            
            const isActive = triaxleBtn.classList.contains('active');
            
            if (isActive) {
                // Turn OFF - set to empty and restore chassis fee
                triaxleInput.value = '';
                triaxleBtn.classList.remove('active');
                triaxleBtn.textContent = 'OFF';
                // Restore chassis fee from stored value
                if (window.storedChassisValue !== undefined) {
                    chassisInput.value = window.storedChassisValue;
                }
            } else {
                // Turn ON - set based on mode and location
                if (currentMode === 'local') {
                    triaxleInput.value = '100.00';
                } else if (currentMode === 'export') {
                    triaxleInput.value = '150.00';
                } else if (fromLocationDropdown === 'los_angeles') {
                    triaxleInput.value = SURCHARGES.triaxleLosAngeles.toFixed(2);
                } else if (fromLocationDropdown === 'phoenix') {
                    triaxleInput.value = SURCHARGES.triaxlePhoenix.toFixed(2);
                } else {
                    triaxleInput.value = SURCHARGES.triaxlePhoenix.toFixed(2);
                }
                triaxleBtn.classList.add('active');
                triaxleBtn.textContent = 'ON';
                // Store current chassis fee and set to 0
                window.storedChassisValue = chassisInput.value;
                chassisInput.value = '0.00';
            }
            
            generateQuote();
        }

        function toggleSplitChassisFee() {
            const splitChassisInput = document.getElementById('splitChassisFee');
            const splitChassisBtn = document.getElementById('splitChassisToggleBtn');
            const transportRateInput = document.getElementById('transportRate');
            
            const isActive = splitChassisBtn.classList.contains('active');
            const currentBaseRate = parseFloat(transportRateInput.value);
            
            if (isActive) {
                // Turn OFF - subtract $150 from base rate
                splitChassisInput.value = '';
                transportRateInput.value = (currentBaseRate - 150).toFixed(2);
                splitChassisBtn.classList.remove('active');
                splitChassisBtn.textContent = 'OFF';
            } else {
                // Turn ON - add $150 to base rate and set split chassis to $150
                splitChassisInput.value = '150.00';
                transportRateInput.value = (currentBaseRate + 150).toFixed(2);
                splitChassisBtn.classList.add('active');
                splitChassisBtn.textContent = 'ON';
            }
            
            generateQuote();
        }

        function toggleResidentialDelivery() {
            const residentialInput = document.getElementById('residentialDelivery');
            const residentialBtn = document.getElementById('residentialToggleBtn');

            const isActive = residentialBtn.classList.contains('active');

            if (isActive) {
                // Turn OFF - clear value
                residentialInput.value = '';
                residentialBtn.classList.remove('active');
                residentialBtn.textContent = 'OFF';
            } else {
                // Turn ON - set default $250
                residentialInput.value = '250.00';
                residentialBtn.classList.add('active');
                residentialBtn.textContent = 'ON';
            }

            generateQuote();
        }

        function toggleReefer() {
            const input = document.getElementById('reeferSurcharge');
            const btn = document.getElementById('reeferToggleBtn');
            if (btn.classList.contains('active')) {
                input.value = '';
                btn.classList.remove('active');
                btn.textContent = 'OFF';
            } else {
                input.value = '300.00';
                btn.classList.add('active');
                btn.textContent = 'ON';
            }
            generateQuote();
        }

        function toggleGenSet() {
            const input = document.getElementById('gensetSurcharge');
            const btn = document.getElementById('gensetToggleBtn');
            if (btn.classList.contains('active')) {
                input.value = '';
                btn.classList.remove('active');
                btn.textContent = 'OFF';
            } else {
                input.value = '225.00';
                btn.classList.add('active');
                btn.textContent = 'ON';
            }
            generateQuote();
        }

        function toggleScaleTicketFee() {
            const input = document.getElementById('scaleTicketFee');
            const btn = document.getElementById('scaleTicketToggleBtn');
            if (btn.classList.contains('active')) {
                input.value = '';
                btn.classList.remove('active');
                btn.textContent = 'OFF';
            } else {
                input.value = '175.00';
                btn.classList.add('active');
                btn.textContent = 'ON';
            }
            generateQuote();
        }

        function toggleMaxCargoWeight() {
            const maxCargoBtn = document.getElementById('maxCargoToggleBtn');
            const isActive = maxCargoBtn.classList.contains('active');
            
            if (isActive) {
                maxCargoBtn.classList.remove('active');
                maxCargoBtn.textContent = 'OFF';
            } else {
                maxCargoBtn.classList.add('active');
                maxCargoBtn.textContent = 'ON';
            }
            
            generateQuote();
        }

        function openRateModal(laneId) {
            // Track which lane (if any) this rate load should populate
            rateModalTarget = (laneId === undefined || laneId === null) ? null : laneId;

            // Load rates from Rate Manager first
            loadRatesFromManager();
            
            modalRateInfo = null;
            document.getElementById('modalDestination').value = '';
            document.getElementById('modalContainerType').value = '';
            document.getElementById('modalSteamshipLine').value = '';
            document.getElementById('modalSteamshipLine').disabled = false;
            document.getElementById('modalRailRamp').value = '';
            document.getElementById('modalRateResult').classList.remove('show');

            // Get form groups
            const containerGroup = document.getElementById('containerTypeGroup');
            const steamshipGroup = document.getElementById('steamshipLineGroup');
            const railRampGroup = document.getElementById('railRampGroup');
            if (railRampGroup) railRampGroup.style.display = 'none';
            document.getElementById('modalContainerType').innerHTML =
                `<option value="">Select type...</option>` +
                `<option value="40ST_HC">40' Standard & 40' HC</option>` +
                `<option value="20_45">(20' / 45')</option>` +
                `<option value="NOR_REEFER">RT (NOR / Reefer)</option>`;
            const reeferOption = document.querySelector('option[value="NOR_REEFER"]');
            const modalDestinationInput = document.getElementById('modalDestination');
            const modalDestinationLabel = document.getElementById('modalDestinationLabel');
            
            const modalMode = getModalMode();
            if (modalMode === 'export') {
                // Export mode - show Pick Up
                modalDestinationLabel.textContent = 'Pick Up';
                modalDestinationInput.placeholder = 'Type pick up location...';
                // Hide container type and steamship line
                if (containerGroup) containerGroup.style.display = 'none';
                if (steamshipGroup) steamshipGroup.style.display = 'none';
                if (reeferOption) reeferOption.style.display = 'block';
                setupExportDestinationAutocomplete();
            } else if (modalMode === 'railExport') {
                // Rail Export mode - show Pick Up (mirror Export)
                modalDestinationLabel.textContent = 'Pick Up';
                modalDestinationInput.placeholder = 'Type pick up location...';
                if (containerGroup) containerGroup.style.display = 'none';
                if (steamshipGroup) steamshipGroup.style.display = 'none';
                if (reeferOption) reeferOption.style.display = 'block';
                setupRailExportDestinationAutocomplete();
            } else if (modalMode === 'railRampExport') {
                // Rail Ramp Export mode - Pick Up plus a Rail Ramp selector
                modalDestinationLabel.textContent = 'Pick Up';
                modalDestinationInput.placeholder = 'Type pick up location...';
                if (containerGroup) containerGroup.style.display = 'none';
                if (steamshipGroup) steamshipGroup.style.display = 'none';
                if (railRampGroup) railRampGroup.style.display = 'block';
                setupRailRampExportDestinationAutocomplete();
            } else if (modalMode === 'local') {
                // Local mode - show Delivery
                modalDestinationLabel.textContent = 'Delivery';
                modalDestinationInput.placeholder = 'Type delivery location...';
                // Show container type but hide reefer option
                if (containerGroup) containerGroup.style.display = 'block';
                if (steamshipGroup) steamshipGroup.style.display = 'none';
                if (reeferOption) reeferOption.style.display = 'none';
                setupLocalDestinationAutocomplete();
            } else if (modalMode === 'rail') {
                // Import Rail mode - Delivery, two container tiers, keep steamship
                modalDestinationLabel.textContent = 'Delivery';
                modalDestinationInput.placeholder = 'Type delivery location...';
                if (containerGroup) containerGroup.style.display = 'block';
                if (steamshipGroup) steamshipGroup.style.display = 'block';
                document.getElementById('modalContainerType').innerHTML =
                    `<option value="">Select type...</option>` +
                    `<option value="40_45">40' / 45'</option>` +
                    `<option value="20">20'</option>`;
                setupRailDestinationAutocomplete();
            } else {
                // Import mode - show Delivery
                modalDestinationLabel.textContent = 'Delivery';
                modalDestinationInput.placeholder = 'Type delivery location...';
                // Show container type and steamship line
                if (containerGroup) containerGroup.style.display = 'block';
                if (steamshipGroup) steamshipGroup.style.display = 'block';
                if (reeferOption) reeferOption.style.display = 'block';
                setupDestinationAutocomplete();
            }
            
            document.getElementById('rateModal').classList.add('show');
        }

        function closeRateModal() {
            document.getElementById('rateModal').classList.remove('show');
            modalRateInfo = null;
            customQuoteMode = false;
            rateModalTarget = null;
            
            // Reset all fields
            document.getElementById('modalDestination').value = '';
            document.getElementById('modalContainerType').value = '';
            document.getElementById('modalSteamshipLine').value = '';
            document.getElementById('modalSteamshipLine').disabled = false;
            document.getElementById('modalRailRamp').value = '';
            document.getElementById('customQuoteDelivery').value = '';
            document.getElementById('customQuoteContainerType').value = '';
            document.getElementById('customQuoteShipmentLine').value = '';
            document.getElementById('customAmount').value = '';

            // Reset field visibility
            const destinationGroup = document.getElementById('modalDestinationLabel').closest('.modal-form-group');
            const containerGroup = document.getElementById('containerTypeGroup');
            const steamshipGroup = document.getElementById('steamshipLineGroup');
            const railRampGroup = document.getElementById('railRampGroup');
            if (destinationGroup) destinationGroup.style.display = 'block';
            if (containerGroup) containerGroup.style.display = 'block';
            if (steamshipGroup) steamshipGroup.style.display = 'block';
            if (railRampGroup) railRampGroup.style.display = 'none';
            document.getElementById('customQuoteSection').style.display = 'none';
        }

        // Steamship line only matters for 40' Standard/HC import containers —
        // 20'/45' and NOR/Reefer don't carry the surcharge, so grey it out.
        function updateSteamshipLineAvailability() {
            const containerType = document.getElementById('modalContainerType').value;
            const steamshipSelect = document.getElementById('modalSteamshipLine');
            const noSteamshipNeeded = (containerType === '20_45' || containerType === 'NOR_REEFER');

            steamshipSelect.disabled = noSteamshipNeeded;
            if (noSteamshipNeeded) {
                steamshipSelect.value = '';
            }
        }

        function toggleCustomQuote() {
            const section = document.getElementById('customQuoteSection');
            const destinationGroup = document.getElementById('modalDestinationLabel').closest('.modal-form-group');
            const containerGroup = document.getElementById('containerTypeGroup');
            const steamshipGroup = document.getElementById('steamshipLineGroup');
            const customDeliveryLabel = document.querySelector('#customQuoteSection .modal-form-group:first-child label');
            
            customQuoteMode = section.style.display === 'none';
            section.style.display = customQuoteMode ? 'block' : 'none';
            
            // Hide original fields when Custom Quote is active
            if (destinationGroup) destinationGroup.style.display = customQuoteMode ? 'none' : 'block';
            if (containerGroup) containerGroup.style.display = customQuoteMode ? 'none' : 'block';
            if (steamshipGroup) steamshipGroup.style.display = customQuoteMode ? 'none' : 'block';
            
            // Change label based on mode
            if (customDeliveryLabel) {
                if (getModalMode() === 'export' || getModalMode() === 'railExport') {
                    customDeliveryLabel.textContent = 'Pickup Location (Optional)';
                } else {
                    customDeliveryLabel.textContent = 'Delivery Location (Optional)';
                }
            }
            
            // Clear original fields when entering custom quote mode
            if (customQuoteMode) {
                document.getElementById('modalDestination').value = '';
                document.getElementById('modalContainerType').value = '';
                document.getElementById('modalSteamshipLine').value = '';
            } else {
                // Clear custom quote fields when exiting
                document.getElementById('customQuoteDelivery').value = '';
                document.getElementById('customQuoteContainerType').value = '';
                document.getElementById('customQuoteShipmentLine').value = '';
                document.getElementById('customAmount').value = '';
            }
        }

        function setupDestinationAutocomplete() {
            const input = document.getElementById('modalDestination');
            input.onInput_handler = function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('modalAutocompleteList');
                
                if (value.length === 0 || !rateData.import) {
                    list.style.display = 'none';
                    return;
                }
                
                const filtered = rateData.import.rates.filter(d => 
                    d.destination.toLowerCase().includes(value)
                );
                
                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }
                
                list.innerHTML = filtered.map(dest => `
                    <div class="autocomplete-item" onclick="selectModalDestination('${dest.destination}')">${dest.destination}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.removeEventListener('input', input.onInput_handler);
            input.addEventListener('input', input.onInput_handler);
        }

        function selectModalDestination(dest) {
            document.getElementById('modalDestination').value = dest;
            document.getElementById('modalAutocompleteList').style.display = 'none';
        }

        function setupRailDestinationAutocomplete() {
            const input = document.getElementById('modalDestination');
            input.onInput_handler = function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('modalAutocompleteList');
                if (value.length === 0 || !rateData.importRail || !rateData.importRail.rates) {
                    list.style.display = 'none';
                    return;
                }
                const filtered = rateData.importRail.rates.filter(d =>
                    d.destination.toLowerCase().includes(value)
                );
                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }
                list.innerHTML = filtered.map(dest => `
                    <div class="autocomplete-item" onclick="selectModalDestination('${dest.destination}')">${dest.destination}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.removeEventListener('input', input.onInput_handler);
            input.addEventListener('input', input.onInput_handler);
        }

        function setupExportDestinationAutocomplete() {
            const input = document.getElementById('modalDestination');
            input.onInput_handler = function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('modalAutocompleteList');
                
                if (value.length === 0 || !rateData.export) {
                    list.style.display = 'none';
                    return;
                }
                
                const filtered = rateData.export.rates.filter(d => 
                    d.destination.toLowerCase().includes(value)
                );
                
                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }
                
                list.innerHTML = filtered.map(dest => `
                    <div class="autocomplete-item" onclick="selectModalDestination('${dest.destination}')">${dest.destination}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.removeEventListener('input', input.onInput_handler);
            input.addEventListener('input', input.onInput_handler);
        }

        function setupRailExportDestinationAutocomplete() {
            const input = document.getElementById('modalDestination');
            input.onInput_handler = function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('modalAutocompleteList');
                
                if (value.length === 0 || !rateData.exportRail) {
                    list.style.display = 'none';
                    return;
                }
                
                const filtered = rateData.exportRail.rates.filter(d =>
                    d.destination.toLowerCase().includes(value)
                );

                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }

                list.innerHTML = filtered.map(dest => `
                    <div class="autocomplete-item" onclick="selectModalDestination('${dest.destination}')">${dest.destination}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.removeEventListener('input', input.onInput_handler);
            input.addEventListener('input', input.onInput_handler);
        }

        function setupRailRampExportDestinationAutocomplete() {
            const input = document.getElementById('modalDestination');
            input.onInput_handler = function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('modalAutocompleteList');

                if (value.length === 0 || !rateData.railRampExport) {
                    list.style.display = 'none';
                    return;
                }

                const filtered = rateData.railRampExport.rates.filter(d =>
                    d.pickupLocation.toLowerCase().includes(value)
                );

                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }

                list.innerHTML = filtered.map(dest => `
                    <div class="autocomplete-item" onclick="selectModalDestination('${dest.pickupLocation}')">${dest.pickupLocation}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.removeEventListener('input', input.onInput_handler);
            input.addEventListener('input', input.onInput_handler);
        }

        function setupLocalDestinationAutocomplete() {
            const input = document.getElementById('modalDestination');
            input.onInput_handler = function(e) {
                const value = e.target.value.toLowerCase();
                const list = document.getElementById('modalAutocompleteList');
                
                if (value.length === 0 || !rateData.local) {
                    list.style.display = 'none';
                    return;
                }
                
                const filtered = rateData.local.rates.filter(d => 
                    d.destination.toLowerCase().includes(value)
                );
                
                if (filtered.length === 0) {
                    list.style.display = 'none';
                    return;
                }
                
                list.innerHTML = filtered.map(dest => `
                    <div class="autocomplete-item" onclick="selectModalDestination('${dest.destination}')">${dest.destination}</div>
                `).join('');
                list.style.display = 'block';
            };
            input.removeEventListener('input', input.onInput_handler);
            input.addEventListener('input', input.onInput_handler);
        }

        function lookupModalRate() {
            // Handle Custom Quote mode
            if (customQuoteMode) {
                modalRateInfo = {
                    baseRate: 0,
                    fuelSurcharge: 0,
                    totalRate: 0,
                    destination: 'Custom Quote'
                };
                
                const resultHTML = `
                    <strong>Custom Quote Mode</strong><br>
                    Enter a dollar amount below to add to the transport rate<br>
                    <small style="color: #666; margin-top: 10px; display: block;">No rates required - just add your custom amount</small>
                `;
                
                document.getElementById('modalRateResultContent').innerHTML = resultHTML;
                document.getElementById('modalRateResult').classList.add('show');
                return;
            }
            
            const destination = document.getElementById('modalDestination').value;
            const modalMode = getModalMode();
            console.log('lookupModalRate called. Mode:', modalMode, 'Destination:', destination);
            console.log('rateData:', rateData);
            
            if (modalMode === 'export') {
                // Export mode - simpler lookup with flexible matching
                if (!destination) {
                    alert('Please select a destination');
                    return;
                }
                
                if (!rateData.export || !rateData.export.rates) {
                    alert('No export rates loaded. Please open Rate Manager first.');
                    return;
                }
                
                // Try exact match first (case-insensitive)
                let exportRate = rateData.export.rates.find(r => 
                    r.destination.toLowerCase() === destination.toLowerCase()
                );
                
                // If no exact match, try partial match
                if (!exportRate) {
                    exportRate = rateData.export.rates.find(r => 
                        r.destination.toLowerCase().includes(destination.toLowerCase()) ||
                        destination.toLowerCase().includes(r.destination.toLowerCase())
                    );
                }
                
                if (!exportRate) {
                    // Log available destinations for debugging
                    const availableDests = rateData.export.rates.map(r => r.destination).join(', ');
                    console.log('Available EXPORT destinations:', availableDests);
                    alert('Destination not found. Available: ' + availableDests);
                    return;
                }
                
                modalRateInfo = {
                    baseRate: exportRate.baseRate,
                    fuelSurcharge: exportRate.fuelSurcharge,
                    totalRate: exportRate.totalRate,
                    destination: destination
                };
                
                // Auto-populate From field in Route Details (skip when loading into a lane)
                if (rateModalTarget === null) {
                // Find the matching city in EXPORT_DESTINATIONS and use that value
                const fromField = document.getElementById('fromLocation');
                console.log('🔍 Trying to auto-populate fromLocation');
                console.log('   Destination searched:', destination);
                console.log('   Available EXPORT cities:', EXPORT_DESTINATIONS.map(d => d.city));
                
                const matchingDest = EXPORT_DESTINATIONS.find(d => 
                    d.city.toLowerCase() === destination.toLowerCase() ||
                    d.city.toLowerCase().includes(destination.toLowerCase()) ||
                    destination.toLowerCase().includes(d.city.toLowerCase())
                );
                
                if (matchingDest) {
                    console.log('   ✅ Match found:', matchingDest.city);
                    fromField.value = matchingDest.city;
                    // Trigger change event
                    fromField.dispatchEvent(new Event('change', { bubbles: true }));
                    generateQuote();
                } else {
                    console.log('   ❌ No match found for:', destination);
                    console.log('   Trying direct destination set...');
                    fromField.value = destination;
                    fromField.dispatchEvent(new Event('change', { bubbles: true }));
                    generateQuote();
                }
                }
                
                const resultHTML = `
                    <strong>${exportRate.destination}</strong><br>
                    Base Rate: $${parseFloat(exportRate.baseRate).toFixed(2)}<br>
                    Fuel Surcharge: ${exportRate.fuelSurcharge}%<br>
                    <strong>Total Rate: $${parseFloat(exportRate.totalRate).toFixed(2)}</strong>
                `;
                
                document.getElementById('modalRateResultContent').innerHTML = resultHTML;
                document.getElementById('modalRateResult').classList.add('show');
                return;
            }
            
            if (modalMode === 'railExport') {
                // Rail Export mode - mirror Export lookup, sourced from rateData.exportRail
                if (!destination) {
                    alert('Please select a pick up location');
                    return;
                }
                
                if (!rateData.exportRail || !rateData.exportRail.rates) {
                    alert('No rail export rates loaded. Please open Rate Manager first.');
                    return;
                }
                
                let railRate = rateData.exportRail.rates.find(r => 
                    r.destination.toLowerCase() === destination.toLowerCase()
                );
                if (!railRate) {
                    railRate = rateData.exportRail.rates.find(r => 
                        r.destination.toLowerCase().includes(destination.toLowerCase()) ||
                        destination.toLowerCase().includes(r.destination.toLowerCase())
                    );
                }
                
                if (!railRate) {
                    const availableDests = rateData.exportRail.rates.map(r => r.destination).join(', ');
                    alert('Pick up location not found. Available: ' + availableDests);
                    return;
                }
                
                modalRateInfo = {
                    baseRate: railRate.baseRate,
                    fuelSurcharge: railRate.fuelSurcharge,
                    totalRate: railRate.totalRate,
                    destination: destination
                };
                
                // Auto-populate From field in Route Details (skip when loading into a lane)
                if (rateModalTarget === null) {
                    const fromField = document.getElementById('fromLocation');
                    const matchingDest = RAIL_EXPORT_DESTINATIONS.find(d => 
                        d.city.toLowerCase() === destination.toLowerCase() ||
                        d.city.toLowerCase().includes(destination.toLowerCase()) ||
                        destination.toLowerCase().includes(d.city.toLowerCase())
                    );
                    if (matchingDest) {
                        fromField.value = matchingDest.city;
                    } else {
                        fromField.value = destination;
                    }
                    fromField.dispatchEvent(new Event('change', { bubbles: true }));
                    generateQuote();
                }
                
                const resultHTML = `
                    <strong>${railRate.destination}</strong><br>
                    Base Rate: $${parseFloat(railRate.baseRate).toFixed(2)}<br>
                    Fuel Surcharge: ${railRate.fuelSurcharge}%<br>
                    <strong>Total Rate: $${parseFloat(railRate.totalRate).toFixed(2)}</strong>
                `;
                
                document.getElementById('modalRateResultContent').innerHTML = resultHTML;
                document.getElementById('modalRateResult').classList.add('show');
                return;
            }

            if (modalMode === 'railRampExport') {
                // Rail Ramp Export mode - pickup + a chosen rail ramp together determine the rate
                if (!destination) {
                    alert('Please select a pick up location');
                    return;
                }

                const ramp = document.getElementById('modalRailRamp').value;
                if (!ramp) {
                    alert('Please select a rail ramp');
                    return;
                }

                if (!rateData.railRampExport || !rateData.railRampExport.rates) {
                    alert('No rail ramp export rates loaded. Please open Rate Manager first.');
                    return;
                }

                let pickupRow = rateData.railRampExport.rates.find(r =>
                    r.pickupLocation.toLowerCase() === destination.toLowerCase()
                );
                if (!pickupRow) {
                    pickupRow = rateData.railRampExport.rates.find(r =>
                        r.pickupLocation.toLowerCase().includes(destination.toLowerCase()) ||
                        destination.toLowerCase().includes(r.pickupLocation.toLowerCase())
                    );
                }

                if (!pickupRow) {
                    const availablePickups = rateData.railRampExport.rates.map(r => r.pickupLocation).join(', ');
                    alert('Pick up location not found. Available: ' + availablePickups);
                    return;
                }

                const rampField = RAIL_RAMPS[ramp];
                const rampRate = pickupRow[rampField];
                if (!rampRate) {
                    alert(ramp + ' does not serve ' + pickupRow.pickupLocation + '. Try a different ramp.');
                    return;
                }

                modalRateInfo = {
                    baseRate: rampRate,
                    fuelSurcharge: pickupRow.fuelSurcharge,
                    totalRate: (rampRate * (1 + pickupRow.fuelSurcharge / 100)).toFixed(2),
                    destination: pickupRow.pickupLocation,
                    ramp: ramp
                };

                const resultHTML = `
                    <strong>${pickupRow.pickupLocation} &rarr; ${ramp}</strong><br>
                    Base Rate: $${parseFloat(rampRate).toFixed(2)}<br>
                    Fuel Surcharge: ${pickupRow.fuelSurcharge}%<br>
                    <strong>Total Rate: $${parseFloat(modalRateInfo.totalRate).toFixed(2)}</strong>
                `;

                document.getElementById('modalRateResultContent').innerHTML = resultHTML;
                document.getElementById('modalRateResult').classList.add('show');
                return;
            }

            if (modalMode === 'local') {
                // Local mode - requires destination but not containerType/steamshipLine
                if (!destination) {
                    alert('Please select a destination');
                    return;
                }
                
                if (!rateData.local) {
                    alert('No local rates loaded. Please open Rate Manager first.');
                    return;
                }
                
                // Try exact match first (case-insensitive)
                let localRate = rateData.local.rates.find(r => 
                    r.destination.toLowerCase() === destination.toLowerCase()
                );
                
                // If no exact match, try partial match
                if (!localRate) {
                    localRate = rateData.local.rates.find(r => 
                        r.destination.toLowerCase().includes(destination.toLowerCase()) ||
                        destination.toLowerCase().includes(r.destination.toLowerCase())
                    );
                }
                
                if (!localRate) {
                    // Log available destinations for debugging
                    const availableDests = rateData.local.rates.map(r => r.destination).join(', ');
                    console.log('Available LOCAL destinations:', availableDests);
                    alert('Destination not found. Available: ' + availableDests);
                    return;
                }
                
                modalRateInfo = {
                    baseRate: parseFloat(localRate.baseRate) || 0,
                    fuelSurcharge: parseFloat(localRate.fuelSurcharge) || 0,
                    totalRate: parseFloat(localRate.totalRate) || 0,
                    destination: destination,
                    containerType: document.getElementById('modalContainerType').value
                };
                
                // Auto-populate delivery location in Route Details (LOCAL uses toLocation)
                // Find the matching destination in LOCAL rates
                const matchingLocal = (rateData.local && rateData.local.rates) ? 
                    rateData.local.rates.find(r => 
                        r.destination.toLowerCase() === destination.toLowerCase() ||
                        r.destination.toLowerCase().includes(destination.toLowerCase()) ||
                        destination.toLowerCase().includes(r.destination.toLowerCase())
                    ) : null;
                if (matchingLocal && rateModalTarget === null) {
                    document.getElementById('toLocation').value = matchingLocal.destination;
                }
                
                const resultHTML = `
                    <strong>${destination}</strong><br>
                    Base Rate: $${modalRateInfo.baseRate.toFixed(2)}<br>
                    Fuel Surcharge: ${modalRateInfo.fuelSurcharge}%<br>
                    <strong>Total Rate: $${modalRateInfo.totalRate.toFixed(2)}</strong>
                `;
                
                document.getElementById('modalRateResultContent').innerHTML = resultHTML;
                document.getElementById('modalRateResult').classList.add('show');
                return;
            }
            
            if (modalMode === 'rail') {
                // Import Rail - requires containerType (40_45 or 20) and steamshipLine
                const containerType = document.getElementById('modalContainerType').value;
                const steamshipLine = document.getElementById('modalSteamshipLine').value;
                if (!destination || !containerType || !steamshipLine) {
                    alert('Please fill in all fields');
                    return;
                }
                if (!rateData.importRail || !rateData.importRail.rates) {
                    alert('No rail rates loaded. Please open Rate Manager first.');
                    return;
                }
                const rateRow = rateData.importRail.rates.find(r => r.destination === destination);
                if (!rateRow) {
                    alert('Destination not found');
                    return;
                }
                let baseRate = rateRow[containerType];
                if (steamshipLine === 'other') {
                    baseRate += 480;
                }
                const fscAmount = baseRate * rateData.fsc;
                const rateWithFSC = baseRate + fscAmount;
                modalRateInfo = {
                    destination,
                    containerType,
                    steamshipLine,
                    baseRate,
                    fsc: rateData.fsc,
                    fscAmount,
                    rateWithFSC
                };
                displayModalRateResult();
                return;
            }

            // Import mode - requires containerType; steamshipLine only applies to 40' Standard/HC
            const containerType = document.getElementById('modalContainerType').value;
            const steamshipLine = document.getElementById('modalSteamshipLine').value;
            const steamshipRequired = containerType === '40ST_HC';

            if (!destination || !containerType || (steamshipRequired && !steamshipLine)) {
                alert('Please fill in all fields');
                return;
            }

            if (!rateData.import) {
                alert('No rates loaded. Please open Rate Manager first.');
                return;
            }
            
            const rateRow = rateData.import.rates.find(r => r.destination === destination);
            if (!rateRow) {
                alert('Destination not found');
                return;
            }
            
            let baseRate = rateRow[containerType];
            
            if (steamshipLine === 'other') {
                baseRate += 480;
            }
            
            const fscAmount = baseRate * rateData.fsc;
            const rateWithFSC = baseRate + fscAmount;
            
            modalRateInfo = {
                destination,
                containerType,
                steamshipLine,
                baseRate,
                fsc: rateData.fsc,
                fscAmount,
                rateWithFSC
            };
            
            displayModalRateResult();
        }

        function displayModalRateResult() {
            if (!modalRateInfo) return;
            
            const html = `
                <div class="rate-result-row">
                    <span class="rate-result-label">Base Rate</span>
                    <span class="rate-result-value">$${modalRateInfo.baseRate.toFixed(2)}</span>
                </div>
                <div class="rate-result-row">
                    <span class="rate-result-label">Fuel Surcharge (${(modalRateInfo.fsc * 100).toFixed(0)}%)</span>
                    <span class="rate-result-value">$${modalRateInfo.fscAmount.toFixed(2)}</span>
                </div>
                <div class="rate-result-row" style="border-top: 1px solid #ddd; padding-top: 8px; font-weight: bold;">
                    <span class="rate-result-label">Total</span>
                    <span class="rate-result-value">$${modalRateInfo.rateWithFSC.toFixed(2)}</span>
                </div>
            `;
            
            document.getElementById('modalRateResultContent').innerHTML = html;
            document.getElementById('modalRateResult').classList.add('show');
        }

        function applyModalRateCore() {
            if (!modalRateInfo) return;
            
            // Get custom amount if provided
            const customAmountInput = document.getElementById('customAmount');
            const customAmount = customAmountInput.value ? parseFloat(customAmountInput.value) : 0;
            
            // Get custom location if in custom quote mode
            const customLocation = customQuoteMode ? document.getElementById('customQuoteDelivery').value : '';
            
            console.log('🔍 applyModalRate Debug:');
            console.log('   currentMode:', currentMode);
            console.log('   customQuoteMode:', customQuoteMode);
            console.log('   customLocation:', customLocation);
            
            const modalMode = getModalMode();
            if (modalMode === 'export' || modalMode === 'railExport') {
                console.log('   ✅ EXPORT/RAIL EXPORT mode detected');
                console.log('   customQuoteDelivery value:', document.getElementById('customQuoteDelivery').value);
                
                // Export mode - update FROM location and rates
                const customLocField = document.getElementById('customQuoteDelivery');
                const fromLocField = document.getElementById('fromLocation');
                if (customQuoteMode) {
                    const customLoc = customLocField ? customLocField.value : '';
                    console.log('   ✅ Custom Quote Mode - customLoc:', customLoc);
                    if (customLoc) {
                        console.log('   ✅ Setting fromLocation to:', customLoc);
                        // Check if this value exists in the dropdown
                        let optionExists = false;
                        for (let i = 0; i < fromLocField.options.length; i++) {
                            if (fromLocField.options[i].value === customLoc) {
                                optionExists = true;
                                break;
                            }
                        }
                        // If option doesn't exist, add it
                        if (!optionExists) {
                            const newOption = document.createElement('option');
                            newOption.value = customLoc;
                            newOption.text = customLoc + ' (Custom)';
                            fromLocField.appendChild(newOption);
                            console.log('   Added custom option to dropdown');
                        }
                        // Now set the value
                        fromLocField.value = customLoc;
                        console.log('   fromLocation value set to:', fromLocField.value);
                    }
                } else if (modalRateInfo.destination && modalRateInfo.destination !== 'Custom Quote') {
                    console.log('   Setting fromLocation from rate lookup:', modalRateInfo.destination);
                    fromLocField.value = modalRateInfo.destination;
                }
                const transportRate = parseFloat(modalRateInfo.baseRate) + customAmount;
                document.getElementById('transportRate').value = transportRate.toFixed(2);
                const fuelSurcharge = customQuoteMode ? 57 : parseFloat(modalRateInfo.fuelSurcharge);
                console.log('   Setting fuel surcharge to:', fuelSurcharge);
                document.getElementById('fuelSurcharge').value = fuelSurcharge;
            } else if (modalMode === 'railRampExport') {
                // Rail Ramp Export mode - update pickup (From) and ramp (To) together
                const customLocField = document.getElementById('customQuoteDelivery');
                const fromLocField = document.getElementById('fromLocation');
                if (customQuoteMode) {
                    const customLoc = customLocField ? customLocField.value : '';
                    if (customLoc) {
                        let optionExists = false;
                        for (let i = 0; i < fromLocField.options.length; i++) {
                            if (fromLocField.options[i].value === customLoc) {
                                optionExists = true;
                                break;
                            }
                        }
                        if (!optionExists) {
                            const newOption = document.createElement('option');
                            newOption.value = customLoc;
                            newOption.text = customLoc + ' (Custom)';
                            fromLocField.appendChild(newOption);
                        }
                        fromLocField.value = customLoc;
                    }
                } else if (modalRateInfo.destination && modalRateInfo.destination !== 'Custom Quote') {
                    fromLocField.value = modalRateInfo.destination;
                }
                document.getElementById('toLocation').value = document.getElementById('modalRailRamp').value;
                const transportRate = parseFloat(modalRateInfo.baseRate) + customAmount;
                document.getElementById('transportRate').value = transportRate.toFixed(2);
                document.getElementById('fuelSurcharge').value = customQuoteMode ? 57 : parseFloat(modalRateInfo.fuelSurcharge);
            } else if (modalMode === 'local') {
                // Local mode - update TO location and rates
                const customLocField = document.getElementById('customQuoteDelivery');
                if (customQuoteMode) {
                    const customLoc = customLocField ? customLocField.value : '';
                    if (customLoc) {
                        document.getElementById('toLocation').value = customLoc;
                    }
                } else if (modalRateInfo.destination && modalRateInfo.destination !== 'Custom Quote') {
                    document.getElementById('toLocation').value = modalRateInfo.destination;
                }
                const transportRate = parseFloat(modalRateInfo.baseRate) + customAmount;
                document.getElementById('transportRate').value = transportRate.toFixed(2);
                // Use 57% for custom quote mode, otherwise use the loaded rate's FSC
                const fuelSurcharge = customQuoteMode ? 57 : parseFloat(modalRateInfo.fuelSurcharge);
                document.getElementById('fuelSurcharge').value = fuelSurcharge;
                document.getElementById('importContainerType').value = customQuoteMode ? '' : (modalRateInfo.containerType || '');

                // Set chassis fee based on destination
                const chassisRateField = document.getElementById('chassisRate');
                const chassisToggleBtn = document.getElementById('chassisToggleBtn');
                
                if (modalRateInfo.destination === 'Albuquerque, NM / Belen, NM / El Paso, TX') {
                    // Albuquerque/Belen/El Paso = $195 chassis fee
                    chassisRateField.value = '195.00';
                } else {
                    // All other LOCAL destinations = $50 chassis fee
                    chassisRateField.value = '50.00';
                }
                
                // Always turn ON chassis fee for LOCAL mode
                chassisToggleBtn.classList.add('active');
                chassisToggleBtn.textContent = 'ON';
            } else {
                // Import mode - update TO location and rates
                const customLocField = document.getElementById('customQuoteDelivery');
                if (customQuoteMode) {
                    const customLoc = customLocField ? customLocField.value : '';
                    if (customLoc) {
                        document.getElementById('toLocation').value = customLoc;
                    }
                } else if (modalRateInfo.destination && modalRateInfo.destination !== 'Custom Quote') {
                    document.getElementById('toLocation').value = modalRateInfo.destination;
                }
                const transportRate = parseFloat(modalRateInfo.baseRate) + customAmount;
                document.getElementById('transportRate').value = transportRate.toFixed(2);
                // Use 57% for custom quote mode, otherwise use the loaded rate's FSC
                const fuelSurcharge = customQuoteMode ? 57 : (parseFloat(modalRateInfo.fsc) * 100);
                document.getElementById('fuelSurcharge').value = fuelSurcharge.toFixed(1);
                document.getElementById('importSteamshipLine').value = customQuoteMode ? '' : (modalRateInfo.steamshipLine || '');
                document.getElementById('importContainerType').value = customQuoteMode ? '' : (modalRateInfo.containerType || '');
                applyImportChassisForDestination();
            }
            
            // Clear custom amount after applying
            customAmountInput.value = '';
            document.getElementById('customQuoteSection').style.display = 'none';
        }

        // Snapshot of the main-form fields that a rate load can touch
        function grabMainRateFields() {
            const chassisBtn = document.getElementById('chassisToggleBtn');
            return {
                fromLocation: document.getElementById('fromLocation').value,
                toLocation: document.getElementById('toLocation').value,
                transportRate: document.getElementById('transportRate').value,
                fuelSurcharge: document.getElementById('fuelSurcharge').value,
                chassisRate: document.getElementById('chassisRate').value,
                chassisActive: chassisBtn.classList.contains('active'),
                chassisText: chassisBtn.textContent,
                steamshipLine: document.getElementById('importSteamshipLine').value,
                containerType: document.getElementById('importContainerType').value
            };
        }

        function setMainRateFields(s) {
            document.getElementById('fromLocation').value = s.fromLocation;
            document.getElementById('toLocation').value = s.toLocation;
            document.getElementById('transportRate').value = s.transportRate;
            document.getElementById('fuelSurcharge').value = s.fuelSurcharge;
            document.getElementById('chassisRate').value = s.chassisRate;
            const chassisBtn = document.getElementById('chassisToggleBtn');
            chassisBtn.classList.toggle('active', s.chassisActive);
            chassisBtn.textContent = s.chassisText;
            document.getElementById('importSteamshipLine').value = s.steamshipLine;
            document.getElementById('importContainerType').value = s.containerType;
        }

        // Copy the values a rate load produced into a specific lane's fields
        function setLaneFromRateFields(id, vals) {
            const mode = getModalMode();
            // Location: prefer the location the user actually picked in the modal,
            // since the main From/To fields may not hold it for a cross-mode lane.
            let loc = '';
            if (customQuoteMode) {
                loc = document.getElementById('customQuoteDelivery').value || '';
            } else if (modalRateInfo && modalRateInfo.destination && modalRateInfo.destination !== 'Custom Quote') {
                loc = modalRateInfo.destination;
            } else {
                loc = (mode === 'export' || mode === 'railExport' || mode === 'railRampExport') ? vals.fromLocation : vals.toLocation;
            }
            const locEl = document.getElementById('laneLocation-' + id);
            if (locEl && loc) locEl.value = loc;
            if (mode === 'railRampExport') {
                const rampEl = document.getElementById('laneRamp-' + id);
                if (rampEl) rampEl.value = (modalRateInfo && modalRateInfo.ramp) ? modalRateInfo.ramp : vals.toLocation;
            }
            const tEl = document.getElementById('laneTransport-' + id);
            const fEl = document.getElementById('laneFuel-' + id);
            if (tEl) tEl.value = vals.transportRate;
            if (fEl) fEl.value = vals.fuelSurcharge;
            // Chassis is only derived from the rate lookup in LOCAL mode
            if (mode === 'local') {
                const cEl = document.getElementById('laneChassis-' + id);
                if (cEl) cEl.value = vals.chassisRate;
            }
            const ssEl = document.getElementById('laneSteamship-' + id);
            if (ssEl) ssEl.value = (mode === 'import' || mode === 'rail') ? vals.steamshipLine : '';
            const ctEl = document.getElementById('laneContainerType-' + id);
            if (ctEl) ctEl.value = (mode === 'import' || mode === 'rail' || mode === 'local') ? vals.containerType : '';
        }

        // Public entry: routes the loaded rate to the main form or a lane
        function applyModalRate() {
            if (!modalRateInfo) return;
            const target = rateModalTarget;

            if (target !== null && document.getElementById('laneLocation-' + target)) {
                // Load into a lane without disturbing the main form
                const snap = grabMainRateFields();
                applyModalRateCore();
                const vals = grabMainRateFields();
                setMainRateFields(snap);
                setLaneFromRateFields(target, vals);
            } else {
                applyModalRateCore();
            }

            closeRateModal();
            generateQuote();
        }

        // Close modal when clicking outside
        window.onclick = function(event) {
            const modal = document.getElementById('rateModal');
            if (event.target == modal) {
                closeRateModal();
            }
        }

        function addCustomField() {
            const name = document.getElementById('customFieldName').value.trim();
            const value = document.getElementById('customFieldValue').value.trim();
            
            if (name && value) {
                customFields.push({ name, value });
                document.getElementById('customFieldName').value = '';
                document.getElementById('customFieldValue').value = '';
                renderCustomFields();
                generateQuote();
            }
        }

        function removeCustomField(index) {
            customFields.splice(index, 1);
            renderCustomFields();
            generateQuote();
        }

        function renderCustomFields() {
            const container = document.getElementById('customFieldsList');
            
            if (customFields.length === 0) {
                container.style.display = 'none';
                container.innerHTML = '';
                return;
            }

            container.style.display = 'block';
            container.innerHTML = customFields.map((field, index) => `
                <div class="custom-field-item">
                    <span class="custom-field-label">${field.name}:</span>
                    <span class="custom-field-value">${field.value}</span>
                    <button class="btn-remove-field" onclick="removeCustomField(${index})">Remove</button>
                </div>
            `).join('');
        }

        function buildExportQuote(customerName, overrides, showNotesFooter) {
            const o = overrides || null;
            const showNF = showNotesFooter !== false;
            const fromCity = o ? (o.location || '') : document.getElementById('fromLocation').value;
            const toLocation = 'Port of Los Angeles/Long Beach';
            const transportRate = (parseFloat(o ? o.transportRate : document.getElementById('transportRate').value) || 0).toFixed(2);
            const fuelSurcharge = (parseFloat(o ? o.fuelSurcharge : document.getElementById('fuelSurcharge').value) || 0).toFixed(1);
            const chassisRate = (parseFloat((o ? o.chassisRate : document.getElementById('chassisRate').value) || '0') || 0).toFixed(2);
            const tankerSurchargeValue = surchargeVal(o, 'tanker', 'tankerSurcharge');
            const hazmatSurchargeValue = surchargeVal(o, 'hazmat', 'hazmatSurcharge');
            const triaxleSurchargeValue = surchargeVal(o, 'triaxle', 'triaxleSurcharge');
            
            // Check if this location has drop/pick free
            const exportRate = (rateData.export && rateData.export.rates) ? rateData.export.rates.find(r => r.destination === fromCity) : null;
            const hasDropPickFree = exportRate && exportRate.dropPickFree;
            const laneFreeStorage = exportRate ? !!exportRate.freeStorage : true;
            
            // Calculate totals for export
            const transportRateNum = parseFloat(transportRate);
            const fuelSurchargeNum = parseFloat(fuelSurcharge) / 100;
            const fuelSurchargeAmount = transportRateNum * fuelSurchargeNum;
            const chassisRateNum = parseFloat(chassisRate);
            const tankerNum = tankerSurchargeValue ? parseFloat(tankerSurchargeValue) : 0;
            const hazmatNum = hazmatSurchargeValue ? parseFloat(hazmatSurchargeValue) : 0;
            const triaxleNum = triaxleSurchargeValue ? parseFloat(triaxleSurchargeValue) : 0;
            const residentialValue = surchargeVal(o, 'residential', 'residentialDelivery');
            const residentialNum = residentialValue ? parseFloat(residentialValue) : 0;
            const reeferSurchargeValue = surchargeVal(o, 'reefer', 'reeferSurcharge');
            const reeferNum = reeferSurchargeValue ? parseFloat(reeferSurchargeValue) : 0;
            const gensetSurchargeValue = surchargeVal(o, 'genset', 'gensetSurcharge');
            const gensetNum = gensetSurchargeValue ? parseFloat(gensetSurchargeValue) : 0;
            const scaleTicketValue = surchargeVal(o, 'scaleTicket', 'scaleTicketFee');
            const scaleTicketNum = scaleTicketValue ? parseFloat(scaleTicketValue) : 0;
            const totalExportCost = (transportRateNum + fuelSurchargeAmount + chassisRateNum + tankerNum + hazmatNum + triaxleNum + residentialNum + reeferNum + gensetNum + scaleTicketNum).toFixed(2);
            
            const quoteHTML = `
                <div class="quote-header">
                    <div class="quote-title">DSL LOGISTICS</div>
                </div>
                
                <div class="divider">&nbsp;</div>
                
                <div class="quote-heading-container">
                    <p class="quote-heading-title">EXPORT SHIPMENT</p>
                    <p class="quote-heading-customer">${customerName}</p>
                </div>
                
                <div class="route-info">
                    <div class="route-from-to">${fromCity.toUpperCase()} &rarr; ${toLocation.toUpperCase()}</div>
                    <div class="route-type">Empty Container Return to LA/LB</div>
                </div>
                
                <table class="quote-table">
                    <thead>
                        <tr>
                            <th>Service</th>
                            <th>Rate</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Base Rate</td>
                            <td>$${transportRate}</td>
                        </tr>
                        <tr>
                            <td>Fuel Surcharge <span class="service-desc">(weekly review)</span></td>
                            <td>${fuelSurcharge}%</td>
                        </tr>
                        ${chassisRateNum > 0 ? `
                        <tr>
                            <td>Chassis Fee <span class="service-desc">(flat, not daily)</span></td>
                            <td>$${chassisRate}</td>
                        </tr>
                        ` : ''}
                        ${tankerSurchargeValue ? `
                        <tr>
                            <td>Tanker Surcharge</td>
                            <td>$${tankerSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${hazmatSurchargeValue ? `
                        <tr>
                            <td>Hazmat</td>
                            <td>$${hazmatSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${triaxleSurchargeValue ? `
                        <tr>
                            <td>Triaxle Surcharge</td>
                            <td>$${triaxleSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${residentialValue ? `
                        <tr>
                            <td>Residential Delivery</td>
                            <td>$${residentialValue}</td>
                        </tr>
                        ` : ''}
                        ${reeferSurchargeValue ? `
                        <tr>
                            <td>Reefer</td>
                            <td>$${reeferSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${gensetSurchargeValue ? `
                        <tr>
                            <td>GenSet</td>
                            <td>$${gensetSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${scaleTicketValue ? `
                        <tr>
                            <td>Scale Ticket Fee <span class="service-desc">(light or heavy)</span></td>
                            <td>$${scaleTicketValue}</td>
                        </tr>
                        ` : ''}
                        <tr style="border-top: 2px solid #FFD700; font-weight: bold; background-color: #f9f9f9;">
                            <td>Total Cost of Transportation</td>
                            <td>$${totalExportCost}</td>
                        </tr>
                    </tbody>
                </table>
                
                <div class="services-section">
                    <div class="services-title">INCLUDED SERVICES</div>
                    <div class="services-list">
                        ${[
                            hasDropPickFree ? `Drop/pick in ${fromCity}: Free` : '',
                            laneFreeStorage ? `4 days free storage in Phoenix CY` : '',
                            `No chassis split or pre-pull charges`,
                            `Live Loading in ${fromCity} (2 free hours) – $97.50/hr`,
                            tankerSurchargeValue ? `Tanker Surcharge – $${tankerSurchargeValue}` : '',
                            triaxleSurchargeValue ? `Triaxle Surcharge – $${triaxleSurchargeValue}` : '',
                            hazmatSurchargeValue ? `Hazmat Surcharge – $${hazmatSurchargeValue}` : '',
                            (document.getElementById('maxCargoToggleBtn').classList.contains('active') && document.getElementById('maxCargoWeight').value) ? `Max Cargo Weight: ${document.getElementById('maxCargoWeight').value} lbs` : ''
                        ].filter(Boolean).join(' - ')}
                    </div>
                </div>
                
                ${showNF ? `<p class="note">NOTE: Rates subject to fuel surcharge adjustment.</p>
                <p class="note">NOTE: For 20' dry containers on this lane weighing between 38,000 and 44,000 LBS, a triaxle fee of $150.00 would apply in place of the flat chassis fee.</p>

                <div class="footer">
                    <p class="footer-cta">To place an order, email <a href="mailto:export@dsllog.com">export@dsllog.com</a></p>
                    <p class="footer-text">dsllog.com</p>
                </div>` : ''}
            `;
            
            return quoteHTML;
        }

        function buildRailExportQuote(customerName, overrides, showNotesFooter) {
            const o = overrides || null;
            const showNF = showNotesFooter !== false;
            const fromCity = o ? (o.location || '') : document.getElementById('fromLocation').value;
            const toLocation = 'Port of Los Angeles/Long Beach RAIL';
            const transportRate = (parseFloat(o ? o.transportRate : document.getElementById('transportRate').value) || 0).toFixed(2);
            const fuelSurcharge = (parseFloat(o ? o.fuelSurcharge : document.getElementById('fuelSurcharge').value) || 0).toFixed(1);
            const chassisRate = (parseFloat((o ? o.chassisRate : document.getElementById('chassisRate').value) || '0') || 0).toFixed(2);
            const tankerSurchargeValue = surchargeVal(o, 'tanker', 'tankerSurcharge');
            const hazmatSurchargeValue = surchargeVal(o, 'hazmat', 'hazmatSurcharge');
            const triaxleSurchargeValue = surchargeVal(o, 'triaxle', 'triaxleSurcharge');
            
            // Check if this location has drop/pick free (sourced from Rail Export rates)
            const railRate = (rateData.exportRail && rateData.exportRail.rates) ? rateData.exportRail.rates.find(r => r.destination === fromCity) : null;
            const hasDropPickFree = railRate && railRate.dropPickFree;
            const laneFreeStorage = railRate ? !!railRate.freeStorage : true;
            
            // Calculate totals
            const transportRateNum = parseFloat(transportRate);
            const fuelSurchargeNum = parseFloat(fuelSurcharge) / 100;
            const fuelSurchargeAmount = transportRateNum * fuelSurchargeNum;
            const chassisRateNum = parseFloat(chassisRate);
            const tankerNum = tankerSurchargeValue ? parseFloat(tankerSurchargeValue) : 0;
            const hazmatNum = hazmatSurchargeValue ? parseFloat(hazmatSurchargeValue) : 0;
            const triaxleNum = triaxleSurchargeValue ? parseFloat(triaxleSurchargeValue) : 0;
            const residentialValue = surchargeVal(o, 'residential', 'residentialDelivery');
            const residentialNum = residentialValue ? parseFloat(residentialValue) : 0;
            const reeferSurchargeValue = surchargeVal(o, 'reefer', 'reeferSurcharge');
            const reeferNum = reeferSurchargeValue ? parseFloat(reeferSurchargeValue) : 0;
            const gensetSurchargeValue = surchargeVal(o, 'genset', 'gensetSurcharge');
            const gensetNum = gensetSurchargeValue ? parseFloat(gensetSurchargeValue) : 0;
            const scaleTicketValue = surchargeVal(o, 'scaleTicket', 'scaleTicketFee');
            const scaleTicketNum = scaleTicketValue ? parseFloat(scaleTicketValue) : 0;
            const totalExportCost = (transportRateNum + fuelSurchargeAmount + chassisRateNum + tankerNum + hazmatNum + triaxleNum + residentialNum + reeferNum + gensetNum + scaleTicketNum).toFixed(2);
            
            const quoteHTML = `
                <div class="quote-header">
                    <div class="quote-title">DSL LOGISTICS</div>
                </div>
                
                <div class="divider">&nbsp;</div>
                
                <div class="quote-heading-container">
                    <p class="quote-heading-title">RAIL EXPORT SHIPMENT</p>
                    <p class="quote-heading-customer">${customerName}</p>
                </div>
                
                <div class="route-info">
                    <div class="route-from-to">${fromCity.toUpperCase()} &rarr; ${toLocation.toUpperCase()}</div>
                    <div class="route-type">Export via Rail to LA/LB</div>
                </div>
                
                <table class="quote-table">
                    <thead>
                        <tr>
                            <th>Service</th>
                            <th>Rate</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Base Rate</td>
                            <td>$${transportRate}</td>
                        </tr>
                        <tr>
                            <td>Fuel Surcharge <span class="service-desc">(weekly review)</span></td>
                            <td>${fuelSurcharge}%</td>
                        </tr>
                        ${chassisRateNum > 0 ? `
                        <tr>
                            <td>Chassis Fee <span class="service-desc">(flat, not daily)</span></td>
                            <td>$${chassisRate}</td>
                        </tr>
                        ` : ''}
                        ${tankerSurchargeValue ? `
                        <tr>
                            <td>Tanker Surcharge</td>
                            <td>$${tankerSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${hazmatSurchargeValue ? `
                        <tr>
                            <td>Hazmat</td>
                            <td>$${hazmatSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${triaxleSurchargeValue ? `
                        <tr>
                            <td>Triaxle Surcharge</td>
                            <td>$${triaxleSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${residentialValue ? `
                        <tr>
                            <td>Residential Delivery</td>
                            <td>$${residentialValue}</td>
                        </tr>
                        ` : ''}
                        ${reeferSurchargeValue ? `
                        <tr>
                            <td>Reefer</td>
                            <td>$${reeferSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${gensetSurchargeValue ? `
                        <tr>
                            <td>GenSet</td>
                            <td>$${gensetSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${scaleTicketValue ? `
                        <tr>
                            <td>Scale Ticket Fee <span class="service-desc">(light or heavy)</span></td>
                            <td>$${scaleTicketValue}</td>
                        </tr>
                        ` : ''}
                        <tr style="border-top: 2px solid #FFD700; font-weight: bold; background-color: #f9f9f9;">
                            <td>Total Cost of Transportation</td>
                            <td>$${totalExportCost}</td>
                        </tr>
                    </tbody>
                </table>
                
                <div class="services-section">
                    <div class="services-title">INCLUDED SERVICES</div>
                    <div class="services-list">
                        ${[
                            hasDropPickFree ? `Drop/pick in ${fromCity}: Free` : '',
                            laneFreeStorage ? `4 days free storage in Phoenix CY` : '',
                            `No chassis split or pre-pull charges`,
                            `Live Loading in ${fromCity} (2 free hours) – $97.50/hr`,
                            tankerSurchargeValue ? `Tanker Surcharge – $${tankerSurchargeValue}` : '',
                            triaxleSurchargeValue ? `Triaxle Surcharge – $${triaxleSurchargeValue}` : '',
                            hazmatSurchargeValue ? `Hazmat Surcharge – $${hazmatSurchargeValue}` : '',
                            (document.getElementById('maxCargoToggleBtn').classList.contains('active') && document.getElementById('maxCargoWeight').value) ? `Max Cargo Weight: ${document.getElementById('maxCargoWeight').value} lbs` : ''
                        ].filter(Boolean).join(' - ')}
                    </div>
                </div>
                
                ${showNF ? `<p class="note">NOTE: Rates subject to fuel surcharge adjustment.</p>
                <p class="note">NOTE: For 20' dry containers on this lane weighing between 38,000 and 44,000 LBS, a triaxle fee of $150.00 would apply in place of the flat chassis fee.</p>

                <div class="footer">
                    <p class="footer-cta">To place an order, email <a href="mailto:export@dsllog.com">export@dsllog.com</a></p>
                    <p class="footer-text">dsllog.com</p>
                </div>` : ''}
            `;

            return quoteHTML;
        }

        function buildRailRampExportQuote(customerName, overrides, showNotesFooter) {
            const o = overrides || null;
            const showNF = showNotesFooter !== false;
            const fromCity = o ? (o.location || '') : document.getElementById('fromLocation').value;
            const toLocation = o ? (o.ramp || '') : document.getElementById('toLocation').value;
            const transportRate = (parseFloat(o ? o.transportRate : document.getElementById('transportRate').value) || 0).toFixed(2);
            const fuelSurcharge = (parseFloat(o ? o.fuelSurcharge : document.getElementById('fuelSurcharge').value) || 0).toFixed(1);
            const chassisRate = (parseFloat((o ? o.chassisRate : document.getElementById('chassisRate').value) || '0') || 0).toFixed(2);
            const tankerSurchargeValue = surchargeVal(o, 'tanker', 'tankerSurcharge');
            const hazmatSurchargeValue = surchargeVal(o, 'hazmat', 'hazmatSurcharge');
            const triaxleSurchargeValue = surchargeVal(o, 'triaxle', 'triaxleSurcharge');

            // Calculate totals
            const transportRateNum = parseFloat(transportRate);
            const fuelSurchargeNum = parseFloat(fuelSurcharge) / 100;
            const fuelSurchargeAmount = transportRateNum * fuelSurchargeNum;
            const chassisRateNum = parseFloat(chassisRate);
            const tankerNum = tankerSurchargeValue ? parseFloat(tankerSurchargeValue) : 0;
            const hazmatNum = hazmatSurchargeValue ? parseFloat(hazmatSurchargeValue) : 0;
            const triaxleNum = triaxleSurchargeValue ? parseFloat(triaxleSurchargeValue) : 0;
            const residentialValue = surchargeVal(o, 'residential', 'residentialDelivery');
            const residentialNum = residentialValue ? parseFloat(residentialValue) : 0;
            const reeferSurchargeValue = surchargeVal(o, 'reefer', 'reeferSurcharge');
            const reeferNum = reeferSurchargeValue ? parseFloat(reeferSurchargeValue) : 0;
            const gensetSurchargeValue = surchargeVal(o, 'genset', 'gensetSurcharge');
            const gensetNum = gensetSurchargeValue ? parseFloat(gensetSurchargeValue) : 0;
            const scaleTicketValue = surchargeVal(o, 'scaleTicket', 'scaleTicketFee');
            const scaleTicketNum = scaleTicketValue ? parseFloat(scaleTicketValue) : 0;
            const totalRampExportCost = (transportRateNum + fuelSurchargeAmount + chassisRateNum + tankerNum + hazmatNum + triaxleNum + residentialNum + reeferNum + gensetNum + scaleTicketNum).toFixed(2);

            const quoteHTML = `
                <div class="quote-header">
                    <div class="quote-title">DSL LOGISTICS</div>
                </div>

                <div class="divider">&nbsp;</div>

                <div class="quote-heading-container">
                    <p class="quote-heading-title">RAIL RAMP EXPORT SHIPMENT</p>
                    <p class="quote-heading-customer">${customerName}</p>
                </div>

                <div class="route-info">
                    <div class="route-from-to">${fromCity.toUpperCase()} &rarr; ${toLocation.toUpperCase()}</div>
                    <div class="route-type">Export via Rail &mdash; Ramp Delivery</div>
                </div>

                <table class="quote-table">
                    <thead>
                        <tr>
                            <th>Service</th>
                            <th>Rate</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Base Rate</td>
                            <td>$${transportRate}</td>
                        </tr>
                        <tr>
                            <td>Fuel Surcharge <span class="service-desc">(weekly review)</span></td>
                            <td>${fuelSurcharge}%</td>
                        </tr>
                        ${chassisRateNum > 0 ? `
                        <tr>
                            <td>Chassis Fee <span class="service-desc">(flat, not daily)</span></td>
                            <td>$${chassisRate}</td>
                        </tr>
                        ` : ''}
                        ${tankerSurchargeValue ? `
                        <tr>
                            <td>Tanker Surcharge</td>
                            <td>$${tankerSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${hazmatSurchargeValue ? `
                        <tr>
                            <td>Hazmat</td>
                            <td>$${hazmatSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${triaxleSurchargeValue ? `
                        <tr>
                            <td>Triaxle Surcharge</td>
                            <td>$${triaxleSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${residentialValue ? `
                        <tr>
                            <td>Residential Delivery</td>
                            <td>$${residentialValue}</td>
                        </tr>
                        ` : ''}
                        ${reeferSurchargeValue ? `
                        <tr>
                            <td>Reefer</td>
                            <td>$${reeferSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${gensetSurchargeValue ? `
                        <tr>
                            <td>GenSet</td>
                            <td>$${gensetSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${scaleTicketValue ? `
                        <tr>
                            <td>Scale Ticket Fee <span class="service-desc">(light or heavy)</span></td>
                            <td>$${scaleTicketValue}</td>
                        </tr>
                        ` : ''}
                        <tr style="border-top: 2px solid #FFD700; font-weight: bold; background-color: #f9f9f9;">
                            <td>Total Cost of Transportation</td>
                            <td>$${totalRampExportCost}</td>
                        </tr>
                    </tbody>
                </table>

                <div class="services-section">
                    <div class="services-title">INCLUDED SERVICES</div>
                    <div class="services-list">
                        ${[
                            `No chassis split or pre-pull charges`,
                            `Live Loading in ${fromCity} (2 free hours) – $97.50/hr`,
                            tankerSurchargeValue ? `Tanker Surcharge – $${tankerSurchargeValue}` : '',
                            triaxleSurchargeValue ? `Triaxle Surcharge – $${triaxleSurchargeValue}` : '',
                            hazmatSurchargeValue ? `Hazmat Surcharge – $${hazmatSurchargeValue}` : '',
                            (document.getElementById('maxCargoToggleBtn').classList.contains('active') && document.getElementById('maxCargoWeight').value) ? `Max Cargo Weight: ${document.getElementById('maxCargoWeight').value} lbs` : ''
                        ].filter(Boolean).join(' - ')}
                    </div>
                </div>

                ${showNF ? `<p class="note">NOTE: Rates subject to fuel surcharge adjustment.</p>
                <p class="note">NOTE: For 20' dry containers on this lane weighing between 38,000 and 44,000 LBS, a triaxle fee of $150.00 would apply in place of the flat chassis fee.</p>

                <div class="footer">
                    <p class="footer-cta">To place an order, email <a href="mailto:export@dsllog.com">export@dsllog.com</a></p>
                    <p class="footer-text">dsllog.com</p>
                </div>` : ''}
            `;

            return quoteHTML;
        }

        function buildLocalQuote(customerName, overrides, showNotesFooter) {
            const o = overrides || null;
            const showNF = showNotesFooter !== false;
            const toCity = o ? (o.location || '') : document.getElementById('toLocation').value;
            const transportRate = (parseFloat(o ? o.transportRate : document.getElementById('transportRate').value) || 0).toFixed(2);
            const fuelSurchargePercent = (parseFloat(o ? o.fuelSurcharge : document.getElementById('fuelSurcharge').value) || 0);  // 57
            const fuelSurchargeDisplay = fuelSurchargePercent.toFixed(0);  // 57 for display
            const chassisRate = (parseFloat((o ? o.chassisRate : document.getElementById('chassisRate').value) || '0') || 0).toFixed(2);
            const tankerSurchargeValue = surchargeVal(o, 'tanker', 'tankerSurcharge');
            const hazmatSurchargeValue = surchargeVal(o, 'hazmat', 'hazmatSurcharge');
            const triaxleSurchargeValue = surchargeVal(o, 'triaxle', 'triaxleSurcharge');
            const liveUnloadRate = parseFloat(document.getElementById('liveUnloadRate').value).toFixed(2);
            const includeNoChassis = document.getElementById('includeNoChassis').checked;
            const maxCargoWeight = document.getElementById('maxCargoWeight').value;
            const maxCargoToggle = document.getElementById('maxCargoToggleBtn').classList.contains('active');
            const containerTypeValue = o ? (o.containerType || '') : (document.getElementById('importContainerType').value || '');
            const containerTypeLabel = IMPORT_CONTAINER_LABELS[containerTypeValue] || '';

            // Check if this location has drop/pick free
            const localRate = (rateData.local && rateData.local.rates) ? rateData.local.rates.find(r => r.destination === toCity) : null;
            const hasDropPickFree = localRate && localRate.dropPickFree;
            const laneFreeStorage = localRate ? !!localRate.freeStorage : true;
            
            // Calculate totals for local
            const transportRateNum = parseFloat(transportRate);
            const fuelSurchargeNum = fuelSurchargePercent / 100;  // Convert 57 to 0.57 for calculation
            const fuelSurchargeAmount = transportRateNum * fuelSurchargeNum;
            const chassisRateNum = parseFloat(chassisRate);
            const tankerNum = tankerSurchargeValue ? parseFloat(tankerSurchargeValue) : 0;
            const hazmatNum = hazmatSurchargeValue ? parseFloat(hazmatSurchargeValue) : 0;
            const triaxleNum = triaxleSurchargeValue ? parseFloat(triaxleSurchargeValue) : 0;
            const residentialValue = surchargeVal(o, 'residential', 'residentialDelivery');
            const residentialNum = residentialValue ? parseFloat(residentialValue) : 0;
            const reeferSurchargeValue = surchargeVal(o, 'reefer', 'reeferSurcharge');
            const reeferNum = reeferSurchargeValue ? parseFloat(reeferSurchargeValue) : 0;
            const gensetSurchargeValue = surchargeVal(o, 'genset', 'gensetSurcharge');
            const gensetNum = gensetSurchargeValue ? parseFloat(gensetSurchargeValue) : 0;
            const scaleTicketValue = surchargeVal(o, 'scaleTicket', 'scaleTicketFee');
            const scaleTicketNum = scaleTicketValue ? parseFloat(scaleTicketValue) : 0;
            const totalLocalCost = (transportRateNum + fuelSurchargeAmount + chassisRateNum + tankerNum + hazmatNum + triaxleNum + residentialNum + reeferNum + gensetNum + scaleTicketNum).toFixed(2);
            
            // Build chassis fee row if it has a value
            let chassisRow = '';
            if (chassisRateNum > 0) {
                chassisRow = `
                    <tr>
                        <td>Chassis Fee <span class="service-desc">(flat, not daily)</span></td>
                        <td>$${chassisRate}</td>
                    </tr>
                `;
            }
            
            // Build tanker row if it has a value
            let tankerRow = '';
            if (tankerSurchargeValue) {
                tankerRow = `
                    <tr>
                        <td>Tanker Surcharge</td>
                        <td>$${tankerSurchargeValue}</td>
                    </tr>
                `;
            }
            
            // Build hazmat row if it has a value
            let hazmatRow = '';
            if (hazmatSurchargeValue) {
                hazmatRow = `
                    <tr>
                        <td>Hazmat</td>
                        <td>$${hazmatSurchargeValue}</td>
                    </tr>
                `;
            }
            
            // Build triaxle row if it has a value
            let triaxleRow = '';
            if (triaxleSurchargeValue) {
                triaxleRow = `
                    <tr>
                        <td>Triaxle Surcharge</td>
                        <td>$${triaxleSurchargeValue}</td>
                    </tr>
                `;
            }
            
            // Build residential delivery row if it has a value
            let residentialRow = '';
            if (residentialValue) {
                residentialRow = `
                    <tr>
                        <td>Residential Delivery</td>
                        <td>$${residentialValue}</td>
                    </tr>
                `;
            }
            let reeferRow = '';
            if (reeferSurchargeValue) {
                reeferRow = `
                    <tr>
                        <td>Reefer</td>
                        <td>$${reeferSurchargeValue}</td>
                    </tr>
                `;
            }
            let gensetRow = '';
            if (gensetSurchargeValue) {
                gensetRow = `
                    <tr>
                        <td>GenSet</td>
                        <td>$${gensetSurchargeValue}</td>
                    </tr>
                `;
            }
            let scaleTicketRow = '';
            if (scaleTicketValue) {
                scaleTicketRow = `
                    <tr>
                        <td>Scale Ticket Fee <span class="service-desc">(light or heavy)</span></td>
                        <td>$${scaleTicketValue}</td>
                    </tr>
                `;
            }

            const localOrigin = (document.getElementById('fromLocation').value === 'phoenix_rr') ? 'PHOENIX RR' : 'PHOENIX CY';
            
            const quoteHTML = `
                <div class="quote-header">
                    <div class="quote-title">DSL LOGISTICS</div>
                </div>
                
                <div class="divider">&nbsp;</div>
                
                <div class="quote-heading-container">
                    <p class="quote-heading-title">LOCAL SHIPMENT</p>
                    <p class="quote-heading-customer">${customerName}</p>
                </div>
                
                <div class="route-info">
                    <div class="route-from-to">${localOrigin} &rarr; ${toCity.toUpperCase()}</div>
                    <div class="route-type">${containerTypeLabel ? containerTypeLabel + ' ' : ''}Local Drayage Service</div>
                </div>
                
                <table class="quote-table">
                    <thead>
                        <tr>
                            <th>Service</th>
                            <th>Rate</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Base Rate</td>
                            <td>$${transportRate}</td>
                        </tr>
                        <tr>
                            <td>Fuel Surcharge <span class="service-desc">(weekly review)</span></td>
                            <td>${fuelSurchargeDisplay}%</td>
                        </tr>
                        ${chassisRow}
                        ${tankerRow}
                        ${hazmatRow}
                        ${triaxleRow}
                        ${residentialRow}
                        ${reeferRow}
                        ${gensetRow}
                        ${scaleTicketRow}
                        <tr style="border-top: 2px solid #FFD700; font-weight: bold; background-color: #f9f9f9;">
                            <td>Total Cost of Transportation</td>
                            <td>$${totalLocalCost}</td>
                        </tr>
                    </tbody>
                </table>
                
                <div class="services-section">
                    <div class="services-title">INCLUDED SERVICES</div>
                    <div class="services-list">
                        ${[
                            hasDropPickFree ? `Drop/pick in ${toCity}: Free` : '',
                            laneFreeStorage ? `4 days free storage in Phoenix CY` : '',
                            includeNoChassis ? `No additional chassis split charges` : '',
                            `Live Unloading in ${toCity}: Includes 2 free hours; $97.50 each hour after`,
                            tankerSurchargeValue ? `Tanker Surcharge – $${tankerSurchargeValue}` : '',
                            triaxleSurchargeValue ? `Triaxle Surcharge – $${triaxleSurchargeValue}` : '',
                            hazmatSurchargeValue ? `Hazmat Surcharge – $${hazmatSurchargeValue}` : '',
                            (maxCargoToggle && maxCargoWeight) ? `Max Cargo Weight: ${maxCargoWeight} lbs` : ''
                        ].filter(Boolean).join(' - ')}
                    </div>
                </div>

                ${showNF ? `<p class="note">NOTE: Rates subject to fuel surcharge adjustment.</p>
                <p class="note">NOTE: For 20' dry containers on this lane weighing between 38,000 and 44,000 LBS, a triaxle fee of $100.00 would apply in place of the flat chassis fee.</p>

                <div class="footer">
                    <p class="footer-cta">To place an order, email <a href="mailto:imports@dsllog.com">imports@dsllog.com</a></p>
                    <p class="footer-text">dsllog.com</p>
                </div>` : ''}
            `;
            
            return quoteHTML;
        }

        function buildImportMenuQuote(customerName) {
            const toLocation = document.getElementById('toLocation').value || 'Delivery Location';
            const fscRaw = parseFloat(document.getElementById('fuelSurcharge').value) || 57;
            const fscDisp = fscRaw.toFixed(0);
            const chassis = (parseFloat(document.getElementById('chassisRate').value) || 195).toFixed(2);
            const chassisNum = parseFloat(chassis);
            const storageDays = document.getElementById('storageDays').value || '4';

            // Three tiers: from the matched import row, else compute from the base transport
            let t1, t2, t3;
            const row = (rateData.import && rateData.import.rates)
                ? rateData.import.rates.find(r => r.destination === toLocation) : null;
            if (row) {
                t1 = parseFloat(row['40ST_HC']);
                t2 = parseFloat(row['20_45']);
                t3 = parseFloat(row['NOR_REEFER']);
            } else {
                t1 = parseFloat(document.getElementById('transportRate').value) || 0;
                t2 = t1 + 130;
                t3 = t1 + 430;
            }
            const f = n => (isNaN(n) ? '0.00' : n.toFixed(2));
            const preferred = 'APL, CMA, Cosco, Evergreen, Hamburg Sud, Hapag-Lloyd, Maersk, Matson, MSC, ONE, OOCL, Wan Hai';

            const tierTable = (transport) => {
                const total = transport + (transport * fscRaw / 100) + chassisNum;
                return `
                    <table class="quote-table">
                        <thead>
                            <tr>
                                <th>Service</th>
                                <th>Rate</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Transport</td>
                                <td>$${f(transport)}</td>
                            </tr>
                            <tr>
                                <td>Fuel Surcharge <span class="service-desc">(weekly review)</span></td>
                                <td>${fscDisp}%</td>
                            </tr>
                            <tr>
                                <td>Chassis Fee <span class="service-desc">(flat, not daily)</span></td>
                                <td>$${chassis}</td>
                            </tr>
                            <tr style="border-top: 2px solid #FFD700; font-weight: bold; background-color: #f9f9f9;">
                                <td>Total Cost of Transportation</td>
                                <td>$${f(total)}</td>
                            </tr>
                        </tbody>
                    </table>`;
            };

            const hasDropPickFree = row && row.dropPickFree;
            const laneFreeStorage = row && row.freeStorage;

            return `
                <div class="quote-header">
                    <div class="quote-title">DSL LOGISTICS</div>
                </div>
                <div class="divider">&nbsp;</div>
                <div class="quote-heading-container">
                    <p class="quote-heading-title">IMPORT SHIPMENT</p>
                    <p class="quote-heading-customer">${customerName}</p>
                </div>
                <div class="menu-quote">
                    <p class="menu-lead"><strong>Delivery Location/Address:</strong> ${toLocation}</p>

                    <p class="menu-cond">For 40&rsquo; standard and/or 40&rsquo; HC dry containers AND for the following lines (${preferred})</p>
                    ${tierTable(t1)}

                    <div class="menu-divider">&nbsp;</div>

                    <p class="menu-cond">For 40&rsquo; standard and/or 40&rsquo; HC dry containers booked with any other Steamship Line not listed above,<br>OR for handling 20&rsquo;/45&rsquo; booked with any Steamship Line<br>OR for handling any specialized container</p>
                    ${tierTable(t2)}

                    <div class="menu-divider">&nbsp;</div>

                    <p class="menu-cond">For reefers and NOR booked with any Steamship Line</p>
                    ${tierTable(t3)}
                    <p class="menu-fee">DSL Genset: Additional $225.00</p>

                    <p class="menu-section"><strong>Standard fees:</strong></p>
                    <p class="menu-fee">Includes: 2 free hours; $97.50/hour thereafter<br>Hazardous Cargo surcharge: Additional $325.00</p>
                </div>
                <p class="note">NOTE: Our chassis fee applies regardless of Steamship Line agreements.</p>
                ${hasDropPickFree ? `<p class="note">NOTE: Drop/pick in ${toLocation}: Free.</p>` : ''}
                ${laneFreeStorage ? `<p class="note">NOTE: ${storageDays} days free storage in Phoenix CY.</p>` : ''}
                <p class="note">NOTE: For 20' dry containers on this lane weighing between 38,000 and 44,000 LBS, a triaxle fee of $250.00 would apply in place of the flat chassis fee.</p>
                <div class="footer">
                    <p class="footer-cta">To place an order, email <a href="mailto:imports@dsllog.com">imports@dsllog.com</a></p>
                    <p class="footer-text">dsllog.com</p>
                </div>
            `;
        }

        function buildImportQuote(customerName, overrides, showNotesFooter, isRail) {
            const o = overrides || null;
            const showNF = showNotesFooter !== false;
            // IMPORT MODE LOGIC (isRail = Import Rail variant: rail origin + rail rate source)
            const fromLocationValue = document.getElementById('fromLocation').value;
            const customLocation = document.getElementById('customLocation').value;
            
            // Convert dropdown value to display text
            let fromLocation;
            if (isRail) {
                fromLocation = (fromLocationValue === 'other')
                    ? (customLocation || 'Custom Location')
                    : 'Port of Los Angeles/Long Beach RAIL';
            } else if (fromLocationValue === 'los_angeles') {
                fromLocation = 'Port of Los Angeles/Long Beach';
            } else if (fromLocationValue === 'phoenix') {
                fromLocation = 'Phoenix Container Yard (CY)/Phoenix Union Pacific Ramp (UP)';
            } else if (fromLocationValue === 'other') {
                fromLocation = customLocation || 'Custom Location';
            } else {
                // Main tab may be in another mode; default an import lane to the standard port origin
                fromLocation = 'Port of Los Angeles/Long Beach';
            }
            
            const toLocation = o ? (o.location || 'Delivery Location') : (document.getElementById('toLocation').value || 'Delivery Location');
            const transportRate = (parseFloat(o ? o.transportRate : document.getElementById('transportRate').value) || 0).toFixed(2);
            const fuelSurcharge = (parseFloat(o ? o.fuelSurcharge : document.getElementById('fuelSurcharge').value) || 0).toFixed(1);
            const chassisRate = (parseFloat(o ? o.chassisRate : document.getElementById('chassisRate').value) || 0).toFixed(2);
            const liveUnloadRate = parseFloat(document.getElementById('liveUnloadRate').value).toFixed(2);
            const tankerSurchargeValue = surchargeVal(o, 'tanker', 'tankerSurcharge');
            const triaxleSurchargeValue = surchargeVal(o, 'triaxle', 'triaxleSurcharge');
            const hazmatSurchargeValue = surchargeVal(o, 'hazmat', 'hazmatSurcharge');
            
            // Calculate Total Cost of Transportation
            const transportRateNum = parseFloat(transportRate);
            const fuelSurchargeNum = parseFloat(fuelSurcharge) / 100;
            const fuelSurchargeAmount = transportRateNum * fuelSurchargeNum;
            const chassisRateNum = chassisRate ? parseFloat(chassisRate) : 0;
            const tankerNum = tankerSurchargeValue ? parseFloat(tankerSurchargeValue) : 0;
            const triaxleNum = triaxleSurchargeValue ? parseFloat(triaxleSurchargeValue) : 0;
            const hazmatNum = hazmatSurchargeValue ? parseFloat(hazmatSurchargeValue) : 0;
            const splitChassisValue = o ? (o.split || '') : document.getElementById('splitChassisFee').value;
            const splitChassisNum = splitChassisValue ? parseFloat(splitChassisValue) : 0;
            const residentialValue = surchargeVal(o, 'residential', 'residentialDelivery');
            const residentialNum = residentialValue ? parseFloat(residentialValue) : 0;
            const reeferSurchargeValue = surchargeVal(o, 'reefer', 'reeferSurcharge');
            const reeferNum = reeferSurchargeValue ? parseFloat(reeferSurchargeValue) : 0;
            const gensetSurchargeValue = surchargeVal(o, 'genset', 'gensetSurcharge');
            const gensetNum = gensetSurchargeValue ? parseFloat(gensetSurchargeValue) : 0;
            const scaleTicketValue = surchargeVal(o, 'scaleTicket', 'scaleTicketFee');
            const scaleTicketNum = scaleTicketValue ? parseFloat(scaleTicketValue) : 0;

            const totalCostTransportation = (transportRateNum + fuelSurchargeAmount + chassisRateNum + tankerNum + triaxleNum + hazmatNum + splitChassisNum + residentialNum + reeferNum + gensetNum + scaleTicketNum).toFixed(2);
            
            const dropLocation = document.getElementById('dropLocation').value;
            const includeStorage = document.getElementById('includeStorage').checked;
            const storageDays = document.getElementById('storageDays').value;
            const includeNoChassis = document.getElementById('includeNoChassis').checked;
            const maxCargoWeight = document.getElementById('maxCargoWeight').value;
            const maxCargoToggle = document.getElementById('maxCargoToggleBtn').classList.contains('active');
            
            // Check if this location has drop/pick free (rail reads its own rate table)
            const rateSrcRows = isRail
                ? ((rateData.importRail && rateData.importRail.rates) ? rateData.importRail.rates : null)
                : ((rateData.import && rateData.import.rates) ? rateData.import.rates : null);
            const importRate = rateSrcRows ? rateSrcRows.find(r => r.destination === toLocation) : null;
            const steamshipLineValue = o ? (o.steamshipLine || '') : (document.getElementById('importSteamshipLine').value || '');
            const isCaliforniaDestination = /,\s*(CA|California)\b/i.test(toLocation);
            const isExemptSteamshipNoteDestination = isCaliforniaDestination
                || /\b(Las Vegas|Henderson|Pahrump),\s*NV\b/i.test(toLocation)
                || /,\s*(UT|Utah)\b/i.test(toLocation);
            const showSteamshipNote = steamshipLineValue === 'ssl' && !isExemptSteamshipNoteDestination;
            const containerTypeValue = o ? (o.containerType || '') : (document.getElementById('importContainerType').value || '');
            const containerTypeLabel = (isRail ? RAIL_CONTAINER_LABELS : IMPORT_CONTAINER_LABELS)[containerTypeValue] || '';
            const hasDropPickFree = importRate && importRate.dropPickFree;
            const laneFreeStorage = importRate ? !!importRate.freeStorage : true;

            let servicesItems = [];
            if (hasDropPickFree) servicesItems.push(`Drop/pick in ${toLocation}: Free`);
            
            if (includeStorage && laneFreeStorage) {
                servicesItems.push(`${storageDays} days free storage in Phoenix CY`);
            }
            if (includeNoChassis) {
                servicesItems.push(`No chassis split or pre-pull charges`);
            }
            if (maxCargoToggle && maxCargoWeight) {
                servicesItems.push(`Max Cargo Weight: ${maxCargoWeight} lbs`);
            }

            // Add custom fields to services section
            if (customFields.length > 0) {
                customFields.forEach(field => {
                    servicesItems.push(`${field.name}: ${field.value}`);
                });
            }

            // Add live unload to services
            servicesItems.push(`Live Unload in ${toLocation} (${/,\s*(CA|California)\b/i.test(toLocation) ? '1 free hour' : '2 free hours'}) – $${liveUnloadRate}/hr`);
            
            // Add hazmat to services if enabled
            if (hazmatSurchargeValue) {
                servicesItems.push(`Hazmat Surcharge – $${hazmatSurchargeValue}`);
            }

            const servicesHTML = servicesItems.join(' - ');

            let customHTML = '';

            const quoteHTML = `
                <div class="quote-header">
                    <div class="quote-title">DSL LOGISTICS</div>
                </div>
                
                <div class="divider">&nbsp;</div>
                
                <div class="quote-heading-container">
                    <p class="quote-heading-title">${isRail ? 'IMPORT RAIL SHIPMENT' : 'IMPORT SHIPMENT'}</p>
                    <p class="quote-heading-customer">${customerName}</p>
                </div>
                
                <div class="route-info">
                    <div class="route-from-to">${fromLocation.toUpperCase()} &rarr; ${toLocation.toUpperCase()}</div>
                    <div class="route-type">${containerTypeLabel ? containerTypeLabel + ' ' : ''}Loaded Container</div>
                </div>

                <table class="quote-table">
                    <thead>
                        <tr>
                            <th>Service</th>
                            <th>Rate</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Transport</td>
                            <td>$${transportRate}</td>
                        </tr>
                        <tr>
                            <td>Fuel Surcharge <span class="service-desc">(weekly review)</span></td>
                            <td>${fuelSurcharge}%</td>
                        </tr>
                        ${!triaxleSurchargeValue ? `
                        <tr>
                            <td>Chassis Fee <span class="service-desc">(flat, not daily)</span></td>
                            <td>$${chassisRate}</td>
                        </tr>
                        ` : ''}
                        ${tankerSurchargeValue ? `
                        <tr>
                            <td>Tanker Surcharge</td>
                            <td>$${tankerSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${triaxleSurchargeValue ? `
                        <tr>
                            <td>Triaxle Surcharge</td>
                            <td>$${triaxleSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${splitChassisValue ? `
                        <tr>
                            <td>Split Chassis Fee</td>
                            <td>$${splitChassisValue}</td>
                        </tr>
                        ` : ''}
                        ${hazmatSurchargeValue ? `
                        <tr>
                            <td>Hazmat</td>
                            <td>$${hazmatSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${residentialValue ? `
                        <tr>
                            <td>Residential Delivery</td>
                            <td>$${residentialValue}</td>
                        </tr>
                        ` : ''}
                        ${reeferSurchargeValue ? `
                        <tr>
                            <td>Reefer</td>
                            <td>$${reeferSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${gensetSurchargeValue ? `
                        <tr>
                            <td>GenSet</td>
                            <td>$${gensetSurchargeValue}</td>
                        </tr>
                        ` : ''}
                        ${scaleTicketValue ? `
                        <tr>
                            <td>Scale Ticket Fee <span class="service-desc">(light or heavy)</span></td>
                            <td>$${scaleTicketValue}</td>
                        </tr>
                        ` : ''}
                        <tr style="border-top: 2px solid #FFD700; font-weight: bold; background-color: #f9f9f9;">
                            <td>Total Cost of Transportation</td>
                            <td>$${totalCostTransportation}</td>
                        </tr>
                    </tbody>
                </table>
                
                <div class="services-section">
                    <div class="services-title">INCLUDED SERVICES</div>
                    <div class="services-list">
                        ${servicesHTML}
                    </div>
                </div>
                
                ${showNF ? `<p class="note">NOTE: Chassis fee applies regardless of Steamship Line agreements.</p>
                ${showSteamshipNote ? `<p class="note">NOTE: If the Steamship Line is not one of our preferred carriers (APL, COSCO, CMA, Evergreen, Hamburg S&uuml;d, Hapag-Lloyd, Maersk, Matson, MSC, ONE, OOCL, Wan Hai), a $480 non-preferred carrier surcharge is added to the base transport rate before the Fuel Surcharge is calculated:<br>(Base Transport Rate + $480) &times; 1.57 = Total Transportation Cost<br>The 57% FSC applies to the combined amount, not the base rate alone.</p>
                ` : ''}<p class="note">NOTE: For 20' dry containers on this lane weighing between 38,000 and 44,000 LBS, a triaxle fee of $250.00 would apply in place of the flat chassis fee.</p>

                <div class="footer">
                    <p class="footer-cta">To place an order, email <a href="mailto:imports@dsllog.com">imports@dsllog.com</a></p>
                    <p class="footer-text">dsllog.com</p>
                </div>` : ''}
            `;

            return quoteHTML;
        }

        function buildBlockForMode(mode, customerName, overrides, showNotesFooter) {
            if (mode === 'export') return buildExportQuote(customerName, overrides, showNotesFooter);
            if (mode === 'railExport') return buildRailExportQuote(customerName, overrides, showNotesFooter);
            if (mode === 'railRampExport') return buildRailRampExportQuote(customerName, overrides, showNotesFooter);
            if (mode === 'local') return buildLocalQuote(customerName, overrides, showNotesFooter);
            if (mode === 'rail') return buildImportQuote(customerName, overrides, showNotesFooter, true);
            return buildImportQuote(customerName, overrides, showNotesFooter);
        }

        function buildBlockForCurrentMode(customerName, overrides, showNotesFooter) {
            return buildBlockForMode(currentMode, customerName, overrides, showNotesFooter);
        }

        function generateQuote() {
            const customerName = document.getElementById('customerName').value || 'Customer';

            // Tiered menu quote (import only) — a standalone full-pricing reply
            const menuBox = document.getElementById('tieredMenuMode');
            if (menuBox && menuBox.checked && currentMode === 'import') {
                document.getElementById('quoteContent').innerHTML = buildImportMenuQuote(customerName);
                document.getElementById('previewContainer').classList.add('show');
                document.getElementById('copyFeedback').classList.remove('show');
                setTimeout(() => {
                    document.getElementById('previewContainer').scrollIntoView({ behavior: 'smooth' });
                }, 100);
                return;
            }

            const laneList = lanes.filter(id => document.getElementById('laneLocation-' + id));
            let html;

            if (laneList.length === 0) {
                // Single quote: its own notes + footer
                html = buildBlockForCurrentMode(customerName, null, true);
            } else {
                // Multiple lanes: each block gets its own notes + footer
                html = buildBlockForCurrentMode(customerName, null, true);
                laneList.forEach(id => {
                    const laneModeEl = document.getElementById('laneMode-' + id);
                    const laneMode = laneModeEl ? laneModeEl.value : currentMode;
                    const laneSteamshipEl = document.getElementById('laneSteamship-' + id);
                    const laneSteamshipValue = laneSteamshipEl ? laneSteamshipEl.value : '';
                    const laneRampEl = document.getElementById('laneRamp-' + id);
                    const overrides = {
                        location: document.getElementById('laneLocation-' + id).value,
                        ramp: laneRampEl ? laneRampEl.value : '',
                        transportRate: document.getElementById('laneTransport-' + id).value,
                        fuelSurcharge: document.getElementById('laneFuel-' + id).value,
                        chassisRate: document.getElementById('laneChassis-' + id).value,
                        steamshipLine: laneSteamshipValue,
                        containerType: document.getElementById('laneContainerType-' + id).value,
                        tanker: document.getElementById('laneTanker-' + id).value,
                        hazmat: document.getElementById('laneHazmat-' + id).value,
                        triaxle: document.getElementById('laneTriaxle-' + id).value,
                        split: document.getElementById('laneSplit-' + id).value,
                        residential: document.getElementById('laneResidential-' + id).value
                    };
                    html += '<div class="lane-quote-separator">&nbsp;</div>' + buildBlockForMode(laneMode, customerName, overrides, true);
                });
            }

            document.getElementById('quoteContent').innerHTML = html;
            document.getElementById('previewContainer').classList.add('show');
            document.getElementById('copyFeedback').classList.remove('show');

            setTimeout(() => {
                document.getElementById('previewContainer').scrollIntoView({ behavior: 'smooth' });
            }, 100);
        }

        // ---- Additional lanes ----
        function laneLocationLabelFor(mode) {
            return (mode === 'export' || mode === 'railExport' || mode === 'railRampExport') ? 'From (Pick Up)' : 'To (Delivery)';
        }

        function defaultLaneChassisFor(mode) {
            if (mode === 'local' || mode === 'rail' || mode === 'railExport' || mode === 'railRampExport') return '50.00';
            if (mode === 'export') return '110.00';
            return '195.00'; // import
        }

        // Read a surcharge value from lane overrides (o) or the main form
        function surchargeVal(o, key, domId) {
            const v = o ? o[key] : document.getElementById(domId).value;
            return v ? parseFloat(v).toFixed(2) : '';
        }

        // Mode to use for the rate modal: the target lane's mode, else the main tab
        function getModalMode() {
            if (rateModalTarget !== null) {
                const sel = document.getElementById('laneMode-' + rateModalTarget);
                if (sel) return sel.value;
            }
            return currentMode;
        }

        // When a lane's type changes, relabel it and reset its rate fields to that mode's defaults
        // For Export / Rail Export lanes, the pickup list is data-driven (like the main tab).
        function laneRateListFor(mode) {
            if (mode === 'export') return EXPORT_DESTINATIONS;
            if (mode === 'railExport') return RAIL_EXPORT_DESTINATIONS;
            if (mode === 'railRampExport') return RAIL_RAMP_EXPORT_PICKUPS;
            return null;
        }

        // Fill a lane's Transport + Fuel from the pickup it has selected (Export / Rail Export /
        // Rail Ramp Export only). Rail Ramp Export also auto-picks a valid ramp for that pickup,
        // same logic as the main tab's updateRailRampExportRate().
        function onLaneLocationRateFill(id) {
            const sel = document.getElementById('laneLocation-' + id);
            const modeEl = document.getElementById('laneMode-' + id);
            if (!sel || !modeEl) return;
            const mode = modeEl.value;

            if (mode === 'railRampExport') {
                const rampSel = document.getElementById('laneRamp-' + id);
                const pickupRow = RAIL_RAMP_EXPORT_PICKUPS.find(d => d.city === sel.value);
                if (pickupRow && rampSel) {
                    const currentRampField = RAIL_RAMPS[rampSel.value];
                    let rampName = (currentRampField && pickupRow[currentRampField]) ? rampSel.value : '';
                    if (!rampName) {
                        rampName = Object.keys(RAIL_RAMPS).find(name => pickupRow[RAIL_RAMPS[name]]) || '';
                    }
                    rampSel.value = rampName;
                    const rate = rampName ? pickupRow[RAIL_RAMPS[rampName]] : 0;
                    document.getElementById('laneTransport-' + id).value = (rate || 0).toFixed(2);
                    document.getElementById('laneFuel-' + id).value = pickupRow.fuelSurcharge;
                }
                generateQuote();
                return;
            }

            const list = laneRateListFor(mode);
            if (!list) { generateQuote(); return; }
            const found = list.find(d => d.city === sel.value);
            if (found) {
                document.getElementById('laneTransport-' + id).value = Number(found.baseRate).toFixed(2);
                document.getElementById('laneFuel-' + id).value = found.fuelSurcharge;
            }
            generateQuote();
        }

        // Swap a lane's Location control to match its mode: a pickup dropdown that auto-fills
        // the rate for Export / Rail Export / Rail Ramp Export, or a free-text input otherwise.
        // Rail Ramp Export also gets a second dropdown for the destination ramp.
        function rebuildLaneLocation(id, mode) {
            loadRatesFromManager(); // ensure the pickup lists are current
            const el = document.getElementById('laneLocation-' + id);
            if (!el) return;
            const group = el.parentElement;
            const list = laneRateListFor(mode);
            const label = laneLocationLabelFor(mode);

            // Drop any ramp selector from a previous mode before rebuilding
            const existingRampGroup = document.getElementById('laneRampGroup-' + id);
            if (existingRampGroup) existingRampGroup.remove();

            if (mode === 'railRampExport') {
                const opts = list.map(d => `<option value="${d.city}">${d.city}</option>`).join('');
                group.innerHTML =
                    `<label id="laneLocationLabel-${id}">${label}</label>` +
                    `<select id="laneLocation-${id}" onchange="onLaneLocationRateFill(${id})">${opts}</select>`;
                const rampOpts = Object.keys(RAIL_RAMPS).map(r => `<option value="${r}">${r}</option>`).join('');
                group.insertAdjacentHTML('afterend',
                    `<div class="form-group" id="laneRampGroup-${id}">` +
                        `<label>To (Rail Ramp)</label>` +
                        `<select id="laneRamp-${id}" onchange="onLaneLocationRateFill(${id})">${rampOpts}</select>` +
                    `</div>`
                );
                onLaneLocationRateFill(id); // auto-fill the first pickup's valid ramp + rate
            } else if (list && list.length) {
                const opts = list.map(d => `<option value="${d.city}">${d.city}</option>`).join('');
                group.innerHTML =
                    `<label id="laneLocationLabel-${id}">${label}</label>` +
                    `<select id="laneLocation-${id}" onchange="onLaneLocationRateFill(${id})">${opts}</select>`;
                onLaneLocationRateFill(id); // auto-fill the first pickup's rate
            } else {
                group.innerHTML =
                    `<label id="laneLocationLabel-${id}">${label}</label>` +
                    `<input type="text" id="laneLocation-${id}" placeholder="Location" autocomplete="off">`;
            }
        }

        function onLaneModeChange(id) {
            const sel = document.getElementById('laneMode-' + id);
            if (!sel) return;
            const mode = sel.value;
            const label = document.getElementById('laneLocationLabel-' + id);
            if (label) label.textContent = laneLocationLabelFor(mode);
            document.getElementById('laneTransport-' + id).value = '0.00';
            document.getElementById('laneFuel-' + id).value = '57';
            document.getElementById('laneChassis-' + id).value = defaultLaneChassisFor(mode);
            const laneContainerTypeEl = document.getElementById('laneContainerType-' + id);
            if (laneContainerTypeEl) laneContainerTypeEl.value = '';
            // Reset this lane's surcharge toggles to OFF
            delete laneStoredChassis[id];
            ['Hazmat', 'Tanker', 'Triaxle', 'Split', 'Residential'].forEach(f => {
                const inp = document.getElementById('lane' + f + '-' + id);
                const btn = document.getElementById('lane' + f + 'Btn-' + id);
                if (inp) inp.value = '';
                if (btn) { btn.classList.remove('active'); btn.textContent = 'OFF'; }
            });
            const triaxleInp = document.getElementById('laneTriaxle-' + id);
            if (triaxleInp) triaxleInp.placeholder = (mode === 'import' || mode === 'rail') ? '$250' : (mode === 'export' || mode === 'railExport' || mode === 'railRampExport') ? '$150' : '$100';
            rebuildLaneLocation(id, mode);
            generateQuote();
        }

        // ---- Per-lane surcharge toggles (mirror the main Rates panel) ----
        function _laneSimpleToggle(id, field, onVal) {
            const inp = document.getElementById('lane' + field + '-' + id);
            const btn = document.getElementById('lane' + field + 'Btn-' + id);
            if (btn.classList.contains('active')) {
                inp.value = '';
                btn.classList.remove('active');
                btn.textContent = 'OFF';
            } else {
                inp.value = onVal;
                btn.classList.add('active');
                btn.textContent = 'ON';
            }
            generateQuote();
        }
        function toggleLaneHazmat(id) { _laneSimpleToggle(id, 'Hazmat', '325.00'); }
        function toggleLaneTanker(id) { _laneSimpleToggle(id, 'Tanker', '225.00'); }
        function toggleLaneResidential(id) { _laneSimpleToggle(id, 'Residential', '250.00'); }

        function toggleLaneTriaxle(id) {
            const inp = document.getElementById('laneTriaxle-' + id);
            const btn = document.getElementById('laneTriaxleBtn-' + id);
            const chassis = document.getElementById('laneChassis-' + id);
            const mode = document.getElementById('laneMode-' + id).value;
            if (btn.classList.contains('active')) {
                inp.value = '';
                btn.classList.remove('active');
                btn.textContent = 'OFF';
                if (laneStoredChassis[id] !== undefined) {
                    chassis.value = laneStoredChassis[id];
                    delete laneStoredChassis[id];
                }
            } else {
                // Triaxle replaces the flat chassis fee, so stash & zero the lane chassis
                inp.value = (mode === 'import' || mode === 'rail') ? '250.00' : (mode === 'export' || mode === 'railExport') ? '150.00' : '100.00';
                btn.classList.add('active');
                btn.textContent = 'ON';
                laneStoredChassis[id] = chassis.value;
                chassis.value = '0.00';
            }
            generateQuote();
        }

        function toggleLaneSplit(id) {
            const inp = document.getElementById('laneSplit-' + id);
            const btn = document.getElementById('laneSplitBtn-' + id);
            const transport = document.getElementById('laneTransport-' + id);
            const cur = parseFloat(transport.value) || 0;
            if (btn.classList.contains('active')) {
                inp.value = '';
                transport.value = (cur - 150).toFixed(2);
                btn.classList.remove('active');
                btn.textContent = 'OFF';
            } else {
                inp.value = '150.00';
                transport.value = (cur + 150).toFixed(2);
                btn.classList.add('active');
                btn.textContent = 'ON';
            }
            generateQuote();
        }

        function addLane() {
            laneCounter++;
            const id = laneCounter;
            lanes.push(id);
            const mode = currentMode; // new lane defaults to the active tab's mode

            const section = document.createElement('div');
            section.className = 'lane-section';
            section.id = 'laneSection-' + id;
            section.innerHTML = `
                <div class="lane-section-header">
                    <span class="lane-section-title" id="laneTitle-${id}">Lane</span>
                    <button type="button" class="btn-remove-lane" onclick="removeLane(${id})">\u2715 Remove</button>
                </div>
                <div class="form-group">
                    <label>Lane Type</label>
                    <select id="laneMode-${id}" onchange="onLaneModeChange(${id})">
                        <option value="import"${mode === 'import' ? ' selected' : ''}>Import</option>
                        <option value="rail"${mode === 'rail' ? ' selected' : ''}>Rail Import</option>
                        <option value="local"${mode === 'local' ? ' selected' : ''}>Local</option>
                        <option value="export"${mode === 'export' ? ' selected' : ''}>Export</option>
                        <option value="railExport"${mode === 'railExport' ? ' selected' : ''}>Rail Export</option>
                        <option value="railRampExport"${mode === 'railRampExport' ? ' selected' : ''}>Rail Local Export</option>
                    </select>
                </div>
                <button type="button" class="btn-load-rate" onclick="openRateModal(${id})">\ud83d\udcca Load Rate from Manager</button>
                <input type="hidden" id="laneSteamship-${id}" value="">
                <input type="hidden" id="laneContainerType-${id}" value="">
                <div class="form-group">
                    <label id="laneLocationLabel-${id}">${laneLocationLabelFor(mode)}</label>
                    <input type="text" id="laneLocation-${id}" placeholder="Location" autocomplete="off">
                </div>
                <div class="form-group">
                    <label>Transport ($)</label>
                    <input type="number" id="laneTransport-${id}" value="0.00" step="0.01">
                </div>
                <div class="form-group">
                    <label>Fuel Surcharge (%)</label>
                    <input type="number" id="laneFuel-${id}" value="57" step="0.1">
                </div>
                <div class="form-group">
                    <label>Chassis Fee ($)</label>
                    <input type="number" id="laneChassis-${id}" value="${defaultLaneChassisFor(mode)}" step="0.01">
                </div>
                <div class="form-group-with-toggle">
                    <div>
                        <label>Hazmat ($)</label>
                        <input type="number" id="laneHazmat-${id}" placeholder="$325" step="0.01">
                    </div>
                    <button type="button" class="toggle-btn" id="laneHazmatBtn-${id}" onclick="toggleLaneHazmat(${id})">OFF</button>
                </div>
                <div class="form-group-with-toggle">
                    <div>
                        <label>Tanker Surcharge ($)</label>
                        <input type="number" id="laneTanker-${id}" placeholder="$225" step="0.01">
                    </div>
                    <button type="button" class="toggle-btn" id="laneTankerBtn-${id}" onclick="toggleLaneTanker(${id})">OFF</button>
                </div>
                <div class="form-group-with-toggle">
                    <div>
                        <label>Triaxle ($)</label>
                        <input type="number" id="laneTriaxle-${id}" placeholder="${(mode === 'import' || mode === 'rail') ? '$250' : (mode === 'export' || mode === 'railExport' || mode === 'railRampExport') ? '$150' : '$100'}" step="0.01">
                    </div>
                    <button type="button" class="toggle-btn" id="laneTriaxleBtn-${id}" onclick="toggleLaneTriaxle(${id})">OFF</button>
                </div>
                <div class="form-group-with-toggle">
                    <div>
                        <label>Split Chassis ($)</label>
                        <input type="number" id="laneSplit-${id}" placeholder="$150" step="0.01">
                    </div>
                    <button type="button" class="toggle-btn" id="laneSplitBtn-${id}" onclick="toggleLaneSplit(${id})">OFF</button>
                </div>
                <div class="form-group-with-toggle">
                    <div>
                        <label>Residential Delivery ($)</label>
                        <input type="number" id="laneResidential-${id}" placeholder="$250" step="0.01">
                    </div>
                    <button type="button" class="toggle-btn" id="laneResidentialBtn-${id}" onclick="toggleLaneResidential(${id})">OFF</button>
                </div>
            `;
            document.getElementById('additionalLanesContainer').appendChild(section);
            rebuildLaneLocation(id, mode);
            renumberLanes();
        }

        function removeLane(id) {
            const idx = lanes.indexOf(id);
            if (idx !== -1) lanes.splice(idx, 1);
            const section = document.getElementById('laneSection-' + id);
            if (section) section.remove();
            renumberLanes();
            generateQuote();
        }

        function renumberLanes() {
            lanes.forEach((id, i) => {
                const title = document.getElementById('laneTitle-' + id);
                if (title) title.textContent = 'Lane ' + (i + 2);
            });
        }

        function updateLaneLabels() {
            lanes.forEach(id => {
                const sel = document.getElementById('laneMode-' + id);
                const label = document.getElementById('laneLocationLabel-' + id);
                if (sel && label) label.textContent = laneLocationLabelFor(sel.value);
            });
        }

        function showCopyFeedback() {
            const feedback = document.getElementById('copyFeedback');
            feedback.classList.add('show');
            setTimeout(() => {
                feedback.classList.remove('show');
            }, 3000);
        }

        function copyQuote() {
            const el = document.getElementById('quoteContent');

            // Primary: reproduce a manual "select the quote and copy" so pasting into
            // Outlook keeps the on-screen formatting (rich HTML), not plain text.
            const range = document.createRange();
            range.selectNodeContents(el);
            const sel = window.getSelection();
            sel.removeAllRanges();
            sel.addRange(range);

            let copied = false;
            try {
                copied = document.execCommand('copy');
            } catch (e) {
                copied = false;
            }
            sel.removeAllRanges();

            if (copied) {
                showCopyFeedback();
                return;
            }

            // Fallback: write both rich (HTML) and plain text via the async Clipboard API
            if (navigator.clipboard && window.ClipboardItem) {
                try {
                    const item = new ClipboardItem({
                        'text/html': new Blob([el.innerHTML], { type: 'text/html' }),
                        'text/plain': new Blob([el.innerText], { type: 'text/plain' })
                    });
                    navigator.clipboard.write([item]).then(showCopyFeedback).catch(() => {
                        navigator.clipboard.writeText(el.innerText).then(showCopyFeedback).catch(() => {
                            alert('Could not copy to clipboard. Please try again.');
                        });
                    });
                } catch (e) {
                    navigator.clipboard.writeText(el.innerText).then(showCopyFeedback).catch(() => {
                        alert('Could not copy to clipboard. Please try again.');
                    });
                }
            } else {
                alert('Could not copy to clipboard. Please try again.');
            }
        }

        // Show/hide storage days based on checkbox
        document.getElementById('includeStorage').addEventListener('change', function() {
            document.getElementById('storageDaysGroup').style.display = this.checked ? 'block' : 'none';
        });

        // Allow Enter key to add custom field
        document.getElementById('customFieldValue').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                addCustomField();
            }
        });

        // Allow Enter key to generate quote
        document.addEventListener('keypress', function(e) {
            if (e.key === 'Enter' && e.target.tagName !== 'TEXTAREA' && e.target.id !== 'customFieldValue') {
                generateQuote();
            }
        });

        // Load rates from Firebase (shared store), then initialize
        async function initPage() {
            try {
                const res = await fetch('https://rate-manager-dsl-default-rtdb.firebaseio.com/rates.json');
                if (res.ok) {
                    const firebaseData = await res.json();
                    if (firebaseData) {
                        localStorage.setItem('dsl_rates', JSON.stringify(firebaseData));
                    }
                }
            } catch (e) {
                console.warn('Firebase unavailable, using cached rates:', e);
            }
            loadRatesFromManager();
            updateChassisFromLocation();
            setupToLocationAutocomplete();
            updateFormForMode();
        }
        initPage();
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DSL Logistics - Rate Manager</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: Calibri, Arial, sans-serif;
            background-color: #f5f5f5;
            padding: 30px 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .header {
            background-color: #000;
            color: #FFD700;
            padding: 20px 30px;
            border-radius: 6px;
            margin-bottom: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 24px;
            margin-bottom: 5px;
        }
        
        .header p {
            font-size: 13px;
            color: #ccc;
        }
        
        .controls-section {
            background: white;
            padding: 25px;
            border-radius: 6px;
            margin-bottom: 30px;
            box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        }
        
        .control-group {
            display: flex;
            gap: 20px;
            align-items: flex-end;
            flex-wrap: wrap;
        }
        
        .control-item {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }
        
        .control-item label {
            font-size: 12px;
            font-weight: 600;
            color: #333;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .control-item input {
            padding: 10px 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-family: Calibri, Arial, sans-serif;
            font-size: 14px;
            width: 120px;
        }
        
        .control-item input:focus {
            outline: none;
            border-color: #FFD700;
            box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.2);
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s;
            font-family: Calibri, Arial, sans-serif;
        }
        
        .btn-primary {
            background-color: #FFD700;
            color: #000;
        }
        
        .btn-primary:hover {
            background-color: #E6C200;
        }
        
        .btn-secondary {
            background-color: #333;
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: #555;
        }
        
        .status {
            padding: 10px 15px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .status.success {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status.info {
            background-color: #d1ecf1;
            color: #0c5460;
        }
        
        .status.error {
            background-color: #f8d7da;
            color: #721c24;
        }
        
        .rates-section {
            background: white;
            border-radius: 6px;
            box-shadow: 0 2px 6px rgba(0,0,0,0.1);
            overflow: hidden;
            margin-bottom: 30px;
        }
        
        .rates-header {
            background-color: #f9f9f9;
            padding: 20px 25px;
            border-bottom: 2px solid #FFD700;
        }
        
        .rates-header h2 {
            font-size: 16px;
            color: #000;
            margin-bottom: 4px;
        }
        
        .rates-header p {
            font-size: 12px;
            color: #666;
        }
        
        .rates-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .rates-table thead {
            background-color: #f9f9f9;
            border-bottom: 2px solid #FFD700;
        }
        
        .rates-table th {
            padding: 12px 15px;
            text-align: left;
            font-size: 12px;
            font-weight: 700;
            color: #000;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .rates-table td {
            padding: 12px 15px;
            border-bottom: 1px solid #e0e0e0;
            font-size: 13px;
        }
        
        .rates-table tbody tr:hover {
            background-color: #f9f9f9;
        }
        
        .destination-cell {
            font-weight: 600;
            color: #000;
        }
        
        .rate-input {
            width: 100px;
            padding: 6px 8px;
            border: 1px solid #ddd;
            border-radius: 3px;
            font-family: Calibri, Arial, sans-serif;
            font-size: 12px;
            text-align: right;
        }
        
        .rate-input:focus {
            outline: none;
            border-color: #FFD700;
            box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.2);
        }
        
        .rate-display {
            text-align: right;
            font-weight: 600;
            color: #333;
        }
        
        .ssl-note {
            font-size: 11px;
            color: #888;
            font-style: italic;
        }
        
        .edit-mode .rate-display {
            display: none;
        }
        
        .view-mode .rate-input {
            display: none;
        }
        
        .action-buttons {
            padding: 20px 25px;
            display: flex;
            gap: 10px;
            justify-content: flex-end;
        }
        
        .footer {
            margin-top: 30px;
            padding: 20px;
            background: white;
            border-radius: 6px;
            font-size: 12px;
            color: #666;
            text-align: center;
            box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>DSL LOGISTICS RATE MANAGER</h1>
            <p>Import Truck Drayage Rates (LA/LGB to Destinations)</p>
        </div>
        
        <!-- Controls Section -->
        <div class="controls-section">
            <div class="control-group">
                <div class="control-item">
                    <label>📤 Import Rates from CSV</label>
                    <input type="file" id="csvUpload" accept=".csv" placeholder="Choose CSV file">
                    <small style="display: block; margin-top: 5px; color: #666;">Upload your master rate spreadsheet (CSV format)</small>
                </div>
                <button class="btn btn-primary" onclick="importRatesFromCSV()">Import Rates</button>
                <div class="status info" id="csvStatus" style="margin-top: 10px;"></div>
            </div>
            
            <hr style="margin: 20px 0; border: none; border-top: 1px solid #ddd;">
            
            <div class="control-group">
                <div class="control-item">
                    <label>Fuel Surcharge (FSC)</label>
                    <input type="number" id="fscInput" step="0.01" min="0" max="2" placeholder="0.57">
                </div>
                <button class="btn btn-primary" onclick="updateFSC()">Update FSC</button>
                <div class="status info" id="fscStatus">Enter FSC and click Update</div>
            </div>
            
            <hr style="margin: 20px 0; border: none; border-top: 1px solid #ddd;">
            
            <div class="control-group">
                <label style="display: block; margin-bottom: 12px; font-weight: bold;">💾 Data Backup & Recovery</label>
                <div style="display: flex; gap: 10px; margin-bottom: 10px;">
                    <button class="btn btn-primary" onclick="downloadBackup()" style="flex: 1;">📥 Download Backup</button>
                    <button class="btn btn-primary" onclick="uploadBackupClick()" style="flex: 1;">📤 Upload Backup</button>
                    <button class="btn btn-secondary" onclick="clearAllDataWithConfirm()" style="flex: 1; background-color: #dc3545;">🗑️ Clear All Data</button>
                </div>
                <input type="file" id="backupUpload" accept=".json" style="display: none;">
                <small style="display: block; color: #666;">
                    • <strong>Download:</strong> Saves all rates as a JSON file<br>
                    • <strong>Upload:</strong> Restores rates from a JSON backup<br>
                    • <strong>Clear:</strong> Deletes all data (cannot be undone!)
                </small>
                <div class="status info" id="backupStatus" style="margin-top: 10px;"></div>
            </div>
        </div>
        
        <!-- Rates Section -->
        <div class="rates-section">
            <div class="rates-header">
                <h2>Import Drayage Rates (SSL Pricing)</h2>
                <p>Premium Steamship Lines: APL, CMA, COSCO, Evergreen, Hamburg Sud, Hapag-Lloyd, Maersk, Matson, MSC, ONE, OOCL, Wan Hai | Non-SSL: Add $130 to all base rates</p>
            </div>
            
            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Destination</th>
                        <th>40' ST/HC</th>
                        <th>RT (20' / 45')</th>
                        <th>RT (NOR / Reefer)</th>
                        <th>Drop/Pick Free</th>
                        <th>Free Storage (4 days)</th>
                    </tr>
                </thead>
                <tbody id="ratesTableBody">
                    <!-- Populated by JavaScript -->
                </tbody>
            </table>
            
            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="toggleEditMode()" id="toggleBtn">Edit Rates</button>
                <button class="btn btn-primary" onclick="saveRates()" id="saveBtn" style="display: none;">Save Changes</button>
            </div>
        </div>
        
        <!-- Import Rail Rates Section -->
        <div class="rates-section">
            <div class="rates-header">
                <h2>Import Rail</h2>
                <p>Import Rail Rates (Ramp to Destination) &mdash; pricing by container size</p>
            </div>
            
            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Destination</th>
                        <th>40' / 45'</th>
                        <th>20'</th>
                        <th>Drop/Pick Free</th>
                        <th>Free Storage (4 days)</th>
                    </tr>
                </thead>
                <tbody id="railRatesTableBody">
                    <!-- Populated by JavaScript -->
                </tbody>
            </table>
            
            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="toggleRailEditMode()" id="toggleRailBtn">Edit Rates</button>
                <button class="btn btn-primary" onclick="saveRailRates()" id="saveRailBtn" style="display: none;">Save Changes</button>
            </div>
        </div>
        
        <!-- Export Rates Section -->
        <div class="rates-section">
            <div class="rates-header">
                <h2>Export Shipments (Phoenix CY to LA/LB)</h2>
                <p>Empty Container Return Rates from Phoenix Container Yard</p>
            </div>
            
            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Pickup Location</th>
                        <th>Base Rate</th>
                        <th>FSC (%)</th>
                        <th>Total Rate</th>
                        <th>Drop/Pick Free</th>
                        <th>Free Storage (4 days)</th>
                    </tr>
                </thead>
                <tbody id="exportRatesTableBody">
                    <!-- Populated by JavaScript -->
                </tbody>
            </table>
            
            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="toggleExportEditMode()" id="toggleExportBtn">Edit Rates</button>
                <button class="btn btn-primary" onclick="saveExportRates()" id="saveExportBtn" style="display: none;">Save Changes</button>
            </div>
        </div>
        
        <!-- Rail Export Rates Section -->
        <div class="rates-section">
            <div class="rates-header">
                <h2>Rail Export (Phoenix Ramp to LA/LB)</h2>
                <p>Export rail rates by pickup location &mdash; Base Rate + FSC (Total = Base &times; 1.57)</p>
            </div>
            
            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Pickup Location</th>
                        <th>Base Rate</th>
                        <th>FSC (%)</th>
                        <th>Total Rate</th>
                        <th>Drop/Pick Free</th>
                        <th>Free Storage (4 days)</th>
                    </tr>
                </thead>
                <tbody id="exportRailRatesTableBody">
                    <!-- Populated by JavaScript -->
                </tbody>
            </table>
            
            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="toggleExportRailEditMode()" id="toggleExportRailBtn">Edit Rates</button>
                <button class="btn btn-primary" onclick="saveExportRailRates()" id="saveExportRailBtn" style="display: none;">Save Changes</button>
            </div>
        </div>

        <!-- Rail Ramp Export Rates Section -->
        <div class="rates-section">
            <div class="rates-header">
                <h2>Rail Ramp Export (Pickup to Rail Ramp)</h2>
                <p>Separate from Rail Export above &mdash; each pickup location prices differently to up to three rail ramps. $0 means that ramp doesn't serve that pickup.</p>
            </div>

            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Pickup Location</th>
                        <th>Laveen Yard/Phoenix RR</th>
                        <th>Tucson Rail</th>
                        <th>BNSF Rail</th>
                        <th>FSC (%)</th>
                    </tr>
                </thead>
                <tbody id="railRampExportRatesTableBody">
                    <!-- Populated by JavaScript -->
                </tbody>
            </table>

            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="toggleRailRampExportEditMode()" id="toggleRailRampExportBtn">Edit Rates</button>
                <button class="btn btn-primary" onclick="saveRailRampExportRates()" id="saveRailRampExportBtn" style="display: none;">Save Changes</button>
            </div>
        </div>

        <!-- Local Rates Section -->
        <div class="rates-section">
            <div class="rates-header">
                <h2>Local Shipments (Phoenix CY to Local Destinations)</h2>
                <p>Local Drayage Rates from Phoenix Container Yard</p>
            </div>
            
            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Destination</th>
                        <th>Base Rate</th>
                        <th>FSC (%)</th>
                        <th>Total Rate</th>
                        <th>Drop/Pick Free</th>
                        <th>Free Storage (4 days)</th>
                    </tr>
                </thead>
                <tbody id="localRatesTableBody">
                    <!-- Populated by JavaScript -->
                </tbody>
            </table>
            
            <div class="action-buttons">
                <button class="btn btn-secondary" onclick="toggleLocalEditMode()" id="toggleLocalBtn">Edit Rates</button>
                <button class="btn btn-primary" onclick="saveLocalRates()" id="saveLocalBtn" style="display: none;">Save Changes</button>
            </div>
        </div>
        
        <div class="footer">
            <p><strong>Last Updated:</strong> <span id="lastUpdated">Loading...</span></p>
            <p>FSC updated every Monday. Edit rates above and click "Save Changes" when done.</p>
        </div>
    </div>

    <script>
        let rateData = {};

        // ===== SoCal Drayage import rates (LA/LGB to SoCal destinations) =====
        // Loaded once into the Import section via a guarded merge in loadRates().
        const SOCAL_IMPORT_RATES = [
            { destination: "Los Angeles, CA 90001", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Los Angeles, CA 90013", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Los Angeles, CA 90021", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Los Angeles, CA 90023", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Los Angeles, CA 90040", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Bell, CA 90201", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Compton, CA 90220", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Compton, CA 90221", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Inglewood, CA 90304", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Torrance, CA 90501", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Buena Park, CA 90620", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Cypress, CA 90630", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "La Mirada, CA 90638", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Santa Fe Springs, CA 90670", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Carson, CA 90745", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Carson, CA 90746", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Carson, CA 90747", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Carson, CA 90749", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Chino, CA 91708", "40ST_HC": 720, "20_45": 720, "NOR_REEFER": 720, freeStorage: true },
            { destination: "Chino, CA 91710", "40ST_HC": 720, "20_45": 720, "NOR_REEFER": 720, freeStorage: true },
            { destination: "City of Industry, CA 91714", "40ST_HC": 640, "20_45": 640, "NOR_REEFER": 640, freeStorage: true },
            { destination: "Mira Loma, CA 91752", "40ST_HC": 795, "20_45": 795, "NOR_REEFER": 795, freeStorage: true },
            { destination: "Upland, CA 91784", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Upland, CA 91785", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Upland, CA 91786", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Beaumont, CA 92223", "40ST_HC": 860, "20_45": 860, "NOR_REEFER": 860, freeStorage: true },
            { destination: "Bloomington, CA 92316", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Colton, CA 92324", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Oak Hills, CA 92344", "40ST_HC": 1330, "20_45": 1330, "NOR_REEFER": 1330, freeStorage: true },
            { destination: "Redlands, CA 92373", "40ST_HC": 820, "20_45": 820, "NOR_REEFER": 820, freeStorage: true },
            { destination: "Redlands, CA 92374", "40ST_HC": 820, "20_45": 820, "NOR_REEFER": 820, freeStorage: true },
            { destination: "Redlands, CA 92375", "40ST_HC": 820, "20_45": 820, "NOR_REEFER": 820, freeStorage: true },
            { destination: "Rialto, CA 92376", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Rialto, CA 92377", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Riverside, CA 92518", "40ST_HC": 820, "20_45": 820, "NOR_REEFER": 820, freeStorage: true },
            { destination: "Perris, CA 92570", "40ST_HC": 860, "20_45": 860, "NOR_REEFER": 860, freeStorage: true },
            { destination: "Perris, CA 92571", "40ST_HC": 860, "20_45": 860, "NOR_REEFER": 860, freeStorage: true },
            { destination: "Perris, CA 92599", "40ST_HC": 860, "20_45": 860, "NOR_REEFER": 860, freeStorage: true },
            { destination: "Anaheim, CA 92801", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Orange, CA 92867", "40ST_HC": 640, "20_45": 640, "NOR_REEFER": 640, freeStorage: true },
            { destination: "Anaheim, CA", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Corona, CA", "40ST_HC": 720, "20_45": 720, "NOR_REEFER": 720, freeStorage: true },
            { destination: "Fontana, CA", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Fullerton, CA", "40ST_HC": 595, "20_45": 595, "NOR_REEFER": 595, freeStorage: true },
            { destination: "Irvine, CA", "40ST_HC": 640, "20_45": 640, "NOR_REEFER": 640, freeStorage: true },
            { destination: "Long Beach, CA", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Mexicali, Baja CA", "40ST_HC": 1815, "20_45": 1815, "NOR_REEFER": 1815, freeStorage: true },
            { destination: "Moreno Valley, CA", "40ST_HC": 820, "20_45": 820, "NOR_REEFER": 820, freeStorage: true },
            { destination: "Ontario, CA", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Pomona, CA", "40ST_HC": 720, "20_45": 720, "NOR_REEFER": 720, freeStorage: true },
            { destination: "Ports, CA", "40ST_HC": 495, "20_45": 495, "NOR_REEFER": 495, freeStorage: true },
            { destination: "Rancho Cucamonga, CA", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Riverside, CA", "40ST_HC": 820, "20_45": 820, "NOR_REEFER": 820, freeStorage: true },
            { destination: "San Bernardino, CA", "40ST_HC": 785, "20_45": 785, "NOR_REEFER": 785, freeStorage: true },
            { destination: "Victorville, CA", "40ST_HC": 1300, "20_45": 1300, "NOR_REEFER": 1300, freeStorage: true },
        ];

        // ===== Import Rail rates (Ramp to Destination) =====
        // Seeded once into rateData.importRail via a guarded create in loadRates().
        const RAIL_IMPORT_RATES = [
            { destination: "Eloy, AZ 85131", "40_45": 2180, "20": 2060, freeStorage: true },
            { destination: "Queen Creek, AZ 85142", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "San Tan Valley, AZ 85143", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "Sun Lakes, AZ 85248", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Scottsdale, AZ 85262", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "Buckeye, AZ 85326", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Litchfield Park, AZ 85340", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Waddell, AZ 85355", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Apache Junction, AZ", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "Avondale, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Casa Grande, AZ", "40_45": 2075, "20": 1955, freeStorage: true },
            { destination: "Cave Creek, AZ", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "Chandler, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Douglas, AZ", "40_45": 3035, "20": 2915, freeStorage: true },
            { destination: "El Mirage, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Fountain Hills, AZ", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "Gilbert, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Glendale, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Goodyear, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Mesa, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Nogales, AZ", "40_45": 2765, "20": 2645, freeStorage: true },
            { destination: "Peoria, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Phoenix, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Queen Creek, AZ", "40_45": 1865, "20": 1745, freeStorage: true },
            { destination: "Scottsdale, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Surprise, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Tempe, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Tolleson, AZ", "40_45": 1815, "20": 1690, freeStorage: true },
            { destination: "Tucson, AZ", "40_45": 2075, "20": 1960, freeStorage: true },
        ];

        // ===== Rail Export rates (Phoenix Ramp to LA/LB) =====
        // Seeded once into rateData.exportRail via a guarded create in loadRates().
        // Base rate + FSC (57%); totalRate = baseRate * 1.57. $0 / unserved lanes are omitted.
        const RAIL_EXPORT_RATES = [
            { destination: "Phoenix, AZ 85003", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Phoenix, AZ 85085", baseRate: 1040, fuelSurcharge: 57, totalRate: 1632.80, dropPickFree: false, freeStorage: true },
            { destination: "Buckeye, AZ 85326", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Cashion, AZ 85329", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Litchfield Park, AZ 85340", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Waddell, AZ 85355", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Sun City West, AZ 85375", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Surprise, AZ 85379", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Avondale, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Chandler, AZ", baseRate: 985, fuelSurcharge: 57, totalRate: 1546.45, dropPickFree: false, freeStorage: true },
            { destination: "Cyazlav, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Douglas, AZ", baseRate: 2195, fuelSurcharge: 57, totalRate: 3446.15, dropPickFree: false, freeStorage: true },
            { destination: "El Mirage, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Flagstaff, AZ", baseRate: 1925, fuelSurcharge: 57, totalRate: 3022.25, dropPickFree: false, freeStorage: true },
            { destination: "Gilbert, AZ", baseRate: 985, fuelSurcharge: 57, totalRate: 1546.45, dropPickFree: false, freeStorage: true },
            { destination: "Glendale, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Goodyear, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Mesa, AZ", baseRate: 985, fuelSurcharge: 57, totalRate: 1546.45, dropPickFree: false, freeStorage: true },
            { destination: "Peoria, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Phoenix, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Queen Creek, AZ", baseRate: 985, fuelSurcharge: 57, totalRate: 1546.45, dropPickFree: false, freeStorage: true },
            { destination: "Scottsdale, AZ", baseRate: 985, fuelSurcharge: 57, totalRate: 1546.45, dropPickFree: false, freeStorage: true },
            { destination: "Sedona, AZ", baseRate: 1790, fuelSurcharge: 57, totalRate: 2810.30, dropPickFree: false, freeStorage: true },
            { destination: "Sun City, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Surprise, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Tempe, AZ", baseRate: 985, fuelSurcharge: 57, totalRate: 1546.45, dropPickFree: false, freeStorage: true },
            { destination: "Tolleson, AZ", baseRate: 910, fuelSurcharge: 57, totalRate: 1428.70, dropPickFree: false, freeStorage: true },
            { destination: "Tucson, AZ", baseRate: 1650, fuelSurcharge: 57, totalRate: 2590.50, dropPickFree: false, freeStorage: true },
        ];

        // ===== Rail Ramp Export rates (Pickup to Rail Ramp) =====
        // Separate from RAIL_EXPORT_RATES above: each pickup can price differently to up to
        // three named rail ramps. A rate of 0 means that ramp doesn't serve that pickup.
        // Seeded once into rateData.railRampExport via a guarded create in loadRates().
        const RAIL_RAMP_EXPORT_RATES = [
            { pickupLocation: "Phoenix, AZ 85024", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Phoenix, AZ 85027", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Phoenix, AZ 85050", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Phoenix, AZ 85083", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Phoenix, AZ 85085", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Phoenix, AZ 85086", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "New River, AZ 85087", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Coolidge, AZ 85128", laveenYard: 595, tucsonRail: 0, bnsfRail: 745, fuelSurcharge: 57 },
            { pickupLocation: "Coolidge, AZ 85132", laveenYard: 460, tucsonRail: 0, bnsfRail: 610, fuelSurcharge: 57 },
            { pickupLocation: "San Tan Valley, AZ 85140", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Queen Creek, AZ 85142", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "San Tan Valley, AZ 85143", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Maricopa, AZ 85145", laveenYard: 700, tucsonRail: 0, bnsfRail: 850, fuelSurcharge: 57 },
            { pickupLocation: "Maricopa, AZ 85172", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Superior, AZ 85173", laveenYard: 595, tucsonRail: 0, bnsfRail: 745, fuelSurcharge: 57 },
            { pickupLocation: "Mesa, AZ 85213", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Coolidge, AZ 85228", laveenYard: 595, tucsonRail: 0, bnsfRail: 745, fuelSurcharge: 57 },
            { pickupLocation: "Chandler, AZ 85248", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Rio Verde, AZ 85263", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Stanfield, AZ 85272", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Arlington, AZ 85322", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Buckeye, AZ 85326", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Cashion, AZ 85329", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Gila Bend, AZ 85337", laveenYard: 460, tucsonRail: 0, bnsfRail: 610, fuelSurcharge: 57 },
            { pickupLocation: "Litchfield Park, AZ 85340", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Roll, AZ 85347", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "San Luis, AZ 85349", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Somerton, AZ 85350", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Tolleson, AZ 85353", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Tonopah, AZ 85354", laveenYard: 595, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Waddell, AZ 85355", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Sun City West, AZ 85375", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Huachuca City, AZ 85613", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Golden Valley, AZ 86413", laveenYard: 1010, tucsonRail: 0, bnsfRail: 1160, fuelSurcharge: 57 },
            { pickupLocation: "Albuquerque, NM", laveenYard: 2095, tucsonRail: 0, bnsfRail: 2245, fuelSurcharge: 57 },
            { pickupLocation: "Apache Junction, AZ", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Avondale, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Casa Grande, AZ", laveenYard: 595, tucsonRail: 0, bnsfRail: 745, fuelSurcharge: 57 },
            { pickupLocation: "Cave Creek, AZ", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Chandler, AZ", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Douglas, AZ", laveenYard: 1310, tucsonRail: 0, bnsfRail: 1460, fuelSurcharge: 57 },
            { pickupLocation: "El Mirage, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "El Paso, TX", laveenYard: 2095, tucsonRail: 0, bnsfRail: 2145, fuelSurcharge: 57 },
            { pickupLocation: "Eloy, AZ", laveenYard: 595, tucsonRail: 0, bnsfRail: 745, fuelSurcharge: 57 },
            { pickupLocation: "Flagstaff, AZ", laveenYard: 925, tucsonRail: 0, bnsfRail: 1075, fuelSurcharge: 57 },
            { pickupLocation: "Fountain Hills, AZ", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Gilbert, AZ", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Glendale, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Goodyear, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Henderson, NV", laveenYard: 0, tucsonRail: 0, bnsfRail: 0, fuelSurcharge: 57 },
            { pickupLocation: "Kingman, AZ", laveenYard: 1230, tucsonRail: 0, bnsfRail: 1380, fuelSurcharge: 57 },
            { pickupLocation: "Lake Havasu City, AZ", laveenYard: 1195, tucsonRail: 0, bnsfRail: 1345, fuelSurcharge: 57 },
            { pickupLocation: "Las Vegas, NV", laveenYard: 1740, tucsonRail: 0, bnsfRail: 1890, fuelSurcharge: 57 },
            { pickupLocation: "Marana, AZ", laveenYard: 785, tucsonRail: 0, bnsfRail: 935, fuelSurcharge: 57 },
            { pickupLocation: "Maricopa, AZ", laveenYard: 475, tucsonRail: 0, bnsfRail: 625, fuelSurcharge: 57 },
            { pickupLocation: "Mesa, AZ", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Nogales, AZ", laveenYard: 1160, tucsonRail: 0, bnsfRail: 1310, fuelSurcharge: 57 },
            { pickupLocation: "Peoria, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Phoenix, AZ", laveenYard: 345, tucsonRail: 785, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Prescott, AZ", laveenYard: 785, tucsonRail: 0, bnsfRail: 935, fuelSurcharge: 57 },
            { pickupLocation: "Queen Creek, AZ", laveenYard: 445, tucsonRail: 0, bnsfRail: 595, fuelSurcharge: 57 },
            { pickupLocation: "Safford, AZ", laveenYard: 1130, tucsonRail: 0, bnsfRail: 1280, fuelSurcharge: 57 },
            { pickupLocation: "Sahuarita, AZ", laveenYard: 905, tucsonRail: 420, bnsfRail: 1055, fuelSurcharge: 57 },
            { pickupLocation: "Scottsdale, AZ", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Sedona, AZ", laveenYard: 800, tucsonRail: 0, bnsfRail: 950, fuelSurcharge: 57 },
            { pickupLocation: "Sierra Vista, AZ", laveenYard: 1255, tucsonRail: 0, bnsfRail: 1405, fuelSurcharge: 57 },
            { pickupLocation: "Sun City, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Surprise, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Tempe, AZ", laveenYard: 390, tucsonRail: 0, bnsfRail: 540, fuelSurcharge: 57 },
            { pickupLocation: "Tolleson, AZ", laveenYard: 345, tucsonRail: 0, bnsfRail: 495, fuelSurcharge: 57 },
            { pickupLocation: "Tucson, AZ", laveenYard: 785, tucsonRail: 295, bnsfRail: 935, fuelSurcharge: 57 },
            { pickupLocation: "Wickenburg, AZ", laveenYard: 595, tucsonRail: 0, bnsfRail: 745, fuelSurcharge: 57 },
            { pickupLocation: "Willcox, AZ", laveenYard: 1305, tucsonRail: 2090, bnsfRail: 1455, fuelSurcharge: 57 },
            { pickupLocation: "Yuma, AZ", laveenYard: 1160, tucsonRail: 0, bnsfRail: 1310, fuelSurcharge: 57 },
        ];

        let isEditMode = false;

        function loadRates() {
            try {
                const stored = localStorage.getItem('dsl_rates');
                if (stored) {
                    rateData = JSON.parse(stored);
                    
                    // Ensure freeStorage property exists for all import rates
                    if (rateData.import && rateData.import.rates) {
                        rateData.import.rates.forEach(rate => {
                            if (rate.freeStorage === undefined) {
                                rate.freeStorage = true;
                            }
                        });
                    }
                    
                    // Ensure export data exists
                    if (!rateData.export) {
                        rateData.export = {
                            description: "Export Shipments (Phoenix CY to LA/LB)",
                            rates: [
                                { destination: "Phoenix, AZ", baseRate: 945.00, fuelSurcharge: 57, totalRate: 1483.65, freeStorage: true },
                                { destination: "Casa Grande, AZ", baseRate: 1195.00, fuelSurcharge: 57, totalRate: 1876.15, freeStorage: true },
                                { destination: "Chandler/Gilbert, AZ", baseRate: 1020.00, fuelSurcharge: 57, totalRate: 1601.40, freeStorage: true },
                                { destination: "Mesa/Tempe/Scottsdale, AZ", baseRate: 1020.00, fuelSurcharge: 57, totalRate: 1601.40, freeStorage: true },
                                { destination: "Maricopa, AZ", baseRate: 1135.00, fuelSurcharge: 57, totalRate: 1781.95, freeStorage: true },
                                { destination: "Tucson, AZ", baseRate: 1510.00, fuelSurcharge: 57, totalRate: 2370.70, freeStorage: true },
                                { destination: "Nogales, AZ", baseRate: 1850.00, fuelSurcharge: 57, totalRate: 2904.50, freeStorage: true },
                                { destination: "Douglas, AZ", baseRate: 2115.00, fuelSurcharge: 57, totalRate: 3320.55, freeStorage: true },
                                { destination: "Flagstaff, AZ", baseRate: 1695.00, fuelSurcharge: 57, totalRate: 2661.15, freeStorage: true },
                                { destination: "El Paso, TX", baseRate: 3080.00, fuelSurcharge: 57, totalRate: 4835.60, freeStorage: true },
                                { destination: "Yuma, AZ", baseRate: 1170.00, fuelSurcharge: 57, totalRate: 1836.90, freeStorage: true },
                                { destination: "Kingman, AZ", baseRate: 1315.00, fuelSurcharge: 57, totalRate: 2064.55, freeStorage: true },
                                { destination: "Lake Havasu, AZ", baseRate: 1260.00, fuelSurcharge: 57, totalRate: 1978.20, freeStorage: true },
                                { destination: "Albuquerque, NM", baseRate: 3080.00, fuelSurcharge: 57, totalRate: 4835.60, freeStorage: true },
                                { destination: "Salt Lake City, UT", baseRate: 3410.00, fuelSurcharge: 57, totalRate: 5353.70, freeStorage: true },
                                { destination: "Silver City, NM", baseRate: 2520.00, fuelSurcharge: 57, totalRate: 3956.40, freeStorage: true },
                                { destination: "Henderson/Las Vegas, NV", baseRate: 1460.00, fuelSurcharge: 57, totalRate: 2292.20, freeStorage: true }
                            ]
                        };
                        localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                    }
                    
                    // Ensure freeStorage property exists for all export rates
                    if (rateData.export && rateData.export.rates) {
                        rateData.export.rates.forEach(rate => {
                            if (rate.freeStorage === undefined) {
                                rate.freeStorage = true;
                            }
                        });
                    }
                    
                    // Ensure local data exists
                    if (!rateData.local) {
                        rateData.local = {
                            description: "Local Shipments (Phoenix CY to Local Destinations)",
                            rates: [
                                { destination: "Phoenix, AZ", baseRate: 250.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 392.50, freeStorage: true },
                                { destination: "Chandler/Mesa/Tempe/Gilbert, AZ", baseRate: 295.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 463.15, freeStorage: true },
                                { destination: "Tucson, AZ", baseRate: 785.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1232.45, freeStorage: true },
                                { destination: "Nogales, AZ", baseRate: 1160.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1821.20, freeStorage: true },
                                { destination: "Albuquerque, NM / Belen, NM / El Paso, TX", baseRate: 2095.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 3289.15, freeStorage: true },
                                { destination: "Casa Grande, AZ", baseRate: 595.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 934.15, freeStorage: true },
                                { destination: "Maricopa, AZ", baseRate: 475.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 745.75, freeStorage: true },
                                { destination: "Eloy, AZ", baseRate: 595.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 934.15, freeStorage: true },
                                { destination: "Prescott, AZ", baseRate: 785.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1232.45, freeStorage: true }
                            ]
                        };
                        localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                    }
                    
                    // Ensure freeStorage property exists for all local rates
                    if (rateData.local && rateData.local.rates) {
                        rateData.local.rates.forEach(rate => {
                            if (rate.freeStorage === undefined) {
                                rate.freeStorage = true;
                            }
                        });
                    }
                } else {
                    // Initialize with default rates
                    rateData = {
                        fsc: 0.57,
                        lastUpdated: new Date().toISOString().split('T')[0],
                        import: {
                            description: "Import Shipments (LA/LGB to Destination)",
                            ssl: "Premium Steamship Lines",
                            rates: [
                                { destination: "Phoenix, AZ", "40ST_HC": 1895, "20_45": 2025, "NOR_REEFER": 2325, freeStorage: true },
                                { destination: "Tempe/Mesa, AZ", "40ST_HC": 1895, "20_45": 2025, "NOR_REEFER": 2325, freeStorage: true },
                                { destination: "Scottsdale/Chandler/Gilbert, AZ", "40ST_HC": 1895, "20_45": 2025, "NOR_REEFER": 2325, freeStorage: true },
                                { destination: "Glendale/Peoria, AZ", "40ST_HC": 1895, "20_45": 2025, "NOR_REEFER": 2325, freeStorage: true },
                                { destination: "Avondale/Goodyear, AZ", "40ST_HC": 1895, "20_45": 2025, "NOR_REEFER": 2325, freeStorage: true },
                                { destination: "Maricopa, AZ", "40ST_HC": 2370, "20_45": 2500, "NOR_REEFER": 2800, freeStorage: true },
                                { destination: "Tucson, AZ", "40ST_HC": 2680, "20_45": 2810, "NOR_REEFER": 3110, freeStorage: true },
                                { destination: "Nogales, AZ", "40ST_HC": 3055, "20_45": 3185, "NOR_REEFER": 3485, freeStorage: true },
                                { destination: "Albuquerque, NM", "40ST_HC": 3990, "20_45": 4120, "NOR_REEFER": 4420, freeStorage: true },
                                { destination: "Eloy, AZ", "40ST_HC": 2490, "20_45": 2620, "NOR_REEFER": 2790, freeStorage: true },
                                { destination: "Casa Grande, AZ", "40ST_HC": 2490, "20_45": 2620, "NOR_REEFER": 2920, freeStorage: true },
                                { destination: "Douglas/Naco, AZ", "40ST_HC": 3205, "20_45": 3335, "NOR_REEFER": 3635, freeStorage: true },
                                { destination: "Sedona, AZ", "40ST_HC": 2690, "20_45": 2820, "NOR_REEFER": 3120, freeStorage: true },
                                { destination: "Flagstaff, AZ", "40ST_HC": 2820, "20_45": 2950, "NOR_REEFER": 3250, freeStorage: true },
                                { destination: "Willcox, AZ", "40ST_HC": 3025, "20_45": 3155, "NOR_REEFER": 3455, freeStorage: true },
                                { destination: "Safford, AZ", "40ST_HC": 3025, "20_45": 3155, "NOR_REEFER": 3455, freeStorage: true },
                                { destination: "El Paso, TX", "40ST_HC": 3990, "20_45": 4120, "NOR_REEFER": 4420, freeStorage: true },
                                { destination: "Prescott, AZ", "40ST_HC": 2680, "20_45": 2810, "NOR_REEFER": 3110, freeStorage: true },
                                { destination: "Yuma, AZ", "40ST_HC": 1670, "20_45": 1670, "NOR_REEFER": 1670, freeStorage: true },
                                { destination: "Lake Havasu, AZ", "40ST_HC": 2175, "20_45": 2175, "NOR_REEFER": 2175, freeStorage: true },
                                { destination: "Washington/St George, UT", "40ST_HC": 2495, "20_45": 2495, "NOR_REEFER": 2495, freeStorage: true },
                                { destination: "Salt Lake City, UT", "40ST_HC": 4060, "20_45": 4060, "NOR_REEFER": 4060, freeStorage: true },
                                { destination: "Las Vegas, NV", "40ST_HC": 1705, "20_45": 1705, "NOR_REEFER": 1705, freeStorage: true },
                                { destination: "Coolidge, AZ", "40ST_HC": 2490, "20_45": 2620, "NOR_REEFER": 2920, freeStorage: true },
                                { destination: "Hurricane, UT", "40ST_HC": 2575, "20_45": 2575, "NOR_REEFER": 2575, freeStorage: true }
                            ]
                        },
                        fees: {
                            chassis: 195.00,
                            hazmat: 325.00,
                            triaxle: 250.00
                        },
                        export: {
                            description: "Export Shipments (Phoenix CY to LA/LB)",
                            rates: [
                                { destination: "Phoenix, AZ", baseRate: 945.00, fuelSurcharge: 57, totalRate: 1483.65 },
                                { destination: "Casa Grande, AZ", baseRate: 1195.00, fuelSurcharge: 57, totalRate: 1876.15 },
                                { destination: "Chandler/Gilbert, AZ", baseRate: 1020.00, fuelSurcharge: 57, totalRate: 1601.40 },
                                { destination: "Mesa/Tempe/Scottsdale, AZ", baseRate: 1020.00, fuelSurcharge: 57, totalRate: 1601.40 },
                                { destination: "Maricopa, AZ", baseRate: 1135.00, fuelSurcharge: 57, totalRate: 1781.95 },
                                { destination: "Tucson, AZ", baseRate: 1510.00, fuelSurcharge: 57, totalRate: 2370.70 },
                                { destination: "Nogales, AZ", baseRate: 1850.00, fuelSurcharge: 57, totalRate: 2904.50 },
                                { destination: "Douglas, AZ", baseRate: 2115.00, fuelSurcharge: 57, totalRate: 3320.55 },
                                { destination: "Flagstaff, AZ", baseRate: 1695.00, fuelSurcharge: 57, totalRate: 2661.15 },
                                { destination: "El Paso, TX", baseRate: 3080.00, fuelSurcharge: 57, totalRate: 4835.60 },
                                { destination: "Yuma, AZ", baseRate: 1170.00, fuelSurcharge: 57, totalRate: 1836.90 },
                                { destination: "Kingman, AZ", baseRate: 1315.00, fuelSurcharge: 57, totalRate: 2064.55 },
                                { destination: "Lake Havasu, AZ", baseRate: 1260.00, fuelSurcharge: 57, totalRate: 1978.20 },
                                { destination: "Albuquerque, NM", baseRate: 3080.00, fuelSurcharge: 57, totalRate: 4835.60 },
                                { destination: "Salt Lake City, UT", baseRate: 3410.00, fuelSurcharge: 57, totalRate: 5353.70 },
                                { destination: "Silver City, NM", baseRate: 2520.00, fuelSurcharge: 57, totalRate: 3956.40 },
                                { destination: "Henderson/Las Vegas, NV", baseRate: 1460.00, fuelSurcharge: 57, totalRate: 2292.20 }
                            ]
                        },
                        local: {
                            description: "Local Shipments (Phoenix CY to Local Destinations)",
                            rates: [
                                { destination: "Phoenix, AZ", baseRate: 250.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 392.50 },
                                { destination: "Chandler/Mesa/Tempe/Gilbert, AZ", baseRate: 295.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 463.15 },
                                { destination: "Tucson, AZ", baseRate: 785.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1232.45 },
                                { destination: "Nogales, AZ", baseRate: 1160.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1821.20 },
                                { destination: "Albuquerque, NM / Belen, NM / El Paso, TX", baseRate: 2095.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 3289.15 },
                                { destination: "Casa Grande, AZ", baseRate: 595.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 934.15 },
                                { destination: "Maricopa, AZ", baseRate: 475.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 745.75 },
                                { destination: "Eloy, AZ", baseRate: 595.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 934.15 },
                                { destination: "Prescott, AZ", baseRate: 785.00, fuelSurcharge: 57, hazmat: 0.00, noReefer: 0.00, totalRate: 1232.45 }
                            ]
                        }
                    };
                    localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                }
                
                // ===== One-time merge of SoCal drayage rates into the Import section =====
                // Runs once (flagged), preserves existing rows, and won't resurrect rows you delete later.
                if (rateData.import && Array.isArray(rateData.import.rates) && !rateData.socalDrayageLoaded) {
                    const existingDest = new Set(rateData.import.rates.map(r => r.destination));
                    let socalAdded = 0;
                    SOCAL_IMPORT_RATES.forEach(r => {
                        if (!existingDest.has(r.destination)) { rateData.import.rates.push({ ...r }); socalAdded++; }
                    });
                    rateData.socalDrayageLoaded = true;
                    if (socalAdded > 0) rateData.lastUpdated = new Date().toISOString().split('T')[0];
                    localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                    if (socalAdded > 0) console.log('Loaded ' + socalAdded + ' SoCal drayage rates into Import section.');
                }

                // ===== Always-on correction: 'California, CA' -> 'Victorville, CA' =====
                // Runs every load so it self-heals any cached/older saved state.
                if (rateData.import && Array.isArray(rateData.import.rates)) {
                    let vFixed = false;
                    rateData.import.rates.forEach(r => {
                        if (r.destination === 'California, CA') { r.destination = 'Victorville, CA'; vFixed = true; }
                    });
                    if (vFixed) localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                }

                // ===== Ensure Import Rail section exists (seed once) =====
                // New additive section; created only if absent so deleted rows are never resurrected.
                if (!rateData.importRail) {
                    rateData.importRail = {
                        description: "Import Rail (Ramp to Destination)",
                        rates: RAIL_IMPORT_RATES.map(r => ({ ...r }))
                    };
                    rateData.lastUpdated = new Date().toISOString().split('T')[0];
                    localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                }

                // ===== Ensure Rail Export section exists (seed once) =====
                // New additive section; created only if absent so deleted rows are never resurrected.
                if (!rateData.exportRail) {
                    rateData.exportRail = {
                        description: "Rail Export (Phoenix Ramp to LA/LB)",
                        rates: RAIL_EXPORT_RATES.map(r => ({ ...r }))
                    };
                    rateData.lastUpdated = new Date().toISOString().split('T')[0];
                    localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                }

                // ===== Ensure Rail Ramp Export section exists (seed once) =====
                // New additive section; created only if absent so deleted rows are never resurrected.
                if (!rateData.railRampExport) {
                    rateData.railRampExport = {
                        description: "Rail Ramp Export (Pickup to Rail Ramp)",
                        rates: RAIL_RAMP_EXPORT_RATES.map(r => ({ ...r }))
                    };
                    rateData.lastUpdated = new Date().toISOString().split('T')[0];
                    localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                }

                // ===== Always-on: normalize Rail Export bare-city labels to "City, AZ" =====
                // Self-heals older cached rows that were seeded as bare city names.
                // ZIP-coded and already-stated labels contain a comma and are left untouched.
                if (rateData.exportRail && Array.isArray(rateData.exportRail.rates)) {
                    let reFixed = false;
                    rateData.exportRail.rates.forEach(r => {
                        if (r.destination && r.destination.indexOf(',') === -1) {
                            r.destination = r.destination + ', AZ';
                            reFixed = true;
                        }
                    });
                    if (reFixed) localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                }

                renderRates();
                renderExportRates();
                renderLocalRates();
                renderRailRates();
                renderExportRailRates();
                renderRailRampExportRates();
                document.getElementById('lastUpdated').textContent = rateData.lastUpdated || 'Unknown';
                document.getElementById('fscInput').value = rateData.fsc;
            } catch (error) {
                console.error('Error loading rates:', error);
            }
        }

        function renderRates() {
            const tbody = document.getElementById('ratesTableBody');
            tbody.innerHTML = rateData.import.rates.map(row => `
                <tr>
                    <td class="destination-cell">${row.destination}</td>
                    <td>
                        <div class="rate-display">$${parseFloat(row["40ST_HC"]).toFixed(2)}</div>
                        <input type="number" class="rate-input" data-dest="${row.destination}" data-field="40ST_HC" value="${row["40ST_HC"]}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">$${parseFloat(row["20_45"]).toFixed(2)}</div>
                        <input type="number" class="rate-input" data-dest="${row.destination}" data-field="20_45" value="${row["20_45"]}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">$${parseFloat(row["NOR_REEFER"]).toFixed(2)}</div>
                        <input type="number" class="rate-input" data-dest="${row.destination}" data-field="NOR_REEFER" value="${row["NOR_REEFER"]}" step="0.01">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="drop-pick-checkbox" data-dest="${row.destination}" ${row.dropPickFree ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="storage-checkbox" data-dest="${row.destination}" ${row.freeStorage !== false ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                </tr>
            `).join('');
        }

        function toggleEditMode() {
            isEditMode = !isEditMode;
            const tbody = document.getElementById('ratesTableBody');
            
            if (isEditMode) {
                tbody.classList.add('edit-mode');
                document.getElementById('toggleBtn').textContent = 'Cancel';
                document.getElementById('saveBtn').style.display = 'inline-block';
            } else {
                tbody.classList.remove('edit-mode');
                document.getElementById('toggleBtn').textContent = 'Edit Rates';
                document.getElementById('saveBtn').style.display = 'none';
                loadRates(); // Reload to discard changes
            }
        }

        let isExportEditMode = false;
        let isLocalEditMode = false;

        function renderExportRates() {
            const tbody = document.getElementById('exportRatesTableBody');
            if (!rateData.export || !rateData.export.rates) {
                tbody.innerHTML = '<tr><td colspan="6">No export rates found</td></tr>';
                return;
            }
            
            tbody.innerHTML = rateData.export.rates.map(row => `
                <tr>
                    <td class="destination-cell">${row.destination}</td>
                    <td>
                        <div class="rate-display">$${parseFloat(row.baseRate).toFixed(2)}</div>
                        <input type="number" class="export-rate-input" data-dest="${row.destination}" data-field="baseRate" value="${row.baseRate}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">${row.fuelSurcharge}%</div>
                        <input type="number" class="export-rate-input" data-dest="${row.destination}" data-field="fuelSurcharge" value="${row.fuelSurcharge}" step="0.01" min="0" max="100">
                    </td>
                    <td>
                        <div class="rate-display">$${parseFloat(row.totalRate).toFixed(2)}</div>
                        <input type="number" class="export-rate-input" data-dest="${row.destination}" data-field="totalRate" value="${row.totalRate}" step="0.01" readonly>
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="export-drop-pick-checkbox" data-dest="${row.destination}" ${row.dropPickFree ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="export-storage-checkbox" data-dest="${row.destination}" ${row.freeStorage !== false ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                </tr>
            `).join('');
        }

        function toggleExportEditMode() {
            isExportEditMode = !isExportEditMode;
            const tbody = document.getElementById('exportRatesTableBody');
            
            if (isExportEditMode) {
                tbody.classList.add('edit-mode');
                document.getElementById('toggleExportBtn').textContent = 'Cancel';
                document.getElementById('saveExportBtn').style.display = 'inline-block';
            } else {
                tbody.classList.remove('edit-mode');
                document.getElementById('toggleExportBtn').textContent = 'Edit Rates';
                document.getElementById('saveExportBtn').style.display = 'none';
                loadRates(); // Reload to discard changes
            }
        }

        function saveExportRates() {
            try {
                const inputs = document.querySelectorAll('.export-rate-input:not([readonly])');
                const dropPickCheckboxes = document.querySelectorAll('.export-drop-pick-checkbox');
                const storageCheckboxes = document.querySelectorAll('.export-storage-checkbox');
                
                inputs.forEach(input => {
                    const dest = input.getAttribute('data-dest');
                    const field = input.getAttribute('data-field');
                    let value = parseFloat(input.value);
                    
                    const rate = rateData.export.rates.find(r => r.destination === dest);
                    if (rate) {
                        rate[field] = value;
                        // Auto-calculate totalRate if baseRate or fuelSurcharge changed
                        if (field === 'baseRate' || field === 'fuelSurcharge') {
                            rate.totalRate = (parseFloat(rate.baseRate) * (1 + parseFloat(rate.fuelSurcharge) / 100)).toFixed(2);
                        }
                    }
                });
                
                dropPickCheckboxes.forEach(checkbox => {
                    const destination = checkbox.dataset.dest;
                    const rate = rateData.export.rates.find(r => r.destination === destination);
                    if (rate) {
                        rate.dropPickFree = checkbox.checked;
                    }
                });
                
                storageCheckboxes.forEach(checkbox => {
                    const destination = checkbox.dataset.dest;
                    const rate = rateData.export.rates.find(r => r.destination === destination);
                    if (rate) {
                        rate.freeStorage = checkbox.checked;
                    }
                });
                
                rateData.lastUpdated = new Date().toISOString().split('T')[0];
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                
                document.getElementById('lastUpdated').textContent = rateData.lastUpdated;
                isExportEditMode = false;
                renderExportRates();
                document.getElementById('toggleExportBtn').textContent = 'Edit Rates';
                document.getElementById('saveExportBtn').style.display = 'none';
                
                alert('Export rates saved successfully!');
            } catch (error) {
                console.error('Error saving export rates:', error);
                alert('Error saving export rates: ' + error.message);
            }
        }

        let isExportRailEditMode = false;

        function renderExportRailRates() {
            const tbody = document.getElementById('exportRailRatesTableBody');
            if (!rateData.exportRail || !rateData.exportRail.rates) {
                tbody.innerHTML = '<tr><td colspan="6">No rail export rates found</td></tr>';
                return;
            }
            
            tbody.innerHTML = rateData.exportRail.rates.map(row => `
                <tr>
                    <td class="destination-cell">${row.destination}</td>
                    <td>
                        <div class="rate-display">$${parseFloat(row.baseRate).toFixed(2)}</div>
                        <input type="number" class="export-rail-rate-input" data-dest="${row.destination}" data-field="baseRate" value="${row.baseRate}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">${row.fuelSurcharge}%</div>
                        <input type="number" class="export-rail-rate-input" data-dest="${row.destination}" data-field="fuelSurcharge" value="${row.fuelSurcharge}" step="0.01" min="0" max="100">
                    </td>
                    <td>
                        <div class="rate-display">$${parseFloat(row.totalRate).toFixed(2)}</div>
                        <input type="number" class="export-rail-rate-input" data-dest="${row.destination}" data-field="totalRate" value="${row.totalRate}" step="0.01" readonly>
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="export-rail-drop-pick-checkbox" data-dest="${row.destination}" ${row.dropPickFree ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="export-rail-storage-checkbox" data-dest="${row.destination}" ${row.freeStorage !== false ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                </tr>
            `).join('');
        }

        function toggleExportRailEditMode() {
            isExportRailEditMode = !isExportRailEditMode;
            const tbody = document.getElementById('exportRailRatesTableBody');
            
            if (isExportRailEditMode) {
                tbody.classList.add('edit-mode');
                document.getElementById('toggleExportRailBtn').textContent = 'Cancel';
                document.getElementById('saveExportRailBtn').style.display = 'inline-block';
            } else {
                tbody.classList.remove('edit-mode');
                document.getElementById('toggleExportRailBtn').textContent = 'Edit Rates';
                document.getElementById('saveExportRailBtn').style.display = 'none';
                loadRates(); // Reload to discard changes
            }
        }

        function saveExportRailRates() {
            try {
                const inputs = document.querySelectorAll('.export-rail-rate-input:not([readonly])');
                const dropPickCheckboxes = document.querySelectorAll('.export-rail-drop-pick-checkbox');
                const storageCheckboxes = document.querySelectorAll('.export-rail-storage-checkbox');
                
                inputs.forEach(input => {
                    const dest = input.getAttribute('data-dest');
                    const field = input.getAttribute('data-field');
                    let value = parseFloat(input.value);
                    
                    const rate = rateData.exportRail.rates.find(r => r.destination === dest);
                    if (rate) {
                        rate[field] = value;
                        // Auto-calculate totalRate if baseRate or fuelSurcharge changed
                        if (field === 'baseRate' || field === 'fuelSurcharge') {
                            rate.totalRate = (parseFloat(rate.baseRate) * (1 + parseFloat(rate.fuelSurcharge) / 100)).toFixed(2);
                        }
                    }
                });
                
                dropPickCheckboxes.forEach(checkbox => {
                    const destination = checkbox.dataset.dest;
                    const rate = rateData.exportRail.rates.find(r => r.destination === destination);
                    if (rate) {
                        rate.dropPickFree = checkbox.checked;
                    }
                });
                
                storageCheckboxes.forEach(checkbox => {
                    const destination = checkbox.dataset.dest;
                    const rate = rateData.exportRail.rates.find(r => r.destination === destination);
                    if (rate) {
                        rate.freeStorage = checkbox.checked;
                    }
                });
                
                rateData.lastUpdated = new Date().toISOString().split('T')[0];
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                
                document.getElementById('lastUpdated').textContent = rateData.lastUpdated;
                isExportRailEditMode = false;
                renderExportRailRates();
                document.getElementById('toggleExportRailBtn').textContent = 'Edit Rates';
                document.getElementById('saveExportRailBtn').style.display = 'none';
                
                alert('Rail export rates saved successfully!');
            } catch (error) {
                console.error('Error saving rail export rates:', error);
                alert('Error saving rail export rates: ' + error.message);
            }
        }

        let isRailRampExportEditMode = false;

        function renderRailRampExportRates() {
            const tbody = document.getElementById('railRampExportRatesTableBody');
            if (!rateData.railRampExport || !rateData.railRampExport.rates) {
                tbody.innerHTML = '<tr><td colspan="5">No rail ramp export rates found</td></tr>';
                return;
            }

            const rampDisplay = v => (v ? '$' + parseFloat(v).toFixed(2) : '&mdash;');

            tbody.innerHTML = rateData.railRampExport.rates.map(row => `
                <tr>
                    <td class="destination-cell">${row.pickupLocation}</td>
                    <td>
                        <div class="rate-display">${rampDisplay(row.laveenYard)}</div>
                        <input type="number" class="railramp-rate-input" data-pickup="${row.pickupLocation}" data-field="laveenYard" value="${row.laveenYard}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">${rampDisplay(row.tucsonRail)}</div>
                        <input type="number" class="railramp-rate-input" data-pickup="${row.pickupLocation}" data-field="tucsonRail" value="${row.tucsonRail}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">${rampDisplay(row.bnsfRail)}</div>
                        <input type="number" class="railramp-rate-input" data-pickup="${row.pickupLocation}" data-field="bnsfRail" value="${row.bnsfRail}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">${row.fuelSurcharge}%</div>
                        <input type="number" class="railramp-rate-input" data-pickup="${row.pickupLocation}" data-field="fuelSurcharge" value="${row.fuelSurcharge}" step="0.01" min="0" max="100">
                    </td>
                </tr>
            `).join('');
        }

        function toggleRailRampExportEditMode() {
            isRailRampExportEditMode = !isRailRampExportEditMode;
            const tbody = document.getElementById('railRampExportRatesTableBody');

            if (isRailRampExportEditMode) {
                tbody.classList.add('edit-mode');
                document.getElementById('toggleRailRampExportBtn').textContent = 'Cancel';
                document.getElementById('saveRailRampExportBtn').style.display = 'inline-block';
            } else {
                tbody.classList.remove('edit-mode');
                document.getElementById('toggleRailRampExportBtn').textContent = 'Edit Rates';
                document.getElementById('saveRailRampExportBtn').style.display = 'none';
                loadRates(); // Reload to discard changes
            }
        }

        function saveRailRampExportRates() {
            try {
                const inputs = document.querySelectorAll('.railramp-rate-input');

                inputs.forEach(input => {
                    const pickup = input.getAttribute('data-pickup');
                    const field = input.getAttribute('data-field');
                    const value = parseFloat(input.value);

                    const rate = rateData.railRampExport.rates.find(r => r.pickupLocation === pickup);
                    if (rate && !isNaN(value)) {
                        rate[field] = value;
                    }
                });

                rateData.lastUpdated = new Date().toISOString().split('T')[0];
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);

                document.getElementById('lastUpdated').textContent = rateData.lastUpdated;
                isRailRampExportEditMode = false;
                renderRailRampExportRates();
                document.getElementById('toggleRailRampExportBtn').textContent = 'Edit Rates';
                document.getElementById('saveRailRampExportBtn').style.display = 'none';

                alert('Rail ramp export rates saved successfully!');
            } catch (error) {
                console.error('Error saving rail ramp export rates:', error);
                alert('Error saving rail ramp export rates: ' + error.message);
            }
        }

        function renderLocalRates() {
            const tbody = document.getElementById('localRatesTableBody');
            if (!rateData.local || !rateData.local.rates) {
                tbody.innerHTML = '<tr><td colspan="6">No local rates found</td></tr>';
                return;
            }
            
            tbody.innerHTML = rateData.local.rates.map(row => {
                const totalRate = (parseFloat(row.baseRate) * (1 + parseFloat(row.fuelSurcharge) / 100)).toFixed(2);
                return `
                <tr>
                    <td class="destination-cell">${row.destination}</td>
                    <td>
                        <div class="rate-display">$${parseFloat(row.baseRate).toFixed(2)}</div>
                        <input type="number" class="local-rate-input" data-dest="${row.destination}" data-field="baseRate" value="${row.baseRate}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">${row.fuelSurcharge}%</div>
                        <input type="number" class="local-rate-input" data-dest="${row.destination}" data-field="fuelSurcharge" value="${row.fuelSurcharge}" step="0.01" min="0" max="100">
                    </td>
                    <td>
                        <div class="rate-display">$${totalRate}</div>
                        <input type="number" class="local-rate-input" data-dest="${row.destination}" data-field="totalRate" value="${totalRate}" step="0.01" readonly>
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="local-drop-pick-checkbox" data-dest="${row.destination}" ${row.dropPickFree ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="local-storage-checkbox" data-dest="${row.destination}" ${row.freeStorage !== false ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                </tr>
            `;
            }).join('');
        }

        function toggleLocalEditMode() {
            isLocalEditMode = !isLocalEditMode;
            const tbody = document.getElementById('localRatesTableBody');
            
            if (isLocalEditMode) {
                tbody.classList.add('edit-mode');
                document.getElementById('toggleLocalBtn').textContent = 'Cancel';
                document.getElementById('saveLocalBtn').style.display = 'inline-block';
            } else {
                tbody.classList.remove('edit-mode');
                document.getElementById('toggleLocalBtn').textContent = 'Edit Rates';
                document.getElementById('saveLocalBtn').style.display = 'none';
                loadRates(); // Reload to discard changes
            }
        }

        function saveLocalRates() {
            try {
                const inputs = document.querySelectorAll('.local-rate-input:not([readonly])');
                const dropPickCheckboxes = document.querySelectorAll('.local-drop-pick-checkbox');
                const storageCheckboxes = document.querySelectorAll('.local-storage-checkbox');
                
                inputs.forEach(input => {
                    const dest = input.getAttribute('data-dest');
                    const field = input.getAttribute('data-field');
                    let value = parseFloat(input.value);
                    
                    const rate = rateData.local.rates.find(r => r.destination === dest);
                    if (rate) {
                        rate[field] = value;
                        // Auto-calculate totalRate if baseRate or fuelSurcharge changed
                        if (field === 'baseRate' || field === 'fuelSurcharge') {
                            rate.totalRate = (parseFloat(rate.baseRate) * (1 + parseFloat(rate.fuelSurcharge) / 100)).toFixed(2);
                        }
                    }
                });
                
                dropPickCheckboxes.forEach(checkbox => {
                    const destination = checkbox.dataset.dest;
                    const rate = rateData.local.rates.find(r => r.destination === destination);
                    if (rate) {
                        rate.dropPickFree = checkbox.checked;
                    }
                });
                
                storageCheckboxes.forEach(checkbox => {
                    const destination = checkbox.dataset.dest;
                    const rate = rateData.local.rates.find(r => r.destination === destination);
                    if (rate) {
                        rate.freeStorage = checkbox.checked;
                    }
                });
                
                rateData.lastUpdated = new Date().toISOString().split('T')[0];
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                
                document.getElementById('lastUpdated').textContent = rateData.lastUpdated;
                isLocalEditMode = false;
                renderLocalRates();
                document.getElementById('toggleLocalBtn').textContent = 'Edit Rates';
                document.getElementById('saveLocalBtn').style.display = 'none';
                
                alert('Local rates saved successfully!');
            } catch (error) {
                console.error('Error saving local rates:', error);
                alert('Error saving local rates: ' + error.message);
            }
        }

        function importRatesFromCSV() {
            const fileInput = document.getElementById('csvUpload');
            const statusDiv = document.getElementById('csvStatus');
            
            if (!fileInput.files.length) {
                statusDiv.textContent = '❌ Please select a CSV file';
                statusDiv.className = 'status error';
                return;
            }
            
            const file = fileInput.files[0];
            const reader = new FileReader();
            
            reader.onload = function(e) {
                try {
                    const csv = e.target.result;
                    const lines = csv.trim().split(/\r?\n/);  // Handle both \r\n and \n
                    
                    if (lines.length < 2) {
                        statusDiv.textContent = '❌ CSV must have header row and data';
                        statusDiv.className = 'status error';
                        return;
                    }
                    
                    // Parse CSV with proper quote handling
                    function parseCSVLine(line) {
                        const result = [];
                        let current = '';
                        let insideQuotes = false;
                        
                        for (let i = 0; i < line.length; i++) {
                            const char = line[i];
                            const nextChar = line[i + 1];
                            
                            if (char === '"') {
                                if (insideQuotes && nextChar === '"') {
                                    // Double quote escape
                                    current += '"';
                                    i++;
                                } else {
                                    // Toggle quote state
                                    insideQuotes = !insideQuotes;
                                }
                            } else if (char === ',' && !insideQuotes) {
                                // End of field
                                result.push(current);
                                current = '';
                            } else {
                                current += char;
                            }
                        }
                        result.push(current);
                        return result;
                    }
                    
                    // Parse header
                    const header = parseCSVLine(lines[0]).map(h => h.trim().toLowerCase());
                    
                    // Determine which rate type this is - check specific formats first
                    const has40ST = header.some(h => h.includes('40st'));
                    const hasBaseRate = header.some(h => h.includes('base'));
                    const hasFuelSurcharge = header.some(h => h.includes('fuel') || h.includes('surcharge'));
                    const hasDestination = header.some(h => h.includes('destination'));
                    
                    // LOCAL = Destination + Base Rate + Fuel Surcharge (3 columns)
                    const isLOCAL = hasDestination && hasBaseRate && hasFuelSurcharge && header.length === 3;
                    // RAIL EXPORT = Base Rate present AND a "rail" token in the header -> Rail Export section
                    const isRAILEXPORT = hasBaseRate && header.some(h => h.includes('rail'));
                    // EXPORT = has Base Rate (different from LOCAL and Rail Export)
                    const isEXPORT = hasBaseRate && !isLOCAL && !isRAILEXPORT;
                    // RAIL = Destination + a 40'/45' column + a 20' column, with no 40ST and no Base Rate
                    const isRAIL = hasDestination && !has40ST && !hasBaseRate
                        && header.some(h => h.includes('45'))
                        && header.some(h => h.includes('20'));
                    
                    console.log('CSV Headers:', header);
                    console.log('isLOCAL:', isLOCAL, 'isEXPORT:', isEXPORT, 'has40ST:', has40ST);
                    
                    let importedCount = 0;
                    
                    if (has40ST) {
                        // IMPORT: Destination,40ST_HC,20_45,NOR_REEFER
                        const importRates = [];
                        
                        // Find column indices
                        let destIdx = header.findIndex(h => h.includes('destination'));
                        let stIdx = header.findIndex(h => h.includes('40st'));
                        let rtIdx = header.findIndex(h => h.includes('20') && h.includes('45'));
                        let norIdx = header.findIndex(h => h.includes('nor'));
                        
                        for (let i = 1; i < lines.length; i++) {
                            if (!lines[i].trim()) continue;
                            
                            const cols = parseCSVLine(lines[i]).map(c => c.trim());
                            if (cols.length < 4) continue;
                            
                            const rate = {
                                destination: cols[destIdx] || cols[0],
                                "40ST_HC": parseFloat(cols[stIdx] || cols[1]),
                                "20_45": parseFloat(cols[rtIdx] || cols[2]),
                                "NOR_REEFER": parseFloat(cols[norIdx] || cols[3]),
                                dropPickFree: false
                            };
                            
                            if (rate.destination && !isNaN(rate["40ST_HC"])) {
                                importRates.push(rate);
                                importedCount++;
                            }
                        }
                        
                        if (importRates.length > 0) {
                            rateData.import.rates = importRates;
                            rateData.lastUpdated = new Date().toISOString().split('T')[0];
                            localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                            renderRates();
                            
                            statusDiv.textContent = `✓ Successfully imported ${importedCount} import rates`;
                            statusDiv.className = 'status success';
                            fileInput.value = '';
                        }
                    } else if (isLOCAL) {
                        // LOCAL rates format: Destination, Base Rate, Fuel Surcharge (exactly 3 columns)
                        console.log('Importing LOCAL rates...');
                        const localRates = [];
                        
                        // Find column indices
                        let destIdx = header.findIndex(h => h.includes('destination'));
                        let baseRateIdx = header.findIndex(h => h.includes('base'));
                        let fscIdx = header.findIndex(h => h.includes('fuel') || h.includes('surcharge'));
                        
                        for (let i = 1; i < lines.length; i++) {
                            if (!lines[i].trim()) continue;
                            
                            const cols = parseCSVLine(lines[i]).map(c => c.trim());
                            if (cols.length < 3) continue;
                            
                            const baseRate = parseFloat(cols[baseRateIdx] || cols[1]);
                            const fuelSurcharge = parseFloat(cols[fscIdx] || cols[2]);
                            const totalRate = (baseRate * (1 + fuelSurcharge / 100)).toFixed(2);
                            
                            const rate = {
                                destination: cols[destIdx] || cols[0],
                                baseRate: baseRate,
                                fuelSurcharge: fuelSurcharge,
                                totalRate: totalRate,
                                dropPickFree: false
                            };
                            
                            if (rate.destination && !isNaN(rate.baseRate)) {
                                localRates.push(rate);
                                importedCount++;
                            }
                        }
                        
                        if (localRates.length > 0) {
                            rateData.local.rates = localRates;
                            rateData.lastUpdated = new Date().toISOString().split('T')[0];
                            localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                            renderLocalRates();
                            
                            statusDiv.textContent = `✓ Successfully imported ${importedCount} local rates`;
                            statusDiv.className = 'status success';
                            fileInput.value = '';
                        }
                    } else if (isRAILEXPORT) {
                        // RAIL EXPORT: Pickup Location, Base Rate, FSC, Total Rate -> writes ONLY to rateData.exportRail (never rateData.export)
                        console.log('Importing RAIL EXPORT rates...');
                        const railExportRates = [];
                        
                        let destIdx = header.findIndex(h => h.includes('pickup') || h.includes('location') || h.includes('destination'));
                        let baseIdx = header.findIndex(h => h.includes('base'));
                        let fscIdx = header.findIndex(h => h.includes('fsc') || h.includes('fuel') || h.includes('surcharge'));
                        let totalIdx = header.findIndex(h => h.includes('total'));
                        let dropIdx = header.findIndex(h => h.includes('drop') || h.includes('pick'));
                        let storageIdx = header.findIndex(h => h.includes('storage'));
                        
                        const truthy = v => /^(true|yes|y|1)$/i.test((v || '').trim());
                        
                        for (let i = 1; i < lines.length; i++) {
                            if (!lines[i].trim()) continue;
                            const cols = parseCSVLine(lines[i]).map(c => c.trim());
                            if (cols.length < 3) continue;
                            
                            const baseRate = parseFloat(baseIdx >= 0 ? cols[baseIdx] : cols[1]);
                            const fuelSurcharge = parseFloat(fscIdx >= 0 ? cols[fscIdx] : cols[2]);
                            const totalRate = totalIdx >= 0 && cols[totalIdx] !== undefined && cols[totalIdx] !== ''
                                ? parseFloat(cols[totalIdx])
                                : parseFloat((baseRate * (1 + fuelSurcharge / 100)).toFixed(2));
                            
                            const rate = {
                                destination: cols[destIdx] || cols[0],
                                baseRate: baseRate,
                                fuelSurcharge: fuelSurcharge,
                                totalRate: totalRate,
                                dropPickFree: dropIdx >= 0 ? truthy(cols[dropIdx]) : false,
                                freeStorage: storageIdx >= 0 ? truthy(cols[storageIdx]) : true
                            };
                            
                            if (rate.destination && !isNaN(rate.baseRate)) {
                                railExportRates.push(rate);
                                importedCount++;
                            }
                        }
                        
                        if (railExportRates.length > 0) {
                            if (!rateData.exportRail) {
                                rateData.exportRail = { description: "Rail Export (Phoenix Ramp to LA/LB)", rates: [] };
                            }
                            rateData.exportRail.rates = railExportRates;
                            rateData.lastUpdated = new Date().toISOString().split('T')[0];
                            localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                            renderExportRailRates();
                            
                            statusDiv.textContent = `✓ Successfully imported ${importedCount} rail export rates`;
                            statusDiv.className = 'status success';
                            fileInput.value = '';
                        }
                    } else if (isEXPORT) {
                        // EXPORT rates - flexible format
                        const exportRates = [];
                        
                        // Find column indices (flexible matching)
                        let destIdx = header.findIndex(h => h.includes('destination') || h.includes('loaded') || h.includes('ship'));
                        let baseIdx = header.findIndex(h => h.includes('base'));
                        let fscIdx = header.findIndex(h => h.includes('fuel') || h.includes('surcharge'));
                        let totalIdx = header.findIndex(h => h.includes('total'));
                        
                        for (let i = 1; i < lines.length; i++) {
                            if (!lines[i].trim()) continue;
                            
                            const cols = parseCSVLine(lines[i]).map(c => c.trim());
                            if (cols.length < 3) continue;
                            
                            const rate = {
                                destination: cols[destIdx] || cols[0],
                                baseRate: parseFloat(cols[baseIdx] || cols[1]),
                                fuelSurcharge: parseFloat(cols[fscIdx] || cols[2]),
                                totalRate: parseFloat(cols[totalIdx] || cols[3]),
                                dropPickFree: false
                            };
                            
                            if (rate.destination && !isNaN(rate.baseRate)) {
                                exportRates.push(rate);
                                importedCount++;
                            }
                        }
                        
                        if (exportRates.length > 0) {
                            rateData.export.rates = exportRates;
                            rateData.lastUpdated = new Date().toISOString().split('T')[0];
                            localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                            renderExportRates();
                            
                            statusDiv.textContent = `✓ Successfully imported ${importedCount} export rates`;
                            statusDiv.className = 'status success';
                            fileInput.value = '';
                        }
                    } else if (isRAIL) {
                        // IMPORT RAIL: Destination, 40'/45', 20' -> writes ONLY to rateData.importRail (never rateData.import)
                        console.log('Importing IMPORT RAIL rates...');
                        const railRates = [];

                        let destIdx = header.findIndex(h => h.includes('destination'));
                        let idx4045 = header.findIndex(h => h.includes('45'));
                        let idx20 = header.findIndex(h => h.includes('20'));

                        for (let i = 1; i < lines.length; i++) {
                            if (!lines[i].trim()) continue;
                            const cols = parseCSVLine(lines[i]).map(c => c.trim());
                            if (cols.length < 3) continue;

                            const rate = {
                                destination: cols[destIdx] || cols[0],
                                "40_45": parseFloat(cols[idx4045] || cols[1]),
                                "20": parseFloat(cols[idx20] || cols[2]),
                                dropPickFree: false,
                                freeStorage: true
                            };

                            if (rate.destination && !isNaN(rate["40_45"])) {
                                railRates.push(rate);
                                importedCount++;
                            }
                        }

                        if (railRates.length > 0) {
                            if (!rateData.importRail) {
                                rateData.importRail = { description: "Import Rail (Ramp to Destination)", rates: [] };
                            }
                            rateData.importRail.rates = railRates;
                            rateData.lastUpdated = new Date().toISOString().split('T')[0];
                            localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                            renderRailRates();

                            statusDiv.textContent = `✓ Successfully imported ${importedCount} import rail rates`;
                            statusDiv.className = 'status success';
                            fileInput.value = '';
                        }
                    } else {
                        statusDiv.textContent = '❌ CSV format not recognized. Use one of: "Destination, 40ST_HC, 20_45, NOR_REEFER" (IMPORT) | "Destination, 40\' / 45\', 20\'" (IMPORT RAIL) | "Destination, Base Rate, Fuel Surcharge" (LOCAL with 3 columns) | "Destination, Base Rate, Fuel Surcharge, Total Rate" (EXPORT) | "Rail Pickup Location, Base Rate, FSC (%), Total Rate" (RAIL EXPORT)';
                        statusDiv.className = 'status error';
                    }
                } catch (error) {
                    statusDiv.textContent = `❌ Error parsing CSV: ${error.message}`;
                    statusDiv.className = 'status error';
                }
            };
            
            reader.readAsText(file);
        }

        function updateFSC() {
            const newFSC = parseFloat(document.getElementById('fscInput').value);
            
            if (isNaN(newFSC) || newFSC < 0) {
                alert('Please enter a valid FSC value');
                return;
            }
            
            rateData.fsc = newFSC;
            rateData.lastUpdated = new Date().toISOString().split('T')[0];
            
            try {
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                const status = document.getElementById('fscStatus');
                status.textContent = `✓ FSC updated to ${newFSC.toFixed(2)} on ${rateData.lastUpdated}`;
                status.classList.remove('info');
                status.classList.add('success');
                setTimeout(() => {
                    status.textContent = 'Enter FSC and click Update';
                    status.classList.remove('success');
                    status.classList.add('info');
                }, 3000);
            } catch (error) {
                alert('Error updating FSC: ' + error.message);
            }
        }

        function saveRates() {
            const inputs = document.querySelectorAll('.rate-input');
            const dropPickCheckboxes = document.querySelectorAll('.drop-pick-checkbox');
            const storageCheckboxes = document.querySelectorAll('.storage-checkbox');
            
            inputs.forEach(input => {
                const destination = input.dataset.dest;
                const field = input.dataset.field;
                const value = parseFloat(input.value);
                
                const rateRow = rateData.import.rates.find(r => r.destination === destination);
                if (rateRow && !isNaN(value)) {
                    rateRow[field] = value;
                }
            });
            
            dropPickCheckboxes.forEach(checkbox => {
                const destination = checkbox.dataset.dest;
                const rateRow = rateData.import.rates.find(r => r.destination === destination);
                if (rateRow) {
                    rateRow.dropPickFree = checkbox.checked;
                }
            });
            
            storageCheckboxes.forEach(checkbox => {
                const destination = checkbox.dataset.dest;
                const rateRow = rateData.import.rates.find(r => r.destination === destination);
                if (rateRow) {
                    rateRow.freeStorage = checkbox.checked;
                }
            });
            
            rateData.lastUpdated = new Date().toISOString().split('T')[0];
            
            try {
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);
                alert('Rates saved successfully!');
                toggleEditMode();
                loadRates();
            } catch (error) {
                alert('Error saving rates: ' + error.message);
            }
        }

        // ============ IMPORT RAIL FUNCTIONS ============
        let isRailEditMode = false;

        function renderRailRates() {
            const tbody = document.getElementById('railRatesTableBody');
            if (!tbody || !rateData.importRail || !rateData.importRail.rates) return;
            tbody.innerHTML = rateData.importRail.rates.map(row => `
                <tr>
                    <td class="destination-cell">${row.destination}</td>
                    <td>
                        <div class="rate-display">$${parseFloat(row["40_45"]).toFixed(2)}</div>
                        <input type="number" class="rail-rate-input" data-dest="${row.destination}" data-field="40_45" value="${row["40_45"]}" step="0.01">
                    </td>
                    <td>
                        <div class="rate-display">$${parseFloat(row["20"]).toFixed(2)}</div>
                        <input type="number" class="rail-rate-input" data-dest="${row.destination}" data-field="20" value="${row["20"]}" step="0.01">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="rail-drop-pick-checkbox" data-dest="${row.destination}" ${row.dropPickFree ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                    <td style="text-align: center;">
                        <input type="checkbox" class="rail-storage-checkbox" data-dest="${row.destination}" ${row.freeStorage !== false ? 'checked' : ''} style="width: 18px; height: 18px; cursor: pointer;">
                    </td>
                </tr>
            `).join('');
        }

        function toggleRailEditMode() {
            isRailEditMode = !isRailEditMode;
            const tbody = document.getElementById('railRatesTableBody');
            if (isRailEditMode) {
                tbody.classList.add('edit-mode');
                document.getElementById('toggleRailBtn').textContent = 'Cancel';
                document.getElementById('saveRailBtn').style.display = 'inline-block';
            } else {
                tbody.classList.remove('edit-mode');
                document.getElementById('toggleRailBtn').textContent = 'Edit Rates';
                document.getElementById('saveRailBtn').style.display = 'none';
                loadRates();
            }
        }

        function saveRailRates() {
            try {
                const inputs = document.querySelectorAll('.rail-rate-input:not([readonly])');
                const dropPickCheckboxes = document.querySelectorAll('.rail-drop-pick-checkbox');
                const storageCheckboxes = document.querySelectorAll('.rail-storage-checkbox');

                inputs.forEach(input => {
                    const dest = input.getAttribute('data-dest');
                    const field = input.getAttribute('data-field');
                    let value = parseFloat(input.value);
                    const rate = rateData.importRail.rates.find(r => r.destination === dest);
                    if (rate) { rate[field] = value; }
                });

                dropPickCheckboxes.forEach(checkbox => {
                    const rate = rateData.importRail.rates.find(r => r.destination === checkbox.dataset.dest);
                    if (rate) { rate.dropPickFree = checkbox.checked; }
                });

                storageCheckboxes.forEach(checkbox => {
                    const rate = rateData.importRail.rates.find(r => r.destination === checkbox.dataset.dest);
                    if (rate) { rate.freeStorage = checkbox.checked; }
                });

                rateData.lastUpdated = new Date().toISOString().split('T')[0];
                localStorage.setItem('dsl_rates', JSON.stringify(rateData)); pushToFirebase(rateData);

                document.getElementById('lastUpdated').textContent = rateData.lastUpdated;
                isRailEditMode = false;
                renderRailRates();
                document.getElementById('toggleRailBtn').textContent = 'Edit Rates';
                document.getElementById('saveRailBtn').style.display = 'none';

                alert('Import Rail rates saved successfully!');
            } catch (error) {
                console.error('Error saving rail rates:', error);
                alert('Error saving rail rates: ' + error.message);
            }
        }

        // ============ BACKUP & RESTORE FUNCTIONS ============
        
        function downloadBackup() {
            try {
                const data = localStorage.getItem('dsl_rates');
                if (!data) {
                    showBackupStatus('❌ No data to backup. Add some rates first.', 'error');
                    return;
                }
                
                const backup = {
                    timestamp: new Date().toISOString(),
                    version: '1.0',
                    data: JSON.parse(data)
                };
                
                const json = JSON.stringify(backup, null, 2);
                const blob = new Blob([json], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = `DSL_Rates_Backup_${new Date().toISOString().split('T')[0]}.json`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                
                showBackupStatus(`✅ Backup downloaded: ${a.download}`, 'success');
            } catch (error) {
                showBackupStatus('❌ Error downloading backup: ' + error.message, 'error');
            }
        }
        
        function uploadBackupClick() {
            document.getElementById('backupUpload').click();
        }
        
        document.addEventListener('DOMContentLoaded', function() {
            const backupUploadInput = document.getElementById('backupUpload');
            if (backupUploadInput) {
                backupUploadInput.addEventListener('change', uploadBackup);
            }
        });
        
        function uploadBackup(event) {
            try {
                const file = event.target.files[0];
                if (!file) return;
                
                const reader = new FileReader();
                reader.onload = function(e) {
                    try {
                        const backup = JSON.parse(e.target.result);
                        
                        if (!backup.data) {
                            showBackupStatus('❌ Invalid backup file format', 'error');
                            return;
                        }
                        
                        if (confirm('⚠️ This will overwrite all current rates.\n\nAre you sure you want to restore from this backup?\n\n' + backup.timestamp)) {
                            localStorage.setItem('dsl_rates', JSON.stringify(backup.data)); pushToFirebase(backup.data);
                            showBackupStatus(`✅ Backup restored from ${backup.timestamp}`, 'success');
                            
                            setTimeout(() => {
                                location.reload();
                            }, 1500);
                        } else {
                            showBackupStatus('⏸️ Restore cancelled', 'info');
                        }
                    } catch (parseError) {
                        showBackupStatus('❌ Invalid JSON file', 'error');
                    }
                };
                reader.readAsText(file);
            } catch (error) {
                showBackupStatus('❌ Error uploading backup: ' + error.message, 'error');
            }
        }
        
        function clearAllDataWithConfirm() {
            const warning = '⚠️ WARNING: This will DELETE ALL RATES!\n\n' +
                           'Make sure you have downloaded a backup first.\n\n' +
                           'Type "DELETE" below to confirm:\n';
            
            const userInput = prompt(warning);
            
            if (userInput === 'DELETE') {
                try {
                    localStorage.removeItem('dsl_rates');
                    showBackupStatus('✅ All data cleared. Page will reload...', 'success');
                    setTimeout(() => {
                        location.reload();
                    }, 1500);
                } catch (error) {
                    showBackupStatus('❌ Error clearing data: ' + error.message, 'error');
                }
            } else if (userInput !== null) {
                showBackupStatus('❌ Confirmation failed. Data NOT cleared.', 'error');
            }
        }
        
        function showBackupStatus(message, type) {
            const statusEl = document.getElementById('backupStatus');
            statusEl.textContent = message;
            statusEl.className = 'status ' + type;
        }

        // Push current rates to Firebase so the Quote Generator can read them from any device
        function pushToFirebase(data) {
            fetch('https://rate-manager-dsl-default-rtdb.firebaseio.com/rates.json', {
                method: 'PUT',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(data)
            }).catch(e => console.warn('Firebase sync failed:', e));
        }

        // Load rates on page load
        loadRates();
    </script>
</body>
</html>
