# OLYMPIA
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Olympia THPT</title>
<script src="https://cdn.tailwindcss.com/3.4.17"></script>
<style>
  :root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);color-scheme:light}
  body{min-height:100vh;font-family:'Segoe UI',system-ui,sans-serif;color:#1e293b;
    background:radial-gradient(circle at 12% 8%,#fef9c3 0,transparent 32%),radial-gradient(circle at 88% 4%,#fed7aa 0,transparent 30%),linear-gradient(180deg,#dbeafe 0%,#eff6ff 55%,#fff7ed 100%) fixed}
  body::after{content:'';position:fixed;left:0;right:0;bottom:0;height:90px;z-index:0;pointer-events:none;
    background:radial-gradient(ellipse 50% 100% at 20% 100%,#bfdbfe 0 60%,transparent 61%),radial-gradient(ellipse 45% 100% at 72% 100%,#fed7aa 0 60%,transparent 61%)}
  #app{position:relative;z-index:1}
  .deco{position:fixed;inset:0;pointer-events:none;overflow:hidden;z-index:0}
  .deco i{position:absolute;display:block;border-radius:50%;animation:float 9s ease-in-out infinite}
  .deco i:nth-child(1){width:120px;height:120px;left:-30px;top:18%;background:#fde68a;opacity:.6}
  .deco i:nth-child(2){width:80px;height:80px;right:6%;top:30%;background:#fdba74;opacity:.5;animation-delay:-2s}
  .deco i:nth-child(3){width:160px;height:160px;right:-50px;bottom:14%;background:#bae6fd;opacity:.7}
  .deco i:nth-child(4){width:60px;height:60px;left:12%;bottom:12%;background:#93c5fd;opacity:.5;animation-delay:-4s}
  .deco i:nth-child(5){width:40px;height:40px;left:46%;top:6%;background:#fcd34d;opacity:.7;animation-delay:-6s}
  .deco i:nth-child(n+6){border-radius:0;font-style:normal}
  .deco i:nth-child(n+6)::after{content:'★'}
  .deco i:nth-child(6){left:8%;top:12%;font-size:30px;color:#f59e0b}
  .deco i:nth-child(7){right:12%;top:10%;font-size:24px;color:#3b82f6;animation-delay:-3s}
  .deco i:nth-child(8){left:30%;bottom:20%;font-size:26px;color:#fb923c;animation-delay:-5s}
  .deco i:nth-child(9){right:28%;bottom:10%;font-size:32px;color:#f59e0b;animation-delay:-1s}
  .deco i:nth-child(10){left:4%;top:56%;font-size:22px;color:#3b82f6;animation-delay:-7s}
  .deco i:nth-child(11){right:4%;top:62%;font-size:28px;color:#fb923c;animation-delay:-2s}
  @keyframes float{0%,100%{transform:translateY(0) rotate(0)}50%{transform:translateY(-22px) rotate(12deg)}}
  .fade{animation:fade .4s ease}
  @keyframes fade{from{opacity:0;transform:translateY(14px) scale(.98)}to{opacity:1;transform:none}}
  @keyframes spin{to{transform:rotate(360deg)}}
  @keyframes glow{0%,100%{box-shadow:0 0 12px #fb923c66}50%{box-shadow:0 0 28px #fb923ccc}}
  @keyframes marq{to{transform:translateX(-100%)}}
  .btn{padding:.65rem 1.2rem;border-radius:.8rem;font-weight:700;transition:.2s;cursor:pointer}
  .btn:hover{transform:translateY(-2px);filter:brightness(1.06)}
  .b1{background:linear-gradient(180deg,#3b82f6,#1d4ed8);color:#fff;box-shadow:0 4px 14px #2563eb55}
  .b2{background:linear-gradient(180deg,#fb923c,#f97316);color:#fff;box-shadow:0 4px 14px #f9731655}
  .b3{background:#fff;color:#1d4ed8;border:2px solid #bfdbfe}
  .b4{background:linear-gradient(180deg,#f87171,#dc2626);color:#fff}
  .card{background:rgba(255,255,255,.94);border:2px solid #bfdbfe;border-top:5px solid #f97316;border-radius:1.25rem;box-shadow:0 10px 35px rgba(37,99,235,.15);padding:1.5rem;color:#1e293b}
  .card h2,.card h3{color:#1e3a8a}
  .inp{width:100%;border:2px solid #bfdbfe;border-radius:.75rem;padding:.55rem .8rem;outline:none;background:#fff;color:#1e293b}
  .inp:focus{border-color:#f97316;box-shadow:0 0 0 3px #fed7aa}
  th,td{padding:.6rem .7rem;text-align:left;border-bottom:1px solid #e2e8f0}
  th{background:#dbeafe;color:#1e40af;font-size:.78rem;text-transform:uppercase;letter-spacing:.05em}
  tr:hover td{background:#f0f9ff}
  .opt{display:block;width:100%;text-align:left;margin-top:.7rem;cursor:pointer;transition:.15s;padding:.95rem 2rem;font-size:1.05rem;
    background:linear-gradient(180deg,#60a5fa,#2563eb);color:#fff;clip-path:polygon(3% 0,97% 0,100% 50%,97% 100%,3% 100%,0 50%)}
  .opt b{color:#fef08a;margin-right:.4rem}
  .opt:hover{filter:brightness(1.12);transform:scale(1.01)}
  .opt.sel{background:linear-gradient(180deg,#fde047,#fb923c);color:#7c2d12;font-weight:700}
  .opt.sel b{color:#7c2d12}
  .clockbox{display:flex;align-items:center;gap:.5rem;padding:.4rem 1.4rem;border-radius:999px;font-size:2rem;font-weight:800;background:#fff;border:3px solid #f97316;animation:glow 2s infinite}
  #clock{font-family:ui-monospace,Consolas,monospace;color:#ea580c}
  .emblem{position:relative;width:140px;height:140px;margin:30px auto 10px}
  .rays{position:absolute;inset:-60px;border-radius:50%;animation:spin 40s linear infinite;
    background:repeating-conic-gradient(rgba(251,146,60,.35) 0 6deg,transparent 6deg 18deg);
    -webkit-mask:radial-gradient(circle,#000 25%,transparent 68%);mask:radial-gradient(circle,#000 25%,transparent 68%)}
  .ring{position:absolute;inset:0;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:4rem;
    background:radial-gradient(circle,#fff,#dbeafe);border:4px solid #f97316;box-shadow:0 0 30px #fb923c99}
  .kicker{margin-top:1.8rem;color:#2563eb;letter-spacing:.3em;text-transform:uppercase;font-size:.8rem;font-weight:700}
  .logo{font-size:clamp(3.2rem,11vw,6.5rem);font-weight:900;letter-spacing:.1em;line-height:1.1;
    background:linear-gradient(180deg,#2563eb,#1e40af);-webkit-background-clip:text;background-clip:text;color:transparent;filter:drop-shadow(0 4px 0 #fdba74)}
  .sub{display:inline-block;background:linear-gradient(90deg,#f97316,#fbbf24);padding:.2rem 1.6rem;font-weight:800;letter-spacing:.45em;border-radius:999px;border:2px solid #fff;color:#fff;margin-top:.4rem;box-shadow:0 4px 12px #f9731666}
  .chip{display:inline-block;margin:.25rem;padding:.3rem .9rem;border:1px solid #fdba74;border-radius:999px;font-size:.8rem;color:#c2410c;background:#fff7ed;font-weight:600}
  .rule{padding:.55rem .9rem;border-left:4px solid #f97316;background:#fff;border-radius:0 .6rem .6rem 0;font-size:.9rem;color:#1e3a8a;box-shadow:0 2px 8px rgba(37,99,235,.08)}
  .steps{display:flex;gap:.4rem;margin-bottom:1rem}
  .step{flex:1;text-align:center;padding:.35rem .2rem;border-radius:999px;font-size:.72rem;font-weight:700;background:#dbeafe;color:#1e40af;border:1px solid #bfdbfe}
  .tile{padding:.7rem .3rem;cursor:pointer;text-align:center;font-weight:800;color:#fff;transition:.15s;background:linear-gradient(180deg,#60a5fa,#2563eb);clip-path:polygon(8% 0,92% 0,100% 50%,92% 100%,8% 100%,0 50%)}
  .tile small{display:block;font-weight:500;font-size:.7rem;opacity:.9}.tile:hover{filter:brightness(1.1)}
  .tile.on{background:linear-gradient(180deg,#fde047,#fb923c);color:#7c2d12}
  .ticker{margin:2rem auto 0;max-width:64rem;overflow:hidden;white-space:nowrap;border-top:2px solid #fdba74;border-bottom:2px solid #fdba74;padding:.4rem 0;color:#c2410c;font-size:.85rem;background:#fff7ed;font-weight:600}
  .ticker span{display:inline-block;padding-left:100%;animation:marq 24s linear infinite}
  label{color:#1e40af}
</style>
</head>
<body>
<div class="deco"><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i></div>
<div id="app" class="max-w-5xl mx-auto p-4"></div>
<div id="net" class="fixed bottom-2 right-3 z-40 text-xs px-3 py-1 rounded-full bg-white border border-blue-200 text-blue-800 shadow">🟠 Đang kết nối…</div>
<div id="modal" class="hidden fixed inset-0 bg-black/60 z-50 flex items-center justify-center p-4"></div>
<script>
const $ = s => document.querySelector(s);
const esc = s => String(s).replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const TEACHER_PASS = 'Vietnhat1234@';
const KEY = 'olympia_db_demo2';
// Môi trường xem thử: hộp thoại gốc có thể bị chặn nên dùng thông báo nội bộ
const alert = m => { const d = document.createElement('div'); d.className = 'fixed top-4 left-1/2 -translate-x-1/2 z-[60] bg-blue-700 text-white px-4 py-2 rounded-xl shadow-lg whitespace-pre-line max-w-sm text-center'; d.textContent = m; document.body.appendChild(d); setTimeout(() => d.remove(), 3000); };
let db = {students: [], questions: {10: [], 11: [], 12: []}, time: 30, results: []};
let view = 'home', cfgLoaded = false, lastCfg = '', lastRes = '';
const save = () => {
  if (!window.cloud || !cfgLoaded) return alert('Chưa tải xong dữ liệu từ máy chủ, hãy đợi vài giây rồi thử lại.');
  cloud.saveConfig({students: db.students, questions: db.questions, time: db.time}).catch(e => alert('Không lưu được: ' + e.message));
};
function setNet(ok, msg) { const n = $('#net'); if (n) n.textContent = msg || (ok ? '🟢 Đã kết nối máy chủ' : '🟠 Đang kết nối…'); }
window.onNet = ok => setNet(ok);
window.onCloudError = e => setNet(false, '🔴 Lỗi máy chủ: ' + (e.code || e.message));
window.onConfig = (d, fromCache) => {
  if (!fromCache) cfgLoaded = true;
  const n = {students: (d && d.students) || [], questions: Object.assign({10: [], 11: [], 12: []}, (d && d.questions) || {}), time: (d && d.time) || 30};
  const j = JSON.stringify(n); if (j === lastCfg) return; lastCfg = j;
  Object.assign(db, n);
  if (view === 'login') studentLogin(true);
};
window.onResults = arr => {
  const j = JSON.stringify(arr.map(r => [r.sid, r.score, r.used])); if (j === lastRes) return; lastRes = j;
  db.results = arr;
  if (view === 'teacher' && tTab === 'results') teacher(); else if (view === 'login') studentLogin(true);
};
function clearResults() {
  if (!confirm('Xoá toàn bộ kết quả? Không thể khôi phục.')) return;
  cloud.clearResults(db.results.map(r => r.sid)).catch(e => alert('Lỗi: ' + e.message));
  db.results = []; teacher();
}
let ex = null, timer = null, tTab = 'students', qGrade = 10, rFilter = 0;

function go(html) { clearInterval(timer); $('#app').innerHTML = `<div class="fade">${html}</div>`; window.scrollTo(0, 0); }
function showModal(html) { const m = $('#modal'); m.innerHTML = `<div class="card max-w-md w-full text-center">${html}</div>`; m.classList.remove('hidden'); }
function closeModal() { $('#modal').classList.add('hidden'); }
const genCode = g => 'OL' + g + '-' + Math.random().toString(36).slice(2, 6).toUpperCase();
function parseLine(l) {
  let m = l.match(/^(.*?)[\s\-–—|,;]+(?:lớp|khối|lop|khoi)?\s*((?:10|11|12)(?:\s*\/\s*\d+|[A-Za-z]+\d*)?)\s*$/iu);
  if (m && m[1].trim()) return [m[1].trim(), m[2].toUpperCase()];
  m = l.match(/^(?:lớp|khối|lop|khoi)?\s*((?:10|11|12)(?:\s*\/\s*\d+|[A-Za-z]+\d*)?)[\s\-–—|,;]+(.+)$/iu);
  return m ? [m[2].trim(), m[1].toUpperCase()] : null;
}
function addStudent(name, cls) {
  const m = String(cls).match(/(10|11|12)\s*(?:\/|[A-Za-z]+)?\s*(\d+)?/);
  name = (name || '').trim();
  if (!m || !name) return false;
  cls = m[2] ? m[1] + '/' + m[2] : m[1];
  db.students.push({id: Date.now() + Math.floor(Math.random() * 1e6), name, cls, grade: parseInt(cls), code: genCode(parseInt(cls))});
  return true;
}
function rankOf(r) { return 1 + db.results.filter(x => x.grade === r.grade && (x.score > r.score || (x.score === r.score && x.used < r.used))).length; }
const fmt = s => String(Math.floor(s / 60)).padStart(2, '0') + ':' + String(s % 60).padStart(2, '0');

function home() { view = 'home';
  go(`<div class="text-center pb-10">
    <div class="emblem"><div class="rays"></div><div class="ring">🏆</div></div>
    <p class="kicker">Chương trình ngoại khoá · Đường lên đỉnh</p>
    <h1 class="logo">OLYMPIA</h1><div class="sub">THPT</div>
    <div class="mt-5"><span class="chip">1 · Khởi động</span><span class="chip">2 · Vượt chướng ngại vật</span><span class="chip">3 · Tăng tốc</span><span class="chip">4 · Về đích</span></div>
    <div class="grid md:grid-cols-2 gap-6 mt-10 max-w-2xl mx-auto">
      <button class="btn b1 text-xl py-6" onclick="teacherLogin()">👨‍🏫 Giáo viên<div class="text-sm font-normal opacity-80">Quản trị cuộc thi</div></button>
      <button class="btn b2 text-xl py-6" onclick="sg=autoGrade();studentLogin()">🎓 Thí sinh<div class="text-sm font-normal opacity-80">Vào phòng thi</div></button>
    </div></div>`);
}
function authShell(icon, title, sub, rules, form) {
  return `<div class="grid md:grid-cols-5 gap-6 max-w-5xl mx-auto mt-4 items-center">
    <div class="md:col-span-2 text-center">
      <div class="emblem !w-28 !h-28"><div class="rays"></div><div class="ring !text-5xl">${icon}</div></div>
      <p class="kicker !mt-6">Olympia THPT</p>
      <h2 class="logo !text-5xl">${title}</h2>
      <p class="mt-2" style="color:#64748b">${sub}</p>
      <div class="text-left mt-5 space-y-2">${rules.map(r => `<div class="rule">${r}</div>`).join('')}</div></div>
    <div class="md:col-span-3 card">${form}</div></div>
    <div class="ticker"><span>★ Chúc các thí sinh thi tốt ★ Đường lên đỉnh Olympia ★ Tự tin · Bản lĩnh · Toả sáng ★ Trung thực là vinh quang cao nhất ★</span></div>`;
}
function teacherLogin() { view = 'tlogin';
  go(authShell('👨‍🏫', 'BAN TỔ CHỨC', 'Khu vực quản trị cuộc thi',
    ['👥 Nhập danh sách & cấp mã thí sinh', '📝 Soạn bộ đề riêng cho khối 10, 11, 12', '⏱️ Cài đặt thời gian thi', '🏅 Xem bảng xếp hạng & xuất báo cáo'],
    `<h3 class="text-2xl font-bold mb-4 text-center">Đăng nhập Giáo viên</h3>
    <input id="pw" type="password" class="inp" placeholder="🔑 Nhập mật khẩu giáo viên" autocomplete="off" onkeydown="if(event.key==='Enter')checkPw()">
    <p class="text-xs mt-1" style="color:#64748b">🔒 Khu vực dành riêng cho Ban tổ chức</p>
    <button class="btn b1 w-full mt-4" onclick="checkPw()">Vào bảng điều khiển</button>
    <button class="btn b3 w-full mt-2" onclick="home()">🏠 Về trang chủ</button>`));
}
function checkPw() { $('#pw').value === TEACHER_PASS ? teacher() : alert('Sai mật khẩu!'); }
function teacher() { view = 'teacher';
  const tabs = [['students','👥 Thí sinh'],['questions','📝 Bộ đề'],['settings','⏱️ Thời gian'],['results','🏅 Kết quả']];
  go(`<div class="flex flex-wrap items-center justify-between gap-3 mb-4">
      <h2 class="text-2xl font-bold text-blue-700">Bảng điều khiển Giáo viên</h2>
      <button class="btn b3" onclick="home()">🏠 Về trang chủ</button></div>
    <div class="flex flex-wrap gap-2 mb-4">${tabs.map(t => `<button class="btn ${tTab === t[0] ? 'b2' : 'b3'}" onclick="tTab='${t[0]}';teacher()">${t[1]}</button>`).join('')}</div>
    <div class="card">${tabHTML()}</div>`);
}
function tabHTML() {
  if (tTab === 'students') return `
    <h3 class="font-bold text-lg mb-2">Nhập danh sách (mỗi dòng: <i>Họ tên - Lớp</i>, ví dụ <b>Nguyễn Văn An - 10/1</b>)</h3>
    <textarea id="bulk" rows="4" class="inp" placeholder="Nguyễn Văn An - 10/1&#10;Trần Thị Bình - 11/2&#10;Lê Hoàng Cường - 12/3"></textarea>
    <button class="btn b1 mt-2" onclick="bulkAdd()">Nhập danh sách & tạo tài khoản</button>
    <div class="grid md:grid-cols-4 gap-2 mt-5">
      <input id="mn" class="inp md:col-span-2" placeholder="Họ tên"><input id="mc" class="inp" placeholder="Lớp (VD: 10/1)">
      <button class="btn b2" onclick="manualAdd()">+ Thêm thủ công</button></div>
    <div class="flex justify-between items-center mt-5"><b>Tổng: ${db.students.length} thí sinh</b>
      <button class="btn b4" onclick="if(confirm('Xoá toàn bộ thí sinh?')){db.students=[];save();teacher()}">Xoá tất cả</button></div>
    <div class="overflow-x-auto mt-2"><table class="w-full"><tr><th>Họ tên</th><th>Lớp</th><th>Khối</th><th>Mã tài khoản</th><th></th></tr>
    ${db.students.map(s => `<tr><td>${esc(s.name)}</td><td>${esc(s.cls)}</td><td>${s.grade}</td><td><b class="font-mono text-orange-600">${s.code}</b></td><td><button onclick="delStu(${s.id})">🗑️</button></td></tr>`).join('') || '<tr><td colspan="5" class="text-center text-slate-400">Chưa có thí sinh</td></tr>'}</table></div>`;
  if (tTab === 'questions') return `
    <div class="flex gap-2 mb-4">${[10,11,12].map(g => `<button class="btn ${qGrade === g ? 'b1' : 'b3'}" onclick="qGrade=${g};teacher()">Khối ${g} (${db.questions[g].length})</button>`).join('')}</div>
    <textarea id="qt" rows="2" class="inp" placeholder="Nội dung câu hỏi khối ${qGrade}"></textarea>
    <div class="grid md:grid-cols-2 gap-2 mt-2">${['A','B','C','D'].map(l => `<input id="o${l}" class="inp" placeholder="Đáp án ${l}">`).join('')}</div>
    <div class="flex flex-wrap gap-2 mt-2 items-center"><b>Đáp án đúng:</b>
      <select id="qa" class="inp !w-24">${['A','B','C','D'].map(l => `<option>${l}</option>`).join('')}</select>
      <button class="btn b2" onclick="addQ()">+ Thêm câu hỏi</button></div>
    <div class="mt-5 space-y-2">${db.questions[qGrade].map((q, i) => `<div class="border rounded-xl p-3 bg-blue-50/50">
      <div class="flex justify-between"><b>Câu ${i + 1}: ${esc(q.q)}</b><button onclick="delQ(${i})">🗑️</button></div>
      <div class="text-sm grid md:grid-cols-2">${q.o.map((o, k) => `<span class="${'ABCD'[k] === q.a ? 'text-green-600 font-bold' : ''}">${'ABCD'[k]}. ${esc(o)}</span>`).join('')}</div></div>`).join('') || '<p class="text-slate-400">Chưa có câu hỏi.</p>'}</div>`;
  if (tTab === 'settings') return `
    <h3 class="font-bold text-lg mb-2">Thời gian làm bài (phút)</h3>
    <div class="flex gap-2 max-w-xs"><input id="tm" type="number" min="1" class="inp" value="${db.time}"><button class="btn b1" onclick="db.time=Math.max(1,+$('#tm').value||30);save();alert('Đã lưu: '+db.time+' phút')">Lưu</button></div>
    <p class="text-sm text-slate-500 mt-2">Áp dụng cho thí sinh bắt đầu làm bài sau khi lưu. Demo đang đặt 5 phút.</p>`;
  const rs = db.results.filter(r => !rFilter || r.grade === rFilter).sort((a, b) => a.grade - b.grade || rankOf(a) - rankOf(b));
  return `<div class="flex flex-wrap gap-2 mb-3">${[0,10,11,12].map(g => `<button class="btn ${rFilter === g ? 'b1' : 'b3'}" onclick="rFilter=${g};teacher()">${g ? 'Khối ' + g : 'Tất cả'}</button>`).join('')}
    <button class="btn b2 ml-auto" onclick="exportCSV()">⬇️ Xuất CSV</button>
    <button class="btn b4" onclick="clearResults()">Xoá KQ</button></div>
    <div class="overflow-x-auto"><table class="w-full"><tr><th>Hạng</th><th>Họ tên</th><th>Lớp</th><th>Khối</th><th>Đúng</th><th>Sai</th><th>Điểm</th><th>Thời gian</th><th>Vi phạm</th></tr>
    ${rs.map(r => `<tr><td><b>${rankOf(r) <= 3 ? ['🥇','🥈','🥉'][rankOf(r) - 1] : rankOf(r)}</b></td><td>${esc(r.name)}</td><td>${esc(r.cls)}</td><td>${r.grade}</td><td class="text-green-600">${r.correct}</td><td class="text-red-500">${r.wrong}</td><td><b>${r.score}</b></td><td>${fmt(r.used)}</td><td>${r.cheats ? '⚠️ ' + r.cheats : '0'}</td></tr>`).join('') || '<tr><td colspan="9" class="text-center text-slate-400">Chưa có kết quả</td></tr>'}</table></div>`;
}
function bulkAdd() {
  let ok = 0, bad = [];
  $('#bulk').value.split('\n').map(l => l.trim()).filter(Boolean).forEach(l => {
    const r = parseLine(l); r && addStudent(r[0], r[1]) ? ok++ : bad.push(l);
  });
  save(); teacher(); alert(`Đã thêm ${ok} thí sinh.` + (bad.length ? `\nKhông đọc được ${bad.length} dòng (cần có lớp 10/11/12).` : ''));
}
function manualAdd() { addStudent($('#mn').value, $('#mc').value) ? (save(), teacher()) : alert('Nhập họ tên và lớp hợp lệ (bắt đầu bằng 10, 11 hoặc 12).'); }
function delStu(id) { db.students = db.students.filter(s => s.id !== id); save(); teacher(); }
function addQ() {
  const q = $('#qt').value.trim(), o = ['A','B','C','D'].map(l => $('#o' + l).value.trim());
  if (!q || o.some(x => !x)) return alert('Hãy nhập đủ câu hỏi và 4 đáp án.');
  db.questions[qGrade].push({q, o, a: $('#qa').value}); save(); teacher();
}
function delQ(i) { db.questions[qGrade].splice(i, 1); save(); teacher(); }
function exportCSV() {
  const rows = [['Hang','Ho ten','Lop','Khoi','Dung','Sai','Diem','Thoi gian','Vi pham']];
  db.results.filter(r => !rFilter || r.grade === rFilter).forEach(r => rows.push([rankOf(r), r.name, r.cls, r.grade, r.correct, r.wrong, r.score, fmt(r.used), r.cheats]));
  const blob = new Blob(['\ufeff' + rows.map(r => r.map(c => `"${c}"`).join(',')).join('\n')], {type: 'text/csv'});
  const a = document.createElement('a'); a.href = URL.createObjectURL(blob); a.download = 'ket-qua-olympia.csv'; a.click();
}

let sg = 10;
const autoGrade = () => [10, 11, 12].find(g => db.students.some(s => s.grade === g)) || 10;
function studentLogin(keep) {
  view = 'login';
  const k1 = keep && $('#sn') ? $('#sn').value : null, k2 = keep && $('#sc') ? $('#sc').value : null;
  const all = db.students.filter(s => s.grade === sg);
  const open = all.filter(s => !db.results.find(r => r.sid === s.id));
  const demo = open[0];
  go(authShell('🎓', 'PHÒNG THI', 'Dành cho thí sinh dự thi',
    ['🔒 Không chuyển tab hay thu nhỏ cửa sổ', '⚠️ Vi phạm 3 lần sẽ bị nộp bài', '⏱️ Hết giờ hệ thống tự thu bài', '🏆 Xem điểm & thứ hạng ngay sau khi nộp'],
    `<div class="steps"><div class="step">① Chọn khối</div><div class="step">② Chọn tên</div><div class="step">③ Nhập mã</div></div>
    <div class="grid grid-cols-3 gap-2 mb-4">${[10, 11, 12].map(g => `<div class="tile ${sg === g ? 'on' : ''}" onclick="sg=${g};studentLogin()">KHỐI ${g}<small>${db.students.filter(s => s.grade === g).length} thí sinh</small></div>`).join('')}</div>
    <label class="font-semibold">Họ tên thí sinh</label>
    <select id="sn" class="inp my-2">
      ${all.map(s => { const d = !open.includes(s); return `<option value="${s.id}" ${d ? 'disabled' : ''} ${s === demo ? 'selected' : ''}>${esc(s.name)} - Lớp ${esc(s.cls)}${d ? ' ✔ đã thi' : ''}</option>`; }).join('') || '<option value="">(Khối này chưa có thí sinh)</option>'}
    </select>
    ${all.length ? '' : '<p class="text-sm text-red-500 mb-2">Chưa có thí sinh khối ' + sg + '. Hãy chọn khối khác hoặc nhờ giáo viên thêm danh sách.</p>'}
    <label class="font-semibold">Mã tài khoản</label>
    <input id="sc" class="inp my-2 uppercase" placeholder="VD: OL10-AB12" autocomplete="off">
    <p class="text-xs" style="color:#64748b">Nhập mã tài khoản do giáo viên cấp cho bạn.</p>
    <p class="text-sm my-2" style="color:#64748b">⏱️ ${db.time} phút · 📝 ${db.questions[sg].length} câu</p>
    <button class="btn b2 w-full" onclick="startExam()">🚀 Vào phòng thi</button>
    <button class="btn b3 w-full mt-2" onclick="home()">🏠 Về trang chủ</button>`));
  if (k1) { const o = [...$('#sn').options].find(x => x.value === k1 && !x.disabled); if (o) { $('#sn').value = k1; if (k2 !== null) $('#sc').value = k2; } }
}
function startExam() {
  const s = db.students.find(x => String(x.id) === $('#sn').value);
  if (!s) return alert('Hãy chọn thí sinh.');
  if (s.code !== $('#sc').value.trim().toUpperCase()) return alert('Mã tài khoản không đúng!');
  const dn = db.results.find(r => r.sid === s.id); if (dn) return showResult(dn, 'Bạn đã dự thi rồi');
  const qs = db.questions[s.grade];
  if (!qs.length) return alert('Khối này chưa có đề thi.');
  if (!confirm(`Bắt đầu thi? Đồng hồ chạy ${db.time} phút. Không chuyển tab/rời trang; vi phạm 3 lần sẽ bị nộp bài.`)) return;
  ex = {sid: s.id, name: s.name, cls: s.cls, grade: s.grade, qs, ans: {}, cur: 0, start: Date.now(), endAt: Date.now() + db.time * 60000, warn: 0};
  renderExam();
}
function tick() {
  if (!ex) return;
  const left = Math.max(0, Math.round((ex.endAt - Date.now()) / 1000));
  const t = $('#clock'); if (t) { t.textContent = fmt(left); t.style.color = left < 60 ? '#f87171' : ''; }
  if (left <= 0) submitExam('Hết giờ!');
}
function nav(i) { ex.cur = i; renderExam(); }
function renderExam() { view = 'exam';
  const q = ex.qs[ex.cur];
  go(`<div class="flex justify-between items-center mb-3 flex-wrap gap-2">
      <div><b class="text-blue-700">${esc(ex.name)}</b> · Lớp ${esc(ex.cls)}</div>
      <div class="clockbox">⏱️ <span id="clock">--:--</span></div>
      <button class="btn b3" onclick="if(confirm('Thoát phòng thi sẽ NỘP BÀI ngay. Chắc chắn?'))submitExam('Bạn đã thoát phòng thi')">🏠 Thoát (nộp bài)</button></div>
    <div class="grid md:grid-cols-4 gap-4">
      <div class="card md:col-span-3">
        <div class="text-orange-500 font-bold">Câu ${ex.cur + 1}/${ex.qs.length}</div>
        <h3 class="text-xl font-bold my-2">${esc(q.q)}</h3>
        ${q.o.map((o, k) => `<div class="opt ${ex.ans[ex.cur] === 'ABCD'[k] ? 'sel' : ''}" onclick="ex.ans[ex.cur]='${'ABCD'[k]}';renderExam()"><b>${'ABCD'[k]}.</b> ${esc(o)}</div>`).join('')}
        <div class="flex justify-between mt-5">
          <button class="btn b3" ${ex.cur === 0 ? 'disabled style="opacity:.4"' : ''} onclick="nav(ex.cur-1)">← Trước</button>
          ${ex.cur < ex.qs.length - 1 ? `<button class="btn b1" onclick="nav(ex.cur+1)">Sau →</button>` : `<button class="btn b2" onclick="if(confirm('Nộp bài?'))submitExam('Đã nộp bài')">Nộp bài ✔</button>`}
        </div></div>
      <div class="card"><b>Danh sách câu</b><div class="grid grid-cols-5 gap-1 mt-2">${ex.qs.map((_, i) => `<button class="btn !p-1 ${i === ex.cur ? 'b2' : ex.ans[i] ? 'b1' : 'b3'}" onclick="nav(${i})">${i + 1}</button>`).join('')}</div>
        <p class="text-sm mt-3 text-slate-500">⚠️ Vi phạm: <b class="text-red-500">${ex.warn}/3</b></p>
        <button class="btn b2 w-full mt-3" onclick="if(confirm('Nộp bài?'))submitExam('Đã nộp bài')">Nộp bài</button>
        </div>
    </div>`);
  tick(); timer = setInterval(tick, 500);
}
function submitExam(msg) {
  if (!ex) return;
  clearInterval(timer);
  let c = 0; ex.qs.forEach((q, i) => { if (ex.ans[i] === q.a) c++; });
  const total = ex.qs.length;
  const r = {sid: ex.sid, name: ex.name, cls: ex.cls, grade: ex.grade, correct: c, wrong: total - c, total, score: +(c / total * 10).toFixed(2),
    used: Math.min(Math.round((Date.now() - ex.start) / 1000), db.time * 60), cheats: ex.warn, ts: Date.now()};
  db.results.push(r); (window.cloud ? cloud.saveResult(r) : Promise.reject(new Error('Chưa kết nối'))).catch(e => alert('Chưa gửi được kết quả: ' + e.message + '. Đừng đóng trang này!')); ex = null; closeModal(); showResult(r, msg);
}
function showResult(r, msg) { view = 'result';
  const rk = rankOf(r), n = db.results.filter(x => x.grade === r.grade).length;
  go(`<div class="card max-w-lg mx-auto mt-10 text-center">
    <div class="text-6xl">${rk === 1 ? '🥇' : rk === 2 ? '🥈' : rk === 3 ? '🥉' : '🎉'}</div>
    <h2 class="text-2xl font-bold text-blue-700 mt-2">${esc(r.name)} · Lớp ${esc(r.cls)}</h2>
    <p class="text-orange-500 font-semibold">${msg || 'Bạn đã hoàn thành bài thi'}</p>
    <div class="grid grid-cols-3 gap-3 my-5">
      <div class="bg-green-50 rounded-xl p-3"><div class="text-3xl font-bold text-green-600">${r.correct}</div>Đúng</div>
      <div class="bg-red-50 rounded-xl p-3"><div class="text-3xl font-bold text-red-500">${r.wrong}</div>Sai</div>
      <div class="bg-blue-50 rounded-xl p-3"><div class="text-3xl font-bold text-blue-600">${r.score}</div>Điểm</div></div>
    <p class="text-lg">Thứ hạng khối ${r.grade}: <b class="text-orange-500 text-2xl">${rk}/${n}</b></p>
    <p class="text-sm text-slate-500">Thời gian: ${fmt(r.used)} · Vi phạm: ${r.cheats}</p>
    <button class="btn b1 w-full mt-5" onclick="home()">🏠 Về trang chủ</button></div>`);
}

let lastV = 0;
function violation(reason) {
  if (!ex || Date.now() - lastV < 1500) return;
  lastV = Date.now(); ex.warn++;
  if (ex.warn >= 3) { showModal(`<div class="text-5xl">🚫</div><h3 class="text-xl font-bold text-red-600 mt-2">Vi phạm 3 lần!</h3><p>Bài thi bị tự động nộp.</p>`); return setTimeout(() => submitExam('Bị nộp bài do vi phạm quy chế'), 1200); }
  showModal(`<div class="text-5xl">⚠️</div><h3 class="text-xl font-bold text-red-600 mt-2">Cảnh báo vi phạm ${ex.warn}/3</h3>
    <p class="my-2">${reason}. Hành vi này đã được ghi nhận!</p><button class="btn b2" onclick="closeModal();renderExam()">Tôi đã hiểu, tiếp tục thi</button>`);
}
document.addEventListener('visibilitychange', () => { if (document.hidden) violation('Bạn đã chuyển tab / thu nhỏ cửa sổ'); });
window.addEventListener('blur', () => violation('Bạn đã rời khỏi cửa sổ thi'));
document.addEventListener('copy', e => { if (ex) { e.preventDefault(); violation('Bạn đã cố sao chép nội dung'); } });
window.addEventListener('beforeunload', e => { if (ex) { e.preventDefault(); e.returnValue = ''; } });
home();
</script>
<script type="module">
import {initializeApp} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
import {getFirestore, doc, setDoc, deleteDoc, onSnapshot, collection} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";
const app = initializeApp({
  apiKey: "AIzaSyCNLdWm8bDvwzhRjHft6StYwiOufQmIJ3Y",
  authDomain: "olympia-9537c.firebaseapp.com",
  projectId: "olympia-9537c",
  storageBucket: "olympia-9537c.firebasestorage.app",
  messagingSenderId: "905047633999",
  appId: "1:905047633999:web:afd37ae6f293c33df23a3a"
});
const fs = getFirestore(app);
window.cloud = {
  saveConfig: d => setDoc(doc(fs, 'olympia', 'config'), d),
  saveResult: r => setDoc(doc(fs, 'results', String(r.sid)), r),
  clearResults: ids => Promise.all(ids.map(id => deleteDoc(doc(fs, 'results', String(id)))))
};
const opt = {includeMetadataChanges: true};
onSnapshot(doc(fs, 'olympia', 'config'), opt, snap => { window.onNet(!snap.metadata.fromCache); window.onConfig(snap.exists() ? snap.data() : null, snap.metadata.fromCache); }, e => window.onCloudError(e));
onSnapshot(collection(fs, 'results'), opt, snap => { window.onResults(snap.docs.map(d => d.data())); }, e => window.onCloudError(e));
</script>
</body>
</html>
