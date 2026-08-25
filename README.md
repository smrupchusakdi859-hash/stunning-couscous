<!DOCTYPE html><!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TJN NEXUS CORE - Command & Surveillance Dashboard</title>
    <!-- Tailwind CSS for modern responsive styling -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <!-- FontAwesome for System Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2/family=Inter:wght@300;400;600;700&family=JetBrains+Mono:wght@400;700&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #0b0f19; color: #f3f4f6; }
        .mono { font-family: 'JetBrains Mono', monospace; }
        .glow { box-shadow: 0 0 25px rgba(14, 165, 233, 0.25); }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between">

    <!-- HEADER / NAVIGATION -->
    <header class="bg-gray-900 border-b border-gray-800 px-6 py-4 flex justify-between items-center shadow-lg">
        <div class="flex items-center space-x-3">
            <div class="bg-sky-500 text-gray-950 p-2 rounded-lg font-bold text-xl flex items-center justify-center shadow-md">
                <i class="fa-solid fa-microchip"></i>
            </div>
            <div>
                <h1 class="text-lg font-bold tracking-wider text-sky-400">TJN NEXUS CORE <span class="text-xs bg-sky-900/50 text-sky-300 px-2 py-0.5 rounded border border-sky-700">v58.0.3</span></h1>
                <p class="text-xs text-gray-400">Command & Autonomous Surveillance System</p>
            </div>
        </div>
        <div class="flex items-center space-x-4">
            <div class="hidden md:flex flex-col text-right">
                <span class="text-xs text-gray-400">DESIGNATED COMMANDER</span>
                <span class="text-sm font-semibold text-emerald-400">Master 01 (ชูศักดิ์ สมรูป)</span>
            </div>
            <div class="flex items-center space-x-2 bg-emerald-950/60 border border-emerald-600/50 px-3 py-1.5 rounded-full">
                <span class="h-2.5 w-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
                <span class="text-xs font-medium text-emerald-300 mono">AUTOPILOT ACTIVE</span>
            </div>
        </div>
    </header>

    <!-- MAIN DASHBOARD CONTENT -->
    <main class="flex-grow container mx-auto px-6 py-8 grid grid-cols-1 lg:grid-cols-3 gap-6">
        
        <!-- COLUMN 1 & 2: SYSTEM METRICS & LOGS -->
        <div class="lg:col-span-2 space-y-6">
            
            <!-- STATUS CARDS -->
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                <div class="bg-gray-900/80 border border-gray-800 p-4 rounded-xl shadow">
                    <div class="flex justify-between items-center text-gray-400 mb-2">
                        <span class="text-xs font-semibold uppercase">Core Link</span>
                        <i class="fa-solid fa-network-wired text-sky-400"></i>
                    </div>
                    <div class="text-xl font-bold text-white mono">100% SYNED</div>
                    <p class="text-xs text-emerald-400 mt-1"><i class="fa-solid fa-arrow-up"></i> Zero Latency Loop</p>
                </div>

                <div class="bg-gray-900/80 border border-gray-800 p-4 rounded-xl shadow">
                    <div class="flex justify-between items-center text-gray-400 mb-2">
                        <span class="text-xs font-semibold uppercase">Watchdog Loop</span>
                        <i class="fa-solid fa-shield-halved text-emerald-400"></i>
                    </div>
                    <div class="text-xl font-bold text-white mono">HEALTHY</div>
                    <p class="text-xs text-sky-400 mt-1">Drift-Corrected Active</p>
                </div>

                <div class="bg-gray-900/80 border border-gray-800 p-4 rounded-xl shadow">
                    <div class="flex justify-between items-center text-gray-400 mb-2">
                        <span class="text-xs font-semibold uppercase">Security Vault</span>
                        <i class="fa-solid fa-lock text-amber-400"></i>
                    </div>
                    <div class="text-xl font-bold text-white mono">ARMED</div>
                    <p class="text-xs text-amber-400 mt-1">SHA-256 Protected</p>
                </div>
            </div>

            <!-- LIVE TELEMETRY LOG CONTAINER -->
            <div class="bg-gray-900/90 border border-gray-800 rounded-xl p-5 shadow-lg glow">
                <div class="flex justify-between items-center mb-4 border-b border-gray-800 pb-3">
                    <h2 class="text-sm font-bold uppercase tracking-wide text-gray-300 flex items-center space-x-2">
                        <i class="fa-solid fa-terminal text-sky-400"></i>
                        <span>Live Telemetry & Surveillance Log</span>
                    </h2>
                    <button onclick="clearLogs()" class="text-xs text-gray-400 hover:text-white bg-gray-800 px-2.5 py-1 rounded transition">Clear Feed</button>
                </div>
                <div id="log-container" class="mono text-xs bg-gray-950 p-4 rounded-lg h-64 overflow-y-auto space-y-2 border border-gray-800/80 text-gray-300">
                    <div>[<span class="text-sky-400">SYSTEM</span>] TJN NEXUS CORE initialized successfully.</div>
                    <div>[<span class="text-emerald-400">AUTOPILOT</span>] Background daemon running with drift-corrected timing.</div>
                    <div>[<span class="text-amber-400">SECURITY</span>] Vault integrity verified under Master 01 command.</div>
                </div>
            </div>
        </div>

        <!-- COLUMN 3: CONTROL PANEL & ACTIONS -->
        <div class="space-y-6">
            <div class="bg-gray-900/90 border border-gray-800 rounded-xl p-5 shadow-lg">
                <h2 class="text-sm font-bold uppercase tracking-wide text-gray-300 mb-4 flex items-center space-x-2 border-b border-gray-800 pb-3">
                    <i class="fa-solid fa-sliders text-emerald-400"></i>
                    <span>Master Command Panel</span>
                </h2>
                
                <div class="space-y-3">
                    <button onclick="triggerAction('Full System Integrity Audit')" class="w-full bg-sky-600 hover:bg-sky-500 text-white font-semibold py-2.5 px-4 rounded-lg text-sm transition flex items-center justify-center space-x-2 shadow">
                        <i class="fa-solid fa-stethoscope"></i>
                        <span>Run Full System Audit</span>
                    </button>
                    
                    <button onclick="triggerAction('Emergency Snapshot Secured')" class="w-full bg-amber-600 hover:bg-amber-500 text-white font-semibold py-2.5 px-4 rounded-lg text-sm transition flex items-center justify-center space-x-2 shadow">
                        <i class="fa-solid fa-vault"></i>
                        <span>Execute Emergency Snapshot</span>
                    </button>

                    <button onclick="triggerAction('ECU Rom & Checksum Verification')" class="w-full bg-indigo-600 hover:bg-indigo-500 text-white font-semibold py-2.5 px-4 rounded-lg text-sm transition flex items-center justify-center space-x-2 shadow">
                        <i class="fa-solid fa-car-rear"></i>
                        <span>Verify ECU & ROM Maps</span>
                    </button>
                </div>
            </div>

            <!-- SYSTEM METADATA -->
            <div class="bg-gray-900/60 border border-gray-800/80 rounded-xl p-4 text-xs text-gray-400 space-y-2">
                <div class="flex justify-between">
                    <span>Protocol Engine:</span>
                    <span class="text-white mono">Auto-Gemini v3</span>
                </div>
                <div class="flex justify-between">
                    <span>Active Interface:</span>
                    <span class="text-emerald-400 mono">Web Cloud Node</span>
                </div>
                <div class="flex justify-between">
                    <span>Authorization:</span>
                    <span class="text-amber-400 mono">SUPREME-01</span>
                </div>
            </div>
        </div>

    </main>

    <!-- FOOTER -->
    <footer class="bg-gray-900 border-t border-gray-800 text-center py-4 text-xs text-gray-500">
        <p>&copy; 2026 TJN NEXUS CORE &mdash; Managed & Controlled by Master 01 (ชูศักดิ์ สมรูป). All Rights Reserved.</p>
    </footer>

    <!-- INTERACTIVE DASHBOARD SCRIPT -->
    <script>
        function logMessage(level, message, colorClass) {
            const container = document.getElementById('log-container');
            const timeStr = new Date().toTimeString().split(' ')[0];
            const div = document.createElement('div');
            div.innerHTML = `[${timeStr}] [<span class="${colorClass}">${level}</span>] ${message}`;
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
        }

        function triggerAction(actionName) {
            logMessage('COMMAND', `Executing: ${actionName}...`, 'text-sky-400');
            setTimeout(() => {
                logMessage('SUCCESS', `${actionName} completed with 100% integrity.`, 'text-emerald-400');
            }, 800);
        }

        function clearLogs() {
            document.getElementById('log-container.').innerHTML = '';
            logMessage('SYSTEM', 'Log feed cleared by Master 01.', 'text-gray-400');
        }

        // Simulate periodic background autopilot heartbeat
        setInterval(() => {
            const events = [
                {lvl: 'AUTOPILOT', msg: 'Background health check cycle nominal.', col: 'text-emerald-400'},
                {lvl: 'TELEMETRY', msg: 'TCP & HTTP socket connections stable.', col: 'text-sky-400'},
                {lvl: 'SECURITY', msg: 'Perimeter defense protocol locked.', col: 'text-amber-400'}
            ];
            const ev = events[Math.floor(Math.random() * events.length)];
            logMessage(ev.lvl, ev.msg, ev.col);
        }, 12000);
    </script>
</body>
</html>

<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TJN NEXUS CORE - Command & Surveillance Dashboard</title>
    <!-- Tailwind CSS for modern responsive styling -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <!-- FontAwesome for System Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2/family=Inter:wght@300;400;600;700&family=JetBrains+Mono:wght@400;700&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #0b0f19; color: #f3f4f6; }
        .mono { font-family: 'JetBrains Mono', monospace; }
        .glow { box-shadow: 0 0 25px rgba(14, 165, 233, 0.25); }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between">

    <!-- HEADER / NAVIGATION -->
    <header class="bg-gray-900 border-b border-gray-800 px-6 py-4 flex justify-between items-center shadow-lg">
        <div class="flex items-center space-x-3">
            <div class="bg-sky-500 text-gray-950 p-2 rounded-lg font-bold text-xl flex items-center justify-center shadow-md">
                <i class="fa-solid fa-microchip"></i>
            </div>
            <div>
                <h1 class="text-lg font-bold tracking-wider text-sky-400">TJN NEXUS CORE <span class="text-xs bg-sky-900/50 text-sky-300 px-2 py-0.5 rounded border border-sky-700">v58.0.3</span></h1>
                <p class="text-xs text-gray-400">Command & Autonomous Surveillance System</p>
            </div>
        </div>
        <div class="flex items-center space-x-4">
            <div class="hidden md:flex flex-col text-right">
                <span class="text-xs text-gray-400">DESIGNATED COMMANDER</span>
                <span class="text-sm font-semibold text-emerald-400">Master 01 (ชูศักดิ์ สมรูป)</span>
            </div>
            <div class="flex items-center space-x-2 bg-emerald-950/60 border border-emerald-600/50 px-3 py-1.5 rounded-full">
                <span class="h-2.5 w-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
                <span class="text-xs font-medium text-emerald-300 mono">AUTOPILOT ACTIVE</span>
            </div>
        </div>
    </header>

    <!-- MAIN DASHBOARD CONTENT -->
    <main class="flex-grow container mx-auto px-6 py-8 grid grid-cols-1 lg:grid-cols-3 gap-6">
        
        <!-- COLUMN 1 & 2: SYSTEM METRICS & LOGS -->
        <div class="lg:col-span-2 space-y-6">
            
            <!-- STATUS CARDS -->
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                <div class="bg-gray-900/80 border border-gray-800 p-4 rounded-xl shadow">
                    <div class="flex justify-between items-center text-gray-400 mb-2">
                        <span class="text-xs font-semibold uppercase">Core Link</span>
                        <i class="fa-solid fa-network-wired text-sky-400"></i>
                    </div>
                    <div class="text-xl font-bold text-white mono">100% SYNED</div>
                    <p class="text-xs text-emerald-400 mt-1"><i class="fa-solid fa-arrow-up"></i> Zero Latency Loop</p>
                </div>

                <div class="bg-gray-900/80 border border-gray-800 p-4 rounded-xl shadow">
                    <div class="flex justify-between items-center text-gray-400 mb-2">
                        <span class="text-xs font-semibold uppercase">Watchdog Loop</span>
                        <i class="fa-solid fa-shield-halved text-emerald-400"></i>
                    </div>
                    <div class="text-xl font-bold text-white mono">HEALTHY</div>
                    <p class="text-xs text-sky-400 mt-1">Drift-Corrected Active</p>
                </div>

                <div class="bg-gray-900/80 border border-gray-800 p-4 rounded-xl shadow">
                    <div class="flex justify-between items-center text-gray-400 mb-2">
                        <span class="text-xs font-semibold uppercase">Security Vault</span>
                        <i class="fa-solid fa-lock text-amber-400"></i>
                    </div>
                    <div class="text-xl font-bold text-white mono">ARMED</div>
                    <p class="text-xs text-amber-400 mt-1">SHA-256 Protected</p>
                </div>
            </div>

            <!-- LIVE TELEMETRY LOG CONTAINER -->
            <div class="bg-gray-900/90 border border-gray-800 rounded-xl p-5 shadow-lg glow">
                <div class="flex justify-between items-center mb-4 border-b border-gray-800 pb-3">
                    <h2 class="text-sm font-bold uppercase tracking-wide text-gray-300 flex items-center space-x-2">
                        <i class="fa-solid fa-terminal text-sky-400"></i>
                        <span>Live Telemetry & Surveillance Log</span>
                    </h2>
                    <button onclick="clearLogs()" class="text-xs text-gray-400 hover:text-white bg-gray-800 px-2.5 py-1 rounded transition">Clear Feed</button>
                </div>
                <div id="log-container" class="mono text-xs bg-gray-950 p-4 rounded-lg h-64 overflow-y-auto space-y-2 border border-gray-800/80 text-gray-300">
                    <div>[<span class="text-sky-400">SYSTEM</span>] TJN NEXUS CORE initialized successfully.</div>
                    <div>[<span class="text-emerald-400">AUTOPILOT</span>] Background daemon running with drift-corrected timing.</div>
                    <div>[<span class="text-amber-400">SECURITY</span>] Vault integrity verified under Master 01 command.</div>
                </div>
            </div>
        </div>

        <!-- COLUMN 3: CONTROL PANEL & ACTIONS -->
        <div class="space-y-6">
            <div class="bg-gray-900/90 border border-gray-800 rounded-xl p-5 shadow-lg">
                <h2 class="text-sm font-bold uppercase tracking-wide text-gray-300 mb-4 flex items-center space-x-2 border-b border-gray-800 pb-3">
                    <i class="fa-solid fa-sliders text-emerald-400"></i>
                    <span>Master Command Panel</span>
                </h2>
                
                <div class="space-y-3">
                    <button onclick="triggerAction('Full System Integrity Audit')" class="w-full bg-sky-600 hover:bg-sky-500 text-white font-semibold py-2.5 px-4 rounded-lg text-sm transition flex items-center justify-center space-x-2 shadow">
                        <i class="fa-solid fa-stethoscope"></i>
                        <span>Run Full System Audit</span>
                    </button>
                    
                    <button onclick="triggerAction('Emergency Snapshot Secured')" class="w-full bg-amber-600 hover:bg-amber-500 text-white font-semibold py-2.5 px-4 rounded-lg text-sm transition flex items-center justify-center space-x-2 shadow">
                        <i class="fa-solid fa-vault"></i>
                        <span>Execute Emergency Snapshot</span>
                    </button>

                    <button onclick="triggerAction('ECU Rom & Checksum Verification')" class="w-full bg-indigo-600 hover:bg-indigo-500 text-white font-semibold py-2.5 px-4 rounded-lg text-sm transition flex items-center justify-center space-x-2 shadow">
                        <i class="fa-solid fa-car-rear"></i>
                        <span>Verify ECU & ROM Maps</span>
                    </button>
                </div>
            </div>

            <!-- SYSTEM METADATA -->
            <div class="bg-gray-900/60 border border-gray-800/80 rounded-xl p-4 text-xs text-gray-400 space-y-2">
                <div class="flex justify-between">
                    <span>Protocol Engine:</span>
                    <span class="text-white mono">Auto-Gemini v3</span>
                </div>
                <div class="flex justify-between">
                    <span>Active Interface:</span>
                    <span class="text-emerald-400 mono">Web Cloud Node</span>
                </div>
                <div class="flex justify-between">
                    <span>Authorization:</span>
                    <span class="text-amber-400 mono">SUPREME-01</span>
                </div>
            </div>
        </div>

    </main>

    <!-- FOOTER -->
    <footer class="bg-gray-900 border-t border-gray-800 text-center py-4 text-xs text-gray-500">
        <p>&copy; 2026 TJN NEXUS CORE &mdash; Managed & Controlled by Master 01 (ชูศักดิ์ สมรูป). All Rights Reserved.</p>
    </footer>

    <!-- INTERACTIVE DASHBOARD SCRIPT -->
    <script>
        function logMessage(level, message, colorClass) {
            const container = document.getElementById('log-container');
            const timeStr = new Date().toTimeString().split(' ')[0];
            const div = document.createElement('div');
            div.innerHTML = `[${timeStr}] [<span class="${colorClass}">${level}</span>] ${message}`;
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
        }

        function triggerAction(actionName) {
            logMessage('COMMAND', `Executing: ${actionName}...`, 'text-sky-400');
            setTimeout(() => {
                logMessage('SUCCESS', `${actionName} completed with 100% integrity.`, 'text-emerald-400');
            }, 800);
        }

        function clearLogs() {
            document.getElementById('log-container.').innerHTML = '';
            logMessage('SYSTEM', 'Log feed cleared by Master 01.', 'text-gray-400');
        }

        // Simulate periodic background autopilot heartbeat
        setInterval(() => {
            const events = [
                {lvl: 'AUTOPILOT', msg: 'Background health check cycle nominal.', col: 'text-emerald-400'},
                {lvl: 'TELEMETRY', msg: 'TCP & HTTP socket connections stable.', col: 'text-sky-400'},
                {lvl: 'SECURITY', msg: 'Perimeter defense protocol locked.', col: 'text-amber-400'}
            ];
            const ev = events[Math.floor(Math.random() * events.length)];
            logMessage(ev.lvl, ev.msg, ev.col);
        }, 12000);
    </script>
</body>
          </html>
  
