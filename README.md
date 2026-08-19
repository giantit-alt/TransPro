<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Logistics TransPro</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.31.0/dist/tabler-icons.min.css">
<style>
:root{
  --bg:#f1f5f9;
  --surface:#ffffff;
  --border:#e2e8f0;
  --border-s:#cbd5e1;
  --primary:#0f172a;
  --accent:#3b82f6;
  --accent-bg:#eff6ff;
  --text:#1e293b;
  --muted:#64748b;
  --green:#10b981;
  --green-bg:#ecfdf5;
  --red:#ef4444;
  --red-bg:#fef2f2;
  --orange:#f59e0b;
  --orange-bg:#fffbeb;
  --sidebar-w:210px;
  --header-h:52px;
  --r:10px;
}
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'IBM Plex Sans Thai',sans-serif;background:var(--bg);color:var(--text);height:100vh;display:flex;flex-direction:column;overflow:hidden;font-size:13px;}

/* ── TOPBAR ── */
.topbar{height:var(--header-h);background:var(--surface);border-bottom:1px solid var(--border);display:flex;align-items:center;padding:0 20px 0 0;flex-shrink:0;position:relative;z-index:10;}
.topbar-logo{width:var(--sidebar-w);display:flex;align-items:center;gap:9px;padding:0 18px;flex-shrink:0;}
.topbar-logo .logo-icon{width:30px;height:30px;background:var(--accent);border-radius:8px;display:flex;align-items:center;justify-content:center;color:#fff;font-size:16px;}
.topbar-logo .logo-text{font-size:14px;font-weight:700;color:var(--primary);letter-spacing:-0.3px;}
.topbar-logo .logo-sub{font-size:10px;color:var(--muted);font-weight:400;}
.topbar-divider{width:1px;height:28px;background:var(--border);margin:0 16px;}
.topbar-title{font-size:13px;font-weight:600;color:var(--text);flex:1;}
.topbar-date{font-size:11.5px;color:var(--muted);margin-right:16px;}
.topbar-user{display:flex;align-items:center;gap:8px;}
.topbar-user .avatar{width:30px;height:30px;border-radius:50%;background:var(--accent-bg);border:1.5px solid var(--accent);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;color:var(--accent);}
.topbar-user .uname{font-size:12px;font-weight:600;color:var(--text);}
.topbar-user .urole{font-size:10px;color:var(--muted);}

/* ── LAYOUT ── */
.layout{display:flex;flex:1;overflow:hidden;}

/* ── SIDEBAR ── */
.sidebar{width:var(--sidebar-w);background:var(--surface);border-right:1px solid var(--border);display:flex;flex-direction:column;flex-shrink:0;overflow-y:auto;padding:12px 0;}
.nav-section{padding:0 10px;margin-bottom:4px;}
.nav-section-label{font-size:10px;font-weight:700;color:var(--muted);letter-spacing:.8px;text-transform:uppercase;padding:6px 8px 4px;}
.nav-item{display:flex;align-items:center;gap:9px;padding:8px 10px;border-radius:8px;cursor:pointer;transition:.15s;color:var(--muted);font-size:12.5px;font-weight:500;margin-bottom:1px;text-decoration:none;}
.nav-item:hover{background:var(--bg);color:var(--text);}
.nav-item.active{background:var(--accent-bg);color:var(--accent);font-weight:600;}
.nav-item i{font-size:17px;flex-shrink:0;width:20px;text-align:center;}
.nav-divider{height:1px;background:var(--border);margin:8px 10px;}
.nav-badge{margin-left:auto;background:var(--red);color:#fff;font-size:10px;font-weight:700;padding:1px 6px;border-radius:10px;}

/* ── CONTENT ── */
.content{flex:1;overflow:hidden;display:flex;flex-direction:column;}
.page{flex:1;overflow-y:auto;padding:10px;display:none;flex-direction:column;gap:16px;}
.page.active{display:flex;}

/* ── PAGE HEADER ── */
.page-header{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:4px;}
.page-header h2{font-size:17px;font-weight:700;color:var(--primary);}
.page-header p{font-size:11.5px;color:var(--muted);margin-top:2px;}
.page-actions{display:flex;gap:8px;align-items:center;}

/* ── CARDS ── */
.card{background:var(--surface);border:1px solid var(--border);border-radius:var(--r);padding:18px;}
.card-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;}
.card-header h3{font-size:13px;font-weight:700;color:var(--primary);display:flex;align-items:center;gap:7px;}
.card-header h3 i{font-size:16px;color:var(--muted);}
.bento{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px;}

/* ── FORM ── */
.form-group{display:flex;flex-direction:column;gap:5px;}
.form-label{font-size:11px;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;}
input,select{padding:8px 12px;border:1px solid var(--border-s);border-radius:8px;font-family:inherit;font-size:13px;outline:none;transition:.15s;background:var(--surface);color:var(--text);}
input:focus,select:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(59,130,246,.1);}
input::placeholder{color:var(--muted);}

/* ── BUTTONS ── */
.btn{padding:8px 16px;border-radius:8px;font-family:inherit;font-size:12.5px;font-weight:600;cursor:pointer;border:none;transition:.15s;display:inline-flex;align-items:center;gap:6px;white-space:nowrap;}
.btn-primary{background:var(--accent);color:#fff;}.btn-primary:hover{background:#2563eb;}
.btn-secondary{background:var(--surface);color:var(--text);border:1px solid var(--border-s);}.btn-secondary:hover{background:var(--bg);}
.btn-danger{background:var(--red-bg);color:var(--red);border:1px solid #fecaca;}.btn-danger:hover{background:#fee2e2;}
.btn-sm{padding:5px 10px;font-size:11.5px;}
.btn i{font-size:15px;}

/* ── SCAN ── */
.scan-zone{background:linear-gradient(135deg,#eff6ff,#f8fafc);border:2px dashed #bfdbfe;border-radius:12px;padding:28px 20px;text-align:center;}
.scan-zone label{font-size:12px;font-weight:700;color:var(--accent);letter-spacing:.5px;text-transform:uppercase;display:block;margin-bottom:10px;}
.scan-input-wrap{display:flex;gap:8px;justify-content:center;}
.scan-input{font-family:'IBM Plex Mono',monospace;font-size:16px;font-weight:600;letter-spacing:1px;text-align:center;max-width:480px;width:100%;border:2px solid #bfdbfe;background:#fff;}
.scan-input:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(59,130,246,.15);}
.feedback{margin-top:10px;padding:9px 14px;border-radius:8px;font-size:12.5px;font-weight:600;display:none;text-align:left;}
.feedback.ok{background:var(--green-bg);color:#047857;display:block;border:1px solid #a7f3d0;}
.feedback.err{background:var(--red-bg);color:#dc2626;display:block;border:1px solid #fecaca;}
.feedback.warn{background:var(--orange-bg);color:#d97706;display:block;border:1px solid #fcd34d;}

/* ── PART LIST ── */
.part-item{padding:10px 0;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;}
.part-item:last-child{border-bottom:none;}
.part-info{display:flex;flex-direction:column;gap:3px;flex:1;}
.part-code{font-family:'IBM Plex Mono',monospace;font-size:12px;font-weight:700;color:var(--primary);}
.part-name{font-size:11px;color:var(--muted);}
.progress-bar{height:5px;background:var(--bg);border-radius:3px;overflow:hidden;margin-top:6px;}
.progress-fill{height:100%;background:var(--accent);border-radius:3px;transition:.3s;}
.progress-fill.done{background:var(--green);}
.progress-fill.over{background:var(--red);}

/* ── PILLS ── */
.pill{display:inline-flex;align-items:center;gap:3px;font-size:10.5px;font-weight:700;padding:2px 8px;border-radius:20px;white-space:nowrap;}
.pill-ok{background:var(--green-bg);color:#047857;}
.pill-short{background:var(--orange-bg);color:#b45309;}
.pill-over{background:var(--red-bg);color:#dc2626;}
.pill-none{background:#f1f5f9;color:var(--muted);}

/* ── KPI ── */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:10px;}
.kpi-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--r);padding:14px 16px;}
.kpi-card .kpi-label{font-size:11px;color:var(--muted);font-weight:600;display:flex;align-items:center;gap:5px;margin-bottom:8px;}
.kpi-card .kpi-label i{font-size:14px;}
.kpi-card .kpi-num{font-size:28px;font-weight:700;line-height:1;}
.kpi-card .kpi-sub{font-size:10.5px;color:var(--muted);margin-top:3px;}
.c-blue{color:var(--accent);}
.c-green{color:var(--green);}
.c-orange{color:var(--orange);}
.c-red{color:var(--red);}
.c-muted{color:var(--muted);}

/* ── FILTER BAR ── */
.filter-bar{display:flex;gap:10px;align-items:flex-end;flex-wrap:wrap;padding:14px 16px;background:var(--surface);border:1px solid var(--border);border-radius:var(--r);}

/* ── TABLE ── */
.tbl-wrap{overflow-x:auto;}
.tbl{width:100%;border-collapse:collapse;font-size:12px;}
.tbl th{background:var(--primary);color:#fff;padding:9px 12px;text-align:left;font-size:11px;font-weight:600;white-space:nowrap;}
.tbl th:first-child{border-radius:0;}
.tbl td{padding:8px 12px;border-bottom:1px solid var(--border);vertical-align:middle;}
.tbl tr:last-child td{border-bottom:none;}
.tbl tr:hover td{background:var(--bg);}
.tbl tr.tr-done td{background:#f0fdf4;}
.tbl tr.tr-over td{background:var(--red-bg);}
.tbl tr.tr-short td{background:var(--orange-bg);}
.tbl tr.row-cust td{background:#f8fafc;font-weight:700;border-top:2px solid var(--border-s);}
.tbl tr.row-inv td{background:var(--bg);color:var(--muted);font-size:11px;font-weight:700;}
.inv-no{font-family:'IBM Plex Mono',monospace;font-size:11px;}

/* ── INVOICE PREVIEW ── */
.inv-preview-item{display:flex;justify-content:space-between;align-items:center;padding:9px 0;border-bottom:1px solid var(--border);}
.inv-preview-item:last-child{border-bottom:none;}

/* ── TOAST ── */
.toast{position:fixed;bottom:20px;right:20px;background:var(--primary);color:#fff;padding:10px 18px;border-radius:var(--r);font-size:12.5px;font-weight:600;transform:translateY(80px);opacity:0;transition:.3s;z-index:1000;box-shadow:0 4px 20px rgba(0,0,0,.15);display:flex;align-items:center;gap:8px;}
.toast.show{transform:translateY(0);opacity:1;}

/* ── EMPTY STATE ── */
.empty-state{text-align:center;padding:32px 20px;color:var(--muted);}
.empty-state i{font-size:36px;margin-bottom:8px;display:block;}
.empty-state p{font-size:13px;}

@keyframes sp{to{transform:rotate(360deg);}}
.spin{display:inline-block;width:18px;height:18px;border:2.5px solid var(--border);border-top-color:var(--accent);border-radius:50%;animation:sp .6s linear infinite;}

/* ── MENU TOGGLE & RESPONSIVE ── */
.hamburger-btn { display: flex; background: none; border: none; font-size: 20px; color: var(--text); cursor: pointer; padding: 0 15px; height: 100%; align-items: center; }
.mobile-overlay { display: none; position: fixed; top: var(--header-h); left: 0; right: 0; bottom: 0; background: rgba(15, 23, 42, 0.4); z-index: 99; backdrop-filter: blur(2px); }
.sidebar { transition: margin-left 0.3s ease, left 0.3s ease; }

/* สำหรับ PC เมื่อกดพับเมนู */
@media (min-width: 769px) {
  .sidebar.collapsed { margin-left: calc(var(--sidebar-w) * -1); }
}

@media (max-width: 768px) {
  .topbar-logo { width: auto; padding: 0 10px 0 0; }
  .topbar-date { display: none; }
  .sidebar { position: fixed; top: var(--header-h); left: calc(var(--sidebar-w) * -1); bottom: 0; z-index: 100; margin-left: 0 !important; }
  .sidebar.open { left: 0; }
  .mobile-overlay.show { display: block; }
  .bento { grid-template-columns: 1fr !important; }
}
</style>
</head>
<body>

<!-- AUDIO -->
<audio id="sndPass" preload="auto" src="data:audio/mp3;base64,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"></audio>
<audio id="sndComplete" preload="auto" src="data:audio/mp3;base64,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1jf3V52fVdZ6EZRydX4vsr7GecO+RblO96pSAs/tTMpP75EcOMZnKUIm1zK/TzsiTLWw/9iOE33XYmkfbPpENCrW979393kW//NkxPYhTCoNapGGCajUTQE2OFpEBJUgzMSqWgJGUkwLXUB81mUNOzDxtrxawzm/cWlFraRJON4b4Vj0NrpZZ0sYrrbTezOWNhunFTGt4e6WmS6fJpP81DYZ6Ieux1xcOtanelPkCB+yyyjMujzzdkRUoxoK6rmbHxV8ze+OZmcq7qTjGmr/eIt02ppRlWqR//NkxO0cK4omNGjGCdVi1NRnkiKhheVpOlS/dLHTZTgqBIUf6rhsdnldyKWL66ezV1i2KQsV3qkcJ4vpkhEqyCa0ybz9LG2YyOF4NhfnIcpckX51giZkNXplMlKR/3KZu+SsZtTPQGsIzKuXx/J8iucD3ppDNYkf8uyP7ytwkPsIEROZ05/Ncg5IWtur/b+0//NkxP8j9CoECsDQBSjJ8LikgzBZDm4q7AV4imPU4t85SSOMKLcnVwBpmk1XXUN4k3ZCVHxoMMf6vL6sHN/6MsKpb4CHM6e/pvqPX3EQ5jL8ZSTre9/TasZICsiF+Qo7S/LRfb/X/8RWUZImVAnn6tunVlS1r/r//3VErPMn3OU0WREoSexyo0uxff8/7//z//NkxPIfZBIIyU8YAaOdzV6HuaFq/CjnodbgT5OthbnqKOpiLclj+3uvzXN/9a1n99EVeHlmBwZHkRWKyZQKw0mc/jqXaecjdTz8vr5hOmzD871nH+PnGviv+f8UpDjsmY6g1eLPlD3O6Hq9/EgRGVtQ1gP00WBOqFse6YsJ4bydmP57FrU4NHEnQoCJKNxV//NkxPc7HDocAZh4AFXDMxwMBMcZmUtmPUlVdgwpvVV/2CiV2PUKx/aqq2ql//8DAQEy/6qUX/jMyr/7NszMfz/6qqdVfqq3+37MzNqqt6qqqv/VUKp1VL1Lq/G9VUv/9mZvZVVf+sf/xlL1VS2DAQ3HhIKf/XeCgqoWRqEAopBPlMFBAgZFRUVEX9V/VEX///NkxI0di9n088MYAf1RF//8wUECBkOioqIpH//on/8plRFT/5TKiKzs5UVUX/9FRFT////////9nKYKCBA0DOVU1UxBTUUzLjEwMFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV//NkxJkSy/1NnhAFZVVVVVVVVVVMQU1FMy4xMDBVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV"></audio>
<audio id="sndDup" preload="auto" src="data:audio/mp3;base64,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"></audio>
<audio id="sndOver" preload="auto" src="data:audio/mp3;base64,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"></audio>

<!-- TOPBAR -->
<div class="topbar">
  <!-- เพิ่มปุ่มนี้เข้าไป -->
  <button class="hamburger-btn" onclick="toggleMenu()">
    <i class="ti ti-menu-2"></i>
  </button>
  <div class="topbar-logo">
    <div class="logo-icon"><i class="ti ti-truck-delivery" aria-hidden="true"></i></div>
    <div>
      <div class="logo-text">TransPro</div>
      <div class="logo-sub">Logistics QC System</div>
    </div>
  </div>
 
  <div class="topbar-title" id="topbarTitle"></div>
  <div class="topbar-date" id="topbarDate"></div>
 
</div>

<!-- MAIN LAYOUT -->
<div class="layout">

 <!-- Overlay สำหรับมือถือ -->
  <div class="mobile-overlay" id="mobileOverlay" onclick="toggleMenu()"></div>

  <!-- SIDEBAR -->
  <nav class="sidebar" id="sidebar">
    <div class="nav-section">
      <div class="nav-section-label">จัดการ</div>
      <div class="nav-item active" id="nav-dash" onclick="switchPage('dash')">
        <i class="ti ti-layout-dashboard" aria-hidden="true"></i> แดชบอร์ด
      </div>
      <div class="nav-item" id="nav-create" onclick="switchPage('create')">
        <i class="ti ti-file-invoice" aria-hidden="true"></i> สร้าง Invoice
      </div>
      <div class="nav-item" id="nav-scan" onclick="switchPage('scan')">
        <i class="ti ti-qrcode" aria-hidden="true"></i> สแกน QC
      </div>
    </div>
    <div class="nav-divider"></div>
    <div class="nav-section">
      <div class="nav-section-label">ข้อมูล</div>
      <div class="nav-item" style="cursor:default;opacity:.5;">
        <i class="ti ti-users" aria-hidden="true"></i> ลูกค้า
      </div>
      <div class="nav-item" style="cursor:default;opacity:.5;">
        <i class="ti ti-package" aria-hidden="true"></i> สินค้า
      </div>
    </div>
    <div class="nav-divider"></div>
    <div class="nav-section">
      <div class="nav-section-label">ระบบ</div>
      <div class="nav-item" style="cursor:default;opacity:.5;">
        <i class="ti ti-settings" aria-hidden="true"></i> ตั้งค่า
      </div>
    </div>
  </nav>

  <!-- CONTENT -->
  <div class="content">

    <!-- PAGE: DASHBOARD -->
    <div class="page active" id="page-dash">
      <div class="page-header">
        <div>
          <h2>แดชบอร์ดสรุปการจัดส่ง</h2>
         
        </div>
        <div class="page-actions">
          <button class="btn btn-secondary btn-sm" onclick="loadDashboard()"><i class="ti ti-refresh"></i> รีเฟรช</button>
          <button class="btn btn-primary btn-sm" onclick="loadDashboard()"><i class="ti ti-download"></i> โหลดข้อมูล</button>
        </div>
      </div>

      <!-- Filter -->
      <div class="filter-bar">
        <div class="form-group">
          <div class="form-label">วันที่จาก</div>
          <input type="date" id="dashFrom">
        </div>
        <div class="form-group">
          <div class="form-label">วันที่ถึง</div>
          <input type="date" id="dashTo">
        </div>
        <div class="form-group">
          <div class="form-label">ลูกค้า</div>
          <select id="dashCust" style="min-width:160px;" onchange="renderDashboard()">
            <option value="">ทั้งหมด</option>
          </select>
        </div>
        <div class="form-group">
          <div class="form-label">สถานะ</div>
          <select id="dashStatus" onchange="renderDashboard()">
            <option value="">ทั้งหมด</option>
            <option value="OK">ครบแล้ว</option>
            <option value="SHORT">ยังขาด</option>
            <option value="NONE">ยังไม่สแกน</option>
          </select>
        </div>
      </div>

      <!-- KPI -->
      <div class="kpi-grid">
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-users c-blue"></i> ลูกค้าครบ / ทั้งหมด</div>
          <div class="kpi-num c-blue" id="kpiCust">—</div>
          <div class="kpi-sub">ลูกค้า</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-list-check c-blue"></i> รายการทั้งหมด</div>
          <div class="kpi-num c-blue" id="kpiTotal">—</div>
          <div class="kpi-sub">Part</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-circle-check c-green"></i> ครบแล้ว</div>
          <div class="kpi-num c-green" id="kpiOk">—</div>
          <div class="kpi-sub">รายการ</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-alert-triangle c-orange"></i> ยังขาด</div>
          <div class="kpi-num c-orange" id="kpiShort">—</div>
          <div class="kpi-sub">รายการ</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-alert-circle c-red"></i> เกิน</div>
          <div class="kpi-num c-red" id="kpiOver">—</div>
          <div class="kpi-sub">รายการ</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-clock c-muted"></i> ยังไม่สแกน</div>
          <div class="kpi-num c-muted" id="kpiNone">—</div>
          <div class="kpi-sub">รายการ</div>
        </div>
        <div class="kpi-card">
          <div class="kpi-label"><i class="ti ti-chart-pie c-green"></i> % ครบ (Part)</div>
          <div class="kpi-num c-green" id="kpiPct">—</div>
          <div class="kpi-sub">ของรายการทั้งหมด</div>
        </div>
      </div>

     <!-- Table -->
      <div class="card" style="padding:0;overflow:hidden; display:flex; flex-direction:column; flex:1; min-height:300px;">
        <div style="padding:12px 16px;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:center; flex-shrink:0;">
          <span style="font-size:13px;font-weight:700;color:var(--primary);display:flex;align-items:center;gap:7px;"><i class="ti ti-table" style="font-size:16px;color:var(--muted);" aria-hidden="true"></i> สรุปตามลูกค้า / Invoice / สินค้า</span>
          <span id="dashCount" style="font-size:11px;color:var(--muted);background:var(--bg);padding:3px 10px;border-radius:20px;border:1px solid var(--border);"></span>
        </div>
        <div class="tbl-wrap" style="flex:1; overflow-y:auto;">
          <table class="tbl">
           <thead>
              <tr>
                <th>ลูกค้า</th>
                <th>Invoice</th>
                <th>Tagpack</th>
                <th>Part Name</th>
                <th style="text-align:right;">เป้าหมาย</th>
                <th style="text-align:right;">สแกนแล้ว</th>
                <th style="text-align:right;">คงเหลือ</th>
                <th style="text-align:center;">สถานะ</th>
              </tr>
            </thead>
            <tbody id="dashTbody">
              <tr><td colspan="8" class="empty-state"><i class="ti ti-database-off"></i><p>กด "โหลดข้อมูล" เพื่อดูสรุป</p></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- PAGE: CREATE INVOICE -->
    <div class="page" id="page-create">
      <div class="page-header">
        <div>
          <h2>สร้างแผนจัดส่ง</h2>
          
        </div>
      </div>

      <div class="bento">
        <div class="card">
          <div class="card-header"><h3><i class="ti ti-file-description"></i> ข้อมูลเอกสาร</h3></div>
          <div class="form-group" style="margin-bottom:12px;">
            <div class="form-label">วันที่จัดส่ง</div>
            <input type="date" id="invDate" oninput="updateInvPreview()">
          </div>
          <div class="form-group" style="margin-bottom:12px;">
            <div class="form-label">ลำดับบิล</div>
            <div style="display:flex;gap:8px;align-items:center;">
              <input type="number" id="invSeq" placeholder="เช่น 1, 55, 100" min="1" max="9999" style="flex:1;" oninput="updateInvPreview()">
              <div id="invNoPreview" style="font-family:'IBM Plex Mono',monospace;font-size:12.5px;font-weight:700;color:var(--accent);background:var(--accent-bg);border:1.5px solid #bfdbfe;border-radius:8px;padding:8px 12px;white-space:nowrap;">IV______</div>
            </div>
          </div>
          <div class="form-group">
            <div class="form-label">ลูกค้า</div>
            <select id="invCustomer"><option value="">กำลังโหลด...</option></select>
          </div>
        </div>

        <div class="card">
          <div class="card-header"><h3><i class="ti ti-package"></i> เพิ่มสินค้า</h3></div>
          <div class="form-group" style="margin-bottom:12px;">
            <div class="form-label">ค้นหาสินค้า (Tagpack / Part Name)</div>
            <input type="text" id="invPartSearch" list="partDatalist" placeholder="พิมพ์เพื่อค้นหา..." autocomplete="off" oninput="onPartSearchInput()">
            <datalist id="partDatalist"></datalist>
            <div id="selectedPartInfo" style="margin-top:5px;font-size:11px;color:var(--accent);font-family:'IBM Plex Mono',monospace;min-height:16px;"></div>
          </div>
          <div class="form-group" style="margin-bottom:12px;">
            <div class="form-label">จำนวนเป้าหมาย (ชิ้น)</div>
            <input type="number" id="invQty" placeholder="ระบุจำนวน" min="1">
          </div>
          <button class="btn btn-secondary" style="width:100%;" onclick="addPartToInvoice()"><i class="ti ti-plus"></i> เพิ่มเข้ารายการ</button>
        </div>
      </div>

      <div class="card">
       <div class="card-header">
          <h3><i class="ti ti-list"></i> รายการสินค้า</h3>
          <button class="btn btn-primary" onclick="saveInvoice()"><i class="ti ti-device-floppy"></i> บันทึกแผนจัดส่ง</button>
        </div>
        <div id="invoicePreview" style="max-height: 350px; overflow-y: auto; -webkit-overflow-scrolling: touch; padding-right: 5px;">
          <div class="empty-state"><i class="ti ti-inbox"></i><p>ยังไม่มีรายการ — เพิ่มสินค้าจากด้านบน</p></div>
        </div>
      </div>
    </div>

    <!-- PAGE: SCAN QC -->
    <div class="page" id="page-scan">
      <div class="page-header">
        <div>
          <h2>สแกน QC</h2>
          
        </div>
        <div class="page-actions">
          <button class="btn btn-secondary btn-sm" onclick="loadActiveCustomersForScan()"><i class="ti ti-refresh"></i> รีเฟรชลูกค้า</button>
        </div>
      </div>

      <div class="bento" style="grid-template-columns:260px 1fr;">

        <!-- LEFT: เลือกลูกค้า + progress -->
        <div style="display:flex;flex-direction:column;gap:12px;">
          <div class="card">
            <div class="card-header"><h3><i class="ti ti-users"></i> เลือกลูกค้า</h3></div>
            <div class="form-group">
              <div class="form-label">ลูกค้า</div>
              <select id="scanCustSelect" onchange="loadCustomerForScan()" style="width:100%;">
                <option value="">-- เลือกลูกค้า --</option>
              </select>
            </div>
          </div>

          <div class="card" style="flex:1;">
            <div class="card-header"><h3><i class="ti ti-chart-bar"></i> ความคืบหน้า</h3></div>
            <div id="scanProgressList">
              <div class="empty-state" style="padding:20px;"><i class="ti ti-arrow-left"></i><p>เลือกลูกค้าเพื่อดูข้อมูล</p></div>
            </div>
          </div>
        </div>

        <!-- RIGHT: scan zone -->
        <div class="card" style="display:flex;flex-direction:column;gap:16px;">
          <div class="card-header"><h3><i class="ti ti-scan"></i> ยิงสแกน QR Code</h3></div>

          <div class="scan-zone">
            <label>สแกนแท็ก — วางเคอร์เซอร์ที่ช่องนี้แล้วยิง</label>
            <div class="scan-input-wrap">
              <input type="text" id="qrInput" class="scan-input" placeholder="รอสแกน..." autocomplete="off" autocorrect="off" spellcheck="false">
            </div>
            <div id="scanFeedback" class="feedback"></div>
          </div>

          <!-- Scan guide -->
          <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;">
            <div style="background:var(--green-bg);border:1px solid #a7f3d0;border-radius:8px;padding:10px;text-align:center;">
              <div style="font-size:20px;margin-bottom:4px;"><i class="ti ti-check" style="color:var(--green);"></i></div>
              <div style="font-size:11px;font-weight:700;color:#047857;">ผ่าน</div>
              <div style="font-size:10px;color:var(--muted);">นับยอดปกติ</div>
            </div>
            <div style="background:var(--orange-bg);border:1px solid #fcd34d;border-radius:8px;padding:10px;text-align:center;">
              <div style="font-size:20px;margin-bottom:4px;"><i class="ti ti-alert-triangle" style="color:var(--orange);"></i></div>
              <div style="font-size:11px;font-weight:700;color:#b45309;">สแกนซ้ำ</div>
              <div style="font-size:10px;color:var(--muted);">แท็กซ้ำ — ข้าม</div>
            </div>
            <div style="background:var(--red-bg);border:1px solid #fecaca;border-radius:8px;padding:10px;text-align:center;">
              <div style="font-size:20px;margin-bottom:4px;"><i class="ti ti-ban" style="color:var(--red);"></i></div>
              <div style="font-size:11px;font-weight:700;color:#dc2626;">บล็อก</div>
              <div style="font-size:10px;color:var(--muted);">เกิน / ไม่พบ</div>
            </div>
          </div>

          <div style="font-size:11px;color:var(--muted);background:var(--bg);border-radius:8px;padding:10px 12px;line-height:1.6;">
            <strong>QR Format:</strong> Tagpack / TagCustomer / LotNo / Qty / Seq<br>
            <span style="font-family:'IBM Plex Mono',monospace;font-size:10px;">MF-FEFB-BK115/RMP000213/CBCC600801-0002/1000/2</span>
          </div>
        </div>
      </div>
    </div>

  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ── STATE ──
var masterData = [];
var currentInvoiceItems = [];
var allCustomersForScan = [];
var activeCustomer = null;
var activeScanMap = {};
var dashRawData = null;

// ── DATE ──
(function(){
  var d = new Date();
  var days = ['อาทิตย์','จันทร์','อังคาร','พุธ','พฤหัสบดี','ศุกร์','เสาร์'];
  var months = ['ม.ค.','ก.พ.','มี.ค.','เม.ย.','พ.ค.','มิ.ย.','ก.ค.','ส.ค.','ก.ย.','ต.ค.','พ.ย.','ธ.ค.'];
  document.getElementById('topbarDate').textContent = days[d.getDay()]+' '+d.getDate()+' '+months[d.getMonth()]+' '+(d.getFullYear()+543);
})();

// ── SOUND ──
function playPass(){ try{ document.getElementById('sndPass').cloneNode().play(); }catch(e){} }
function playComplete(){ try{ document.getElementById('sndComplete').cloneNode().play(); }catch(e){} }
function playDup(){ try{ document.getElementById('sndDup').cloneNode().play(); }catch(e){} }
function playOver(){ try{ document.getElementById('sndOver').cloneNode().play(); }catch(e){} }

// ── INIT ──
window.onload = function(){
  document.getElementById('invDate').valueAsDate = new Date();
  initDashFilters();
  google.script.run.withSuccessHandler(function(r){
    if(r.ok){ masterData = r.list; populateCustomerDropdown(); }
  }).getMasterData();
};

// ── MENU TOGGLE (PC & MOBILE) ──
function toggleMenu() {
  if (window.innerWidth <= 768) {
    // พฤติกรรมบนมือถือ: เลื่อนเมนูออกมาทับหน้าจอ + โชว์ Overlay สีดำ
    document.getElementById('sidebar').classList.toggle('open');
    document.getElementById('mobileOverlay').classList.toggle('show');
  } else {
    // พฤติกรรมบน PC: หดเมนูเก็บไปด้านซ้าย เพื่อขยายพื้นที่เนื้อหา
    document.getElementById('sidebar').classList.toggle('collapsed');
  }
}

// ── NAVIGATION ──
var pageTitles = {
  dash:'แดชบอร์ดสรุปการจัดส่ง',
  create:'สร้างแผนจัดส่ง (Invoice)',
  scan:'สแกน QC'
};

function switchPage(page){
  ['dash','create','scan'].forEach(function(p){
    document.getElementById('page-'+p).classList.remove('active');
    document.getElementById('nav-'+p).classList.remove('active');
  });
  document.getElementById('page-'+page).classList.add('active');
  document.getElementById('nav-'+page).classList.add('active');

  // ปิดเมนูอัตโนมัติบนมือถือ
  if (window.innerWidth <= 768) {
    document.getElementById('sidebar').classList.remove('open');
    document.getElementById('mobileOverlay').classList.remove('show');
  }

  if(page==='scan'){
    loadActiveCustomersForScan();
    setTimeout(function(){ document.getElementById('qrInput').focus(); }, 300);
  }
  if(page==='dash') loadDashboard();
}

function showToast(msg, isErr){
  var t = document.getElementById('toast');
  t.innerHTML = '<i class="ti ti-'+(isErr?'alert-circle':'circle-check')+'"></i> '+msg;
  t.style.background = isErr ? 'var(--red)' : '#1e293b';
  t.classList.add('show');
  setTimeout(function(){ t.classList.remove('show'); }, 3000);
}

function formatDateBE(ds){
  if(!ds) return '';
  var d = new Date(ds);
  return ('0'+d.getDate()).slice(-2)+'/'+('0'+(d.getMonth()+1)).slice(-2)+'/'+(d.getFullYear()+543);
}

// ── INVOICE NO ──
function buildInvNo(){
  var ds = document.getElementById('invDate').value;
  var seq = document.getElementById('invSeq').value.trim();
  if(!ds||!seq) return '';
  var d = new Date(ds);
  var yy = String(d.getFullYear()+543).slice(-2);
  var mm = ('0'+(d.getMonth()+1)).slice(-2);
  return 'IV'+yy+mm+('000'+seq).slice(-4);
}
function updateInvPreview(){
  document.getElementById('invNoPreview').textContent = buildInvNo() || 'IV______';
}

// ── CUSTOMER + DATALIST ──
function populateCustomerDropdown(){
  var custs=[],seen={};
  masterData.forEach(function(d){ if(d.customer&&!seen[d.customer]){seen[d.customer]=1;custs.push(d.customer);} });
  custs.sort();
  var sel=document.getElementById('invCustomer');
  sel.innerHTML='<option value="">-- เลือกลูกค้า --</option>';
  custs.forEach(function(c){ sel.innerHTML+='<option value="'+c+'">'+c+'</option>'; });
  sel.addEventListener('change', function(){ rebuildPartDatalist(this.value); });
}

function rebuildPartDatalist(customer){
  var dl=document.getElementById('partDatalist');
  var filtered=customer?masterData.filter(function(d){return d.customer===customer;}):masterData;
  dl.innerHTML='';
  filtered.forEach(function(p){
    var o=document.createElement('option');
    o.value=p.tagpack; o.label=p.partName||'';
    dl.appendChild(o);
  });
  document.getElementById('invPartSearch').value='';
  document.getElementById('selectedPartInfo').textContent='';
}

function onPartSearchInput(){
  var val=document.getElementById('invPartSearch').value.trim();
  var info=document.getElementById('selectedPartInfo');
  var found=masterData.find(function(d){return d.tagpack===val;});
  if(found){
    info.textContent=found.partName+(found.tagCustomer?' | Customer Code: '+found.tagCustomer:'');
    info.style.color='var(--accent)';
  } else {
    info.textContent=val?'พิมพ์ต่อหรือเลือกจากรายการ...':'';
    info.style.color='var(--muted)';
  }
}

// ── ADD / REMOVE PART ──
function addPartToInvoice(){
  var val=document.getElementById('invPartSearch').value.trim();
  var qty=parseInt(document.getElementById('invQty').value);
  if(!val||isNaN(qty)||qty<=0){showToast('กรุณาเลือกสินค้าและระบุจำนวน',true);return;}
  var part=masterData.find(function(d){return d.tagpack===val;});
  if(!part){showToast('ไม่พบสินค้า: '+val,true);return;}
  if(currentInvoiceItems.find(function(i){return i.tagpack===val;})){showToast('สินค้านี้อยู่ในรายการแล้ว',true);return;}
  currentInvoiceItems.push({tagpack:part.tagpack,tagCustomer:part.tagCustomer,partName:part.partName,targetQty:qty});
  document.getElementById('invPartSearch').value='';
  document.getElementById('selectedPartInfo').textContent='';
  document.getElementById('invQty').value='';
  renderInvoicePreview();
}

function renderInvoicePreview(){
  var c=document.getElementById('invoicePreview');
  if(!currentInvoiceItems.length){
    c.innerHTML='<div class="empty-state"><i class="ti ti-inbox"></i><p>ยังไม่มีรายการ — เพิ่มสินค้าจากด้านบน</p></div>';
    return;
  }
  var html='<div style="margin-bottom:10px;font-size:12px;color:var(--muted);padding:0 0 8px;border-bottom:1px solid var(--border);">'+currentInvoiceItems.length+' รายการ</div>';
  currentInvoiceItems.forEach(function(item,idx){
    html+='<div class="inv-preview-item">'
      +'<div class="part-info">'
      +'<div class="part-code">'+item.tagpack+(item.tagCustomer?' <span style="color:var(--muted);font-weight:400;">('+item.tagCustomer+')</span>':'')+'</div>'
      +'<div class="part-name">'+item.partName+'</div>'
      +'</div>'
      +'<div style="text-align:right;display:flex;align-items:center;gap:10px;">'
      +'<div style="font-size:14px;font-weight:700;color:var(--primary);">'+item.targetQty.toLocaleString('th-TH')+' ชิ้น</div>'
      +'<button class="btn btn-danger btn-sm" onclick="removePart('+idx+')"><i class="ti ti-trash" style="font-size:13px;"></i></button>'
      +'</div></div>';
  });
  c.innerHTML=html;
}

function removePart(idx){currentInvoiceItems.splice(idx,1);renderInvoicePreview();}

function saveInvoice(){
  var invNo=buildInvNo();
  if(!invNo){showToast('กรุณาระบุวันที่และลำดับบิล',true);return;}
  var ds=document.getElementById('invDate').value;
  var cust=document.getElementById('invCustomer').value;
  if(!cust||!currentInvoiceItems.length){showToast('กรุณากรอกข้อมูลให้ครบ',true);return;}
  google.script.run
    .withSuccessHandler(function(r){
      if(r.ok){showToast('บันทึกแผนจัดส่ง '+invNo+' เรียบร้อย');document.getElementById('invSeq').value='';updateInvPreview();currentInvoiceItems=[];renderInvoicePreview();}
      else showToast('Error: '+r.error,true);
    })
    .withFailureHandler(function(e){showToast('Error: '+e.message,true);})
    .saveInvoiceTarget({invoiceNo:invNo,deliveryDate:formatDateBE(ds),customer:cust,items:currentInvoiceItems});
}

// ── SCAN ──
function loadActiveCustomersForScan(){
  var sel=document.getElementById('scanCustSelect');
  sel.innerHTML='<option value="">กำลังโหลด...</option>';
  google.script.run
    .withSuccessHandler(function(r){
      if(!r.ok){sel.innerHTML='<option value="">โหลดไม่สำเร็จ</option>';return;}
      allCustomersForScan=r.customers;
      sel.innerHTML='<option value="">-- เลือกลูกค้า --</option>';
      r.customers.forEach(function(c){sel.innerHTML+='<option value="'+c.customer+'">'+c.customer+'</option>';});
    })
    .withFailureHandler(function(){sel.innerHTML='<option value="">Error</option>';})
    .getActiveCustomersForScan();
}

function loadCustomerForScan(){
  var name=document.getElementById('scanCustSelect').value;
  if(!name){
    document.getElementById('scanProgressList').innerHTML='<div class="empty-state" style="padding:20px;"><i class="ti ti-arrow-left"></i><p>เลือกลูกค้า</p></div>';
    activeCustomer=null;return;
  }
  activeCustomer=allCustomersForScan.find(function(c){return c.customer===name;});
  activeScanMap={};
  activeCustomer.items.forEach(function(item){
    activeScanMap[item.tagpack]={targetQty:item.targetQty,scannedQty:0,tags:[],partName:item.partName,invoiceNos:item.invoiceNos||[]};
  });
  document.getElementById('scanProgressList').innerHTML='<div style="text-align:center;padding:20px;"><span class="spin"></span></div>';
  google.script.run
    .withSuccessHandler(function(r){
      if(r.ok){
        r.logs.forEach(function(log){
          if(activeScanMap[log.tagpack]){
            var sm=activeScanMap[log.tagpack];
            if(sm.tags.indexOf(log.seq)<0){sm.tags.push(log.seq);sm.scannedQty+=log.qty;}
          }
        });
        renderScanProgress();
        setTimeout(function(){document.getElementById('qrInput').focus();},100);
      }
    })
    .withFailureHandler(function(){renderScanProgress();})
    .getScanHistoryByCustomer(name);
}

function renderScanProgress(){
  if(!activeCustomer){return;}
  var html='';
  activeCustomer.items.forEach(function(item){
    var st=activeScanMap[item.tagpack];
    if(!st) return;
    var pct=st.targetQty>0?Math.min(st.scannedQty/st.targetQty*100,100):0;
    var isDone=st.scannedQty===st.targetQty,isOver=st.scannedQty>st.targetQty;
    var statusText=isDone?'ครบ':isOver?'เกิน '+(st.scannedQty-st.targetQty):'ขาด '+(st.targetQty-st.scannedQty);
    var pillCls=isDone?'pill-ok':isOver?'pill-over':'pill-short';
    html+='<div class="part-item">'
      +'<div class="part-info" style="width:100%;">'
      +'<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:2px;">'
      +'<span class="part-code" style="font-size:11.5px;">'+item.tagpack+'</span>'
      +'<span class="pill '+pillCls+'">'+statusText+'</span>'
      +'</div>'
      +'<div class="part-name">'+item.partName+'</div>'
      +'<div style="display:flex;justify-content:space-between;align-items:center;margin-top:4px;">'
      +'<div class="progress-bar" style="flex:1;margin-right:8px;"><div class="progress-fill'+(isDone?' done':isOver?' over':'')+'" style="width:'+pct+'%"></div></div>'
      +'<span style="font-size:11px;font-weight:700;color:'+(isOver?'var(--red)':isDone?'var(--green)':'var(--primary)')+'">'+st.scannedQty.toLocaleString('th-TH')+'/'+st.targetQty.toLocaleString('th-TH')+'</span>'
      +'</div>'
      +'</div></div>';
  });
  document.getElementById('scanProgressList').innerHTML=html||'<div class="empty-state" style="padding:20px;"><i class="ti ti-database-off"></i><p>ไม่มีข้อมูล</p></div>';
}

document.addEventListener('DOMContentLoaded', function(){
  document.getElementById('qrInput').addEventListener('keydown', function(e){
    if(e.key==='Enter'){
      var raw=this.value.trim(); this.value='';
      if(!raw) return;
      processScanData(raw);
    }
  });
});

function setFeedback(msg,type){
  var fb=document.getElementById('scanFeedback');
  fb.className='feedback '+type;
  fb.textContent=msg;
}

function processScanData(qrData){
  if(!activeCustomer){setFeedback('กรุณาเลือกลูกค้าก่อนสแกน','err');return;}
  var parts=qrData.split('/');
  if(parts.length<5){setFeedback('รูปแบบ QR ไม่ถูกต้อง (ต้องมี 5 ส่วน)','err');return;}
  var tagpack=parts[0].trim(),tagCustomer=parts[1].trim(),lotNo=parts[2].trim();
  var qty=parseInt(parts[3])||0, seq=parseInt(parts[4])||0;
  var map=activeScanMap[tagpack];
  if(!map){playOver();setFeedback('🚫 ไม่พบ '+tagpack+' ในรายการจัดส่งของลูกค้านี้','err');setTimeout(function(){document.getElementById('qrInput').focus();},50);return;}
  if(map.tags.indexOf(seq)>=0){playDup();setFeedback('⚠️ '+tagpack+' แท็ก #'+seq+' สแกนไปแล้ว (ข้าม)','warn');setTimeout(function(){document.getElementById('qrInput').focus();},50);return;}
  var remaining=map.targetQty-map.scannedQty;
  if(qty>remaining){playOver();setFeedback('🚫 บล็อก! '+tagpack+' มี '+qty+' ชิ้น แต่รับได้อีก '+remaining+' ชิ้น','err');setTimeout(function(){document.getElementById('qrInput').focus();},50);return;}
  map.tags.push(seq);
  map.scannedQty+=qty;
  var isDone=map.scannedQty===map.targetQty;
  if(isDone){
    playComplete();
    setFeedback('✅ '+tagpack+' ครบแล้ว! ('+map.scannedQty.toLocaleString('th-TH')+'/'+map.targetQty.toLocaleString('th-TH')+')', 'ok');
  } else {
    playPass();
    setFeedback('✓ '+tagpack+' [Lot:'+lotNo+'] #'+seq+' — '+map.scannedQty.toLocaleString('th-TH')+'/'+map.targetQty.toLocaleString('th-TH')+' (ขาด '+(map.targetQty-map.scannedQty)+')', 'ok');
  }
  renderScanProgress();
  google.script.run
    .withSuccessHandler(function(){})
    .withFailureHandler(function(e){showToast('⚠️ บันทึกไม่สำเร็จ: '+e.message,true);})
    .saveScanLog({customer:activeCustomer.customer,invoiceNo:map.invoiceNos?map.invoiceNos.join(','):'',tagpack:tagpack,tagCustomer:tagCustomer,lotNo:lotNo,qty:qty,seq:seq,scannedQtyTotal:map.scannedQty,targetQty:map.targetQty,status:isDone?'OK':'SHORT'});
  setTimeout(function(){document.getElementById('qrInput').focus();},50);
}

// ── DASHBOARD ──
function initDashFilters(){
  var today=new Date(),y=today.getFullYear(),m=today.getMonth(),d=today.getDate();
  document.getElementById('dashFrom').value=y+'-'+('0'+(m+1)).slice(-2)+'-01';
  document.getElementById('dashTo').value=y+'-'+('0'+(m+1)).slice(-2)+'-'+('0'+d).slice(-2);
}

function loadDashboard(){
  var tbody=document.getElementById('dashTbody');
  tbody.innerHTML='<tr><td colspan="8" style="text-align:center;padding:28px;"><span class="spin"></span> <span style="margin-left:8px;color:var(--muted);">กำลังโหลด...</span></td></tr>';
  google.script.run
    .withSuccessHandler(function(r){
      if(!r.ok){tbody.innerHTML='<tr><td colspan="8" style="text-align:center;color:var(--red);padding:20px;">'+r.error+'</td></tr>';return;}
      dashRawData=r;
      populateDashCustFilter(r.rows);
      renderDashboard();
    })
    .withFailureHandler(function(e){tbody.innerHTML='<tr><td colspan="8" style="text-align:center;color:var(--red);padding:20px;">'+e.message+'</td></tr>';})
    .getDashboardData(document.getElementById('dashFrom').value,document.getElementById('dashTo').value);
}

function populateDashCustFilter(rows){
  var seen={},custs=[];
  rows.forEach(function(r){if(!seen[r.customer]){seen[r.customer]=1;custs.push(r.customer);}});
  custs.sort();
  var sel=document.getElementById('dashCust'),cur=sel.value;
  sel.innerHTML='<option value="">ทั้งหมด</option>';
  custs.forEach(function(c){sel.innerHTML+='<option value="'+c+'"'+(c===cur?' selected':'')+'>'+c+'</option>';});
}

function renderDashboard(){
  if(!dashRawData) return;
  var filterCust=document.getElementById('dashCust').value;
  var filterStatus=document.getElementById('dashStatus').value;
  var filtered=dashRawData.rows.filter(function(r){
    if(filterCust&&r.customer!==filterCust) return false;
    if(filterStatus&&r.status!==filterStatus) return false;
    return true;
  });

  var total=0,ok=0,short=0,over=0,none=0;
  var custTotal={},tempCustMap={};
  filtered.forEach(function(r){
    total++;custTotal[r.customer]=1;
    if(r.status==='OK') ok++;
    else if(r.status==='SHORT') short++;
    else if(r.status==='OVER') over++;
    else none++;
    if(!tempCustMap[r.customer]) tempCustMap[r.customer]={total:0,ok:0};
    tempCustMap[r.customer].total++;
    if(r.status==='OK') tempCustMap[r.customer].ok++;
  });
  var custTotalCount=Object.keys(custTotal).length,custOkCount=0;
  Object.keys(tempCustMap).forEach(function(c){if(tempCustMap[c].ok===tempCustMap[c].total&&tempCustMap[c].total>0) custOkCount++;});

  document.getElementById('kpiCust').textContent=custOkCount+'/'+custTotalCount;
  document.getElementById('kpiTotal').textContent=total;
  document.getElementById('kpiOk').textContent=ok;
  document.getElementById('kpiShort').textContent=short;
  document.getElementById('kpiOver').textContent=over;
  document.getElementById('kpiNone').textContent=none;
  document.getElementById('kpiPct').textContent=total>0?Math.round(ok/total*100)+'%':'—';
  document.getElementById('dashCount').textContent=filtered.length+' รายการ | '+custTotalCount+' ลูกค้า';

  var custMap={};
  filtered.forEach(function(r){
    if(!custMap[r.customer]) custMap[r.customer]={invoices:{},totalTarget:0,totalScanned:0,parts:0,okParts:0};
    var cm=custMap[r.customer];
    if(!cm.invoices[r.invoiceNo]) cm.invoices[r.invoiceNo]=[];
    cm.invoices[r.invoiceNo].push(r);
    cm.totalTarget+=r.targetQty;cm.totalScanned+=r.scannedQty;cm.parts++;
    if(r.status==='OK') cm.okParts++;
  });

  var custKeys=Object.keys(custMap).sort(),html='';
  if(!custKeys.length){
    html='<tr><td colspan="8" class="empty-state"><i class="ti ti-database-off"></i><p>ไม่พบข้อมูลในช่วงเวลานี้</p></td></tr>';
  } else {
    custKeys.forEach(function(cust){
      var cm=custMap[cust];
      var invKeys=Object.keys(cm.invoices).sort();
      var custStatus=cm.totalScanned>=cm.totalTarget?'OK':cm.totalScanned>0?'SHORT':'NONE';
      html+='<tr class="row-cust '+(custStatus==='OK'?'tr-done':custStatus==='SHORT'?'tr-short':'')+'">'
        +'<td colspan="4"><i class="ti ti-building-store" style="margin-right:5px;color:var(--muted);"></i>'+cust+'</td>'
        +'<td style="text-align:right;">'+cm.totalTarget.toLocaleString('th-TH')+'</td>'
        +'<td style="text-align:right;">'+cm.totalScanned.toLocaleString('th-TH')+'</td>'
        +'<td style="text-align:right;color:'+(cm.totalTarget-cm.totalScanned>0?'var(--red)':'var(--green)')+';">'+(cm.totalTarget-cm.totalScanned).toLocaleString('th-TH')+'</td>'
        +'<td style="text-align:center;">'+badgeHtml(custStatus,cm.totalScanned,cm.totalTarget)+'</td></tr>';
      invKeys.forEach(function(invNo){
        var invRows=cm.invoices[invNo];
        html+='<tr class="row-inv"><td colspan="8" style="padding-left:20px;"><i class="ti ti-file-invoice" style="margin-right:5px;"></i>Invoice: <span class="inv-no">'+invNo+'</span> ('+invRows.length+' รายการ)</td></tr>';
        invRows.forEach(function(r){
          var trCls=r.status==='OK'?'tr-done':r.status==='OVER'?'tr-over':r.status==='SHORT'?'tr-short':'';
          var remain=r.targetQty-r.scannedQty;
          html+='<tr class="'+trCls+'">'
            +'<td style="padding-left:30px;color:var(--muted);font-size:11px;">'+r.customer+'</td>'
            +'<td class="inv-no">'+r.invoiceNo+'</td>'
            +'<td style="font-family:\'IBM Plex Mono\',monospace;font-size:11.5px;font-weight:700;">'+r.tagpack+'</td>'
            +'<td style="font-size:11.5px;">'+r.partName+'</td>'
            +'<td style="text-align:right;">'+r.targetQty.toLocaleString('th-TH')+'</td>'
            +'<td style="text-align:right;font-weight:700;">'+r.scannedQty.toLocaleString('th-TH')+'</td>'
            +'<td style="text-align:right;color:'+(remain>0?'var(--red)':remain<0?'var(--orange)':'var(--green)')+';">'+remain.toLocaleString('th-TH')+'</td>'
            +'<td style="text-align:center;">'+badgeHtml(r.status,r.scannedQty,r.targetQty)+'</td></tr>';
        });
      });
    });
  }
  document.getElementById('dashTbody').innerHTML=html;
}

function badgeHtml(status,scanned,target){
  if(status==='OK')    return '<span class="pill pill-ok">ครบ</span>';
  if(status==='OVER')  return '<span class="pill pill-over">เกิน '+(scanned-target)+'</span>';
  if(status==='SHORT') return '<span class="pill pill-short">ขาด '+(target-scanned)+'</span>';
  return '<span class="pill" style="background:var(--bg);color:var(--muted);">ยังไม่สแกน</span>';
}
</script>
</body>
</html>
