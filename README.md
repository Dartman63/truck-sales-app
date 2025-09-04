FLOWCustomer One
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Peach State Truck Sales - Visit Logger</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', sans-serif;
            background-color: #f9fafb;
        }
        
        .header {
            background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .header h1 {
            font-size: 1.25rem;
            font-weight: bold;
        }
        
        .privacy-btn {
            background: #10b981;
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 1rem;
            border: none;
            font-size: 0.875rem;
        }
        
        .privacy-btn.private {
            background: #374151;
        }
        
        .ai-section {
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
            color: white;
            padding: 1rem;
        }
        
        .ai-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.5rem;
        }
        
        .rep-select {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 0.5rem;
            border-radius: 0.25rem;
            font-size: 0.875rem;
        }
        
        .rep-select option {
            color: #374151;
        }
        
        .stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 0.75rem;
            margin: 1rem;
        }
        
        .stat-card {
            background: white;
            padding: 1rem;
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #1f2937;
        }
        
        .stat-label {
            font-size: 0.75rem;
            color: #6b7280;
            margin-top: 0.25rem;
        }
        
        .search-section {
            margin: 1rem;
        }
        
        .search-bar {
            display: flex;
            gap: 0.5rem;
        }
        
        .search-input {
            flex: 1;
            padding: 0.75rem;
            border: 1px solid #d1d5db;
            border-radius: 0.5rem;
            font-size: 1rem;
        }
        
        .add-btn {
            background: #10b981;
            color: white;
            padding: 0.75rem 1rem;
            border: none;
            border-radius: 0.5rem;
            font-weight: 500;
            cursor: pointer;
        }
        
        .customer-list {
            margin: 1rem;
        }
        
        .section-title {
            font-weight: 600;
            margin-bottom: 0.75rem;
            color: #374151;
        }
        
        .customer-card {
            background: white;
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
            margin-bottom: 0.75rem;
            overflow: hidden;
        }
        
        .customer-btn {
            width: 100%;
            text-align: left;
            border: none;
            background: none;
            padding: 1rem;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        
        .customer-btn:hover {
            background-color: #eff6ff;
        }
        
        .customer-header {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.25rem;
            flex-wrap: wrap;
        }
        
        .customer-name {
            font-size: 1.125rem;
            font-weight: 600;
            color: #111827;
        }
        
        .status-badge {
            font-size: 0.75rem;
            padding: 0.25rem 0.5rem;
            border-radius: 9999px;
            font-weight: 500;
        }
        
        .status-customer {
            background: #dcfce7;
            color: #166534;
        }
        
        .status-prospect {
            background: #fed7aa;
            color: #9a3412;
        }
        
        .customer-details {
            font-size: 0.875rem;
            color: #4b5563;
            line-height: 1.5;
        }
        
        .customer-meta {
            display: flex;
            gap: 0.75rem;
            font-size: 0.75rem;
            color: #6b7280;
            margin-top: 0.25rem;
        }
        
        .intelligence-preview {
            background: linear-gradient(135deg, #eff6ff 0%, #f3f4f6 100%);
            border-top: 1px solid #e5e7eb;
            padding: 0.75rem 1rem;
            font-size: 0.875rem;
        }
        
        .intel-item {
            display: flex;
            align-items: flex-start;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
        }
        
        .intel-label {
            font-weight: 500;
            color: #374151;
        }
        
        .intel-text {
            color: #4b5563;
        }
        
        /* Modal Styles */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 1rem;
        }
        
        .modal-content {
            background: white;
            border-radius: 0.5rem;
            padding: 1.5rem;
            width: 100%;
            max-width: 500px;
            max-height: 80vh;
            overflow-y: auto;
        }
        
        .modal-header {
            font-size: 1.25rem;
            font-weight: bold;
            margin-bottom: 1rem;
            color: #111827;
        }
        
        .form-group {
            margin-bottom: 1rem;
        }
        
        .form-input {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #d1d5db;
            border-radius: 0.5rem;
            font-size: 1rem;
        }
        
        .form-select {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #d1d5db;
            border-radius: 0.5rem;
            font-size: 1rem;
            background: white;
        }
        
        .modal-buttons {
            display: flex;
            gap: 0.5rem;
            margin-top: 1.5rem;
        }
        
        .btn-primary {
            flex: 1;
            padding: 0.75rem;
            background: #10b981;
            color: white;
            border: none;
            border-radius: 0.5rem;
            font-weight: 500;
            cursor: pointer;
        }
        
        .btn-primary:disabled {
            background: #9ca3af;
            cursor: not-allowed;
        }
        
        .btn-secondary {
            flex: 1;
            padding: 0.75rem;
            background: transparent;
            color: #6b7280;
            border: none;
            border-radius: 0.5rem;
            cursor: pointer;
        }
        
        /* Visit screen styles */
        .visit-header {
            background: #10b981;
            color: white;
            padding: 1rem;
        }
        
        .visit-title {
            font-size: 0.875rem;
            opacity: 0.9;
        }
        
        .visit-customer {
            font-size: 1.25rem;
            font-weight: bold;
        }
        
        .visit-meta {
            font-size: 0.75rem;
            margin-top: 0.25rem;
        }
        
        .intelligence-panel {
            background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
            color: white;
            padding: 1rem;
        }
        
        .intel-header {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.75rem;
            font-weight: 600;
        }
        
        .intel-cards {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }
        
        .intel-card {
            background: rgba(255, 255, 255, 0.2);
            padding: 0.5rem;
            border-radius: 0.25rem;
            font-size: 0.875rem;
        }
        
        .visit-form {
            padding: 1rem;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }
        
        .form-section {
            background: white;
            padding: 1rem;
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
        }
        
        .form-label {
            font-size: 0.875rem;
            font-weight: 500;
            color: #374151;
            margin-bottom: 0.5rem;
            display: block;
        }
        
        .form-textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #d1d5db;
            border-radius: 0.5rem;
            min-height: 100px;
            font-family: inherit;
            font-size: 1rem;
            resize: vertical;
        }
        
        .outcome-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 0.5rem;
        }
        
        .outcome-btn {
            padding: 0.75rem;
            border: 1px solid #d1d5db;
            border-radius: 0.5rem;
            background: #f9fafb;
            font-size: 0.875rem;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .outcome-btn.selected {
            background: #dbeafe;
            border-color: #3b82f6;
            color: #1d4ed8;
        }
        
        .followup-btn {
            width: 100%;
            padding: 1rem;
            border: 2px solid #d1d5db;
            border-radius: 0.5rem;
            background: white;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .followup-btn.active {
            border-color: #f97316;
            background: #fff7ed;
            color: #ea580c;
            font-weight: 500;
        }
        
        .complete-btn {
            width: 100%;
            padding: 1rem;
            background: #10b981;
            color: white;
            border: none;
            border-radius: 0.5rem;
            font-size: 1.125rem;
            font-weight: bold;
            cursor: pointer;
        }
        
        .hidden {
            display: none;
        }
        
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                gap: 0.5rem;
            }
            
            .ai-header {
                flex-direction: column;
                gap: 0.5rem;
            }
            
            .outcome-grid {
                grid-template-columns: 1fr;
            }
            
            .customer-meta {
                flex-direction: column;
                gap: 0.25rem;
            }
        }
    </style>
</head>
<body>
    <!-- Home Screen -->
    <div id="homeScreen">
        <!-- Header -->
        <div class="header">
            <h1>🚛 Peach State Truck Sales</h1>
            <button class="privacy-btn" id="privacyBtn">👁️ Sharing</button>
        </div>
        
        <!-- AI Assistant Section -->
        <div class="ai-section">
            <div class="ai-header">
                <div>
                    <div style="font-weight: 600; margin-bottom: 0.25rem;">✨ Truck Sales AI Assistant</div>
                </div>
                <select class="rep-select" id="repSelect">
                    <option value="mike">Mike Sullivan - Norcross Truck Sales Rep</option>
                    <option value="sarah">Sarah Johnson - Norcross Truck Sales Rep</option>
                    <option value="david">David Wilson - Norcross Truck Sales Rep</option>
                    <option value="lisa">Lisa Martinez - Norcross Truck Sales Rep</option>
                </select>
            </div>
            <div style="font-size: 0.875rem; opacity: 0.9;">Customer intelligence and equipment recommendations ready</div>
        </div>
        
        <!-- Stats -->
        <div class="stats">
            <div class="stat-card">
                <div class="stat-number" id="visitsToday">0</div>
                <div class="stat-label">Visits Today</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="peachStateCustomers">2</div>
                <div class="stat-label">Peach State Customer</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="prospects">1</div>
                <div class="stat-label">Prospect</div>
            </div>
        </div>
        
        <!-- Search -->
        <div class="search-section">
            <div class="search-bar">
                <input type="text" class="search-input" placeholder="Search accounts..." id="searchInput">
                <button class="add-btn" id="addBtn">+ Add</button>
            </div>
        </div>
        
        <!-- Customer List -->
        <div class="customer-list">
            <div class="section-title">Visits (<span id="accountCount">3</span> accounts for <span id="currentDate"></span>)</div>
            <div id="customerContainer">
                <!-- Customers will be loaded here -->
            </div>
        </div>
    </div>
    
    <!-- Add Customer Modal -->
    <div id="addCustomerModal" class="modal hidden">
        <div class="modal-content">
            <div class="modal-header">Add New Customer Account</div>
            <form id="addCustomerForm">
                <div class="form-group">
                    <input type="text" class="form-input" placeholder="Company Name *" id="companyName" required>
                </div>
                <div class="form-group">
                    <input type="text" class="form-input" placeholder="Contact Name & Title" id="contactName">
                </div>
                <div class="form-group">
                    <input type="tel" class="form-input" placeholder="Phone" id="contactPhone">
                </div>
                <div class="form-group">
                    <input type="email" class="form-input" placeholder="Email" id="contactEmail">
                </div>
                <div class="form-group">
                    <input type="text" class="form-input" placeholder="Address" id="contactAddress">
                </div>
                <div class="form-group">
                    <select class="form-select" id="fleetType">
                        <option value="OTR/Long Haul">OTR/Long Haul</option>
                        <option value="Regional Delivery">Regional Delivery</option>
                        <option value="Local/P&D">Local/P&D</option>
                        <option value="Vocational/Construction">Vocational/Construction</option>
                        <option value="Last Mile/Local">Last Mile/Local</option>
                        <option value="Owner-Operator">Owner-Operator</option>
                    </select>
                </div>
                <div class="form-group">
                    <input type="number" class="form-input" placeholder="Current Fleet Size" id="fleetSize">
                </div>
                <div class="form-group">
                    <input type="text" class="form-input" placeholder="Current Truck Brands (Freightliner, Peterbilt, etc.)" id="truckBrands">
                </div>
                <div class="modal-buttons">
                    <button type="submit" class="btn-primary" id="submitCustomer">Add Customer & Start Visit</button>
                    <button type="button" class="btn-secondary" id="cancelAdd">Cancel</button>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Visit Screen -->
    <div id="visitScreen" class="hidden">
        <!-- Visit Header -->
        <div class="visit-header">
            <div class="visit-title">Customer Visit in Progress</div>
            <div class="visit-customer" id="visitCustomerName">Customer Name</div>
            <div class="visit-meta" id="visitCustomerMeta">Fleet Type • Size</div>
        </div>
        
        <!-- Customer Intelligence -->
        <div class="intelligence-panel" id="intelligencePanel">
            <div class="intel-header">
                🚛 Customer Intelligence
            </div>
            <div class="intel-cards" id="intelCards">
                <!-- Intelligence will be loaded here -->
            </div>
        </div>
        
        <!-- AI Sales Tips -->
        <div style="background: #fef3c7; border-left: 4px solid #f59e0b; padding: 1rem;" id="salesTips">
            <div style="display: flex; gap: 0.5rem;">
                <div style="color: #d97706;">✨</div>
                <div>
                    <div style="font-weight: 600; color: #374151; margin-bottom: 0.25rem;">Sales Tip:</div>
                    <div style="color: #4b5563; font-size: 0.875rem;" id="salesTipText">🚛 Lead with: New equipment available - perfect for their operation</div>
                </div>
            </div>
        </div>
        
        <!-- Visit Form -->
        <div class="visit-form">
            <!-- Visit Discussion -->
            <div class="form-section">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.5rem;">
                    <label class="form-label">Visit Discussion</label>
                    <button type="button" style="color: #3b82f6; text-decoration: underline; border: none; background: none; font-size: 0.875rem; cursor: pointer;">
                        🎤 Voice Notes
                    </button>
                </div>
                <textarea class="form-textarea" placeholder="Equipment discussed, customer needs, concerns..." id="visitNotes"></textarea>
            </div>
            
            <!-- Visit Outcome -->
            <div class="form-section">
                <label class="form-label">Truck Sales Visit Outcome</label>
                <div class="outcome-grid">
                    <button type="button" class="outcome-btn" onclick="selectOutcome(this, 'Truck Quote Requested')">📋 Truck Quote Requested</button>
                    <button type="button" class="outcome-btn" onclick="selectOutcome(this, 'Truck Demo Scheduled')">🚛 Truck Demo Scheduled</button>
                    <button type="button" class="outcome-btn" onclick="selectOutcome(this, 'Parts & Service Discussion')">🔧 Parts & Service Discussion</button>
                    <button type="button" class="outcome-btn" onclick="selectOutcome(this, 'Trade-In Evaluation')">💰 Trade-In Evaluation</button>
                    <button type="button" class="outcome-btn" onclick="selectOutcome(this, 'Financing Discussion')">💳 Financing Discussion</button>
                    <button type="button" class="outcome-btn" onclick="selectOutcome(this, 'Customer Relationship Building')">🤝 Customer Relationship Building</button>
                </div>
            </div>
            
            <!-- Follow-up -->
            <button type="button" class="followup-btn" id="followupBtn" onclick="toggleFollowup()">
                Need Follow-up?
            </button>
            
            <!-- Complete Visit -->
            <button type="button" class="complete-btn" onclick="completeVisit()">Complete Customer Visit</button>
        </div>
    </div>

    <script>
        // Global variables
        let currentCustomer = null;
        let currentRep = 'mike';
        let selectedOutcome = '';
        let needsFollowup = false;
        let visitCount = 0;
        let privacyMode = false;
        
        // Customer database for each rep
        const customerDatabase = {
            mike: [
                {
                    id: 1,
                    name: 'TransPacific Logistics',
                    contact: 'James Mitchell - VP Operations',
                    phone: '(404) 555-0123',
                    email: 'jmitchell@transpac.com',
                    address: '3455 Peachtree Industrial Blvd, Atlanta, GA',
                    fleetType: 'OTR/Long Haul',
                    fleetSize: 247,
                    truckBrands: 'Freightliner, Western Star',
                    status: 'Peach State Customer',
                    serviceContract: 'Premium - Expires March 2025',
                    lastVisit: '2 days ago',
                    hasIntelligence: true,
                    intelligence: {
                        needs: '15-20 Cascadia units for Q2 expansion',
                        specs: 'Detroit DD15, DT12 automatic, 72" sleeper',
                        decision: 'James Mitchell (VP) specs equipment',
                        tradeIns: '47 units approaching trade-in age (2019-2020)',
                        opportunity: '🔥 Immediate: 2020 fleet reaching 5-year replacement'
                    }
                },
                {
                    id: 2,
                    name: 'Southern Freight Lines',
                    contact: 'Robert Johnson - Fleet Manager',
                    phone: '(770) 555-0234',
                    email: 'rjohnson@southern.com',
                    address: '2100 Marietta Hwy, Canton, GA',
                    fleetType: 'Regional Delivery',
                    fleetSize: 89,
                    truckBrands: 'Freightliner',
                    status: 'Peach State Customer',
                    serviceContract: 'Basic - Month-to-month',
                    lastVisit: '1 week ago',
                    hasIntelligence: true,
                    intelligence: {
                        needs: 'Upgrading 10 regional units',
                        specs: 'Day cabs, Detroit DD13, manual preferred',
                        decision: 'Robert makes all decisions',
                        tradeIns: 'Keeps trucks 7-8 years typically',
                        opportunity: '📈 Growth: Adding new Amazon routes'
                    }
                },
                {
                    id: 3,
                    name: 'Quick Haul Express',
                    contact: 'Tom Anderson - President',
                    phone: '(404) 555-0789',
                    email: 'tanderson@quickhaul.com',
                    address: '890 Commerce Dr, Decatur, GA',
                    fleetType: 'Regional Delivery',
                    fleetSize: 35,
                    truckBrands: 'Peterbilt',
                    status: 'Prospect',
                    serviceContract: 'None - Using Rush',
                    lastVisit: 'First meeting scheduled',
                    hasIntelligence: false
                }
            ],
            sarah: [
                {
                    id: 4,
                    name: 'Metro Delivery Services',
                    contact: 'David Park - Owner',
                    phone: '(678) 555-0456',
                    email: 'dpark@metrodelivery.com',
                    address: '1200 Satellite Blvd, Duluth, GA',
                    fleetType: 'Last Mile/Local',
                    fleetSize: 45,
                    truckBrands: 'Freightliner M2, Ford',
                    status: 'Peach State Customer',
                    serviceContract: 'None',
                    lastVisit: '2 weeks ago',
                    hasIntelligence: false
                },
                {
                    id: 5,
                    name: 'Atlanta Express Corp',
                    contact: 'Michelle Davis - Operations Manager',
                    phone: '(770) 555-0890',
                    email: 'mdavis@atlantaexpress.com',
                    address: '5600 Jimmy Carter Blvd, Norcross, GA',
                    fleetType: 'OTR/Long Haul',
                    fleetSize: 156,
                    truckBrands: 'Freightliner, Volvo',
                    status: 'Peach State Customer',
                    serviceContract: 'Premium - Active',
                    lastVisit: '5 days ago',
                    hasIntelligence: true,
                    intelligence: {
                        needs: '25 Cascadia units for new contracts',
                        specs: 'Detroit DD15, DT12 automatic, 72" sleeper',
                        decision: 'Michelle Davis handles specifications',
                        tradeIns: '2019-2020 Freightliners ready for trade',
                        opportunity: '🚛 Immediate: Ready to order 25 units'
                    }
                },
                {
                    id: 6,
                    name: 'North Georgia Transport',
                    contact: 'Kevin Brown - Fleet Director',
                    phone: '(678) 555-0234',
                    email: 'kbrown@ngtr.com',
                    address: '2400 Pleasant Hill Rd, Duluth, GA',
                    fleetType: 'Regional Delivery',
                    fleetSize: 28,
                    truckBrands: 'International',
                    status: 'Prospect',
                    serviceContract: 'None',
                    lastVisit: 'Cold call planned',
                    hasIntelligence: false
                }
            ],
            david: [
                {
                    id: 7,
                    name: 'Georgia Freight Solutions',
                    contact: 'Maria Rodriguez - Fleet Director',
                    phone: '(770) 555-0567',
                    email: 'mrodriguez@gafreight.com',
                    address: '4500 Logistics Way, Kennesaw, GA',
                    fleetType: 'OTR/Long Haul',
                    fleetSize: 78,
                    truckBrands: 'Kenworth, Mack',
                    status: 'Prospect',
                    serviceContract: 'None',
                    lastVisit: 'Cold call last month',
                    hasIntelligence: false
                },
                {
                    id: 8,
                    name: 'Peachtree Logistics',
                    contact: 'Brian Thompson - VP Fleet',
                    phone: '(404) 555-0678',
                    email: 'bthompson@peachtreelog.com',
                    address: '1800 Century Blvd, Atlanta, GA',
                    fleetType: 'OTR/Long Haul',
                    fleetSize: 134,
                    truckBrands: 'Freightliner, Peterbilt',
                    status: 'Peach State Customer',
                    serviceContract: 'Basic - Month-to-month',
                    lastVisit: '1 week ago',
                    hasIntelligence: true,
                    intelligence: {
                        needs: 'Replacing 12 aging Peterbilts',
                        specs: 'Cascadia, Detroit DD15, DT12, 72" sleeper',
                        decision: 'Brian Thompson makes final decisions',
                        tradeIns: 'Has 18 units ready for trade',
                        opportunity: '🎯 Hot prospect: Ready to standardize on Freightliner'
                    }
                }
            ],
            lisa: [
                {
                    id: 9,
                    name: 'Superior Transport LLC',
                    contact: 'Amanda White - Fleet Manager',
                    phone: '(678) 555-0789',
                    email: 'awhite@superiortrans.com',
                    address: '3200 Buford Dr, Buford, GA',
                    fleetType: 'Regional Delivery',
                    fleetSize: 67,
                    truckBrands: 'Freightliner, International',
                    status: 'Peach State Customer',
                    serviceContract: 'Premium - Active',
                    lastVisit: '3 days ago',
                    hasIntelligence: false
                },
                {
                    id: 10,
                    name: 'Gwinnett County Delivery',
                    contact: 'Carlos Rivera - Operations Director',
                    phone: '(770) 555-0345',
                    email: 'crivera@gwinnettdelivery.com',
                    address: '900 Harbins Rd, Dacula, GA',
                    fleetType: 'Last Mile/Local',
                    fleetSize: 52,
                    truckBrands: 'Ford, Isuzu',
                    status: 'Peach State Customer',
                    serviceContract: 'Basic - Month-to-month',
                    lastVisit: '1 week ago',
                    hasIntelligence: false
                },
                {
                    id: 11,
                    name: 'Southeast Hauling Co',
                    contact: 'Jason Miller - President',
                    phone: '(404) 555-0456',
                    email: 'jmiller@seahaul.com',
                    address: '1500 Old Peachtree Rd, Suwanee, GA',
                    fleetType: 'OTR/Long Haul',
                    fleetSize: 95,
                    truckBrands: 'Volvo, Mack',
                    status: 'Prospect',
                    serviceContract: 'None - Using Volvo dealer',
                    lastVisit: 'Initial contact made',
                    hasIntelligence: false
                }
            ]
        };
        
        // Initialize app
        document.addEventListener('DOMContentLoaded', function() {
            // Set current date
            const today = new Date().toLocaleDateString('en-US', { 
                weekday: 'long', 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            });
            document.getElementById('currentDate').textContent = today;
            
            // Load visit count from localStorage if available
            if (localStorage.getItem('visitCount')) {
                visitCount = parseInt(localStorage.getItem('visitCount'));
                document.getElementById('visitsToday').textContent = visitCount;
            }
            
            // Load initial customers
            loadCustomers();
            
            // Set up event listeners
            document.getElementById('repSelect').addEventListener('change', function() {
                currentRep = this.value;
                loadCustomers();
            });
            
            document.getElementById('addBtn').addEventListener('click', showAddModal);
            document.getElementById('cancelAdd').addEventListener('click', hideAddModal);
            document.getElementById('addCustomerForm').addEventListener('submit', addNewCustomer);
            
            document.getElementById('privacyBtn').addEventListener('click', function() {
                privacyMode = !privacyMode;
                if (privacyMode) {
                    this.textContent = '👁️‍🗨️ Private';
                    this.classList.add('private');
                } else {
                    this.textContent = '👁️ Sharing';
                    this.classList.remove('private');
                }
            });
            
            // Search functionality
            document.getElementById('searchInput').addEventListener('input', function() {
                const searchTerm = this.value.toLowerCase();
                const customers = document.querySelectorAll('.customer-card');
                
                customers.forEach(customer => {
                    const text = customer.textContent.toLowerCase();
                    if (text.includes(searchTerm)) {
                        customer.style.display = 'block';
                    } else {
                        customer.style.display = 'none';
                    }
                });
            });
        });
        
        // Load customers for current rep
        function loadCustomers() {
            const customers = customerDatabase[currentRep] || [];
            const container = document.getElementById('customerContainer');
            container.innerHTML = '';
            
            // Update stats
            const peachStateCount = customers.filter(c => c.status === 'Peach State Customer').length;
            const prospectCount = customers.filter(c => c.status === 'Prospect').length;
            
            document.getElementById('peachStateCustomers').textContent = peachStateCount;
            document.getElementById('prospects').textContent = prospectCount;
            document.getElementById('accountCount').textContent = customers.length;
            
            // Create customer cards
            customers.forEach(customer => {
                const customerCard = createCustomerCard(customer);
                container.appendChild(customerCard);
            });
        }
        
        // Create customer card HTML
        function createCustomerCard(customer) {
            const card = document.createElement('div');
            card.className = 'customer-card';
            
            const statusClass = customer.status === 'Peach State Customer' ? 'status-customer' : 'status-prospect';
            
            card.innerHTML = `
                <button class="customer-btn" onclick="startVisit(${customer.id})">
                    <div class="customer-header">
                        <div class="customer-name">${customer.name}</div>
                        <div class="status-badge ${statusClass}">${customer.status}</div>
                    </div>
                    <div class="customer-details">
                        ${customer.contact} • ${customer.phone}<br>
                        <div class="customer-meta">
                            <span>🚛 ${customer.fleetSize} units</span>
                            <span>${customer.truckBrands}</span>
                            <span>${customer.fleetType}</span>
                        </div>
                        <div class="customer-meta">
                            <span>Service: ${customer.serviceContract}</span>
                            <span>Last visit: ${customer.lastVisit}</span>
                        </div>
                    </div>
                </button>
                ${customer.hasIntelligence ? `
                <div class="intelligence-preview">
                    <div class="intel-item">
                        <div class="intel-label">🚛 Immediate Need:</div>
                        <div class="intel-text">${customer.intelligence.needs}</div>
                    </div>
                    <div class="intel-text">${customer.intelligence.opportunity}</div>
                </div>
                ` : ''}
            `;
            
            return card;
        }
        
        // Show add customer modal
        function showAddModal() {
            document.getElementById('addCustomerModal').classList.remove('hidden');
        }
        
        // Hide add customer modal
        function hideAddModal() {
            document.getElementById('addCustomerModal').classList.add('hidden');
            document.getElementById('addCustomerForm').reset();
        }
        
        // Add new customer
        function addNewCustomer(e) {
            e.preventDefault();
            
            const formData = new FormData(e.target);
            const newCustomer = {
                id: Date.now(),
                name: document.getElementById('companyName').value,
                contact: document.getElementById('contactName').value || 'Contact TBD',
                phone: document.getElementById('contactPhone').value || 'Phone TBD',
                email: document.getElementById('contactEmail').value || '',
                address: document.getElementById('contactAddress').value || '',
                fleetType: document.getElementById('fleetType').value,
                fleetSize: parseInt(document.getElementById('fleetSize').value) || 0,
                truckBrands: document.getElementById('truckBrands').value || 'TBD',
                status: 'Prospect',
                serviceContract: 'None',
                lastVisit: 'First Visit',
                hasIntelligence: false
            };
            
            // Add to current rep's customer list
            customerDatabase[currentRep].push(newCustomer);
            
            // Reload customers
            loadCustomers();
            
            // Hide modal
            hideAddModal();
            
            // Start visit with new customer
            startVisit(newCustomer.id);
        }
        
        // Start visit
        function startVisit(customerId) {
            const customers = customerDatabase[currentRep];
            const customer = customers.find(c => c.id === customerId);
            
            if (!customer) return;
            
            currentCustomer = customer;
            document.getElementById('visitCustomerName').textContent = customer.name;
            document.getElementById('visitCustomerMeta').textContent = `${customer.fleetType} • ${customer.fleetSize} units`;
            
            // Load intelligence if available
            const intelligencePanel = document.getElementById('intelligencePanel');
            const salesTips = document.getElementById('salesTips');
            
            if (customer.hasIntelligence && customer.intelligence) {
                intelligencePanel.classList.remove('hidden');
                salesTips.classList.remove('hidden');
                
                // Load intelligence cards
                const intelCards = document.getElementById('intelCards');
                intelCards.innerHTML = `
                    <div class="intel-card">
                        <strong>Customer Needs:</strong> ${customer.intelligence.needs}
                    </div>
                    <div class="intel-card">
                        <strong>Equipment Specs:</strong> ${customer.intelligence.specs}
                    </div>
                    <div class="intel-card">
                        <strong>Decision Process:</strong> ${customer.intelligence.decision}
                    </div>
                    <div class="intel-card">
                        <strong>Trade-ins:</strong> ${customer.intelligence.tradeIns}
                    </div>
                `;
                
                // Update sales tip
                document.getElementById('salesTipText').textContent = 
                    customer.status === 'Peach State Customer' 
                        ? '🚛 Lead with: New Cascadia Evolution in stock - perfect spec for their routes'
                        : '🎯 Focus on: Understanding their current pain points and equipment needs';
            } else {
                intelligencePanel.classList.add('hidden');
                document.getElementById('salesTipText').textContent = 
                    '🤝 Focus on: Building relationship and understanding their business needs';
            }
            
            // Switch to visit screen
            document.getElementById('homeScreen').classList.add('hidden');
            document.getElementById('visitScreen').classList.remove('hidden');
        }
        
        // Select outcome
        function selectOutcome(button, outcome) {
            // Remove previous selection
            document.querySelectorAll('.outcome-btn').forEach(btn => {
                btn.classList.remove('selected');
            });
            
            // Add selection to clicked button
            button.classList.add('selected');
            selectedOutcome = outcome;
        }
        
        // Toggle follow-up
        function toggleFollowup() {
            needsFollowup = !needsFollowup;
            const btn = document.getElementById('followupBtn');
            
            if (needsFollowup) {
                btn.textContent = '✓ Follow-up Required';
                btn.classList.add('active');
            } else {
                btn.textContent = 'Need Follow-up?';
                btn.classList.remove('active');
            }
        }
        
        // Complete visit
        function completeVisit() {
            if (!currentCustomer) return;
            
            // Increment visit count
            visitCount++;
            document.getElementById('visitsToday').textContent = visitCount;
            localStorage.setItem('visitCount', visitCount);
            
            // Show completion message
            const notes = document.getElementById('visitNotes').value;
            alert(`Visit completed with ${currentCustomer.name}!\n\nOutcome: ${selectedOutcome || 'Not specified'}\nFollow-up needed: ${needsFollowup ? 'Yes' : 'No'}${notes ? '\n\nNotes: ' + notes.substring(0, 100) + (notes.length > 100 ? '...' : '') : ''}`);
            
            // Reset form
            document.getElementById('visitNotes').value = '';
            document.querySelectorAll('.outcome-btn').forEach(btn => {
                btn.classList.remove('selected');
            });
            document.getElementById('followupBtn').classList.remove('active');
            document.getElementById('followupBtn').textContent = 'Need Follow-up?';
            
            selectedOutcome = '';
            needsFollowup = false;
            currentCustomer = null;
            
            // Return to home screen
            document.getElementById('visitScreen').classList.add('hidden');
            document.getElementById('homeScreen').classList.remove('hidden');
        }
    </script>
</body>
</html>
