<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Aplikasi Peminjaman Ruangan</title>
  <style>
    :root{font-family:system-ui,-apple-system,Segoe UI,Roboto,'Helvetica Neue',Arial;}
    body{max-width:1100px;margin:24px auto;padding:16px;line-height:1.45}
    h1{font-size:1.6rem;margin-bottom:6px}
    .grid{display:grid;grid-template-columns:1fr 380px;gap:18px}
    .card{background:#fff;border:1px solid #e6e6e6;border-radius:8px;padding:12px;box-shadow:0 3px 8px rgba(0,0,0,0.03)}
    label{display:block;margin-top:8px;font-size:0.9rem}
    input,select,button,textarea{width:100%;padding:8px;border:1px solid #cfcfcf;border-radius:6px;margin-top:6px}
    button{cursor:pointer}
    .room-list{display:flex;flex-direction:column;gap:10px}
    .room{display:flex;align-items:center;justify-content:space-between;padding:10px;border-radius:8px}
    .room.available{background:#f6ffef;border:1px solid #bfeeb0}
    .room.booked{background:#fff6f6;border:1px solid #ffc6c6}
    .status{font-weight:600}
    .small{font-size:0.9rem;color:#555}
    .booking-row{display:flex;gap:8px;align-items:center}
    .bookings-list{max-height:300px;overflow:auto;margin-top:8px}
    .booking-item{border-bottom:1px dashed #e8e8e8;padding:8px 0}
    .muted{color:#666;font-size:0.9rem}
    .actions{display:flex;gap:8px}
    .hint{background:#f5f7ff;padding:10px;border-radius:6px;border:1px solid #e1e6ff;font-size:0.95rem}
    @media(max-width:900px){.grid{grid-template-columns:1fr}}
  </style>
</head>
<body>
  <h1>Aplikasi Peminjaman Ruangan</h1>
  <p class="muted">Pilih tanggal dan lihat status tiap ruangan. <strong>Sudah dibooking</strong> = ada peminjaman pada tanggal & waktu yang dipilih. <strong>Masih kosong</strong> = tidak ada peminjaman pada rentang waktu yang dipilih.</p>

  <div class="grid">
    <div class="card">
      <div style="display:flex;gap:10px;align-items:center;justify-content:space-between;margin-bottom:10px">
        <div>
          <label for="checkDate">Tanggal pemeriksaan</label>
          <input type="date" id="checkDate" />
        </div>
        <div style="width:160px">
          <label for="checkStart">Jam mulai</label>
          <input type="time" id="checkStart" value="08:00" />
        </div>
        <div style="width:160px">
          <label for="checkEnd">Jam selesai</label>
          <input type="time" id="checkEnd" value="10:00" />
        </div>
      </div>

      <div class="hint">Daftar ruangan</div>
      <div id="rooms" class="room-list" style="margin-top:10px"></div>

      <hr style="margin:14px 0" />
      <div>
        <h3 style="margin:0 0 8px 0">Daftar Booking (terakhir)</h3>
        <div id="bookings" class="bookings-list"></div>
      </div>
    </div>

    <div class="card">
      <h3>Form Peminjaman Ruangan</h3>
      <form id="bookingForm">
        <label for="roomSelect">Pilih Ruangan</label>
        <select id="roomSelect"></select>

        <label for="date">Tanggal</label>
        <input type="date" id="date" required />

        <div style="display:flex;gap:8px">
          <div style="flex:1">
            <label for="start">Jam Mulai</label>
            <input type="time" id="start" required />
          </div>
          <div style="flex:1">
            <label for="end">Jam Selesai</label>
            <input type="time" id="end" required />
          </div>
        </div>

        <label for="name">Nama Pemohon</label>
        <input type="text" id="name" placeholder="Nama lengkap" required />

        <label for="purpose">Keperluan</label>
        <textarea id="purpose" rows="3" placeholder="Contoh: Persekutuan doa, pertemuan lingkungan, dsb."></textarea>

        <div style="display:flex;gap:8px;margin-top:10px">
          <button type="submit">Booking</button>
          <button type="button" id="clearAll">Hapus Semua Booking (reset)</button>
        </div>
      </form>

      <hr style="margin:14px 0" />
      <div>
        <h4>Petunjuk singkat</h4>
        <ul>
          <li>Pilih ruang, tanggal, dan jam. Sistem akan memeriksa bentrok waktu.</li>
          <li>Booking disimpan di penyimpanan browser (localStorage) — hanya tersedia di perangkat ini.</li>
          <li>Untuk fitur penyimpanan terpusat/akun atau cetak laporan, minta penambahan fitur.</li>
        </ul>
      </div>
    </div>
  </div>

  <script>
    // Daftar ruangan
    const ROOMS = [
      'Gedung Gereja',
      'Aula St. Vincentius',
      'St. Louisa',
      'St. Katarina',
      'St. Yoh. Don Bosco (BIAK)',
      'St. Yohanes Paulus II',
      'St. Yohanes XXIII',
      'St. Caecilia'
    ];

    // localStorage key
    const STORAGE_KEY = 'peminjaman_ruangan_bookings_v1';

    // util: load bookings
    function loadBookings(){
      const raw = localStorage.getItem(STORAGE_KEY);
      try{ return raw? JSON.parse(raw) : []; } catch(e){ return []; }
    }
    function saveBookings(arr){ localStorage.setItem(STORAGE_KEY, JSON.stringify(arr)); }

    // util: time compare helpers (HH:MM)
    function timeToMinutes(t){ const [h,m]=t.split(':').map(Number); return h*60+m; }
    function rangesOverlap(aStart,aEnd,bStart,bEnd){ return Math.max(aStart,bStart) < Math.min(aEnd,bEnd); }

    // render room list for the selected check date/time
    function renderRoomList(){
      const date = document.getElementById('checkDate').value;
      const start = document.getElementById('checkStart').value;
      const end = document.getElementById('checkEnd').value;
      const container = document.getElementById('rooms');
      container.innerHTML = '';
      const bookings = loadBookings();

      ROOMS.forEach(room => {
        const div = document.createElement('div');
        const isBooked = (date && start && end) ? bookings.some(b => b.room===room && b.date===date && rangesOverlap(timeToMinutes(b.start), timeToMinutes(b.end), timeToMinutes(start), timeToMinutes(end))) : false;
        div.className = 'room ' + (isBooked ? 'booked' : 'available');
        div.innerHTML = `
          <div>
            <div style="font-weight:700">${room}</div>
            <div class="small">${isBooked ? 'Sudah dibooking pada rentang waktu ini' : 'Masih kosong pada rentang waktu ini'}</div>
          </div>
          <div style="text-align:right">
            <div class="status">${isBooked ? 'Sudah dibooking' : 'Masih kosong'}</div>
            <div class="small">Klik untuk melihat booking</div>
          </div>
        `;
        div.addEventListener('click', ()=>{ showBookingsForRoom(room); });
        container.appendChild(div);
      });
    }

    // render bookings list (all)
    function renderBookings(){
      const container = document.getElementById('bookings');
      const bookings = loadBookings().slice().sort((a,b)=> (a.date>b.date)?1:(a.date<b.date)?-1:(a.start>b.start)?1:-1 );
      container.innerHTML = '';
      if(bookings.length===0){ container.innerHTML = '<div class="muted">Belum ada booking.</div>'; return; }
      bookings.forEach((b,idx)=>{
        const div = document.createElement('div'); div.className='booking-item';
        div.innerHTML = `
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div>
              <div style="font-weight:700">${b.room}</div>
              <div class="small">${b.date} • ${b.start} - ${b.end}</div>
              <div class="small">Pemohon: ${b.name} — ${b.purpose || '-'} </div>
            </div>
            <div class="actions">
              <button data-idx="${idx}" class="cancelBtn">Batal</button>
            </div>
          </div>
        `;
        container.appendChild(div);
      });

      // add event listeners for cancel
      container.querySelectorAll('.cancelBtn').forEach(btn=>{
        btn.addEventListener('click', (e)=>{
          const i = Number(e.target.dataset.idx);
          const arr = loadBookings();
          const b = arr[i];
          if(!b) return alert('Booking tidak ditemukan.');
          if(!confirm(`Batalkan booking ${b.room} pada ${b.date} ${b.start}-${b.end}?`)) return;
          arr.splice(i,1);
          saveBookings(arr);
          renderBookings(); renderRoomList();
        });
      });
    }

    function showBookingsForRoom(room){
      const arr = loadBookings().filter(b=>b.room===room).sort((a,b)=> (a.date>b.date)?1:-1);
      const list = arr.map(b=>`${b.date} • ${b.start}-${b.end} — ${b.name} (${b.purpose||'-'})`).join('\n');
      alert((list||'Tidak ada booking untuk ruangan ini.') );
    }

    // init
    function init(){
      const roomSelect = document.getElementById('roomSelect');
      ROOMS.forEach(r=>{ const opt = document.createElement('option'); opt.value=r; opt.textContent=r; roomSelect.appendChild(opt); });

      // set default dates to today
      const today = new Date().toISOString().slice(0,10);
      document.getElementById('checkDate').value = today;
      document.getElementById('date').value = today;

      // listeners
      ['checkDate','checkStart','checkEnd'].forEach(id=>document.getElementById(id).addEventListener('change', renderRoomList));

      document.getElementById('bookingForm').addEventListener('submit', (e)=>{
        e.preventDefault();
        const room = document.getElementById('roomSelect').value;
        const date = document.getElementById('date').value;
        const start = document.getElementById('start').value;
        const end = document.getElementById('end').value;
        const name = document.getElementById('name').value.trim();
        const purpose = document.getElementById('purpose').value.trim();

        if(!date || !start || !end || !name){ return alert('Isi semua data yang wajib.'); }
        if(timeToMinutes(end) <= timeToMinutes(start)) return alert('Jam selesai harus lebih besar dari jam mulai.');

        const bookings = loadBookings();
        const conflict = bookings.find(b=> b.room===room && b.date===date && rangesOverlap(timeToMinutes(b.start), timeToMinutes(b.end), timeToMinutes(start), timeToMinutes(end)) );
        if(conflict) return alert(`Gagal booking — ruangan bentrok dengan booking lain: ${conflict.name}, ${conflict.start}-${conflict.end}`);

        bookings.push({room,date,start,end,name,purpose,createdAt:new Date().toISOString()});
        saveBookings(bookings);
        alert('Booking berhasil disimpan.');
        renderBookings(); renderRoomList();
        document.getElementById('bookingForm').reset();
        document.getElementById('date').value = date; // keep date
      });

      document.getElementById('clearAll').addEventListener('click', ()=>{
        if(confirm('Hapus semua booking dari localStorage? Tindakan ini tidak dapat dibatalkan.')){
          localStorage.removeItem(STORAGE_KEY);
          renderBookings(); renderRoomList();
        }
      });

      renderBookings(); renderRoomList();
    }

    document.addEventListener('DOMContentLoaded', init);
  </script>
</body>
</html>
