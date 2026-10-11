!DOCTYPE html>
<html lang="en">
<head>
  <script type="module" src="/@vite/client"></script>

  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LEXENO Admin Portal | CRM & Partner Dashboard</title>
  <meta name="description" content="Official management portal for LEXENO - Loans, Cards & Insurance, Data Analytics, B2B Leads, and Channel Partner Operations.">
  
  <link rel="icon" type="image/jpeg" href="assets/lexeno-logo.jpg">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800;900&family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
  <link rel="stylesheet" href="admin.css">
</head>
<body>

  <!-- Login Overlay (Shown if unauthenticated) -->
  <div class="login-wrapper" id="loginWrapper">
    <div class="login-card">
      <div class="login-brand">
        <img src="assets/lexeno-logo.jpg" alt="LEXENO Logo" class="login-logo-img">
        <h2>LEXENO Admin Portal</h2>
        <p>Enterprise Operations &amp; Partner Management</p>
      </div>

      <form id="adminLoginForm" class="login-form">
        <div class="form-group">
          <label for="adminEmail"><i class="fa-solid fa-user-shield"></i> Admin Username / Email</label>
          <input type="text" id="adminEmail" class="form-input" placeholder="admin@lexeno.com" value="admin@lexeno.com" required>
        </div>

        <div class="form-group">
          <label for="adminPassword"><i class="fa-solid fa-lock"></i> Security Password / PIN</label>
          <div class="password-input-wrap">
            <input type="password" id="adminPassword" class="form-input" placeholder="Enter password" value="admin123" required>
            <button type="button" class="btn-toggle-pwd" id="togglePwdBtn" aria-label="Toggle password visibility">
              <i class="fa-solid fa-eye"></i>
            </button>
          </div>
        </div>

        <div class="login-hint-box">
          <i class="fa-solid fa-circle-info"></i> Demo credentials pre-filled: <code>admin@lexeno.com</code> / <code>admin123</code>
        </div>

        <button type="submit" class="btn btn-primary btn-block btn-login">
          <span>Secure Sign In</span>
          <i class="fa-solid fa-arrow-right-to-bracket"></i>
        </button>

        <a href="index.html" class="back-to-site-link">
          <i class="fa-solid fa-arrow-left"></i> Return to Main Website
        </a>
      </form>
    </div>
  </div>

  <!-- Admin Application (Shown once authenticated) -->
  <div class="admin-app" id="adminApp" style="display: none;">

    <!-- Left Sidebar -->
    <aside class="admin-sidebar" id="adminSidebar">
      <div class="sidebar-header">
        <a href="index.html" class="sidebar-brand">
          <img src="assets/lexeno-logo.jpg" alt="LEXENO" class="sidebar-logo">
          <div class="sidebar-brand-text">
            <span class="sb-title">LEXENO</span>
            <span class="sb-sub">ADMIN SUITE</span>
          </div>
        </a>
        <button class="sidebar-close-btn" id="sidebarCloseBtn" aria-label="Close sidebar">&times;</button>
      </div>

      <nav class="sidebar-nav">
        <div class="nav-section-label">MAIN DESK</div>
        <ul class="nav-menu">
          <li>
            <a href="#overview" class="nav-item active" data-tab="overview">
              <i class="fa-solid fa-gauge-high"></i>
              <span>Dashboard Overview</span>
            </a>
          </li>
          <li>
            <a href="#leads" class="nav-item" data-tab="leads">
              <i class="fa-solid fa-users"></i>
              <span>Leads CRM</span>
              <span class="badge-count" id="totalLeadsBadge">0</span>
            </a>
          </li>
          <li>
            <a href="#partners" class="nav-item" data-tab="partners">
              <i class="fa-solid fa-handshake"></i>
              <span>Channel Partners</span>
              <span class="badge-count count-green" id="partnersBadge">0</span>
            </a>
          </li>
          <li>
            <a href="#loans" class="nav-item" data-tab="loans">
              <i class="fa-solid fa-sack-dollar"></i>
              <span>Loan Applications</span>
            </a>
          </li>
        </ul>

        <div class="nav-section-label">SERVICES MANAGEMENT</div>
        <ul class="nav-menu">
          <li>
            <a href="#cards-ins" class="nav-item" data-tab="cards-ins">
              <i class="fa-solid fa-credit-card"></i>
              <span>Cards &amp; Insurance</span>
            </a>
          </li>
          <li>
            <a href="#analytics-b2b" class="nav-item" data-tab="analytics-b2b">
              <i class="fa-solid fa-chart-pie"></i>
              <span>Analytics &amp; B2B</span>
            </a>
          </li>
        </ul>

        <div class="nav-section-label">SYSTEM</div>
        <ul class="nav-menu">
          <li>
            <a href="index.html" class="nav-item highlight-link">
              <i class="fa-solid fa-globe"></i>
              <span>View Live Website</span>
            </a>
          </li>
          <li>
            <a href="#" class="nav-item text-danger" id="logoutBtn">
              <i class="fa-solid fa-arrow-right-from-bracket"></i>
              <span>Sign Out</span>
            </a>
          </li>
        </ul>
      </nav>

      <div class="sidebar-footer">
        <div class="msme-cert-badge">
          <i class="fa-solid fa-shield-check"></i>
          <span>MSME: UDYAM-UP-29-0187255</span>
        </div>
      </div>
    </aside>

    <!-- Main Content Area -->
    <div class="admin-main">

      <!-- Topbar Header -->
      <header class="admin-topbar">
        <div class="topbar-left">
          <button class="menu-toggle-btn" id="menuToggleBtn" aria-label="Toggle navigation menu">
            <i class="fa-solid fa-bars"></i>
          </button>
          <div class="page-title-box">
            <h1 id="currentSectionTitle">Dashboard Overview</h1>
            <span class="page-breadcrumb">Lexeno Admin &bull; Operations &amp; Lead Management</span>
          </div>
        </div>

        <div class="topbar-right">
          <div class="topbar-search">
            <i class="fa-solid fa-magnifying-glass"></i>
            <input type="text" id="globalSearchInput" placeholder="Search client name, phone, city...">
          </div>

          <button class="btn-topbar-action" id="addNewLeadBtn" title="Add New Lead Manually">
            <i class="fa-solid fa-plus"></i>
            <span>Add Lead</span>
          </button>

          <a href="index.html" class="btn-site-preview" target="_blank" title="Open client website in new tab">
            <i class="fa-solid fa-arrow-up-right-from-square"></i>
            <span>Live Site</span>
          </a>

          <div class="admin-profile-pill">
            <div class="avatar-circle">AR</div>
            <div class="profile-info">
              <span class="profile-name">Ashwani Raj</span>
              <span class="profile-role">Admin Lead</span>
            </div>
          </div>
        </div>
      </header>

      <!-- Scrollable Tab Container -->
      <main class="admin-content-body">

        <!-- TAB 1: OVERVIEW -->
        <section class="tab-pane active" id="pane-overview">
          
          <!-- KPI Cards Strip -->
          <div class="kpi-grid">
            <div class="kpi-card">
              <div class="kpi-icon icon-blue"><i class="fa-solid fa-users"></i></div>
              <div class="kpi-data">
                <span class="kpi-label">Total Leads Received</span>
                <div class="kpi-value" id="kpiTotalLeads">0</div>
                <span class="kpi-trend trend-up"><i class="fa-solid fa-arrow-up"></i> Live Tracking</span>
              </div>
            </div>

            <div class="kpi-card">
              <div class="kpi-icon icon-green"><i class="fa-solid fa-handshake"></i></div>
              <div class="kpi-data">
                <span class="kpi-label">Channel Partners</span>
                <div class="kpi-value" id="kpiTotalPartners">0</div>
                <span class="kpi-trend trend-up"><i class="fa-solid fa-arrow-up"></i> Nationwide Network</span>
              </div>
            </div>

            <div class="kpi-card">
              <div class="kpi-icon icon-purple"><i class="fa-solid fa-sack-dollar"></i></div>
              <div class="kpi-data">
                <span class="kpi-label">Loan Demand Pipeline</span>
                <div class="kpi-value" id="kpiLoanVolume">₹ 0</div>
                <span class="kpi-trend trend-neutral"><i class="fa-solid fa-chart-line"></i> Estimated Value</span>
              </div>
            </div>

            <div class="kpi-card">
              <div class="kpi-icon icon-amber"><i class="fa-solid fa-circle-check"></i></div>
              <div class="kpi-data">
                <span class="kpi-label">Active / In Progress</span>
                <div class="kpi-value" id="kpiActiveCases">0</div>
                <span class="kpi-trend trend-up"><i class="fa-solid fa-bolt"></i> Ready for Closing</span>
              </div>
            </div>
          </div>

          <!-- Charts / Visual Breakdown Section -->
          <div class="dashboard-split-grid">
            
            <!-- Service Distribution Box -->
            <div class="dash-box">
              <div class="dash-box-header">
                <h3><i class="fa-solid fa-chart-pie"></i> Inquiries by Service Category</h3>
                <span class="box-badge">Live Share</span>
              </div>
              <div class="category-breakdown-list" id="categoryBreakdownList">
                <!-- Injected via JavaScript -->
              </div>
            </div>

            <!-- Quick Partner Roster -->
            <div class="dash-box">
              <div class="dash-box-header">
                <h3><i class="fa-solid fa-handshake-angle"></i> Recent Channel Partner Sign-ups</h3>
                <a href="#partners" class="box-link" id="viewAllPartnersLink">View All</a>
              </div>
              <div class="recent-partners-roster" id="recentPartnersRoster">
                <!-- Injected via JavaScript -->
              </div>
            </div>

          </div>

          <!-- Recent Leads Preview Table -->
          <div class="dash-box">
            <div class="dash-box-header">
              <h3><i class="fa-solid fa-clock-rotate-left"></i> Latest Client Inquiries</h3>
              <div class="box-actions">
                <button class="btn btn-outline-sm" id="exportCsvBtnOverview"><i class="fa-solid fa-file-excel"></i> Export CSV</button>
                <a href="#leads" class="btn btn-primary-sm" id="viewAllLeadsBtn">Go to Leads CRM</a>
              </div>
            </div>
            <div class="table-responsive">
              <table class="admin-table">
                <thead>
                  <tr>
                    <th>Date</th>
                    <th>Customer Name</th>
                    <th>Contact</th>
                    <th>Service Required</th>
                    <th>Details / Scope</th>
                    <th>Status</th>
                    <th>Actions</th>
                  </tr>
                </thead>
                <tbody id="overviewRecentLeadsTableBody">
                  <!-- Injected via JavaScript -->
                </tbody>
              </table>
            </div>
          </div>

        </section>

        <!-- TAB 2: LEADS CRM -->
        <section class="tab-pane" id="pane-leads">
          <div class="crm-toolbar">
            <div class="crm-filters">
              <button class="filter-chip active" data-filter="all">All Inquiries (<span id="countAll">0</span>)</button>
              <button class="filter-chip" data-filter="Loans">Loans (<span id="countLoans">0</span>)</button>
              <button class="filter-chip" data-filter="Cards & Insurance">Cards &amp; Insurance (<span id="countCards">0</span>)</button>
              <button class="filter-chip" data-filter="Data Analytics">Data Analytics (<span id="countAnalytics">0</span>)</button>
              <button class="filter-chip" data-filter="B2B Leads">B2B Leads (<span id="countB2b">0</span>)</button>
              <button class="filter-chip" data-filter="Partner">Channel Partners (<span id="countCp">0</span>)</button>
            </div>

            <div class="crm-actions">
              <div class="status-select-wrap">
                <select id="statusFilterSelect" class="form-select-sm">
                  <option value="all">All Statuses</option>
                  <option value="New">New</option>
                  <option value="Contacted">Contacted</option>
                  <option value="In Progress">In Progress</option>
                  <option value="Sanctioned / Approved">Sanctioned / Approved</option>
                  <option value="Closed / Disbursed">Closed / Disbursed</option>
                  <option value="Rejected">Rejected</option>
                </select>
              </div>
              <button class="btn btn-outline-sm" id="exportCsvBtn"><i class="fa-solid fa-file-csv"></i> Export CSV</button>
              <button class="btn btn-primary-sm" id="openAddLeadModalBtn"><i class="fa-solid fa-plus"></i> Add Lead</button>
            </div>
          </div>

          <div class="dash-box">
            <div class="table-responsive">
              <table class="admin-table">
                <thead>
                  <tr>
                    <th>Ref ID</th>
                    <th>Date &amp; Time</th>
                    <th>Client Name</th>
                    <th>Phone / WhatsApp</th>
                    <th>Email</th>
                    <th>Service Category</th>
                    <th>Requirement / Amount</th>
                    <th>Lead Status</th>
                    <th>Actions</th>
                  </tr>
                </thead>
                <tbody id="leadsTableBody">
                  <!-- Injected via JavaScript -->
                </tbody>
              </table>
            </div>
            <div class="table-empty-state" id="leadsEmptyState" style="display: none;">
              <i class="fa-solid fa-inbox"></i>
              <h4>No leads found matching your filters</h4>
              <p>Try resetting the search or filters above.</p>
            </div>
          </div>
        </section>

        <!-- TAB 3: CHANNEL PARTNERS -->
        <section class="tab-pane" id="pane-partners">
          <div class="crm-toolbar">
            <div class="crm-toolbar-title">
              <h3>LEXENO Channel Partner Network</h3>
              <p>Manage DSAs, Loan Connectors, Insurance Agents, and Business Associates</p>
            </div>
            <button class="btn btn-primary-sm" id="addNewPartnerBtn"><i class="fa-solid fa-user-plus"></i> Register New Partner</button>
          </div>

          <div class="dash-box">
            <div class="table-responsive">
              <table class="admin-table">
                <thead>
                  <tr>
                    <th>Partner ID</th>
                    <th>Date Joined</th>
                    <th>Partner / Agency Name</th>
                    <th>Phone / WhatsApp</th>
                    <th>City / State</th>
                    <th>Domain / Background</th>
                    <th>Partner Status</th>
                    <th>Direct Connect</th>
                    <th>Manage</th>
                  </tr>
                </thead>
                <tbody id="partnersTableBody">
                  <!-- Injected via JavaScript -->
                </tbody>
              </table>
            </div>
          </div>
        </section>

        <!-- TAB 4: LOAN APPLICATIONS -->
        <section class="tab-pane" id="pane-loans">
          <div class="dash-box">
            <div class="dash-box-header">
              <h3><i class="fa-solid fa-sack-dollar"></i> Loan Applications &amp; EMI Calculator Leads</h3>
              <span class="box-badge">Personal, Business, Home, LAP</span>
            </div>
            <div class="table-responsive">
              <table class="admin-table">
                <thead>
                  <tr>
                    <th>Ref ID</th>
                    <th>Date</th>
                    <th>Applicant</th>
                    <th>Phone</th>
                    <th>Loan Type</th>
                    <th>Requested Amount</th>
                    <th>Status</th>
                    <th>Actions</th>
                  </tr>
                </thead>
                <tbody id="loansTableBody">
                  <!-- Injected via JavaScript -->
                </tbody>
              </table>
            </div>
          </div>
        </section>

        <!-- TAB 5: CARDS & INSURANCE -->
        <section class="tab-pane" id="pane-cards-ins">
          <div class="dash-box">
            <div class="dash-box-header">
              <h3><i class="fa-solid fa-credit-card"></i> Credit Card &amp; Insurance Pipeline</h3>
              <span class="box-badge">Cashback Cards, Health, Term Life, Motor</span>
            </div>
            <div class="table-responsive">
              <table class="admin-table">
                <thead>
                  <tr>
                    <th>Ref ID</th>
                    <th>Date</th>
                    <th>Customer</th>
                    <th>Phone</th>
                    <th>Category</th>
                    <th>Specific Requirement</th>
                    <th>Status</th>
                    <th>Actions</th>
                  </tr>
                </thead>
                <tbody id="cardsInsTableBody">
                  <!-- Injected via JavaScript -->
                </tbody>
              </table>
            </div>
          </div>
        </section>

        <!-- TAB 6: DATA ANALYTICS & B2B -->
        <section class="tab-pane" id="pane-analytics-b2b">
          <div class="dash-box">
            <div class="dash-box-header">
              <h3><i class="fa-solid fa-chart-pie"></i> Enterprise Data Analytics &amp; B2B Leads</h3>
              <span class="box-badge">BI Dashboards, Risk Scoring, B2B Acquisition</span>
            </div>
            <div class="table-responsive">
              <table class="admin-table">
                <thead>
                  <tr>
                    <th>Ref ID</th>
                    <th>Date</th>
                    <th>Company / Client</th>
                    <th>Phone</th>
                    <th>Service Domain</th>
                    <th>Scope Description</th>
                    <th>Status</th>
                    <th>Actions</th>
                  </tr>
                </thead>
                <tbody id="analyticsB2bTableBody">
                  <!-- Injected via JavaScript -->
                </tbody>
              </table>
            </div>
          </div>
        </section>

      </main>
    </div>
  </div>

  <!-- Modal: Add / Edit Lead Manually -->
  <div class="modal" id="leadModal" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-header">
        <h3 id="leadModalTitle"><i class="fa-solid fa-user-plus"></i> Add New Lead</h3>
        <button class="modal-close" id="leadModalCloseBtn">&times;</button>
      </div>
      <form id="leadModalForm">
        <div class="modal-body">
          <input type="hidden" id="editLeadId">
          <div class="form-row">
            <div class="form-group">
              <label for="modalLeadName">Client Full Name *</label>
              <input type="text" id="modalLeadName" class="form-input" placeholder="e.g. Rahul Sharma" required>
            </div>
            <div class="form-group">
              <label for="modalLeadPhone">Phone Number *</label>
              <input type="tel" id="modalLeadPhone" class="form-input" placeholder="e.g. 9876543210" required>
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="modalLeadEmail">Email Address</label>
              <input type="email" id="modalLeadEmail" class="form-input" placeholder="client@company.com">
            </div>
            <div class="form-group">
              <label for="modalLeadService">Service Category *</label>
              <select id="modalLeadService" class="form-select" required>
                <option value="Personal Loan">Personal Loan</option>
                <option value="Business Loan">Business &amp; MSME Loan</option>
                <option value="Home Loan">Home Loan / Balance Transfer</option>
                <option value="Loan Against Property">Loan Against Property (LAP)</option>
                <option value="Credit Card">Credit Card</option>
                <option value="Health Insurance">Health Insurance</option>
                <option value="Term Life Insurance">Term Life Insurance</option>
                <option value="Data Analytics">Data Analytics &amp; Dashboards</option>
                <option value="B2B Leads Generation">B2B Leads Generation</option>
                <option value="Channel Partner">Channel Partner Application</option>
              </select>
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="modalLeadStatus">Lead Status *</label>
              <select id="modalLeadStatus" class="form-select" required>
                <option value="New">New</option>
                <option value="Contacted">Contacted</option>
                <option value="In Progress">In Progress</option>
                <option value="Sanctioned / Approved">Sanctioned / Approved</option>
                <option value="Closed / Disbursed">Closed / Disbursed</option>
                <option value="Rejected">Rejected</option>
              </select>
            </div>
            <div class="form-group">
              <label for="modalLeadCity">City / Location</label>
              <input type="text" id="modalLeadCity" class="form-input" placeholder="Noida / Delhi NCR">
            </div>
          </div>

          <div class="form-group">
            <label for="modalLeadNotes">Requirement / Notes *</label>
            <textarea id="modalLeadNotes" rows="3" class="form-input" placeholder="Loan amount, cibil score, timeline, or scope details..." required></textarea>
          </div>
        </div>

        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" id="leadModalCancelBtn">Cancel</button>
          <button type="submit" class="btn btn-primary"><i class="fa-solid fa-check"></i> Save Lead</button>
        </div>
      </form>
    </div>
  </div>

  <!-- Modal: Add Partner Manually -->
  <div class="modal" id="partnerModal" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-header">
        <h3><i class="fa-solid fa-handshake"></i> Register Channel Partner</h3>
        <button class="modal-close" id="partnerModalCloseBtn">&times;</button>
      </div>
      <form id="partnerModalForm">
        <div class="modal-body">
          <div class="form-row">
            <div class="form-group">
              <label for="modalCpName">Partner / Agency Name *</label>
              <input type="text" id="modalCpName" class="form-input" placeholder="e.g. Apex Financial Solutions" required>
            </div>
            <div class="form-group">
              <label for="modalCpPhone">Mobile Number *</label>
              <input type="tel" id="modalCpPhone" class="form-input" placeholder="e.g. 9709600354" required>
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="modalCpCity">City &amp; State *</label>
              <input type="text" id="modalCpCity" class="form-input" placeholder="e.g. Ghaziabad, UP" required>
            </div>
            <div class="form-group">
              <label for="modalCpDomain">Domain Background *</label>
              <select id="modalCpDomain" class="form-select" required>
                <option value="Existing Loan DSA / Connector">Existing Loan DSA / Connector</option>
                <option value="Insurance Advisor / Agent">Insurance Advisor / Agent</option>
                <option value="Financial Consultant / CA">Financial Consultant / CA</option>
                <option value="Digital Marketer / Lead Provider">Digital Marketer / Lead Provider</option>
                <option value="Freelancer / New Entrepreneur">Freelancer / New Entrepreneur</option>
              </select>
            </div>
          </div>

          <div class="form-group">
            <label for="modalCpStatus">Partner Status</label>
            <select id="modalCpStatus" class="form-select">
              <option value="Active">Active</option>
              <option value="Pending">Pending Approval</option>
            </select>
          </div>
        </div>

        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" id="partnerModalCancelBtn">Cancel</button>
          <button type="submit" class="btn btn-primary"><i class="fa-solid fa-check"></i> Register Partner</button>
        </div>
      </form>
    </div>
  </div>

  <!-- Toast Notification Container -->
  <div class="toast-container" id="adminToastContainer"></div>

  <!-- Admin JavaScript -->
  <script src="admin.js"></script>
</body>
</html>
