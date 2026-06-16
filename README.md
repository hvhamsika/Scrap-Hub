
<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Scrap Hub</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@500;600&display=swap" rel="stylesheet">
<style>
:root{
  --forest-900:#0B1F1C;
  --forest-800:#0F2A25;
  --forest-700:#163730;
  --mint-50:#F3FBF7;
  --mint-100:#E6F4ED;
  --emerald-500:#1FAA77;
  --emerald-400:#2DC98E;
  --sky-500:#1C7ED6;
  --sky-400:#3D97EA;
  --amber-400:#F2B705;
  --coral-400:#E8604C;
  --ink-900:#0B1614;
  --ink-50:#F6FBF9;
 
  --bg: var(--forest-900);
  --bg-grad-a: rgba(31,170,119,0.20);
  --bg-grad-b: rgba(28,126,214,0.18);
  --surface: rgba(255,255,255,0.07);
  --surface-strong: rgba(255,255,255,0.12);
  --border: rgba(255,255,255,0.14);
  --text-hi: #F2FBF6;
  --text-lo: rgba(242,251,246,0.62);
  --shadow: 0 16px 40px rgba(0,0,0,0.35);
}
[data-theme="light"]{
  --bg: var(--mint-50);
  --bg-grad-a: rgba(31,170,119,0.16);
  --bg-grad-b: rgba(28,126,214,0.14);
  --surface: rgba(255,255,255,0.55);
  --surface-strong: rgba(255,255,255,0.75);
  --border: rgba(11,31,28,0.10);
  --text-hi: #0B1F1C;
  --text-lo: rgba(11,31,28,0.58);
  --shadow: 0 16px 36px rgba(20,60,50,0.14);
}
 
*{box-sizing:border-box; margin:0; padding:0;}
html,body{height:100%;}
body{
  font-family:'Inter',sans-serif;
  background:
    radial-gradient(circle at 12% 8%, var(--bg-grad-a), transparent 45%),
    radial-gradient(circle at 88% 18%, var(--bg-grad-b), transparent 40%),
    radial-gradient(circle at 50% 100%, rgba(31,170,119,0.10), transparent 50%),
    var(--bg);
  color:var(--text-hi);
  min-height:100vh;
  transition:background .35s ease,color .35s ease;
  padding-bottom:40px;
}
.display{font-family:'Space Grotesk',sans-serif;}
.mono{font-family:'JetBrains Mono',monospace;}
 
/* ---------- top bar ---------- */
.topbar{
  display:flex; align-items:center; justify-content:space-between;
  max-width:1180px; margin:0 auto; padding:22px 24px 14px;
  flex-wrap:wrap; gap:14px;
}
.brand{display:flex; align-items:center; gap:10px;}
.brand-mark{
  width:36px;height:36px;border-radius:11px;
  background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));
  display:flex;align-items:center;justify-content:center;
  box-shadow:0 6px 16px rgba(31,170,119,0.35);
}
.brand-mark svg{width:20px;height:20px;}
.brand-name{font-family:'Space Grotesk',sans-serif;font-weight:700;font-size:19px;letter-spacing:-0.01em;}
.brand-tag{font-size:11px;color:var(--text-lo);letter-spacing:.04em;text-transform:uppercase;margin-top:-2px;}
 
.topbar-right{display:flex; align-items:center; gap:10px;}
.segmented{
  display:flex; background:var(--surface); border:1px solid var(--border);
  border-radius:999px; padding:4px; gap:2px; backdrop-filter:blur(16px);
}
.segmented button{
  border:none; background:transparent; color:var(--text-lo);
  font-family:'Inter',sans-serif; font-weight:600; font-size:13px;
  padding:8px 16px; border-radius:999px; cursor:pointer; transition:.2s;
}
.segmented button.active{
  background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));
  color:#fff;
}
.icon-btn{
  width:38px;height:38px;border-radius:50%;border:1px solid var(--border);
  background:var(--surface); display:flex;align-items:center;justify-content:center;
  cursor:pointer; backdrop-filter:blur(16px);
}
.icon-btn svg{width:17px;height:17px;stroke:var(--text-hi);}
 
/* ---------- layout ---------- */
.stage{max-width:1180px;margin:0 auto;padding:10px 24px 0;}
.view{display:none;}
.view.active{display:block;}
 
/* ===================== MOBILE PHONE ===================== */
.phone-wrap{display:flex;justify-content:center;padding:18px 0 30px;}
.phone{
  width:375px; height:760px; border-radius:42px;
  background:linear-gradient(180deg,var(--forest-800),var(--forest-900));
  border:1px solid var(--border);
  box-shadow:var(--shadow), 0 0 0 8px rgba(255,255,255,0.02) inset;
  position:relative; overflow:hidden;
}
[data-theme="light"] .phone{ background:linear-gradient(180deg,#fff,var(--mint-100)); }
.phone-notch{
  position:absolute; top:0; left:50%; transform:translateX(-50%);
  width:130px;height:24px;background:var(--forest-900);
  border-radius:0 0 16px 16px; z-index:5;
}
[data-theme="light"] .phone-notch{background:#0B1F1C;}
.phone-screen{
  position:absolute; inset:0; padding:40px 18px 86px;
  overflow-y:auto; display:none;
}
.phone-screen.active{display:block;}
.phone-screen::-webkit-scrollbar{display:none;}
 
.bottom-nav{
  position:absolute; left:14px; right:14px; bottom:14px; height:62px;
  background:var(--surface-strong); border:1px solid var(--border);
  border-radius:24px; backdrop-filter:blur(20px);
  display:none; align-items:center; justify-content:space-around; z-index:6;
}
.bottom-nav.show{display:flex;}
.nav-item{display:flex;flex-direction:column;align-items:center;gap:3px;cursor:pointer;color:var(--text-lo);}
.nav-item svg{width:19px;height:19px;stroke:var(--text-lo);transition:.2s;}
.nav-item span{font-size:10px;font-weight:600;}
.nav-item.active, .nav-item.active svg{color:var(--emerald-400);stroke:var(--emerald-400);}
 
/* glass card */
.glass{
  background:var(--surface); border:1px solid var(--border);
  border-radius:20px; backdrop-filter:blur(20px);
  box-shadow:var(--shadow);
}
.glass-top-hl{position:relative;}
.glass-top-hl::before{
  content:""; position:absolute; top:0; left:14px; right:14px; height:1px;
  background:linear-gradient(90deg,transparent,rgba(255,255,255,0.45),transparent);
}
 
/* ---- Login screen ---- */
.login-logo{display:flex;flex-direction:column;align-items:center;margin:30px 0 26px;}
.login-logo .ring{
  width:74px;height:74px;border-radius:22px;
  background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));
  display:flex;align-items:center;justify-content:center;margin-bottom:14px;
  box-shadow:0 10px 26px rgba(31,170,119,0.4);
}
.login-logo .ring svg{width:38px;height:38px;}
.login-logo h1{font-size:22px;}
.login-logo p{font-size:12.5px;color:var(--text-lo);margin-top:4px;text-align:center;}
.field{margin-bottom:13px;}
.field label{font-size:11.5px;color:var(--text-lo);font-weight:600;display:block;margin-bottom:6px;letter-spacing:.02em;}
.field input{
  width:100%;padding:13px 14px;border-radius:14px;border:1px solid var(--border);
  background:var(--surface); color:var(--text-hi); font-family:'Inter';font-size:13.5px;
  outline:none;
}
.field input::placeholder{color:var(--text-lo);}
.btn-primary{
  width:100%;padding:13px;border:none;border-radius:14px;cursor:pointer;
  background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));
  color:#fff;font-weight:700;font-family:'Inter';font-size:14px;
  box-shadow:0 10px 22px rgba(31,170,119,0.32);
}
.btn-google{
  width:100%;padding:12px;border-radius:14px;border:1px solid var(--border);
  background:var(--surface);color:var(--text-hi);font-weight:600;font-size:13.5px;
  display:flex;align-items:center;justify-content:center;gap:8px;cursor:pointer;margin-top:10px;
}
.divider{display:flex;align-items:center;gap:10px;margin:18px 0;color:var(--text-lo);font-size:11px;}
.divider::before,.divider::after{content:"";flex:1;height:1px;background:var(--border);}
.link-row{display:flex;justify-content:space-between;font-size:12px;margin-top:14px;color:var(--text-lo);}
.link-row a, .role-pick span{color:var(--sky-400);font-weight:600;cursor:pointer;}
.role-pick{display:flex;gap:8px;margin-bottom:16px;}
.role-chip{
  flex:1;text-align:center;padding:9px 4px;border-radius:12px;border:1px solid var(--border);
  font-size:11.5px;font-weight:600;color:var(--text-lo);background:var(--surface);cursor:pointer;
}
.role-chip.sel{background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));color:#fff;border:none;}
 
/* ---- Home screen ---- */
.greet{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:16px;}
.greet h2{font-size:19px;}
.greet p{font-size:12px;color:var(--text-lo);margin-top:2px;}
.avatar{
  width:40px;height:40px;border-radius:50%;
  background:linear-gradient(135deg,var(--amber-400),var(--coral-400));
  display:flex;align-items:center;justify-content:center;font-weight:700;color:#1a1206;font-size:14px;
}
.stat-row{display:flex;gap:10px;margin-bottom:16px;}
.stat-chip{flex:1;padding:13px 12px;text-align:left;}
.stat-chip .lbl{font-size:10px;color:var(--text-lo);font-weight:600;text-transform:uppercase;letter-spacing:.03em;}
.stat-chip .val{font-family:'JetBrains Mono';font-size:17px;font-weight:600;margin-top:5px;}
.stat-chip .val.green{color:var(--emerald-400);}
.stat-chip .val.blue{color:var(--sky-400);}
.stat-chip .val.amber{color:var(--amber-400);}
 
.section-title{display:flex;justify-content:space-between;align-items:center;margin:18px 0 10px;}
.section-title h3{font-size:14px;font-weight:700;}
.section-title span{font-size:11px;color:var(--sky-400);font-weight:600;cursor:pointer;}
 
.req-scroll{display:flex;gap:10px;overflow-x:auto;padding-bottom:4px;}
.req-card{min-width:148px;padding:13px;flex-shrink:0;}
.req-card .icon{width:30px;height:30px;border-radius:9px;background:var(--surface-strong);display:flex;align-items:center;justify-content:center;margin-bottom:8px;}
.req-card .icon svg{width:16px;height:16px;}
.req-card h4{font-size:12.5px;font-weight:700;}
.req-card p{font-size:10.5px;color:var(--text-lo);margin:3px 0 8px;}
.chip{display:inline-block;font-size:9.5px;font-weight:700;padding:4px 9px;border-radius:999px;letter-spacing:.02em;}
.chip.requested{background:rgba(28,126,214,0.18);color:var(--sky-400);}
.chip.scheduled{background:rgba(242,183,5,0.18);color:var(--amber-400);}
.chip.progress{background:rgba(31,170,119,0.18);color:var(--emerald-400);}
.chip.completed{background:rgba(255,255,255,0.10);color:var(--text-lo);}
 
.tiles{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:6px;}
.tile{padding:14px 12px;cursor:pointer;display:flex;flex-direction:column;gap:8px;}
.tile .icon{width:32px;height:32px;border-radius:10px;display:flex;align-items:center;justify-content:center;}
.tile .icon svg{width:16px;height:16px;color:#fff;}
.tile h4{font-size:12.5px;font-weight:700;}
 
.quick-fab{
  position:absolute; right:20px; bottom:94px; z-index:7;
  padding:13px 18px; border-radius:999px; border:none;cursor:pointer;
  background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));
  color:#fff;font-weight:700;font-size:12.5px;display:flex;align-items:center;gap:7px;
  box-shadow:0 12px 26px rgba(31,170,119,0.4);
}
.quick-fab svg{width:14px;height:14px;}
 
/* ---- Scanner screen ---- */
.upload-zone{
  border:1.6px dashed var(--border); border-radius:20px; padding:30px 16px;
  text-align:center; margin-bottom:16px; position:relative; background:var(--surface);
}
.upload-zone .icon-circle{
  width:54px;height:54px;border-radius:50%;margin:0 auto 12px;
  background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));
  display:flex;align-items:center;justify-content:center;
}
.upload-zone .icon-circle svg{width:24px;height:24px;}
.upload-zone h4{font-size:13.5px;font-weight:700;margin-bottom:4px;}
.upload-zone p{font-size:11px;color:var(--text-lo);margin-bottom:14px;}
.upload-actions{display:flex;gap:8px;}
.upload-actions button, .upload-actions label{
  flex:1;padding:10px;border-radius:12px;font-size:12px;font-weight:600;cursor:pointer;
  border:1px solid var(--border);background:var(--surface-strong);color:var(--text-hi);text-align:center;
}
#fileInput{display:none;}
.scan-preview{width:100%;border-radius:16px;margin-bottom:14px;display:none;max-height:160px;object-fit:cover;}
 
.result-card{display:none;padding:16px;margin-bottom:14px;}
.result-card.show{display:block;}
.result-head{display:flex;align-items:center;gap:10px;margin-bottom:12px;}
.result-head .icon{width:38px;height:38px;border-radius:11px;display:flex;align-items:center;justify-content:center;}
.result-head .icon svg{width:18px;height:18px;color:#fff;}
.result-head h4{font-size:14.5px;font-weight:700;}
.result-head p{font-size:11px;color:var(--text-lo);}
.conf-wrap{margin-bottom:12px;}
.conf-label{display:flex;justify-content:space-between;font-size:11px;color:var(--text-lo);margin-bottom:6px;}
.conf-track{height:7px;border-radius:99px;background:rgba(255,255,255,0.1);overflow:hidden;}
.conf-fill{height:100%;border-radius:99px;width:0%;transition:width 1s cubic-bezier(.2,.9,.2,1);}
.result-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.result-grid .box{background:var(--surface-strong);border-radius:13px;padding:11px;}
.result-grid .box .l{font-size:10px;color:var(--text-lo);text-transform:uppercase;}
.result-grid .box .v{font-family:'JetBrains Mono';font-size:15px;font-weight:600;margin-top:4px;}
.rate-list{display:flex;flex-direction:column;gap:8px;}
.rate-row{display:flex;align-items:center;justify-content:space-between;padding:11px 13px;}
.rate-row .left{display:flex;align-items:center;gap:10px;}
.rate-row .ic{width:28px;height:28px;border-radius:9px;display:flex;align-items:center;justify-content:center;}
.rate-row .ic svg{width:14px;height:14px;color:#fff;}
.rate-row h5{font-size:12.5px;font-weight:700;}
.rate-row span.cat{font-size:10px;color:var(--text-lo);}
.rate-row .price{font-family:'JetBrains Mono';font-weight:600;font-size:13px;text-align:right;}
.rate-row .trend{font-size:10px;}
.trend.up{color:var(--emerald-400);}
.trend.down{color:var(--coral-400);}
 
/* ---- Map screen ---- */
.map-canvas{
  height:300px;border-radius:20px;position:relative;overflow:hidden;margin-bottom:14px;
  background:
   linear-gradient(0deg,transparent 24%, rgba(255,255,255,0.05) 25%, rgba(255,255,255,0.05) 26%, transparent 27%, transparent 74%, rgba(255,255,255,0.05) 75%, rgba(255,255,255,0.05) 76%, transparent 77%),
   linear-gradient(90deg,transparent 24%, rgba(255,255,255,0.05) 25%, rgba(255,255,255,0.05) 26%, transparent 27%, transparent 74%, rgba(255,255,255,0.05) 75%, rgba(255,255,255,0.05) 76%, transparent 77%),
   radial-gradient(circle at 70% 30%, rgba(28,126,214,0.18), transparent 55%),
   radial-gradient(circle at 25% 75%, rgba(31,170,119,0.2), transparent 55%),
   var(--forest-700);
  background-size:60px 60px,60px 60px,100% 100%,100% 100%;
  border:1px solid var(--border);
}
[data-theme="light"] .map-canvas{background-color:#DCEFE6;}
.pin{position:absolute;display:flex;flex-direction:column;align-items:center;}
.pin .dot{width:14px;height:14px;border-radius:50%;border:2px solid #fff;box-shadow:0 3px 8px rgba(0,0,0,0.3);}
.pin.you .dot{background:var(--coral-400);}
.pin.collector .dot{background:var(--sky-500);}
.pin.drop .dot{background:var(--emerald-500);}
.pin .eta{margin-top:4px;font-size:9.5px;font-weight:700;background:rgba(0,0,0,0.55);color:#fff;padding:2px 6px;border-radius:8px;white-space:nowrap;}
.tracking-marker{position:absolute;width:14px;height:14px;border-radius:50%;background:var(--sky-500);border:2px solid #fff;transition:left 5.5s linear, top 5.5s linear;box-shadow:0 0 0 6px rgba(28,126,214,0.25);}
.sheet{padding:16px;}
.sheet h4{font-size:14px;font-weight:700;margin-bottom:10px;}
.addr-row{display:flex;align-items:center;gap:10px;padding:11px;border-radius:13px;background:var(--surface-strong);margin-bottom:10px;}
.addr-row svg{width:16px;height:16px;flex-shrink:0;}
.addr-row .t{font-size:12px;font-weight:600;}
.addr-row .s{font-size:10.5px;color:var(--text-lo);}
.item-chip{display:flex;align-items:center;justify-content:space-between;padding:10px 12px;border-radius:13px;background:var(--surface-strong);margin-bottom:10px;font-size:12px;}
select.slot{
  width:100%;padding:11px;border-radius:13px;border:1px solid var(--border);
  background:var(--surface-strong);color:var(--text-hi);font-family:'Inter';font-size:12.5px;margin-bottom:12px;
}
.timeline{display:none;flex-direction:column;gap:0;margin-bottom:4px;}
.timeline.show{display:flex;}
.tl-step{display:flex;gap:12px;align-items:flex-start;padding-bottom:18px;position:relative;}
.tl-step:not(:last-child)::before{content:"";position:absolute;left:8px;top:20px;bottom:0;width:2px;background:var(--border);}
.tl-dot{width:18px;height:18px;border-radius:50%;border:2px solid var(--border);background:var(--surface);flex-shrink:0;margin-top:2px;}
.tl-step.active .tl-dot{background:var(--emerald-500);border-color:var(--emerald-500);box-shadow:0 0 0 4px rgba(31,170,119,0.2);}
.tl-step h5{font-size:12.5px;font-weight:700;}
.tl-step p{font-size:10.5px;color:var(--text-lo);}
 
/* ---- Rewards screen ---- */
.ring-wrap{display:flex;flex-direction:column;align-items:center;padding:24px 10px;margin-bottom:16px;}
.ring-wrap .pts{font-family:'JetBrains Mono';font-size:13px;color:var(--text-lo);margin-top:10px;}
.ring-wrap .tier{font-size:11px;color:var(--emerald-400);font-weight:700;margin-top:2px;}
.tabs{display:flex;gap:6px;margin-bottom:12px;background:var(--surface);border-radius:14px;padding:4px;border:1px solid var(--border);}
.tabs button{flex:1;border:none;background:transparent;padding:9px;border-radius:11px;font-weight:600;font-size:12px;color:var(--text-lo);cursor:pointer;}
.tabs button.active{background:var(--surface-strong);color:var(--text-hi);}
.tab-panel{display:none;}
.tab-panel.show{display:block;}
.history-row{display:flex;justify-content:space-between;align-items:center;padding:11px 4px;border-bottom:1px solid var(--border);}
.history-row:last-child{border-bottom:none;}
.history-row .t{font-size:12px;font-weight:600;}
.history-row .d{font-size:10px;color:var(--text-lo);}
.history-row .p{font-family:'JetBrains Mono';font-weight:700;font-size:12.5px;}
.history-row .p.pos{color:var(--emerald-400);}
.history-row .p.neg{color:var(--coral-400);}
.coupon{padding:13px;display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;}
.coupon .t{font-size:12.5px;font-weight:700;}
.coupon .s{font-size:10.5px;color:var(--text-lo);margin-top:2px;}
.redeem-btn{padding:8px 13px;border-radius:11px;border:none;font-size:11px;font-weight:700;cursor:pointer;background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));color:#fff;}
.eco-row{display:flex;gap:8px;margin-top:14px;}
.eco-box{flex:1;text-align:center;padding:12px 6px;}
.eco-box .v{font-family:'JetBrains Mono';font-weight:700;font-size:15px;color:var(--emerald-400);}
.eco-box .l{font-size:9.5px;color:var(--text-lo);margin-top:3px;}
 
/* ---- Profile ---- */
.profile-head{display:flex;flex-direction:column;align-items:center;padding:14px 0 22px;}
.profile-head .av{width:64px;height:64px;border-radius:50%;background:linear-gradient(135deg,var(--amber-400),var(--coral-400));display:flex;align-items:center;justify-content:center;font-size:22px;font-weight:700;color:#1a1206;margin-bottom:10px;}
.profile-head h3{font-size:15px;}
.role-badge{font-size:10px;font-weight:700;padding:3px 10px;border-radius:999px;background:rgba(31,170,119,0.18);color:var(--emerald-400);margin-top:6px;}
.settings-row{display:flex;justify-content:space-between;align-items:center;padding:13px 14px;margin-bottom:8px;}
.settings-row .l{display:flex;align-items:center;gap:10px;font-size:12.5px;font-weight:600;}
.settings-row svg{width:16px;height:16px;}
.switch{width:38px;height:21px;border-radius:99px;background:var(--surface-strong);position:relative;cursor:pointer;border:1px solid var(--border);}
.switch::after{content:"";position:absolute;width:16px;height:16px;border-radius:50%;background:#fff;top:1.5px;left:2px;transition:.2s;}
.switch.on{background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));}
.switch.on::after{left:19px;}
.logout-btn{width:100%;padding:12px;border-radius:13px;border:1px solid var(--border);background:var(--surface);color:var(--coral-400);font-weight:700;font-size:12.5px;margin-top:10px;cursor:pointer;}
 
.toast{
  position:fixed; bottom:30px; left:50%; transform:translateX(-50%) translateY(20px);
  background:var(--ink-900); color:#fff; padding:11px 20px; border-radius:13px;
  font-size:12.5px; font-weight:600; opacity:0; transition:.3s; z-index:999; box-shadow:0 10px 30px rgba(0,0,0,0.4);
  pointer-events:none;
}
.toast.show{opacity:1; transform:translateX(-50%) translateY(0);}
 
/* ===================== ADMIN ===================== */
.admin-wrap{padding-bottom:20px;}
.admin-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:18px;flex-wrap:wrap;gap:10px;}
.admin-head h2{font-size:21px;}
.admin-head p{font-size:12px;color:var(--text-lo);margin-top:2px;}
.range-pick{display:flex;gap:6px;}
.range-pick button{padding:8px 13px;border-radius:11px;border:1px solid var(--border);background:var(--surface);font-size:11.5px;font-weight:600;color:var(--text-lo);cursor:pointer;}
.range-pick button.active{background:linear-gradient(135deg,var(--emerald-500),var(--sky-500));color:#fff;border:none;}
 
.kpi-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:14px;margin-bottom:18px;}
.kpi-card{padding:16px;}
.kpi-card .l{font-size:10.5px;color:var(--text-lo);text-transform:uppercase;letter-spacing:.03em;font-weight:600;}
.kpi-card .v{font-family:'JetBrains Mono';font-size:22px;font-weight:600;margin:8px 0 4px;}
.kpi-card .d{font-size:11px;font-weight:600;}
.kpi-card .d.up{color:var(--emerald-400);}
.kpi-card .d.down{color:var(--coral-400);}
 
.grid-2{display:grid;grid-template-columns:1.6fr 1fr;gap:16px;margin-bottom:18px;}
.panel{padding:20px;}
.panel h4{font-size:14px;font-weight:700;margin-bottom:14px;}
.legend{display:flex;flex-wrap:wrap;gap:12px;margin-top:14px;}
.legend-item{display:flex;align-items:center;gap:6px;font-size:11px;color:var(--text-lo);}
.legend-dot{width:9px;height:9px;border-radius:50%;}
 
.bars{display:flex;align-items:flex-end;gap:10px;height:150px;margin-top:10px;}
.bar-col{flex:1;display:flex;flex-direction:column;align-items:center;gap:6px;}
.bar-col .bar{width:100%;border-radius:8px 8px 3px 3px;background:linear-gradient(180deg,var(--emerald-400),var(--sky-500));}
.bar-col .lbl{font-size:10px;color:var(--text-lo);}
 
.tables-row{display:grid;grid-template-columns:1.1fr 1fr;gap:16px;}
table{width:100%;border-collapse:collapse;}
th{text-align:left;font-size:10.5px;color:var(--text-lo);text-transform:uppercase;letter-spacing:.03em;padding:8px 6px;border-bottom:1px solid var(--border);}
td{padding:10px 6px;font-size:12.5px;border-bottom:1px solid var(--border);}
td.mono{font-family:'JetBrains Mono';}
.mini-btn{padding:5px 11px;border-radius:9px;border:none;font-size:10.5px;font-weight:700;cursor:pointer;}
.mini-btn.ok{background:rgba(31,170,119,0.2);color:var(--emerald-400);}
.mini-btn.no{background:rgba(232,96,76,0.2);color:var(--coral-400);margin-left:6px;}
.status-pill{font-size:10px;font-weight:700;padding:3px 9px;border-radius:999px;}
.status-pill.ok{background:rgba(31,170,119,0.18);color:var(--emerald-400);}
.status-pill.warn{background:rgba(242,183,5,0.18);color:var(--amber-400);}
 
@media (max-width:980px){
  .kpi-grid{grid-template-columns:repeat(2,1fr);}
  .grid-2{grid-template-columns:1fr;}
  .tables-row{grid-template-columns:1fr;}
}
@media (max-width:420px){
  .phone{width:100%;border-radius:30px;height:680px;}
}
</style>
</head>
<body>
 
<div class="topbar">
  <div class="brand">
    <div class="brand-mark">
      <svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2 C7 7 4 11 4 15a8 8 0 0 0 16 0c0-4-3-8-8-13z"/></svg>
    </div>
    <div>
      <div class="brand-name">Scrap Hub</div>
      <div class="brand-tag">Recycle · Earn · Track</div>
    </div>
  </div>
  <div class="topbar-right">
    <div class="segmented">
      <button class="active" id="seg-mobile" onclick="setView('mobile')">Mobile App</button>
      <button id="seg-admin" onclick="setView('admin')">Admin Panel</button>
    </div>
    <div class="icon-btn" onclick="toggleTheme()" title="Toggle dark / light">
      <svg id="themeIcon" viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
    </div>
  </div>
</div>
 
<div class="stage">
 
<!-- ============ MOBILE VIEW ============ -->
<div class="view active" id="view-mobile">
<div class="phone-wrap">
  <div class="phone">
    <div class="phone-notch"></div>
 
    <!-- LOGIN -->
    <div class="phone-screen active" id="screen-login">
      <div class="login-logo">
        <div class="ring"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2 C7 7 4 11 4 15a8 8 0 0 0 16 0c0-4-3-8-8-13z"/></svg></div>
        <h1 class="display">Welcome back</h1>
        <p>Turn scrap into rewards. Sign in to schedule a pickup.</p>
      </div>
      <div class="role-pick">
        <div class="role-chip sel" id="roleUser" onclick="pickRole('user')">User</div>
        <div class="role-chip" id="roleCollector" onclick="pickRole('collector')">Collector</div>
      </div>
      <div class="field"><label>Email address</label><input type="email" placeholder="you@example.com" value="anita.rao@example.com"></div>
      <div class="field"><label>Password</label><input type="password" placeholder="••••••••" value="••••••••"></div>
      <div class="link-row"><span></span><a>Forgot password?</a></div>
      <div style="margin-top:14px;">
        <button class="btn-primary" onclick="loginEnter()">Continue</button>
        <div class="divider">OR</div>
        <button class="btn-google" onclick="loginEnter()">
          <svg width="16" height="16" viewBox="0 0 24 24"><path fill="#EA4335" d="M12 11v2.8h7.7c-.3 1.8-2.3 5.2-7.7 5.2-4.6 0-8.4-3.8-8.4-8.5s3.8-8.5 8.4-8.5c2.6 0 4.4 1.1 5.4 2.1l2.3-2.3C18 .8 15.3 0 12 0 5.4 0 0 5.4 0 12s5.4 12 12 12c6.9 0 11.5-4.9 11.5-11.7 0-.8-.1-1.4-.2-2H12z"/></svg>
          Continue with Google
        </button>
      </div>
      <div class="link-row" style="justify-content:center;margin-top:18px;">Don't have an account? <a>&nbsp;Sign up</a></div>
    </div>
 
    <!-- HOME -->
    <div class="phone-screen" id="screen-home">
      <div class="greet">
        <div>
          <h2 class="display">Hi, Anita 👋</h2>
          <p>Let's keep that eco-streak going.</p>
        </div>
        <div class="avatar">AR</div>
      </div>
 
      <div class="stat-row">
        <div class="glass stat-chip"><div class="lbl">Points</div><div class="val green mono" id="homePoints">1,240</div></div>
        <div class="glass stat-chip"><div class="lbl">Eco Score</div><div class="val blue mono">86</div></div>
        <div class="glass stat-chip"><div class="lbl">Active</div><div class="val amber mono">2</div></div>
      </div>
 
      <div class="section-title"><h3>Scrap Requests</h3><span onclick="showScreen('map')">See all</span></div>
      <div class="req-scroll">
        <div class="glass req-card">
          <div class="icon" style="background:linear-gradient(135deg,#1C7ED6,#3D97EA)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/></svg></div>
          <h4>Mixed Metal</h4><p>4.2 kg · Koramangala</p>
          <span class="chip progress">In progress</span>
        </div>
        <div class="glass req-card">
          <div class="icon" style="background:linear-gradient(135deg,#F2B705,#E8604C)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><rect x="4" y="4" width="16" height="16" rx="3"/></svg></div>
          <h4>E-Waste</h4><p>1.8 kg · Tomorrow, 5–7pm</p>
          <span class="chip scheduled">Scheduled</span>
        </div>
        <div class="glass req-card">
          <div class="icon" style="background:linear-gradient(135deg,#1FAA77,#2DC98E)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M4 7h16M4 12h16M4 17h10"/></svg></div>
          <h4>Cardboard</h4><p>6.0 kg · Completed</p>
          <span class="chip completed">Completed</span>
        </div>
      </div>
 
      <div class="section-title"><h3>Quick Actions</h3><span></span></div>
      <div class="tiles">
        <div class="glass tile" onclick="showScreen('scan')">
          <div class="icon" style="background:linear-gradient(135deg,#1FAA77,#2DC98E)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M4 8V6a2 2 0 0 1 2-2h2M20 8V6a2 2 0 0 0-2-2h-2M4 16v2a2 2 0 0 0 2 2h2M20 16v2a2 2 0 0 1-2 2h-2"/><circle cx="12" cy="12" r="3"/></svg></div>
          <h4>Scan Scrap</h4>
        </div>
        <div class="glass tile" onclick="showScreen('rates')">
          <div class="icon" style="background:linear-gradient(135deg,#1C7ED6,#3D97EA)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M3 17l6-6 4 4 8-8"/></svg></div>
          <h4>Market Rates</h4>
        </div>
        <div class="glass tile" onclick="showScreen('map')">
          <div class="icon" style="background:linear-gradient(135deg,#F2B705,#E8604C)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M12 21s-7-6.1-7-11a7 7 0 1 1 14 0c0 4.9-7 11-7 11z"/><circle cx="12" cy="10" r="2.4"/></svg></div>
          <h4>Find Pickup</h4>
        </div>
        <div class="glass tile" onclick="showScreen('rewards')">
          <div class="icon" style="background:linear-gradient(135deg,#1FAA77,#1C7ED6)"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="8"/><path d="M12 8v8M8 12h8"/></svg></div>
          <h4>Rewards</h4>
        </div>
      </div>
      <button class="quick-fab" onclick="showScreen('map')"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2.4"><path d="M12 5v14M5 12h14"/></svg>Quick Pickup</button>
    </div>
 
    <!-- SCAN -->
    <div class="phone-screen" id="screen-scan">
      <h2 class="display" style="font-size:18px;margin-bottom:4px;">AI Scrap Scanner</h2>
      <p style="font-size:11.5px;color:var(--text-lo);margin-bottom:16px;">Upload a photo and we'll estimate type, weight & price.</p>
 
      <div class="upload-zone">
        <div class="icon-circle"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"/><circle cx="12" cy="13" r="4"/></svg></div>
        <h4>Upload scrap photo</h4>
        <p>JPG/PNG · camera or gallery</p>
        <div class="upload-actions">
          <label for="fileInput">📷 Camera</label>
          <label for="fileInput">🖼 Gallery</label>
        </div>
        <input id="fileInput" type="file" accept="image/*" onchange="runScan()">
      </div>
 
      <img id="scanPreview" class="scan-preview">
 
      <div class="glass result-card" id="resultCard">
        <div class="result-head">
          <div class="icon" id="resIcon"></div>
          <div>
            <h4 id="resType">Copper Wire</h4>
            <p id="resCat">Metal · Recyclable</p>
          </div>
        </div>
        <div class="conf-wrap">
          <div class="conf-label"><span>AI Confidence</span><span id="confPct" class="mono">0%</span></div>
          <div class="conf-track"><div class="conf-fill" id="confFill"></div></div>
        </div>
        <div class="result-grid">
          <div class="box"><div class="l">Est. Weight</div><div class="v" id="resWeight">0 kg</div></div>
          <div class="box"><div class="l">Est. Price</div><div class="v" id="resPrice">₹0</div></div>
        </div>
      </div>
      <button class="btn-primary" style="display:none;" id="scheduleBtn" onclick="showScreen('map')">Schedule Pickup →</button>
    </div>
 
    <!-- RATES -->
    <div class="phone-screen" id="screen-rates">
      <h2 class="display" style="font-size:18px;margin-bottom:4px;">Market Rates</h2>
      <p style="font-size:11.5px;color:var(--text-lo);margin-bottom:14px;">Updated 12 min ago · Bengaluru zone</p>
      <div class="rate-list">
        <div class="glass rate-row"><div class="left"><div class="ic" style="background:#E8604C"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/></svg></div><div><h5>Copper</h5><span class="cat">Metal</span></div></div><div><div class="price">₹612/kg</div><div class="trend up">▲ 3.1%</div></div></div>
        <div class="glass rate-row"><div class="left"><div class="ic" style="background:#9CA3AF"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/></svg></div><div><h5>Aluminium</h5><span class="cat">Metal</span></div></div><div><div class="price">₹148/kg</div><div class="trend down">▼ 1.2%</div></div></div>
        <div class="glass rate-row"><div class="left"><div class="ic" style="background:#1C7ED6"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><rect x="4" y="4" width="16" height="16" rx="3"/></svg></div><div><h5>E-Waste (PCB)</h5><span class="cat">Electronics</span></div></div><div><div class="price">₹95/kg</div><div class="trend up">▲ 0.8%</div></div></div>
        <div class="glass rate-row"><div class="left"><div class="ic" style="background:#1FAA77"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M4 7h16M4 12h16M4 17h10"/></svg></div><div><h5>Cardboard</h5><span class="cat">Paper</span></div></div><div><div class="price">₹11/kg</div><div class="trend up">▲ 0.4%</div></div></div>
        <div class="glass rate-row"><div class="left"><div class="ic" style="background:#F2B705"><svg viewBox="0 0 24 24" fill="none" stroke="#1a1206" stroke-width="2"><path d="M5 22h14M12 2v13M8 9l4 4 4-4"/></svg></div><div><h5>PET Plastic</h5><span class="cat">Plastic</span></div></div><div><div class="price">₹19/kg</div><div class="trend down">▼ 0.6%</div></div></div>
        <div class="glass rate-row"><div class="left"><div class="ic" style="background:#3D97EA"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><rect x="5" y="5" width="14" height="14" rx="2"/></svg></div><div><h5>Glass Bottles</h5><span class="cat">Glass</span></div></div><div><div class="price">₹4/kg</div><div class="trend up">▲ 0.2%</div></div></div>
      </div>
    </div>
 
    <!-- MAP -->
    <div class="phone-screen" id="screen-map">
      <h2 class="display" style="font-size:18px;margin-bottom:10px;">Find Pickup</h2>
      <div class="map-canvas" id="mapCanvas">
        <div class="pin you" style="left:48%;top:55%;"><div class="dot"></div></div>
        <div class="pin collector" style="left:20%;top:25%;"><div class="dot"></div><div class="eta">Ravi K · 9 min</div></div>
        <div class="pin drop" style="left:75%;top:68%;"><div class="dot"></div><div class="eta">Drop Point</div></div>
        <div class="pin collector" style="left:68%;top:20%;"><div class="dot"></div><div class="eta">Suresh · 14 min</div></div>
        <div class="tracking-marker" id="trackMarker" style="left:20%;top:25%;display:none;"></div>
      </div>
 
      <div class="glass sheet" id="requestSheet">
        <h4>Confirm pickup</h4>
        <div class="addr-row"><svg viewBox="0 0 24 24" fill="none" stroke="var(--emerald-400)" stroke-width="2"><path d="M12 21s-7-6.1-7-11a7 7 0 1 1 14 0c0 4.9-7 11-7 11z"/><circle cx="12" cy="10" r="2.4"/></svg><div><div class="t">Home — 4th Block</div><div class="s">Koramangala, Bengaluru</div></div></div>
        <div class="item-chip"><span id="mapItemName">Copper Wire · ~2.1 kg</span><strong id="mapItemPrice" class="mono">₹1,285</strong></div>
        <select class="slot"><option>Today, 5:00 – 7:00 PM</option><option>Tomorrow, 9:00 – 11:00 AM</option></select>
        <button class="btn-primary" onclick="requestPickup()">Request Pickup</button>
      </div>
 
      <div class="glass sheet timeline" id="timelineSheet">
        <h4>Live status</h4>
        <div class="tl-step active" id="tl1"><div class="tl-dot"></div><div><h5>Assigned</h5><p>Ravi K. accepted your request</p></div></div>
        <div class="tl-step" id="tl2"><div class="tl-dot"></div><div><h5>On the way</h5><p>ETA updating live</p></div></div>
        <div class="tl-step" id="tl3"><div class="tl-dot"></div><div><h5>Arrived</h5><p>Collector is at your location</p></div></div>
        <div class="tl-step" id="tl4"><div class="tl-dot"></div><div><h5>Weighing & Payment</h5><p>Final weight confirmed</p></div></div>
        <div class="tl-step" id="tl5" style="padding-bottom:0;"><div class="tl-dot"></div><div><h5>Completed</h5><p>Points & eco impact added</p></div></div>
      </div>
    </div>
 
    <!-- REWARDS -->
    <div class="phone-screen" id="screen-rewards">
      <h2 class="display" style="font-size:18px;margin-bottom:6px;">Rewards Wallet</h2>
      <div class="glass ring-wrap">
        <svg width="150" height="150" viewBox="0 0 150 150" id="leafRing"></svg>
        <div class="pts" id="ringPts">1,240 pts</div>
        <div class="tier">Gold Tier · 260 pts to Platinum</div>
        <div class="eco-row">
          <div class="eco-box"><div class="v">186</div><div class="l">kg recycled</div></div>
          <div class="eco-box"><div class="v">72</div><div class="l">kg CO₂ saved</div></div>
          <div class="eco-box"><div class="v">3.4</div><div class="l">trees equiv.</div></div>
        </div>
      </div>
 
      <div class="tabs">
        <button class="active" onclick="switchTab('history',this)">Earn History</button>
        <button onclick="switchTab('redeem',this)">Redeem</button>
      </div>
 
      <div class="glass tab-panel show" id="tab-history" style="padding:8px 14px;">
        <div class="history-row"><div><div class="t">Mixed Metal pickup</div><div class="d">12 Jun · Koramangala</div></div><div class="p pos mono">+45</div></div>
        <div class="history-row"><div><div class="t">Cardboard pickup</div><div class="d">9 Jun · Indiranagar</div></div><div class="p pos mono">+22</div></div>
        <div class="history-row"><div><div class="t">Redeemed: Café Voucher</div><div class="d">5 Jun</div></div><div class="p neg mono">−150</div></div>
        <div class="history-row"><div><div class="t">E-Waste pickup</div><div class="d">1 Jun · HSR Layout</div></div><div class="p pos mono">+60</div></div>
      </div>
 
      <div class="tab-panel" id="tab-redeem">
        <div class="glass coupon"><div><div class="t">₹100 Grocery Voucher</div><div class="s">BigBasket partner offer</div></div><button class="redeem-btn" onclick="redeem(this,300)">300 pts</button></div>
        <div class="glass coupon"><div><div class="t">Free Café Coffee</div><div class="s">Third Wave Coffee</div></div><button class="redeem-btn" onclick="redeem(this,150)">150 pts</button></div>
        <div class="glass coupon"><div><div class="t">₹50 Mobile Recharge</div><div class="s">Any operator</div></div><button class="redeem-btn" onclick="redeem(this,200)">200 pts</button></div>
        <div class="glass coupon"><div><div class="t">Eco Tote Bag</div><div class="s">Limited edition</div></div><button class="redeem-btn" onclick="redeem(this,500)">500 pts</button></div>
      </div>
    </div>
 
    <!-- PROFILE -->
    <div class="phone-screen" id="screen-profile">
      <div class="profile-head">
        <div class="av">AR</div>
        <h3>Anita Rao</h3>
        <span class="role-badge">USER ACCOUNT</span>
      </div>
      <div class="glass settings-row"><div class="l"><svg viewBox="0 0 24 24" fill="none" stroke="var(--text-hi)" stroke-width="2"><circle cx="12" cy="12" r="4"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3M4.9 4.9l2.1 2.1M17 17l2.1 2.1M4.9 19.1L7 17M17 7l2.1-2.1"/></svg>Dark mode</div><div class="switch on" id="profileSwitch" onclick="toggleTheme()"></div></div>
      <div class="glass settings-row"><div class="l"><svg viewBox="0 0 24 24" fill="none" stroke="var(--text-hi)" stroke-width="2"><path d="M12 21s-7-6.1-7-11a7 7 0 1 1 14 0c0 4.9-7 11-7 11z"/></svg>Saved addresses</div><span style="color:var(--text-lo);font-size:11px;">2 saved</span></div>
      <div class="glass settings-row"><div class="l"><svg viewBox="0 0 24 24" fill="none" stroke="var(--text-hi)" stroke-width="2"><rect x="2" y="5" width="20" height="14" rx="2"/><path d="M2 10h20"/></svg>Payment methods</div><span style="color:var(--text-lo);font-size:11px;">UPI linked</span></div>
      <div class="glass settings-row"><div class="l"><svg viewBox="0 0 24 24" fill="none" stroke="var(--text-hi)" stroke-width="2"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.7 21a2 2 0 0 1-3.4 0"/></svg>Notifications</div><div class="switch on"></div></div>
      <button class="logout-btn" onclick="logout()">Log out</button>
    </div>
 
    <div class="bottom-nav" id="bottomNav">
      <div class="nav-item active" data-s="home" onclick="navTo('home',this)"><svg viewBox="0 0 24 24" fill="none" stroke-width="2"><path d="M3 11l9-8 9 8M5 10v10h14V10"/></svg><span>Home</span></div>
      <div class="nav-item" data-s="scan" onclick="navTo('scan',this)"><svg viewBox="0 0 24 24" fill="none" stroke-width="2"><path d="M4 8V6a2 2 0 0 1 2-2h2M20 8V6a2 2 0 0 0-2-2h-2M4 16v2a2 2 0 0 0 2 2h2M20 16v2a2 2 0 0 1-2 2h-2"/><circle cx="12" cy="12" r="3"/></svg><span>Scan</span></div>
      <div class="nav-item" data-s="map" onclick="navTo('map',this)"><svg viewBox="0 0 24 24" fill="none" stroke-width="2"><path d="M12 21s-7-6.1-7-11a7 7 0 1 1 14 0c0 4.9-7 11-7 11z"/><circle cx="12" cy="10" r="2.4"/></svg><span>Map</span></div>
      <div class="nav-item" data-s="rewards" onclick="navTo('rewards',this)"><svg viewBox="0 0 24 24" fill="none" stroke-width="2"><circle cx="12" cy="12" r="8"/><path d="M12 8v8M8 12h8"/></svg><span>Rewards</span></div>
      <div class="nav-item" data-s="profile" onclick="navTo('profile',this)"><svg viewBox="0 0 24 24" fill="none" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 4-6 8-6s8 2 8 6"/></svg><span>Profile</span></div>
    </div>
  </div>
</div>
</div>
 
<!-- ============ ADMIN VIEW ============ -->
<div class="view" id="view-admin">
<div class="admin-wrap">
  <div class="admin-head">
    <div><h2 class="display">Admin Dashboard</h2><p>Operational overview across all regions</p></div>
    <div class="range-pick">
      <button>24h</button><button class="active">7 days</button><button>30 days</button>
    </div>
  </div>
 
  <div class="kpi-grid">
    <div class="glass kpi-card"><div class="l">Total Users</div><div class="v mono">18,420</div><div class="d up">▲ 4.2% wow</div></div>
    <div class="glass kpi-card"><div class="l">Active Collectors</div><div class="v mono">312</div><div class="d up">▲ 1.8%</div></div>
    <div class="glass kpi-card"><div class="l">Pickups Today</div><div class="v mono">486</div><div class="d up">▲ 6.1%</div></div>
    <div class="glass kpi-card"><div class="l">Scrap Volume</div><div class="v mono">9.2t</div><div class="d down">▼ 0.6%</div></div>
    <div class="glass kpi-card"><div class="l">Revenue</div><div class="v mono">₹6.4L</div><div class="d up">▲ 3.4%</div></div>
  </div>
 
  <div class="grid-2">
    <div class="glass panel">
      <h4>Pickups over time</h4>
      <svg viewBox="0 0 560 170" width="100%" height="170">
        <defs>
          <linearGradient id="lineFill" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#1FAA77" stop-opacity="0.35"/>
            <stop offset="100%" stop-color="#1FAA77" stop-opacity="0"/>
          </linearGradient>
        </defs>
        <polyline points="0,130 80,110 160,120 240,80 320,90 400,50 480,60 560,30" fill="none" stroke="#1C7ED6" stroke-width="3" stroke-linecap="round"/>
        <polygon points="0,130 80,110 160,120 240,80 320,90 400,50 480,60 560,30 560,170 0,170" fill="url(#lineFill)"/>
        <circle cx="560" cy="30" r="5" fill="#1FAA77"/>
      </svg>
      <div style="display:flex;justify-content:space-between;font-size:10.5px;color:var(--text-lo);margin-top:4px;"><span>Mon</span><span>Tue</span><span>Wed</span><span>Thu</span><span>Fri</span><span>Sat</span><span>Sun</span></div>
 
      <h4 style="margin-top:22px;">Top regions by volume (kg)</h4>
      <div class="bars">
        <div class="bar-col"><div class="bar" style="height:88%;"></div><div class="lbl">Koramangala</div></div>
        <div class="bar-col"><div class="bar" style="height:64%;"></div><div class="lbl">Indiranagar</div></div>
        <div class="bar-col"><div class="bar" style="height:100%;"></div><div class="lbl">HSR Layout</div></div>
        <div class="bar-col"><div class="bar" style="height:46%;"></div><div class="lbl">Whitefield</div></div>
        <div class="bar-col"><div class="bar" style="height:30%;"></div><div class="lbl">Jayanagar</div></div>
      </div>
    </div>
 
    <div class="glass panel">
      <h4>Scrap type distribution</h4>
      <div style="display:flex;justify-content:center;margin:6px 0 4px;">
        <div style="width:150px;height:150px;border-radius:50%;background:conic-gradient(#1FAA77 0% 38%, #1C7ED6 38% 63%, #F2B705 63% 80%, #E8604C 80% 92%, #9CA3AF 92% 100%); position:relative;">
          <div style="position:absolute;inset:24px;border-radius:50%;background:var(--bg);display:flex;align-items:center;justify-content:center;flex-direction:column;">
            <div class="mono" style="font-weight:700;font-size:16px;">9.2t</div>
            <div style="font-size:9.5px;color:var(--text-lo);">this week</div>
          </div>
        </div>
      </div>
      <div class="legend">
        <div class="legend-item"><div class="legend-dot" style="background:#1FAA77;"></div>Metal · 38%</div>
        <div class="legend-item"><div class="legend-dot" style="background:#1C7ED6;"></div>Paper · 25%</div>
        <div class="legend-item"><div class="legend-dot" style="background:#F2B705;"></div>Plastic · 17%</div>
        <div class="legend-item"><div class="legend-dot" style="background:#E8604C;"></div>E-Waste · 12%</div>
        <div class="legend-item"><div class="legend-dot" style="background:#9CA3AF;"></div>Glass · 8%</div>
      </div>
    </div>
  </div>
 
  <div class="tables-row">
    <div class="glass panel">
      <h4>Pending collector approvals</h4>
      <table>
        <tr><th>Name</th><th>Region</th><th>Applied</th><th></th></tr>
        <tbody id="approvalsBody">
        <tr><td>Manoj Kumar</td><td>Whitefield</td><td class="mono">2d ago</td><td><button class="mini-btn ok" onclick="resolveRow(this)">Approve</button><button class="mini-btn no" onclick="resolveRow(this)">Reject</button></td></tr>
        <tr><td>Fatima Sheikh</td><td>Jayanagar</td><td class="mono">1d ago</td><td><button class="mini-btn ok" onclick="resolveRow(this)">Approve</button><button class="mini-btn no" onclick="resolveRow(this)">Reject</button></td></tr>
        <tr><td>Deepak N.</td><td>HSR Layout</td><td class="mono">6h ago</td><td><button class="mini-btn ok" onclick="resolveRow(this)">Approve</button><button class="mini-btn no" onclick="resolveRow(this)">Reject</button></td></tr>
        </tbody>
      </table>
    </div>
    <div class="glass panel">
      <h4>Recent transactions</h4>
      <table>
        <tr><th>User</th><th>Amount</th><th>Status</th></tr>
        <tr><td>Anita Rao</td><td class="mono">₹1,285</td><td><span class="status-pill ok">Settled</span></td></tr>
        <tr><td>Rahul Verma</td><td class="mono">₹430</td><td><span class="status-pill ok">Settled</span></td></tr>
        <tr><td>Priya S.</td><td class="mono">₹95</td><td><span class="status-pill warn">Pending</span></td></tr>
        <tr><td>Imran Q.</td><td class="mono">₹612</td><td><span class="status-pill ok">Settled</span></td></tr>
      </table>
    </div>
  </div>
</div>
</div>
 
</div>
 
<div class="toast" id="toast"></div>
 
<script>
/* ---------- theme ---------- */
function toggleTheme(){
  const html=document.documentElement;
  const next = html.getAttribute('data-theme')==='dark' ? 'light':'dark';
  html.setAttribute('data-theme', next);
  document.getElementById('themeIcon').innerHTML = next==='dark'
    ? '<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>'
    : '<circle cx="12" cy="12" r="5"/><path d="M12 1v2M12 21v2M4.2 4.2l1.4 1.4M18.4 18.4l1.4 1.4M1 12h2M21 12h2M4.2 19.8l1.4-1.4M18.4 5.6l1.4-1.4"/>';
  const sw=document.getElementById('profileSwitch');
  if(sw) sw.classList.toggle('on', next==='dark');
}
 
/* ---------- view toggle ---------- */
function setView(v){
  document.getElementById('seg-mobile').classList.toggle('active', v==='mobile');
  document.getElementById('seg-admin').classList.toggle('active', v==='admin');
  document.getElementById('view-mobile').classList.toggle('active', v==='mobile');
  document.getElementById('view-admin').classList.toggle('active', v==='admin');
}
 
/* ---------- toast ---------- */
function toast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg; t.classList.add('show');
  clearTimeout(window._tt);
  window._tt=setTimeout(()=>t.classList.remove('show'),2400);
}
 
/* ---------- login ---------- */
function pickRole(r){
  document.getElementById('roleUser').classList.toggle('sel', r==='user');
  document.getElementById('roleCollector').classList.toggle('sel', r==='collector');
}
function loginEnter(){
  showScreen('home');
  document.getElementById('bottomNav').classList.add('show');
  toast('Signed in successfully');
}
function logout(){
  document.getElementById('bottomNav').classList.remove('show');
  showScreen('login');
}
 
/* ---------- screen / nav switching ---------- */
function showScreen(name){
  document.querySelectorAll('.phone-screen').forEach(s=>s.classList.remove('active'));
  document.getElementById('screen-'+name).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.toggle('active', n.dataset.s===name));
}
function navTo(name, el){
  showScreen(name);
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  el.classList.add('active');
}
 
/* ---------- AI scanner mock ---------- */
const MATERIALS=[
  {name:'Copper Wire', cat:'Metal · Recyclable', rate:612, color:'linear-gradient(135deg,#E8604C,#F2B705)', icon:'<svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/></svg>'},
  {name:'Aluminium Sheet', cat:'Metal · Recyclable', rate:148, color:'linear-gradient(135deg,#9CA3AF,#6B7280)', icon:'<svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/></svg>'},
  {name:'PET Bottle', cat:'Plastic · Recyclable', rate:19, color:'linear-gradient(135deg,#F2B705,#E8604C)', icon:'<svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M5 22h14M12 2v13M8 9l4 4 4-4"/></svg>'},
  {name:'Cardboard', cat:'Paper · Recyclable', rate:11, color:'linear-gradient(135deg,#1FAA77,#2DC98E)', icon:'<svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M4 7h16M4 12h16M4 17h10"/></svg>'},
  {name:'Circuit Board', cat:'E-Waste · Hazardous-safe', rate:95, color:'linear-gradient(135deg,#1C7ED6,#3D97EA)', icon:'<svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><rect x="4" y="4" width="16" height="16" rx="3"/></svg>'},
];
let lastScan=null;
function runScan(){
  const file=document.getElementById('fileInput').files[0];
  const prev=document.getElementById('scanPreview');
  if(file){ prev.src=URL.createObjectURL(file); prev.style.display='block'; }
 
  const m=MATERIALS[Math.floor(Math.random()*MATERIALS.length)];
  const weight=(Math.random()*4+0.6).toFixed(1);
  const conf=Math.floor(Math.random()*22+76);
  const price=Math.round(weight*m.rate);
  lastScan={name:m.name, weight, price};
 
  document.getElementById('resType').textContent=m.name;
  document.getElementById('resCat').textContent=m.cat;
  document.getElementById('resIcon').style.background=m.color;
  document.getElementById('resIcon').innerHTML=m.icon;
  document.getElementById('resWeight').textContent=weight+' kg';
  document.getElementById('resPrice').textContent='₹'+price.toLocaleString();
  document.getElementById('confPct').textContent=conf+'%';
  const fill=document.getElementById('confFill');
  fill.style.width='0%';
  fill.style.background = conf>85?'var(--emerald-400)':conf>70?'var(--amber-400)':'var(--coral-400)';
  setTimeout(()=>{ fill.style.width=conf+'%'; },80);
 
  document.getElementById('resultCard').classList.add('show');
  document.getElementById('scheduleBtn').style.display='block';
 
  document.getElementById('mapItemName').textContent=m.name+' · ~'+weight+' kg';
  document.getElementById('mapItemPrice').textContent='₹'+price.toLocaleString();
  toast('Scan complete: '+m.name+' detected');
}
 
/* ---------- map / tracking ---------- */
function requestPickup(){
  document.getElementById('requestSheet').style.display='none';
  document.getElementById('timelineSheet').classList.add('show');
  const marker=document.getElementById('trackMarker');
  marker.style.display='block';
  marker.style.left='20%'; marker.style.top='25%';
  setTimeout(()=>{ marker.style.left='48%'; marker.style.top='55%'; },200);
  toast('Pickup requested — collector notified');
 
  const steps=['tl2','tl3','tl4','tl5'];
  steps.forEach((id,i)=>{
    setTimeout(()=>{
      document.getElementById(id).classList.add('active');
      if(id==='tl5'){
        const pts = lastScan ? Math.round(lastScan.price*0.05)+20 : 45;
        const ptsEl=document.getElementById('homePoints');
        const cur=parseInt(ptsEl.textContent.replace(/,/g,''))||1240;
        ptsEl.textContent=(cur+pts).toLocaleString();
        toast('Pickup completed! +'+pts+' points earned 🎉');
      }
    }, 1500*(i+1));
  });
}
 
/* ---------- rewards ---------- */
function switchTab(name, el){
  document.querySelectorAll('.tabs button').forEach(b=>b.classList.remove('active'));
  el.classList.add('active');
  document.getElementById('tab-history').classList.toggle('show', name==='history');
  document.getElementById('tab-redeem').classList.toggle('show', name==='redeem');
}
function redeem(btn, cost){
  const ptsEl=document.getElementById('ringPts');
  const cur=parseInt(ptsEl.textContent.replace(/[^0-9]/g,''));
  if(cur<cost){ toast('Not enough points for this reward'); return; }
  ptsEl.textContent=(cur-cost).toLocaleString()+' pts';
  drawRing(cur-cost);
  toast('Redeemed! Code sent to your email');
}
 
/* leaf ring */
function drawRing(points){
  const svg=document.getElementById('leafRing');
  const tierMax=1500;
  const pct=Math.min(points/tierMax,1);
  const cx=75, cy=75, r=58;
  let html='';
  html+=`<circle cx="${cx}" cy="${cy}" r="${r}" fill="none" stroke="rgba(255,255,255,0.12)" stroke-width="10"/>`;
  const circumference=2*Math.PI*r;
  html+=`<circle cx="${cx}" cy="${cy}" r="${r}" fill="none" stroke="url(#ringGrad)" stroke-width="10" stroke-linecap="round" stroke-dasharray="${circumference}" stroke-dashoffset="${circumference*(1-pct)}" transform="rotate(-90 ${cx} ${cy})"/>`;
  html+=`<defs><linearGradient id="ringGrad" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#1FAA77"/><stop offset="100%" stop-color="#1C7ED6"/></linearGradient></defs>`;
  const leafCount=12;
  for(let i=0;i<leafCount;i++){
    const ang=(i/leafCount)*2*Math.PI - Math.PI/2;
    const lx=cx+ (r+15)*Math.cos(ang);
    const ly=cy+ (r+15)*Math.sin(ang);
    const filled = i/leafCount <= pct;
    html+=`<circle cx="${lx}" cy="${ly}" r="3.2" fill="${filled?'#2DC98E':'rgba(255,255,255,0.18)'}"/>`;
  }
  html+=`<text x="${cx}" y="${cy-2}" text-anchor="middle" font-family="Space Grotesk" font-size="20" font-weight="700" fill="var(--text-hi)">${points.toLocaleString()}</text>`;
  html+=`<text x="${cx}" y="${cy+16}" text-anchor="middle" font-family="Inter" font-size="9.5" fill="var(--text-lo)">points</text>`;
  svg.innerHTML=html;
}
drawRing(1240);
 
/* ---------- admin table actions ---------- */
function resolveRow(btn){
  const row=btn.closest('tr');
  row.style.opacity='0.35';
  toast('Application updated');
  setTimeout(()=>row.remove(),500);
}
</script>
</body>
</html>
