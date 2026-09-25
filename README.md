<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sorpresas & Detalles Escolares 🎁✨</title>
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=Plus+Jakarta+Sans:wght@400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              50: '#f5f3ff',
              100: '#ede9fe',
              200: '#ddd6fe',
              300: '#c4b5fd',
              400: '#a78bfa',
              500: '#8b5cf6',
              600: '#7c3aed',
              700: '#6d28d9',
              800: '#5b21b6',
              900: '#4c1d95',
            },
            accent: {
              400: '#facc15',
              500: '#eab308',
              600: '#ca8a04',
            },
            roseaccent: {
              400: '#f43f5e',
              500: '#e11d48',
            }
          },
          fontFamily: {
            title: ['Outfit', 'sans-serif'],
            sans: ['Plus Jakarta Sans', 'sans-serif'],
          }
        }
      }
    }
  </script>

  <style>
    body {
      background: linear-gradient(135deg, #2e1065 0%, #4c1d95 40%, #7c3aed 100%);
      min-height: 100vh;
      font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Confetti Particle effect */
    .bg-particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }

    .particle {
      position: absolute;
      list-style: none;
      display: block;
      border-radius: 4px;
      bottom: -100px;
      animation: floatUp 20s linear infinite;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) rotate(0deg);
        opacity: 0.9;
      }
      100% {
        transform: translateY(-1100px) rotate(720deg);
        opacity: 0;
      }
    }

    .calendar-day-btn {
      transition: all 0.2s ease;
    }

    .calendar-day-btn:hover:not(:disabled) {
      transform: scale(1.08);
    }

    .combo-card {
      transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .combo-card:hover {
      transform: translateY(-3px);
    }

    .combo-card.selected {
      border-color: #8b5cf6;
      background-color: #f5f3ff;
      box-shadow: 0 10px 25px -5px rgba(139, 92, 246, 0.25);
    }

    /* Custom scrollbar for modern feel */
    ::-webkit-scrollbar {
      width: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #f1f1f1;
    }
    ::-webkit-scrollbar-thumb {
      background: #c4b5fd;
      border-radius: 4px;
    }
  </style>
</head>
<body class="text-slate-800 relative flex items-center justify-center p-3 sm:p-6 min-h-screen">

  <ul class="bg-particles" id="bgParticles"></ul>

  <div class="relative z-10 w-full max-w-2xl bg-white/95 backdrop-blur-md rounded-3xl shadow-2xl border border-white/50 p-5 sm:p-9 my-6">
    
    <!-- Header Banner -->
    <div class="text-center mb-8 relative">
      <div class="inline-flex items-center justify-center bg-gradient-to-r from-brand-600 to-brand-500 text-white w-16 h-16 rounded-2xl shadow-lg mb-3 transform -rotate-3 hover:rotate-0 transition-transform">
        <span class="text-3xl">🎁</span>
      </div>
      <h1 class="font-title text-3xl sm:text-4xl font-extrabold text-brand-900 tracking-tight">
        Sorpresas & Detalles Escolares
      </h1>
      <p class="text-xs sm:text-sm font-medium text-brand-600 mt-1 max-w-md mx-auto">
        ¡Hazle el día a un amigo, compañero o alguien especial con un detalle inolvidable en su descanso! ✨🎉
      </p>
    </div>

    <!-- Info Box -->
    <div class="bg-brand-50 border-l-4 border-brand-500 rounded-r-2xl p-4 mb-7 text-xs sm:text-sm text-brand-900 shadow-inner">
      <div class="flex items-center space-x-2 font-bold text-brand-700 mb-1">
        <i class="fa-solid fa-sparkles text-accent-500 text-base"></i>
        <span>¿Cómo funciona la sorpresa?</span>
      </div>
      <p class="leading-relaxed text-slate-600">
        Elige tu combo favorito, dinos a quién quieres sorprender y selecciona la fecha y el descanso exacto. ¡Nosotros nos encargamos de llevar el mensaje, dulce o serenata hasta su salón o lugar del colegio!
      </p>
    </div>

    <!-- FORMULARIO PRINCIPAL -->
    <form id="surpriseForm" action="https://formsubmit.co/lorenzolozanoserrano@gmail.com" method="POST" class="space-y-6">
      
      <!-- Campos de Configuración FormSubmit -->
      <input type="hidden" name="_subject" value="🎁 ¡Nueva Reserva de Sorpresa / Serenata!">
      <input type="hidden" name="_captcha" value="false">
      <input type="hidden" id="hiddenCombo" name="Combo Seleccionado" required>
      <input type="hidden" id="hiddenFecha" name="Fecha Seleccionada" required>
      <input type="hidden" id="hiddenTurno" name="Turno del Descanso" required>
      <input type="hidden" id="hiddenEsAnonimo" name="¿Es Anónimo?" value="No">

      <!-- 1. SELECCIÓN DE COMBOS / SERVICIOS -->
      <div>
        <label class="block text-xs font-bold uppercase tracking-wider text-brand-900 mb-2 flex items-center">
          <i class="fa-solid fa-gift text-brand-500 mr-2 text-sm"></i> 1. Elige tu Combo o Sorpresa:
        </label>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3" id="combosGrid">
          
          <div class="combo-card border-2 border-slate-200 hover:border-brand-300 rounded-2xl p-3.5 cursor-pointer bg-white" data-combo="Mensaje personalizado">
            <div class="flex items-center space-x-3">
              <span class="text-2xl p-2 bg-purple-100 rounded-xl">💌</span>
              <div>
                <h4 class="font-bold text-sm text-slate-800">Mensaje Personalizado</h4>
                <p class="text-[11px] text-slate-500 leading-tight">Nota o carta especial escrita con cariño.</p>
              </div>
            </div>
          </div>

          <div class="combo-card border-2 border-slate-200 hover:border-brand-300 rounded-2xl p-3.5 cursor-pointer bg-white" data-combo="Mensaje + Dulce">
            <div class="flex items-center space-x-3">
              <span class="text-2xl p-2 bg-pink-100 rounded-xl">🍬</span>
              <div>
                <h4 class="font-bold text-sm text-slate-800">Mensaje + Dulce</h4>
                <p class="text-[11px] text-slate-500 leading-tight">Carta más un delicioso detalle dulce.</p>
              </div>
            </div>
          </div>

          <div class="combo-card border-2 border-slate-200 hover:border-brand-300 rounded-2xl p-3.5 cursor-pointer bg-white" data-combo="Serenata">
            <div class="flex items-center space-x-3">
              <span class="text-2xl p-2 bg-amber-100 rounded-xl">🎶</span>
              <div>
                <h4 class="font-bold text-sm text-slate-800">Serenata</h4>
                <p class="text-[11px] text-slate-500 leading-tight">Música en vivo o canción dedicada.</p>
              </div>
            </div>
          </div>

          <div class="combo-card border-2 border-slate-200 hover:border-brand-300 rounded-2xl p-3.5 cursor-pointer bg-white" data-combo="Mensaje + Serenata">
            <div class="flex items-center space-x-3">
              <span class="text-2xl p-2 bg-indigo-100 rounded-xl">🎼</span>
              <div>
                <h4 class="font-bold text-sm text-slate-800">Mensaje + Serenata</h4>
                <p class="text-[11px] text-slate-500 leading-tight">Música con lectura de mensaje especial.</p>
              </div>
            </div>
          </div>

          <div class="combo-card border-2 border-slate-200 hover:border-brand-300 rounded-2xl p-3.5 cursor-pointer bg-white sm:col-span-2" data-combo="Combo Especial: Regalo + Serenata">
            <div class="flex items-center space-x-3">
              <span class="text-2xl p-2 bg-rose-100 rounded-xl">🎁</span>
              <div>
                <h4 class="font-bold text-sm text-slate-800">Combo Especial: Regalo + Serenata</h4>
                <p class="text-[11px] text-slate-500 leading-tight">La experiencia completa: Regalo físico, serenata en vivo y tarjeta.</p>
              </div>
            </div>
          </div>

        </div>
      </div>

      <!-- 2. DATOS DE REMITENTE Y DESTINATARIO -->
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
        
        <div>
          <div class="flex items-center justify-between mb-1">
            <label for="remitente" class="text-xs font-bold uppercase tracking-wider text-brand-900">
              <i class="fa-solid fa-user-tag text-brand-500 mr-1"></i> Remitente (De:):
            </label>
            
            <!-- Anonymous Toggle Switch -->
            <label class="flex items-center cursor-pointer text-[11px] text-slate-600 font-semibold select-none">
              <input type="checkbox" id="anonimoToggle" class="sr-only peer">
              <div class="w-7 h-4 bg-slate-300 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-slate-300 after:border after:rounded-full after:h-3 after:w-3 after:transition-all peer-checked:bg-brand-600 relative"></div>
              <span class="ml-1.5">🕵️‍♂️ Anónimo</span>
            </label>
          </div>
          <input type="text" id="remitente" name="De (Remitente)" placeholder="Ej. Carlos Mendoza" required
            class="w-full px-4 py-2.5 rounded-xl border-2 border-slate-200 focus:border-brand-500 focus:outline-none transition-colors text-sm shadow-sm bg-slate-50/50">
        </div>

        <div>
          <label for="destinatario" class="block text-xs font-bold uppercase tracking-wider text-brand-900 mb-1">
            <i class="fa-solid fa-heart text-roseaccent-500 mr-1"></i> Destinatario (Para:):
          </label>
          <input type="text" id="destinatario" name="Para (Destinatario)" placeholder="Ej. Laura Gómez" required
            class="w-full px-4 py-2.5 rounded-xl border-2 border-slate-200 focus:border-brand-500 focus:outline-none transition-colors text-sm shadow-sm bg-slate-50/50">
        </div>

        <div class="sm:col-span-2">
          <label for="curso" class="block text-xs font-bold uppercase tracking-wider text-brand-900 mb-1">
            <i class="fa-solid fa-graduation-cap text-brand-500 mr-1"></i> Curso / Salón del Destinatario:
          </label>
          <input type="text" id="curso" name="Curso / Salón" placeholder="Ej. Grado 11-B (Edificio Principal, 2do piso)" required
            class="w-full px-4 py-2.5 rounded-xl border-2 border-slate-200 focus:border-brand-500 focus:outline-none transition-colors text-sm shadow-sm bg-slate-50/50">
        </div>

      </div>

      <!-- 3. CALENDARIO INTERACTIVO -->
      <div class="bg-gradient-to-br from-brand-50/80 to-white rounded-2xl border-2 border-brand-100 p-4 shadow-sm">
        <div class="flex items-center justify-between mb-3">
          <span class="text-xs font-bold uppercase tracking-wider text-brand-900 flex items-center">
            <i class="fa-solid fa-calendar-days text-brand-500 mr-2 text-sm"></i> 2. Elige el día del detalle:
          </span>
          <div class="flex items-center space-x-2">
            <button type="button" id="prevMonthBtn" class="w-7 h-7 rounded-full bg-brand-100 hover:bg-brand-200 text-brand-800 flex items-center justify-center text-xs font-bold transition">
              <i class="fa-solid fa-chevron-left"></i>
            </button>
            <span id="currentMonthYear" class="text-xs font-bold text-brand-800 min-w-[100px] text-center"></span>
            <button type="button" id="nextMonthBtn" class="w-7 h-7 rounded-full bg-brand-100 hover:bg-brand-200 text-brand-800 flex items-center justify-center text-xs font-bold transition">
              <i class="fa-solid fa-chevron-right"></i>
            </button>
          </div>
        </div>

        <div class="grid grid-cols-7 gap-1 text-center text-[11px] font-bold text-brand-400 mb-1">
          <div>Lun</div><div>Mar</div><div>Mié</div><div>Jue</div><div>Vie</div><div>Sáb</div><div>Dom</div>
        </div>
        <div id="calendarDaysGrid" class="grid grid-cols-7 gap-1.5"></div>
        <p id="selectedDateDisplay" class="text-center text-xs font-semibold text-brand-600 mt-2.5 italic">Por favor haz clic en un día del calendario.</p>
      </div>

      <!-- 4. TURNOS DISPONIBLES POR DESCANSO -->
      <div id="slotsSection" class="bg-gradient-to-br from-brand-50/80 to-white rounded-2xl border-2 border-brand-100 p-4 shadow-sm opacity-50 pointer-events-none transition-all">
        <label class="block text-xs font-bold uppercase tracking-wider text-brand-900 mb-3 flex items-center">
          <i class="fa-solid fa-clock text-brand-500 mr-2 text-sm"></i> 3. Elige el turno disponible (10 min):
        </label>

        <!-- Primer Descanso -->
        <div class="mb-4">
          <span class="inline-block text-[11px] font-bold text-brand-800 bg-brand-100 px-3 py-1 rounded-full mb-2">
            <i class="fa-solid fa-sun text-accent-500 mr-1"></i> Primer Descanso (10:50 AM - 11:20 AM)
          </span>
          <div class="grid grid-cols-1 sm:grid-cols-3 gap-2" id="firstBreakSlots"></div>
        </div>

        <!-- Segundo Descanso -->
        <div>
          <span class="inline-block text-[11px] font-bold text-brand-800 bg-brand-100 px-3 py-1 rounded-full mb-2">
            <i class="fa-solid fa-cloud-sun text-amber-500 mr-1"></i> Segundo Descanso (2:00 PM - 2:35 PM)
          </span>
          <div class="grid grid-cols-2 sm:grid-cols-4 gap-2" id="secondBreakSlots"></div>
        </div>
      </div>

      <!-- 5. MENSAJE PERSONALIZADO O CANCIÓN -->
      <div>
        <label for="cancion" class="block text-xs font-bold uppercase tracking-wider text-brand-900 mb-1">
          <i class="fa-solid fa-comment-dots text-brand-500 mr-1"></i> Mensaje Dedicado o Canción para Serenata:
        </label>
        <textarea id="cancion" name="Mensaje o Canción" rows="3" placeholder="Escribe aquí el mensaje especial que quieres que le leamos o la canción que deseas dedicar..."
          class="w-full px-4 py-2.5 rounded-xl border-2 border-slate-200 focus:border-brand-500 focus:outline-none transition-colors text-sm shadow-sm bg-slate-50/50 resize-none"></textarea>
      </div>

      <!-- BOTÓN PRINCIPAL DE SUBMIT -->
      <button type="submit" id="submitBtn" disabled
        class="w-full bg-gradient-to-r from-brand-600 to-brand-500 hover:from-brand-500 hover:to-brand-400 disabled:from-slate-300 disabled:to-slate-300 disabled:cursor-not-allowed text-white font-bold py-4 px-6 rounded-2xl shadow-lg hover:shadow-xl transition-all transform hover:-translate-y-0.5 active:translate-y-0 flex items-center justify-center space-x-2 text-base">
        <i class="fa-solid fa-paper-plane"></i>
        <span>Agendar Sorpresa (Enviar Solicitud)</span>
      </button>

    </form>

    <!-- Modal de Éxito / Confirmación -->
    <div id="successModal" class="hidden fixed inset-0 bg-black/60 backdrop-blur-sm z-50 flex items-center justify-center p-4">
      <div class="bg-white rounded-3xl p-6 max-w-sm w-full text-center shadow-2xl border-4 border-brand-400 space-y-4">
        <div class="text-5xl">🎉</div>
        <h3 class="text-2xl font-title text-brand-900 font-bold">¡Reserva Registrada!</h3>
        <p class="text-xs text-slate-600 leading-relaxed">
          Tu turno ha sido <strong class="text-brand-700">bloqueado y guardado</strong>. Ahora serás redirigido para enviar los datos directamente al correo <span class="font-bold text-brand-600">lorenzolozanoserrano@gmail.com</span>.
        </p>
        <button id="modalConfirmBtn" type="button" class="w-full py-3 bg-brand-600 text-white font-bold rounded-xl text-sm shadow-lg hover:bg-brand-500 transition">
          Confirmar y Finalizar
        </button>
      </div>
    </div>

    <!-- Footer -->
    <footer class="mt-8 text-center text-xs text-slate-400 font-medium border-t border-slate-100 pt-4">
      <p>Organizado con ✨ y ❤️ para la comunidad escolar</p>
    </footer>

  </div>

  <!-- JAVASCRIPT LOGIC -->
  <script>
    // --- Confetti Particles ---
    const bgParticles = document.getElementById('bgParticles');
    const colors = ['#8b5cf6', '#a78bfa', '#facc15', '#f43f5e', '#38bdf8'];
    for (let i = 0; i < 15; i++) {
      const li = document.createElement('li');
      li.className = 'particle';
      li.style.left = `${Math.random() * 100}%`;
      li.style.width = `${10 + Math.random() * 15}px`;
      li.style.height = li.style.width;
      li.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
      li.style.animationDelay = `${Math.random() * 10}s`;
      li.style.animationDuration = `${12 + Math.random() * 15}s`;
      bgParticles.appendChild(li);
    }

    // --- Definition of Slots ---
    const FIRST_BREAK_SLOTS = [
      "10:50 AM - 11:00 AM",
      "11:00 AM - 11:10 AM",
      "11:10 AM - 11:20 AM"
    ];

    const SECOND_BREAK_SLOTS = [
      "2:00 PM - 2:10 PM",
      "2:10 PM - 2:20 PM",
      "2:20 PM - 2:30 PM",
      "2:30 PM - 2:35 PM"
    ];

    // --- State Variables ---
    let currentDate = new Date();
    let selectedCombo = "";
    let selectedDateStr = "";
    let selectedSlot = "";

    // --- LocalStorage Slot Lock Manager ---
    const STORAGE_KEY = 'surprise_booked_slots';

    function getBookedSlots() {
      const data = localStorage.getItem(STORAGE_KEY);
      return data ? JSON.parse(data) : {};
    }

    function saveBookedSlot(dateStr, slotStr) {
      const booked = getBookedSlots();
      if (!booked[dateStr]) {
        booked[dateStr] = [];
      }
      if (!booked[dateStr].includes(slotStr)) {
        booked[dateStr].push(slotStr);
      }
      localStorage.setItem(STORAGE_KEY, JSON.stringify(booked));
    }

    // --- Combo Selection Handling ---
    const comboCards = document.querySelectorAll('.combo-card');
    comboCards.forEach(card => {
      card.addEventListener('click', () => {
        comboCards.forEach(c => c.classList.remove('selected'));
        card.classList.add('selected');
        selectedCombo = card.getAttribute('data-combo');
        document.getElementById('hiddenCombo').value = selectedCombo;
        validateForm();
      });
    });

    // --- Anonymous Toggle ---
    const anonimoToggle = document.getElementById('anonimoToggle');
    const remitenteInput = document.getElementById('remitente');
    const hiddenEsAnonimo = document.getElementById('hiddenEsAnonimo');

    anonimoToggle.addEventListener('change', function() {
      if (this.checked) {
        remitenteInput.value = "Anónimo / Secreto";
        remitenteInput.disabled = true;
        hiddenEsAnonimo.value = "Sí";
      } else {
        remitenteInput.value = "";
        remitenteInput.disabled = false;
        hiddenEsAnonimo.value = "No";
      }
      validateForm();
    });

    // --- Calendar Rendering ---
    const monthNames = ["Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio", "Julio", "Agosto", "Septiembre", "Octubre", "Noviembre", "Diciembre"];

    function renderCalendar() {
      const year = currentDate.getFullYear();
      const month = currentDate.getMonth();

      document.getElementById('currentMonthYear').textContent = `${monthNames[month]} ${year}`;

      const grid = document.getElementById('calendarDaysGrid');
      grid.innerHTML = "";

      const firstDayOfMonth = new Date(year, month, 1);
      const daysInMonth = new Date(year, month + 1, 0).getDate();

      let startingDay = firstDayOfMonth.getDay() - 1;
      if (startingDay === -1) startingDay = 6;

      const today = new Date();
      today.setHours(0, 0, 0, 0);

      for (let i = 0; i < startingDay; i++) {
        const blank = document.createElement('div');
        grid.appendChild(blank);
      }

      for (let day = 1; day <= daysInMonth; day++) {
        const dateObj = new Date(year, month, day);
        dateObj.setHours(0, 0, 0, 0);

        const dateStr = `${year}-${String(month + 1).padStart(2, '0')}-${String(day).padStart(2, '0')}`;

        const btn = document.createElement('button');
        btn.type = "button";
        btn.className = "calendar-day-btn h-9 rounded-xl text-xs font-semibold flex items-center justify-center border";

        const isPast = dateObj < today;
        const isSelected = selectedDateStr === dateStr;
        const isToday = dateObj.getTime() === today.getTime();

        if (isPast) {
          btn.className += " bg-slate-100 text-slate-300 cursor-not-allowed border-transparent";
          btn.disabled = true;
        } else if (isSelected) {
          btn.className += " bg-brand-600 text-white font-bold border-brand-700 shadow-md transform scale-105";
        } else if (isToday) {
          btn.className += " bg-brand-100 text-brand-800 border-brand-300 font-bold";
        } else {
          btn.className += " bg-white text-slate-700 border-slate-200 hover:bg-brand-50 hover:border-brand-300";
        }

        btn.textContent = day;

        btn.addEventListener('click', () => {
          selectedDateStr = dateStr;
          selectedSlot = "";
          document.getElementById('hiddenFecha').value = selectedDateStr;
          
          const formatOptions = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
          const formattedDate = new Date(year, month, day).toLocaleDateString('es-ES', formatOptions);
          document.getElementById('selectedDateDisplay').innerHTML = `📅 Día elegido: <strong class="text-brand-700">${formattedDate}</strong>`;

          renderCalendar();
          renderSlots();
          validateForm();
        });

        grid.appendChild(btn);
      }
    }

    // --- Render Time Slots & Check Lock ---
    function renderSlots() {
      const slotsSection = document.getElementById('slotsSection');
      if (!selectedDateStr) {
        slotsSection.classList.add('opacity-50', 'pointer-events-none');
        return;
      }

      slotsSection.classList.remove('opacity-50', 'pointer-events-none');
      const bookedSlots = getBookedSlots()[selectedDateStr] || [];

      renderSlotGroup('firstBreakSlots', FIRST_BREAK_SLOTS, bookedSlots);
      renderSlotGroup('secondBreakSlots', SECOND_BREAK_SLOTS, bookedSlots);
    }

    function renderSlotGroup(containerId, slotsArray, bookedSlots) {
      const container = document.getElementById(containerId);
      container.innerHTML = "";

      slotsArray.forEach(slot => {
        const isBooked = bookedSlots.includes(slot);
        const isSelected = selectedSlot === slot;

        const btn = document.createElement('button');
        btn.type = "button";
        btn.className = "w-full py-2 px-2 text-[11px] sm:text-xs font-semibold rounded-xl border transition flex flex-col items-center justify-center space-y-0.5";

        if (isBooked) {
          btn.className += " bg-slate-100 text-slate-400 border-slate-200 cursor-not-allowed line-through";
          btn.innerHTML = `<span>${slot}</span> <span class="text-[9px] font-bold text-rose-500 no-underline">❌ OCUPADO</span>`;
          btn.disabled = true;
        } else if (isSelected) {
          btn.className += " bg-brand-600 text-white border-brand-700 font-bold shadow-md transform scale-102";
          btn.innerHTML = `<span>${slot}</span> <span class="text-[9px] font-normal text-brand-100">✓ Elegido</span>`;
        } else {
          btn.className += " bg-white text-slate-700 border-slate-200 hover:bg-brand-50 hover:border-brand-300";
          btn.innerHTML = `<span>${slot}</span> <span class="text-[9px] font-normal text-emerald-600">Disponible</span>`;
        }

        btn.addEventListener('click', () => {
          selectedSlot = slot;
          document.getElementById('hiddenTurno').value = selectedSlot;
          renderSlots();
          validateForm();
        });

        container.appendChild(btn);
      });
    }

    // --- Form Validation ---
    function validateForm() {
      const remitente = document.getElementById('remitente').value.trim();
      const destinatario = document.getElementById('destinatario').value.trim();
      const curso = document.getElementById('curso').value.trim();
      const submitBtn = document.getElementById('submitBtn');

      if (selectedCombo && remitente && destinatario && curso && selectedDateStr && selectedSlot) {
        submitBtn.disabled = false;
      } else {
        submitBtn.disabled = true;
      }
    }

    document.getElementById('remitente').addEventListener('input', validateForm);
    document.getElementById('destinatario').addEventListener('input', validateForm);
    document.getElementById('curso').addEventListener('input', validateForm);

    // --- Month Navigation ---
    document.getElementById('prevMonthBtn').addEventListener('click', () => {
      currentDate.setMonth(currentDate.getMonth() - 1);
      renderCalendar();
    });

    document.getElementById('nextMonthBtn').addEventListener('click', () => {
      currentDate.setMonth(currentDate.getMonth() + 1);
      renderCalendar();
    });

    // --- Form Submit and Slot Lock Flow ---
    const form = document.getElementById('surpriseForm');
    const successModal = document.getElementById('successModal');

    form.addEventListener('submit', function(e) {
      e.preventDefault();

      if (!selectedDateStr || !selectedSlot) return;

      // Lock slot in LocalStorage
      saveBookedSlot(selectedDateStr, selectedSlot);

      // Show confirmation modal
      successModal.classList.remove('hidden');
    });

    document.getElementById('modalConfirmBtn').addEventListener('click', () => {
      // Re-enable disabled input for FormSubmit if anonymous
      if (remitenteInput.disabled) {
        remitenteInput.disabled = false;
      }
      form.submit();
    });

    // Initial Execution
    renderCalendar();
  </script>

</body>
</html>
    
