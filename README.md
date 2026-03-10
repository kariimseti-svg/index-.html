<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Admin \u2014 STORE</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&family=Playfair+Display:wght@900&display=swap" rel="stylesheet">
<style>
:root{--primary:#0f0f0f;--accent:#d4a853;--bg:#f3f4f6;--card:#fff;--text:#111;--muted:#6b7280;--border:#e5e7eb;--danger:#ef4444;--success:#10b981;--warning:#f59e0b;--info:#3b82f6;--purple:#8b5cf6;--radius:14px;--shadow:0 2px 16px rgba(0,0,0,0.08);}
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Cairo',sans-serif;background:var(--bg);color:var(--text);display:flex;min-height:100vh;}
.sidebar{width:230px;background:var(--primary);min-height:100vh;position:fixed;top:0;bottom:0;right:0;z-index:50;display:flex;flex-direction:column;overflow-y:auto;}
.sb-logo{padding:22px 18px;border-bottom:1px solid rgba(255,255,255,0.08);}
.sb-logo .logo{font-family:'Playfair Display',serif;font-size:22px;color:var(--accent);letter-spacing:4px;}
.sb-logo small{display:block;font-size:10px;color:rgba(255,255,255,.3);margin-top:2px;}
.sb-sec{padding:14px 12px 4px;font-size:10px;font-weight:700;color:rgba(255,255,255,.25);letter-spacing:2px;text-transform:uppercase;}
.nav{padding:0 10px 10px;}
.ni{display:flex;align-items:center;gap:10px;padding:10px 12px;border-radius:10px;cursor:pointer;font-size:13px;font-weight:600;color:rgba(255,255,255,.6);transition:all .2s;margin-bottom:2px;border:none;background:transparent;font-family:'Cairo',sans-serif;width:100%;text-align:right;}
.ni:hover{background:rgba(255,255,255,.07);color:#fff;}
.ni.active{background:var(--accent);color:var(--primary);}
.ni .ic{font-size:17px;width:22px;text-align:center;}
.ni .bc{background:var(--danger);color:#fff;font-size:10px;font-weight:700;padding:1px 6px;border-radius:20px;margin-right:auto;}
.main{margin-right:230px;padding:22px;flex:1;max-width:calc(100% - 230px);}
.topbar{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;flex-wrap:wrap;gap:10px;}
.page-title{font-size:20px;font-weight:900;}
.topbar-right{display:flex;gap:8px;flex-wrap:wrap;}
.page{display:none;}
.page.active{display:block;}
/* STATS */
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:20px;}
.stat{background:var(--card);border-radius:var(--radius);padding:16px;box-shadow:var(--shadow);display:flex;align-items:center;gap:12px;}
.stat-ic{width:48px;height:48px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:24px;flex-shrink:0;}
.ic-blue{background:#dbeafe;}.ic-green{background:#d1fae5;}.ic-yellow{background:#fef3c7;}.ic-purple{background:#ede9fe;}
.stat-num{font-size:24px;font-weight:900;line-height:1;}
.stat-lbl{font-size:11px;color:var(--muted);margin-top:2px;}
/* CARD */
.card{background:var(--card);border-radius:var(--radius);box-shadow:var(--shadow);margin-bottom:18px;overflow:hidden;}
.card-head{display:flex;align-items:center;justify-content:space-between;padding:14px 18px;border-bottom:1px solid var(--border);flex-wrap:wrap;gap:8px;}
.card-title{font-size:14px;font-weight:700;}
.card-body{padding:18px;}
/* BUTTONS */
.btn{border:none;border-radius:9px;padding:8px 16px;font-size:13px;font-weight:700;font-family:'Cairo',sans-serif;cursor:pointer;transition:all .2s;display:inline-flex;align-items:center;gap:5px;}
.btn:active{transform:scale(.97);}
.btn-primary{background:var(--primary);color:#fff;}
.btn-accent{background:var(--accent);color:var(--primary);}
.btn-danger{background:#fee2e2;color:var(--danger);}
.btn-success{background:#d1fae5;color:var(--success);}
.btn-warning{background:#fef3c7;color:#92400e;}
.btn-info{background:#dbeafe;color:#1d4ed8;}
.btn-purple{background:#ede9fe;color:#5b21b6;}
.btn-outline{background:transparent;border:1.5px solid var(--border);color:var(--muted);}
.btn-outline:hover{border-color:var(--primary);color:var(--primary);}
.btn-sm{padding:5px 11px;font-size:12px;border-radius:7px;}
.btn-xs{padding:3px 8px;font-size:11px;border-radius:6px;}
/* TABLE */
.tbl-wrap{overflow-x:auto;border-radius:10px;border:1px solid var(--border);}
table{width:100%;border-collapse:collapse;font-size:13px;}
thead{background:#f9fafb;}
th{padding:11px 14px;text-align:right;font-size:11px;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;white-space:nowrap;border-bottom:1px solid var(--border);}
td{padding:11px 14px;border-bottom:1px solid var(--bg);vertical-align:middle;}
tr:last-child td{border:none;}
tr:hover td{background:#f9fafb;}
.td-name{font-weight:700;}
.td-sub{font-size:11px;color:var(--muted);margin-top:1px;}
/* BADGES */
.badge{display:inline-flex;align-items:center;gap:3px;font-size:11px;font-weight:700;padding:3px 9px;border-radius:20px;}
.b-pending{background:#fef3c7;color:#92400e;}
.b-confirmed{background:#dbeafe;color:#1d4ed8;}
.b-delivering{background:#ede9fe;color:#6d28d9;}
.b-delivered{background:#d1fae5;color:#065f46;}
.b-cancelled{background:#fee2e2;color:#991b1b;}
.b-price{background:#f0fdf4;color:#166534;}
.b-cat{background:#ede9fe;color:#5b21b6;}
.b-stock{background:#dbeafe;color:#1e40af;}
.b-out{background:#fee2e2;color:#991b1b;}
/* STATUS SELECT */
.status-sel{border:1.5px solid var(--border);border-radius:8px;padding:5px 10px;font-family:'Cairo',sans-serif;font-size:12px;font-weight:700;outline:none;cursor:pointer;background:#fff;}
/* FORM */
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px;}
.form-grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;}
.f-full{grid-column:1/-1;}
.fg{display:flex;flex-direction:column;gap:5px;}
.fl{font-size:11px;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;}
.fi,.fta,.fsel{background:var(--bg);border:2px solid transparent;border-radius:10px;padding:10px 13px;font-size:13px;font-family:'Cairo',sans-serif;outline:none;color:var(--text);transition:border-color .2s;width:100%;}
.fi:focus,.fta:focus,.fsel:focus{border-color:var(--primary);background:#fff;}
.fta{resize:vertical;min-height:75px;}
.f-actions{grid-column:1/-1;display:flex;gap:8px;justify-content:flex-end;padding-top:6px;border-top:1px solid var(--border);margin-top:4px;}
/* TABS */
.tabs{display:flex;gap:3px;background:var(--bg);padding:4px;border-radius:10px;margin-bottom:16px;}
.tab{flex:1;padding:7px;text-align:center;border:none;border-radius:7px;font-size:12px;font-weight:700;font-family:'Cairo',sans-serif;cursor:pointer;background:transparent;color:var(--muted);transition:all .2s;}
.tab.active{background:#fff;color:var(--primary);box-shadow:0 1px 4px rgba(0,0,0,.1);}
/* MODAL */
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:100;display:none;align-items:center;justify-content:center;padding:16px;backdrop-filter:blur(4px);}
.overlay.show{display:flex;}
.modal{background:#fff;border-radius:20px;width:100%;max-width:680px;max-height:92vh;overflow-y:auto;box-shadow:0 20px 60px rgba(0,0,0,.2);animation:popIn .25s ease;}
@keyframes popIn{from{transform:scale(.95);opacity:0}to{transform:scale(1);opacity:1}}
.modal-head{padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:#fff;z-index:2;}
.modal-title{font-size:16px;font-weight:900;}
.modal-close{background:var(--bg);border:none;width:30px;height:30px;border-radius:8px;cursor:pointer;font-size:14px;}
.modal-body{padding:20px;}
/* ORDER DETAIL */
.od-section{margin-bottom:16px;}
.od-title{font-size:12px;font-weight:700;color:var(--muted);letter-spacing:1px;text-transform:uppercase;margin-bottom:8px;padding-bottom:6px;border-bottom:1px solid var(--border);}
.od-row{display:flex;justify-content:space-between;align-items:center;padding:6px 0;font-size:13px;border-bottom:1px solid var(--bg);}
.od-row:last-child{border:none;}
.od-row span:first-child{color:var(--muted);}
.od-row span:last-child{font-weight:700;}
.od-prod{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--bg);}
.od-prod:last-child{border:none;}
.tl-item{display:flex;gap:12px;align-items:flex-start;margin-bottom:12px;}
.tl-dot{width:10px;height:10px;border-radius:50%;background:var(--success);flex-shrink:0;margin-top:4px;}
/* SWITCH */
.sw{position:relative;display:inline-block;width:40px;height:22px;}
.sw input{opacity:0;width:0;height:0;}
.sl{position:absolute;cursor:pointer;inset:0;background:#d1d5db;border-radius:22px;transition:.3s;}
.sl:before{content:'';position:absolute;width:16px;height:16px;left:3px;bottom:3px;background:#fff;border-radius:50%;transition:.3s;}
input:checked+.sl{background:var(--success);}
input:checked+.sl:before{transform:translateX(18px);}
/* IMG PREVIEW */
.img-prev{width:65px;height:65px;border-radius:10px;object-fit:cover;border:2px solid var(--border);display:none;margin-top:6px;}
/* FILTER BAR */
.filter-bar{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:14px;align-items:center;}
.filter-btn{background:var(--bg);border:1.5px solid var(--border);border-radius:8px;padding:6px 14px;font-size:12px;font-weight:600;font-family:'Cairo',sans-serif;cursor:pointer;color:var(--muted);transition:all .2s;}
.filter-btn.active{background:var(--primary);color:#fff;border-color:var(--primary);}
.srch-mini{background:var(--bg);border:1.5px solid var(--border);border-radius:8px;padding:7px 12px;font-size:12px;font-family:'Cairo',sans-serif;outline:none;color:var(--text);min-width:180px;}
.srch-mini:focus{border-color:var(--primary);}
/* CODE */
.code-box{background:#0a0a0a;color:#a5f3fc;border-radius:12px;padding:16px;font-family:monospace;font-size:11px;line-height:1.7;overflow:auto;max-height:300px;white-space:pre;}
/* DELIVERY */
.del-section{background:var(--bg);border-radius:14px;padding:18px;margin-bottom:16px;border:2px solid transparent;transition:border-color .2s;}
.del-section:hover{border-color:var(--border);}
.del-sec-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.del-sec-title{font-size:15px;font-weight:700;display:flex;align-items:center;gap:8px;}
/*
