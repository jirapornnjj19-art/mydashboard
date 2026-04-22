# mydashboard
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Dashboard ✨</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Noto+Sans+Thai:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --coral:   #FF6B6B; --coral-l:  #FFE8E8; --coral-m:  #FF9B9B;
  --amber:   #FF9F43; --amber-l:  #FFF3E0; --amber-m:  #FFBD6B;
  --yellow:  #FECA57; --yellow-l: #FFFBE0; --yellow-m: #FFD97D;
  --green:   #1DD1A1; --green-l:  #E0FBF4; --green-m:  #55EFC4;
  --teal:    #00CEC9; --teal-l:   #E0FAFA; --teal-m:   #48D9D5;
  --blue:    #4A90D9; --blue-l:   #E8F2FC; --blue-m:   #74ACE8;
  --purple:  #A29BFE; --purple-l: #F0EFFE; --purple-m: #C0BAFF;
  --pink:    #FD79A8; --pink-l:   #FEE8F1; --pink-m:   #FF9EC4;
  --bg: #F8F6FF;
  --surface: #FFFFFF;
  --text: #2D3436;
  --muted: #B2BEC3;
  --border: #EEE9FF;
  --shadow: 0 4px 20px rgba(100,80,180,0.08);
  --shadow-hover: 0 8px 32px rgba(100,80,180,0.16);
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Noto Sans Thai', sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* BACKGROUND BLOBS */
body::before {
  content: '';
  position: fixed;
  top: -120px; left: -120px;
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(162,155,254,0.18) 0%, transparent 70%);
  pointer-events: none; z-index: 0;
}
body::after {
  content: '';
  position: fixed;
  bottom: -100px; right: -100px;
  width: 360px; height: 360px;
  background: radial-gradient(circle, rgba(253,121,168,0.14) 0%, transparent 70%);
  pointer-events: none; z-index: 0;
}

/* NAV */
.nav {
  position: sticky; top: 0; z-index: 100;
  background: rgba(248,246,255,0.88);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border);
  padding: 0 24px;
  display: flex; align-items: center; gap: 0;
}
.nav-brand {
  font-family: 'Fredoka', sans-serif;
  font-size: 20px; font-weight: 700;
  background: linear-gradient(135deg, var(--purple), var(--pink));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  margin-right: 28px;
  padding: 14px 0;
  white-space: nowrap;
}
.nav-tabs { display: flex; gap: 0; }
.nav-tab {
  padding: 14px 18px;
  font-size: 13px; font-weight: 500;
  color: var(--muted);
  cursor: pointer;
  border-bottom: 3px solid transparent;
  transition: all 0.2s;
  white-space: nowrap;
}
.nav-tab:hover { color: var(--text); }
.nav-tab.active { color: var(--purple); border-bottom-color: var(--purple); }

.date-badge {
  margin-left: auto;
  font-size: 12px; color: var(--muted);
  background: var(--purple-l);
  padding: 4px 12px; border-radius: 20px;
  font-weight: 500;
}

/* VIEWS */
.view { display: none; padding: 28px 24px 60px; max-width: 1080px; margin: 0 auto; position: relative; z-index: 1; }
.view.active { display: block; }

/* SECTION HEADER */
.sec-hdr {
  display: flex; align-items: center; gap: 10px;
  margin-bottom: 18px; margin-top: 32px;
}
.sec-hdr:first-child { margin-top: 0; }
.sec-icon {
  width: 36px; height: 36px; border-radius: 10px;
  display: flex; align-items: center; justify-content: center;
  font-size: 18px; flex-shrink: 0;
}
.sec-title {
  font-family: 'Fredoka', sans-serif;
  font-size: 20px; font-weight: 600;
  color: var(--text);
}
.sec-sub { font-size: 12px; color: var(--muted); margin-left: auto; }

/* DAY SELECTOR */
.day-selector {
  display: flex; gap: 8px; flex-wrap: wrap;
  margin-bottom: 24px;
}
.day-btn {
  padding: 8px 16px;
  border-radius: 20px;
  border: 2px solid var(--border);
  background: var(--surface);
  font-family: 'Noto Sans Thai', sans-serif;
  font-size: 13px; font-weight: 500;
  cursor: pointer;
  transition: all 0.18s;
  color: var(--muted);
}
.day-btn:hover { border-color: var(--purple-m); color: var(--purple); }
.day-btn.active {
  border-color: transparent;
  color: white;
  transform: scale(1.05);
}
.day-btn.beauty-btn.active { background: linear-gradient(135deg, var(--pink), var(--purple)); }
.day-btn[data-day="0"].active  { background: linear-gradient(135deg, var(--amber), var(--yellow)); }
.day-btn[data-day="1"].active  { background: linear-gradient(135deg, var(--coral), var(--amber)); }
.day-btn[data-day="2"].active  { background: linear-gradient(135deg, var(--teal), var(--blue)); }
.day-btn[data-day="3"].active  { background: linear-gradient(135deg, var(--purple), var(--blue)); }
.day-btn[data-day="4"].active  { background: linear-gradient(135deg, var(--green), var(--teal)); }
.day-btn[data-day="5"].active  { background: linear-gradient(135deg, var(--blue), var(--purple)); }
.day-btn[data-day="6"].active  { background: linear-gradient(135deg, var(--pink), var(--coral)); }

/* CHECKLIST CARD */
.checklist-card {
  background: var(--surface);
  border-radius: 20px;
  padding: 20px 20px 12px;
  box-shadow: var(--shadow);
  border: 1px solid var(--border);
  margin-bottom: 12px;
}
.checklist-card-hdr {
  display: flex; align-items: center; gap: 10px;
  margin-bottom: 14px;
  padding-bottom: 12px;
  border-bottom: 1px dashed var(--border);
}
.card-emoji { font-size: 22px; }
.card-title {
  font-family: 'Fredoka', sans-serif;
  font-size: 17px; font-weight: 600;
}
.card-progress {
  margin-left: auto;
  font-size: 12px; font-weight: 600;
  padding: 3px 10px;
  border-radius: 12px;
  background: var(--purple-l);
  color: var(--purple);
  transition: all 0.3s;
}
.card-progress.done { background: var(--green-l); color: var(--green); }

/* TASK ITEM */
.task-item {
  display: flex; align-items: center; gap: 12px;
  padding: 9px 6px;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.15s;
  user-select: none;
  position: relative;
}
.task-item:hover { background: var(--bg); }
.task-item.done .task-text { text-decoration: line-through; color: var(--muted); }
.task-item.done .task-time { color: var(--muted); }

.task-check {
  width: 22px; height: 22px;
  border-radius: 7px;
  border: 2.5px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
  transition: all 0.2s cubic-bezier(0.34,1.56,0.64,1);
  font-size: 13px;
  background: white;
}
.task-item.done .task-check {
  border-color: transparent;
  transform: scale(1.1);
}

.task-time {
  font-size: 11px; color: var(--muted);
  min-width: 38px;
  font-variant-numeric: tabular-nums;
  font-weight: 500;
}
.task-text { font-size: 13.5px; flex: 1; line-height: 1.4; }

/* confetti pop */
@keyframes popCheck {
  0% { transform: scale(1); }
  40% { transform: scale(1.35); }
  70% { transform: scale(0.92); }
  100% { transform: scale(1.08); }
}
.task-item.just-done .task-check { animation: popCheck 0.4s ease forwards; }

/* BEAUTY DAY */
.beauty-card {
  background: linear-gradient(135deg, #FFF0F8, #F8F0FF);
  border: 2px solid var(--pink-m);
  border-radius: 20px;
  padding: 24px;
  text-align: center;
}
.beauty-card h2 {
  font-family: 'Fredoka', sans-serif;
  font-size: 28px;
  background: linear-gradient(135deg, var(--pink), var(--purple));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  margin-bottom: 6px;
}
.beauty-card p { color: var(--muted); font-size: 14px; margin-bottom: 16px; }
.beauty-items {
  display: flex; flex-wrap: wrap; gap: 8px; justify-content: center;
}
.beauty-pill {
  background: white;
  border: 1.5px solid var(--pink-m);
  color: var(--pink);
  font-size: 13px; font-weight: 500;
  padding: 6px 14px; border-radius: 20px;
  cursor: pointer; transition: all 0.2s;
}
.beauty-pill:hover { background: var(--pink-l); }
.beauty-pill.ticked {
  background: linear-gradient(135deg, var(--pink), var(--purple));
  border-color: transparent; color: white;
}

/* PROGRESS BAR */
.progress-wrap {
  background: var(--border);
  border-radius: 10px; height: 6px;
  margin: 12px 0 4px;
  overflow: hidden;
}
.progress-bar {
  height: 100%; border-radius: 10px;
  transition: width 0.4s ease;
  background: linear-gradient(90deg, var(--purple), var(--pink));
}

/* HABIT GRID */
.habit-grid {
  background: var(--surface);
  border-radius: 20px;
  padding: 20px;
  box-shadow: var(--shadow);
  border: 1px solid var(--border);
}
.habit-row {
  display: grid;
  grid-template-columns: 160px repeat(7,1fr);
  gap: 6px;
  align-items: center;
  margin-bottom: 8px;
}
.habit-label { font-size: 13px; font-weight: 500; }
.habit-day-hdr {
  text-align: center;
  font-size: 10px; font-weight: 600;
  color: var(--muted);
  letter-spacing: 0.5px;
}
.habit-dot {
  width: 32px; height: 32px;
  border-radius: 50%;
  border: 2px solid var(--border);
  background: var(--bg);
  cursor: pointer;
  transition: all 0.2s cubic-bezier(0.34,1.56,0.64,1);
  margin: 0 auto;
  display: flex; align-items: center; justify-content: center;
  font-size: 14px;
}
.habit-dot:hover { border-color: var(--purple-m); transform: scale(1.1); }
.habit-dot.done { border-color: transparent; transform: scale(1.12); }

/* GOAL CARDS */
.goals-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 14px;
}
.goal-card {
  border-radius: 16px;
  padding: 18px;
  border: 1.5px solid transparent;
  position: relative; overflow: hidden;
}
.goal-card::before {
  content: '';
  position: absolute; inset: 0;
  opacity: 0.08;
  background: inherit;
}
.goal-title { font-size: 12px; font-weight: 600; opacity: 0.8; margin-bottom: 6px; letter-spacing: 0.5px; }
.goal-text { font-size: 14px; font-weight: 600; line-height: 1.5; }
.goal-emoji { font-size: 28px; margin-bottom: 8px; display: block; }

/* WEEKLY OVERVIEW */
.week-strip {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  gap: 8px;
  margin-bottom: 8px;
}
.week-col {
  background: var(--surface);
  border-radius: 14px;
  padding: 12px 6px;
  text-align: center;
  border: 1.5px solid var(--border);
  cursor: pointer;
  transition: all 0.18s;
}
.week-col:hover { border-color: var(--purple-m); box-shadow: var(--shadow-hover); transform: translateY(-2px); }
.week-col.today { border-color: var(--purple); background: var(--purple-l); }
.week-col.beauty-day { border-color: var(--pink); background: var(--pink-l); }
.wc-dow { font-size: 10px; font-weight: 600; color: var(--muted); letter-spacing: 1px; margin-bottom: 4px; }
.wc-date { font-family: 'Fredoka', sans-serif; font-size: 22px; font-weight: 600; }
.wc-label { font-size: 9px; color: var(--muted); margin-top: 4px; line-height: 1.3; }
.wc-dots { display: flex; gap: 3px; justify-content: center; margin-top: 6px; flex-wrap: wrap; }
.wc-dot { width: 6px; height: 6px; border-radius: 50%; }

/* RESET BTN */
.reset-btn {
  background: var(--coral-l);
  border: 1.5px solid var(--coral-m);
  color: var(--coral);
  font-family: 'Noto Sans Thai', sans-serif;
  font-size: 12px; font-weight: 500;
  padding: 6px 14px; border-radius: 20px;
  cursor: pointer; transition: all 0.2s;
  margin-left: 8px;
}
.reset-btn:hover { background: var(--coral-m); color: white; }

/* CHIP */
.chip {
  display: inline-flex; align-items: center; gap: 4px;
  font-size: 11px; font-weight: 600;
  padding: 3px 10px; border-radius: 12px;
}

@media (max-width: 640px) {
  .view { padding: 16px 12px 48px; }
  .nav { padding: 0 12px; }
  .habit-row { grid-template-columns: 120px repeat(7,1fr); }
  .week-strip { gap: 4px; }
  .wc-date { font-size: 17px; }
}
</style>
</head>
<body>

<nav class="nav">
  <div class="nav-brand">✨ My Dashboard</div>
  <div class="nav-tabs">
    <div class="nav-tab active" onclick="switchView('today',this)">วันนี้</div>
    <div class="nav-tab" onclick="switchView('weekly',this)">สัปดาห์</div>
    <div class="nav-tab" onclick="switchView('habits',this)">Habits</div>
    <div class="nav-tab" onclick="switchView('goals',this)">Goals</div>
  </div>
  <div class="date-badge" id="todayBadge"></div>
</nav>

<!-- TODAY VIEW -->
<div class="view active" id="view-today">
  <div class="day-selector" id="daySelector"></div>
  <div id="checklistContent"></div>
</div>

<!-- WEEKLY VIEW -->
<div class="view" id="view-weekly">
  <div class="sec-hdr">
    <div class="sec-icon" style="background:#F0EFFE;">📅</div>
    <div class="sec-title">ภาพรวมสัปดาห์นี้</div>
  </div>
  <div class="week-strip" id="weekStrip"></div>
  <div id="weekDetail"></div>
</div>

<!-- HABITS VIEW -->
<div class="view" id="view-habits">
  <div class="sec-hdr">
    <div class="sec-icon" style="background:#E0FBF4;">💪</div>
    <div class="sec-title">Habit Tracker</div>
    <button class="reset-btn" onclick="resetHabits()">Reset สัปดาห์ใหม่</button>
  </div>
  <div class="habit-grid" id="habitGrid"></div>
</div>

<!-- GOALS VIEW -->
<div class="view" id="view-goals">
  <div class="sec-hdr">
    <div class="sec-icon" style="background:#FFF3E0;">🎯</div>
    <div class="sec-title">Goals เดือนนี้</div>
  </div>
  <div class="goals-grid" id="goalsGrid"></div>
</div>

<script>
// ================================================================
// CONFIG
// ================================================================
const DOW = ['จ','อ','พ','พฤ','ศ','ส','อา'];
const DOW_FULL = ['จันทร์','อังคาร','พุธ','พฤหัส','ศุกร์','เสาร์','อาทิตย์'];
const DAY_LABELS = ['Content Day 🎬','Babebrow + Live 💉','สักคิ้ว + แว่น 🕶️','อสังหา + เรียน 🏠','สักคิ้ว + Live 🔴','สักคิ้ว + แฟน ❤️','สักคิ้ว + Content 🎬'];

// Color per dow
const DAY_COLORS = [
  {bg:'#FFF3E0',accent:'#FF9F43',gradient:'linear-gradient(135deg,#FF9F43,#FECA57)'},
  {bg:'#FFE8E8',accent:'#FF6B6B',gradient:'linear-gradient(135deg,#FF6B6B,#FF9F43)'},
  {bg:'#E0FAFA',accent:'#00CEC9',gradient:'linear-gradient(135deg,#00CEC9,#4A90D9)'},
  {bg:'#F0EFFE',accent:'#A29BFE',gradient:'linear-gradient(135deg,#A29BFE,#4A90D9)'},
  {bg:'#E0FBF4',accent:'#1DD1A1',gradient:'linear-gradient(135deg,#1DD1A1,#00CEC9)'},
  {bg:'#E8F2FC',accent:'#4A90D9',gradient:'linear-gradient(135deg,#4A90D9,#A29BFE)'},
  {bg:'#FEE8F1',accent:'#FD79A8',gradient:'linear-gradient(135deg,#FD79A8,#FF6B6B)'},
];

// ================================================================
// ROUTINES
// ================================================================
function getRoutine(dow, isBeauty) {
  if (isBeauty) return {
    beauty: true,
    items: ['💆 นวด / สปา','🌸 ทำผม','💅 ทำเล็บ','☕ Cafe อร่อยๆ','🛍️ Shopping','🎬 Netflix','😴 นอนเร็ว']
  };

  const r = {
    0: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย 1.5 ชม.',color:'#1DD1A1'},
      {time:'10:00',text:'📝 Plan + Script คลิปทั้งสัปดาห์',color:'#FF9F43'},
      {time:'11:00',text:'📖 เรียนภาษา (อังกฤษ/จีน) 1 ชม.',color:'#00CEC9'},
      {time:'12:00',text:'🍽️ พักกินข้าวเที่ยง',color:'#B2BEC3'},
      {time:'13:00',text:'🎬 ถ่าย Batch คลิป 3–5 คลิป',color:'#FF9F43'},
      {time:'15:00',text:'📘 คอร์สธุรกิจ 1 ชม.',color:'#00CEC9'},
      {time:'16:00',text:'✂️ ตัดต่อ + Schedule โพสต์ทั้งสัปดาห์',color:'#FF9F43'},
      {time:'17:30',text:'🌙 กินข้าวเย็น / พัก',color:'#B2BEC3'},
      {time:'19:00',text:'📖 เรียนภาษา 1 ชม.',color:'#00CEC9'},
      {time:'20:30',text:'📚 อ่านหนังสือ 1 ชม.',color:'#A29BFE'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
    1: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย 1–1.5 ชม.',color:'#1DD1A1'},
      {time:'10:00',text:'📚 อ่านหนังสือเบาๆ / พักก่อนสัก',color:'#B2BEC3'},
      {time:'11:00',text:'💉 สักคิ้ว ลูกค้า (11:00–17:00)',color:'#FF6B6B'},
      {time:'17:00',text:'🖼️ แต่งรูป + โพสต์ IG / ลงคิว',color:'#FF6B6B'},
      {time:'18:30',text:'⚡ เตรียม Live 30 นาที',color:'#FF6B6B'},
      {time:'19:00',text:'🔴 Live IG/TikTok 1 ชม.',color:'#FF6B6B'},
      {time:'20:30',text:'📊 เช็ค Engage Content',color:'#FF9F43'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
    2: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย 1.5 ชม.',color:'#1DD1A1'},
      {time:'10:00',text:'📚 อ่านหนังสือเบาๆ / พักก่อนสัก',color:'#B2BEC3'},
      {time:'11:00',text:'💉 สักคิ้ว ลูกค้า (11:00–17:00)',color:'#FF6B6B'},
      {time:'17:00',text:'🖼️ แต่งรูป Babebrow + โพสต์ IG',color:'#FF6B6B'},
      {time:'18:00',text:'🕶️ Gales Haus: ถ่ายแว่น + โพสต์ + Ads',color:'#4A90D9'},
      {time:'19:00',text:'🏠 อสังหา: หาทรัพย์ / อัพเพจ',color:'#A29BFE'},
      {time:'20:30',text:'📘 คอร์สธุรกิจ 1 ชม.',color:'#00CEC9'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
    3: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย 1.5 ชม.',color:'#1DD1A1'},
      {time:'10:00',text:'🏠 อสังหา: หาทรัพย์ใน Social',color:'#A29BFE'},
      {time:'11:00',text:'📖 เรียนภาษา 1 ชม.',color:'#00CEC9'},
      {time:'12:00',text:'🍽️ พักกินข้าวเที่ยง',color:'#B2BEC3'},
      {time:'13:00',text:'📘 คอร์สธุรกิจ 1 ชม.',color:'#00CEC9'},
      {time:'14:00',text:'🏠 อสังหา: อัพเดทเพจ / ตอบ DM',color:'#A29BFE'},
      {time:'17:30',text:'🌙 กินข้าวเย็น / พัก',color:'#B2BEC3'},
      {time:'19:00',text:'🏠 อสังหา: Engage / ออกดูทรัพย์',color:'#A29BFE'},
      {time:'20:30',text:'📚 อ่านหนังสือ 1 ชม.',color:'#A29BFE'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
    4: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย 1.5 ชม.',color:'#1DD1A1'},
      {time:'10:00',text:'📚 อ่านหนังสือเบาๆ / พักก่อนสัก',color:'#B2BEC3'},
      {time:'11:00',text:'💉 สักคิ้ว ลูกค้า (11:00–17:00)',color:'#FF6B6B'},
      {time:'17:00',text:'🖼️ แต่งรูป Babebrow + โพสต์ IG',color:'#FF6B6B'},
      {time:'17:30',text:'🕶️ Gales Haus: Ads + ดู Insight',color:'#4A90D9'},
      {time:'18:30',text:'⚡ เตรียม Live 30 นาที',color:'#FF6B6B'},
      {time:'19:00',text:'🔴 Live IG/TikTok 1 ชม.',color:'#FF6B6B'},
      {time:'20:30',text:'📝 Plan Content สัปดาห์หน้า',color:'#FF9F43'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
    5: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย (เบา) 1 ชม.',color:'#1DD1A1'},
      {time:'09:30',text:'📚 อ่านหนังสือเบาๆ / พักก่อนสัก',color:'#B2BEC3'},
      {time:'11:00',text:'💉 สักคิ้ว ลูกค้า (11:00–17:00)',color:'#FF6B6B'},
      {time:'17:00',text:'😌 พักผ่อน',color:'#B2BEC3'},
      {time:'19:00',text:'❤️ เวลาแฟน / ออกไปกิน',color:'#FD79A8'},
      {time:'21:00',text:'📚 อ่านหนังสือ / Netflix',color:'#A29BFE'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
    6: [
      {time:'08:00',text:'ตื่น + Morning routine',color:'#A29BFE'},
      {time:'08:30',text:'🏋️ ออกกำลังกาย (เบา) 1 ชม.',color:'#1DD1A1'},
      {time:'09:30',text:'📚 อ่านหนังสือเบาๆ / พักก่อนสัก',color:'#B2BEC3'},
      {time:'11:00',text:'💉 สักคิ้ว ลูกค้า (11:00–17:00)',color:'#FF6B6B'},
      {time:'17:00',text:'🌙 กินข้าวเย็น / พักผ่อน',color:'#B2BEC3'},
      {time:'18:00',text:'✂️ Content: ตัดคลิป + Schedule',color:'#FF9F43'},
      {time:'19:00',text:'📖 เรียนภาษา 1 ชม.',color:'#00CEC9'},
      {time:'20:00',text:'❤️ เวลาแฟน / พักผ่อน',color:'#FD79A8'},
      {time:'23:00',text:'😴 นอน',color:'#B2BEC3'},
    ],
  };
  return { beauty: false, items: r[dow] };
}

// Beauty days: every 2nd & 4th Thursday of month
function isBeautyDay(date) {
  if ((date.getDay()+6)%7 !== 3) return false; // not Thursday
  const d = date.getDate();
  // count Thursdays up to this date
  let count = 0;
  for (let i = 1; i <= d; i++) {
    const t = new Date(date.getFullYear(), date.getMonth(), i);
    if ((t.getDay()+6)%7 === 3) count++;
  }
  return count === 2 || count === 4;
}

// ================================================================
// STORAGE
// ================================================================
const STORE = {
  key: k => `dash_${k}`,
  get: k => { try { return JSON.parse(localStorage.getItem(STORE.key(k))) || {}; } catch { return {}; } },
  set: (k,v) => { try { localStorage.setItem(STORE.key(k), JSON.stringify(v)); } catch {} },
};

function todayKey() {
  const d = new Date();
  return `${d.getFullYear()}-${d.getMonth()+1}-${d.getDate()}`;
}
function dateKey(date) {
  return `${date.getFullYear()}-${date.getMonth()+1}-${date.getDate()}`;
}

// ================================================================
// STATE
// ================================================================
const now = new Date();
const todayDOW = (now.getDay()+6)%7;
let selectedDOW = todayDOW;
let selectedDateKey = todayKey();

// ================================================================
// TODAY VIEW
// ================================================================
function renderDaySelector() {
  const el = document.getElementById('daySelector');
  el.innerHTML = '';
  // Current week Mon
  const weekStart = new Date(now);
  weekStart.setDate(now.getDate() - todayDOW);

  for (let i = 0; i < 7; i++) {
    const d = new Date(weekStart);
    d.setDate(weekStart.getDate() + i);
    const beauty = isBeautyDay(d);
    const isToday = i === todayDOW;
    const btn = document.createElement('button');
    btn.className = 'day-btn' + (beauty ? ' beauty-btn' : '') + (i === selectedDOW ? ' active' : '');
    btn.dataset.day = i;
    btn.innerHTML = `<span style="font-size:11px;opacity:0.7;">${DOW[i]}</span> <span style="font-size:16px;font-family:'Fredoka',sans-serif;font-weight:600;">${d.getDate()}</span>${isToday ? ' <span style="font-size:9px;">●</span>' : ''}`;
    btn.style.display = 'flex'; btn.style.flexDirection = 'column'; btn.style.alignItems = 'center'; btn.style.padding = '8px 14px'; btn.style.gap = '2px';
    btn.onclick = () => {
      selectedDOW = i;
      selectedDateKey = dateKey(d);
      document.querySelectorAll('.day-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      renderChecklist();
    };
    el.appendChild(btn);
  }
}

function renderChecklist() {
  const el = document.getElementById('checklistContent');
  el.innerHTML = '';
  const beauty = isBeautyDay(new Date(now.getFullYear(), now.getMonth(), parseInt(selectedDateKey.split('-')[2])));
  const routine = getRoutine(selectedDOW, beauty);
  const stored = STORE.get(selectedDateKey);
  const col = DAY_COLORS[selectedDOW];

  if (beauty) {
    const card = document.createElement('div');
    card.className = 'beauty-card';
    card.innerHTML = `<h2>⭐ Beauty Day</h2><p>ไม่มีงานแม้แต่ชิ้นเดียว · กดติ๊กสิ่งที่ทำแล้ว!</p><div class="beauty-items" id="beautyItems"></div>`;
    el.appendChild(card);
    const bi = card.querySelector('#beautyItems');
    routine.items.forEach((item, idx) => {
      const pill = document.createElement('div');
      pill.className = 'beauty-pill' + (stored[idx] ? ' ticked' : '');
      pill.textContent = item;
      pill.onclick = () => {
        const s = STORE.get(selectedDateKey);
        s[idx] = !s[idx];
        STORE.set(selectedDateKey, s);
        pill.classList.toggle('ticked');
      };
      bi.appendChild(pill);
    });
    return;
  }

  // Normal day card
  const card = document.createElement('div');
  card.className = 'checklist-card';

  const hdr = document.createElement('div');
  hdr.className = 'checklist-card-hdr';

  const total = routine.items.length;
  const done = routine.items.filter((_, i) => stored[i]).length;

  hdr.innerHTML = `
    <span class="card-emoji">📋</span>
    <span class="card-title" style="background:${col.gradient};-webkit-background-clip:text;-webkit-text-fill-color:transparent;">${DOW_FULL[selectedDOW]} — ${DAY_LABELS[selectedDOW]}</span>
    <span class="card-progress ${done===total?'done':''}" id="progressLabel">${done}/${total}</span>
  `;
  card.appendChild(hdr);

  // Progress bar
  const pw = document.createElement('div'); pw.className = 'progress-wrap';
  const pb = document.createElement('div'); pb.className = 'progress-bar';
  pb.id = 'progressBar';
  pb.style.width = total > 0 ? `${(done/total)*100}%` : '0%';
  pb.style.background = col.gradient;
  pw.appendChild(pb); card.appendChild(pw);

  // Tasks
  routine.items.forEach((item, idx) => {
    const isDone = !!stored[idx];
    const row = document.createElement('div');
    row.className = 'task-item' + (isDone ? ' done' : '');
    row.innerHTML = `
      <div class="task-check" style="${isDone ? `background:${col.gradient};` : ''}">
        ${isDone ? '✓' : ''}
      </div>
      <span class="task-time">${item.time}</span>
      <span class="task-text">${item.text}</span>
    `;
    row.onclick = () => toggleTask(selectedDateKey, idx, row, total, col);
    card.appendChild(row);
  });

  el.appendChild(card);
}

function toggleTask(dkey, idx, row, total, col) {
  const s = STORE.get(dkey);
  s[idx] = !s[idx];
  STORE.set(dkey, s);

  const isDone = s[idx];
  row.classList.toggle('done', isDone);
  row.classList.add('just-done');
  setTimeout(() => row.classList.remove('just-done'), 400);

  const check = row.querySelector('.task-check');
  if (isDone) {
    check.style.background = col.gradient;
    check.textContent = '✓';
  } else {
    check.style.background = '';
    check.textContent = '';
  }

  // Update progress
  const allDone = Object.values(STORE.get(dkey)).filter(Boolean).length;
  const lbl = document.getElementById('progressLabel');
  const bar = document.getElementById('progressBar');
  if (lbl) { lbl.textContent = `${allDone}/${total}`; lbl.className = 'card-progress' + (allDone===total?' done':''); }
  if (bar) bar.style.width = `${(allDone/total)*100}%`;
}

// ================================================================
// WEEKLY VIEW
// ================================================================
function renderWeekly() {
  const strip = document.getElementById('weekStrip');
  strip.innerHTML = '';
  const weekStart = new Date(now);
  weekStart.setDate(now.getDate() - todayDOW);

  for (let i = 0; i < 7; i++) {
    const d = new Date(weekStart);
    d.setDate(weekStart.getDate() + i);
    const beauty = isBeautyDay(d);
    const isToday = i === todayDOW;
    const dkey = dateKey(d);
    const stored = STORE.get(dkey);
    const routine = getRoutine(i, beauty);
    const total = beauty ? routine.items.length : routine.items.length;
    const done = Object.values(stored).filter(Boolean).length;
    const col = DAY_COLORS[i];

    const col_el = document.createElement('div');
    col_el.className = 'week-col' + (isToday ? ' today' : '') + (beauty ? ' beauty-day' : '');
    col_el.onclick = () => { switchView('today', null); selectedDOW = i; selectedDateKey = dkey; renderDaySelector(); renderChecklist(); document.querySelectorAll('.day-btn')[i].click(); };

    const pct = total > 0 ? Math.round((done/total)*100) : 0;
    col_el.innerHTML = `
      <div class="wc-dow">${DOW[i]}</div>
      <div class="wc-date" style="color:${beauty?'#FD79A8':isToday?'#A29BFE':col.accent}">${d.getDate()}</div>
      <div class="wc-label">${beauty?'⭐ Beauty':DAY_LABELS[i].split(' ')[0]}</div>
      <div class="wc-dots">
        <div class="wc-dot" style="background:${pct>0?col.accent:'#EEE9FF'};width:${Math.max(6,pct/100*40)}px;border-radius:3px;height:5px;"></div>
      </div>
      <div style="font-size:10px;color:${pct===100?'#1DD1A1':'#B2BEC3'};margin-top:3px;font-weight:600;">${done}/${total}</div>
    `;
    strip.appendChild(col_el);
  }

  // Detail for today
  const det = document.getElementById('weekDetail');
  det.innerHTML = '';
  const routine = getRoutine(todayDOW, isBeautyDay(now));
  const stored = STORE.get(todayKey());
  const col = DAY_COLORS[todayDOW];

  const card = document.createElement('div');
  card.className = 'checklist-card';
  card.innerHTML = `<div class="checklist-card-hdr"><span class="card-emoji">📌</span><span class="card-title" style="background:${col.gradient};-webkit-background-clip:text;-webkit-text-fill-color:transparent;">วันนี้ — ${DAY_LABELS[todayDOW]}</span></div>`;

  if (!routine.beauty) {
    routine.items.forEach((item, idx) => {
      const isDone = !!stored[idx];
      const row = document.createElement('div');
      row.className = 'task-item' + (isDone ? ' done' : '');
      row.innerHTML = `<div class="task-check" style="${isDone?`background:${col.gradient}`:''}">${isDone?'✓':''}</div><span class="task-time">${item.time}</span><span class="task-text">${item.text}</span>`;
      row.onclick = () => { toggleTask(todayKey(), idx, row, routine.items.length, col); };
      card.appendChild(row);
    });
  }
  det.appendChild(card);
}

// ================================================================
// HABITS
// ================================================================
const HABITS = [
  {emoji:'🏋️', label:'ออกกำลังกาย', color:'#1DD1A1'},
  {emoji:'📖', label:'เรียนภาษา', color:'#00CEC9'},
  {emoji:'📚', label:'อ่านหนังสือ', color:'#A29BFE'},
  {emoji:'🎬', label:'โพสต์ Content', color:'#FF9F43'},
  {emoji:'💉', label:'สักคิ้ว/งาน', color:'#FF6B6B'},
  {emoji:'😴', label:'นอนก่อน 23:30', color:'#FD79A8'},
];

function renderHabits() {
  const grid = document.getElementById('habitGrid');
  grid.innerHTML = '';
  const stored = STORE.get('habits_week') || {};

  // Header row
  const hdr = document.createElement('div');
  hdr.className = 'habit-row';
  hdr.innerHTML = '<div></div>' + DOW.map(d => `<div class="habit-day-hdr">${d}</div>`).join('');
  grid.appendChild(hdr);

  HABITS.forEach((habit, hi) => {
    const row = document.createElement('div');
    row.className = 'habit-row';
    const lbl = document.createElement('div');
    lbl.className = 'habit-label';
    lbl.innerHTML = `<span style="margin-right:6px;">${habit.emoji}</span>${habit.label}`;
    row.appendChild(lbl);

    for (let di = 0; di < 7; di++) {
      const key = `${hi}_${di}`;
      const done = stored[key];
      const dot = document.createElement('div');
      dot.className = 'habit-dot' + (done ? ' done' : '');
      dot.style.background = done ? habit.color : '';
      dot.style.borderColor = done ? habit.color : '';
      dot.textContent = done ? '✓' : '';
      dot.style.color = 'white';
      dot.onclick = () => {
        const s = STORE.get('habits_week') || {};
        s[key] = !s[key];
        STORE.set('habits_week', s);
        dot.classList.toggle('done');
        dot.style.background = s[key] ? habit.color : '';
        dot.style.borderColor = s[key] ? habit.color : '';
        dot.textContent = s[key] ? '✓' : '';
      };
      row.appendChild(dot);
    }
    grid.appendChild(row);
  });
}

function resetHabits() {
  if (confirm('Reset Habit Tracker สำหรับสัปดาห์ใหม่?')) {
    STORE.set('habits_week', {});
    renderHabits();
  }
}

// ================================================================
// GOALS
// ================================================================
const GOALS = [
  {emoji:'💉', title:'BABEBROW STUDIO', text:'ลูกค้าใหม่ 20 คน\nIG Followers +500\nLive 2x/สัปดาห์', bg:'#FFE8E8', accent:'#FF6B6B'},
  {emoji:'🎬', title:'CONTENT CREATOR', text:'คลิปลงทุกวัน (30+ คลิป)\nเริ่ม channel ใหม่', bg:'#FFF3E0', accent:'#FF9F43'},
  {emoji:'🕶️', title:'GALES HAUS', text:'ยอดขายเพิ่มขึ้น\nPost 3x/สัปดาห์\nAds ROI เป็นบวก', bg:'#E0FAFA', accent:'#00CEC9'},
  {emoji:'🏠', title:'อสังหา', text:'ออกดูทรัพย์ 4 ครั้ง\nลูกค้าใหม่ 2 คน\nอัพเพจสม่ำเสมอ', bg:'#F0EFFE', accent:'#A29BFE'},
  {emoji:'📖', title:'ภาษา', text:'เรียน 12 ครั้ง/เดือน\nอังกฤษ + จีน\n3 ครั้ง/สัปดาห์', bg:'#E0FBF4', accent:'#1DD1A1'},
  {emoji:'💪', title:'สุขภาพ', text:'ออกกำลัง 4–5x/สัปดาห์\nนอน 7–8 ชม.\nBeauty Day 2x/เดือน', bg:'#FEE8F1', accent:'#FD79A8'},
];

function renderGoals() {
  const grid = document.getElementById('goalsGrid');
  grid.innerHTML = '';
  GOALS.forEach(g => {
    const card = document.createElement('div');
    card.className = 'goal-card';
    card.style.background = g.bg;
    card.style.borderColor = g.accent + '40';
    card.innerHTML = `
      <span class="goal-emoji">${g.emoji}</span>
      <div class="goal-title" style="color:${g.accent};">${g.title}</div>
      <div class="goal-text">${g.text.replace(/\n/g,'<br>')}</div>
    `;
    grid.appendChild(card);
  });
}

// ================================================================
// INIT & NAV
// ================================================================
function switchView(name, tabEl) {
  document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
  document.getElementById('view-' + name).classList.add('active');
  if (tabEl) {
    document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
    tabEl.classList.add('active');
  }
  if (name === 'weekly') renderWeekly();
  if (name === 'habits') renderHabits();
  if (name === 'goals') renderGoals();
}

function updateDateBadge() {
  const days = ['อาทิตย์','จันทร์','อังคาร','พุธ','พฤหัส','ศุกร์','เสาร์'];
  const months = ['ม.ค.','ก.พ.','มี.ค.','เม.ย.','พ.ค.','มิ.ย.','ก.ค.','ส.ค.','ก.ย.','ต.ค.','พ.ย.','ธ.ค.'];
  const d = new Date();
  document.getElementById('todayBadge').textContent =
    `วัน${days[d.getDay()]} ${d.getDate()} ${months[d.getMonth()]} ${d.getFullYear()+543}`;
}

updateDateBadge();
renderDaySelector();
renderChecklist();
</script>
</body>
</html>
