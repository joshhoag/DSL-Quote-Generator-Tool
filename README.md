[DSL_Rate_Manager_12_1.html](https://github.com/user-attachments/files/31524178/DSL_Rate_Manager_12_1.html)
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
