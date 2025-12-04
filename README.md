<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cyber IP Tracker By tuffa</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Courier New', monospace;
        }
        
        :root {
            --cyber-blue: #00f3ff;
            --cyber-purple: #b967ff;
            --cyber-pink: #ff2a6d;
            --dark-bg: #0a0a16;
            --darker-bg: #050510;
            --card-bg: rgba(16, 16, 32, 0.8);
        }
        
        body {
            background: linear-gradient(135deg, var(--darker-bg) 0%, var(--dark-bg) 100%);
            color: #e0e0ff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 243, 255, 0.2);
            padding: 30px;
            max-width: 900px;
            width: 100%;
            text-align: center;
            border: 1px solid var(--cyber-blue);
            position: relative;
            overflow: hidden;
        }
        
        .container::before {
            content: '';
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            background: linear-gradient(45deg, var(--cyber-blue), var(--cyber-purple), var(--cyber-pink));
            z-index: -1;
            filter: blur(20px);
            opacity: 0.3;
        }
        
        h1 {
            color: var(--cyber-blue);
            margin-bottom: 20px;
            font-size: 2.5rem;
            text-shadow: 0 0 10px rgba(0, 243, 255, 0.5);
            letter-spacing: 2px;
        }
        
        .tagline {
            color: var(--cyber-purple);
            margin-bottom: 30px;
            font-size: 1.1rem;
            letter-spacing: 1px;
        }
        
        .input-group {
            display: flex;
            margin-bottom: 30px;
            position: relative;
        }
        
        .input-group input {
            flex: 1;
            padding: 15px 20px;
            border: 1px solid var(--cyber-blue);
            border-radius: 5px 0 0 5px;
            background: rgba(10, 10, 22, 0.8);
            color: var(--cyber-blue);
            font-size: 1.1rem;
            outline: none;
            box-shadow: inset 0 0 10px rgba(0, 243, 255, 0.1);
        }
        
        .input-group input::placeholder {
            color: #6b6b8a;
        }
        
        .input-group button {
            padding: 0 25px;
            background: linear-gradient(45deg, var(--cyber-blue), var(--cyber-purple));
            color: var(--darker-bg);
            border: none;
            border-radius: 0 5px 5px 0;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 1rem;
        }
        
        .input-group button:hover {
            background: linear-gradient(45deg, var(--cyber-purple), var(--cyber-pink));
            box-shadow: 0 0 15px rgba(185, 103, 255, 0.5);
        }
        
        .ip-display {
            background: rgba(5, 5, 16, 0.7);
            border-radius: 5px;
            padding: 20px;
            margin: 20px 0;
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--cyber-blue);
            border: 1px solid var(--cyber-blue);
            word-break: break-all;
            display: flex;
            justify-content: space-between;
            align-items: center;
            text-shadow: 0 0 5px rgba(0, 243, 255, 0.5);
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.1);
        }
        
        .copy-btn {
            background: transparent;
            border: 1px solid var(--cyber-blue);
            color: var(--cyber-blue);
            padding: 8px 12px;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.9rem;
        }
        
        .copy-btn:hover {
            background: var(--cyber-blue);
            color: var(--darker-bg);
        }
        
        .loading {
            display: none;
            color: var(--cyber-blue);
            font-size: 1.2rem;
            margin: 20px 0;
        }
        
        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .info-card {
            background: rgba(16, 16, 32, 0.7);
            border-radius: 8px;
            padding: 20px;
            text-align: center;
            border-left: 4px solid var(--cyber-purple);
            transition: all 0.3s;
            box-shadow: 0 0 10px rgba(16, 16, 32, 0.5);
        }
        
        .info-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(185, 103, 255, 0.3);
        }
        
        .info-card i {
            font-size: 2rem;
            color: var(--cyber-pink);
            margin-bottom: 10px;
        }
        
        .info-card h3 {
            color: var(--cyber-blue);
            margin-bottom: 10px;
            font-size: 1rem;
            letter-spacing: 1px;
        }
        
        .info-card p {
            color: #e0e0ff;
            font-weight: 600;
            margin: 0;
            font-size: 1.1rem;
        }
        
        .maps-link {
            display: inline-block;
            margin-top: 10px;
            color: var(--cyber-purple);
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .maps-link:hover {
            color: var(--cyber-pink);
            text-shadow: 0 0 5px rgba(255, 42, 109, 0.5);
        }
        
        .action-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 30px;
        }
        
        .action-btn {
            background: transparent;
            color: var(--cyber-blue);
            border: 1px solid var(--cyber-blue);
            padding: 12px 25px;
            border-radius: 5px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .action-btn:hover {
            background: var(--cyber-blue);
            color: var(--darker-bg);
            box-shadow: 0 0 15px rgba(0, 243, 255, 0.5);
        }
        
        .action-btn.copy-all {
            border-color: var(--cyber-purple);
            color: var(--cyber-purple);
        }
        
        .action-btn.copy-all:hover {
            background: var(--cyber-purple);
            color: var(--darker-bg);
            box-shadow: 0 0 15px rgba(185, 103, 255, 0.5);
        }
        
        .footer {
            margin-top: 40px;
            color: #6b6b8a;
            font-size: 0.9rem;
            border-top: 1px solid rgba(0, 243, 255, 0.2);
            padding-top: 20px;
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(0, 243, 255, 0.4);
            }
            70% {
                box-shadow: 0 0 0 10px rgba(0, 243, 255, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(0, 243, 255, 0);
            }
        }
        
        .error-message {
            color: var(--cyber-pink);
            margin: 15px 0;
            font-weight: bold;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1><i class="fas fa-network-wired"></i> CYBER IP TRACKER BY TUFFA</h1>
        <p class="tagline">Lacak informasi lengkap dari alamat IP mana pun</p>
        
        <div class="input-group">
            <input type="text" id="ipInput" placeholder="Masukkan alamat IP target (contoh: 8.8.8.8 atau 2001:4860:4860::8888)">
            <button id="trackBtn"><i class="fas fa-crosshairs"></i> LACAK IP</button>
        </div>
        
        <div class="error-message" id="errorMessage"></div>
        
        <div class="ip-display pulse" id="ipDisplay">
            <span><i class="fas fa-location-arrow"></i> <span id="ipValue">Masukkan IP target di atas ya member Frostwolf</span></span>
            <button class="copy-btn" id="copyIpBtn"><i class="far fa-copy"></i> Salin</button>
        </div>
        
        <div class="loading" id="loadingIndicator">
            <i class="fas fa-spinner fa-spin"></i> Memuat informasi IP...
        </div>
        
        <div class="info-grid" id="infoGrid">
            
        </div>
        
        <div class="action-buttons">
            <button class="action-btn" id="refreshBtn"><i class="fas fa-redo"></i> Perbarui</button>
            <button class="action-btn copy-all" id="copyAllBtn"><i class="fas fa-copy"></i> Salin Semua Info</button>
        </div>
        
        <div class="footer">
            <p><i class="fas fa-info-circle"></i> Website ini menggunakan layanan pihak ketiga untuk mendapatkan informasi IP</p>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const ipInput = document.getElementById('ipInput');
            const trackBtn = document.getElementById('trackBtn');
            const ipDisplay = document.getElementById('ipDisplay');
            const ipValue = document.getElementById('ipValue');
            const infoGrid = document.getElementById('infoGrid');
            const loadingIndicator = document.getElementById('loadingIndicator');
            const refreshBtn = document.getElementById('refreshBtn');
            const copyIpBtn = document.getElementById('copyIpBtn');
            const copyAllBtn = document.getElementById('copyAllBtn');
            const errorMessage = document.getElementById('errorMessage');
            
           
            function isValidIP(ip) {
                
                const ipv4Regex = /^((25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/;
                
                const ipv6Regex = /^([0-9a-fA-F]{1,4}:){7}[0-9a-fA-F]{1,4}$/;
                
                return ipv4Regex.test(ip) || ipv6Regex.test(ip);
            }
            
           
            async function fetchIPData(ip = '') {
               
                errorMessage.style.display = 'none';
                
                
                if (ip && !isValidIP(ip)) {
                    errorMessage.textContent = 'Format IP tidak valid! Gunakan format IPv4 (contoh: 8.8.8.8) atau IPv6 (contoh: 2001:4860:4860::8888)';
                    errorMessage.style.display = 'block';
                    return;
                }
                
                loadingIndicator.style.display = 'block';
                ipValue.textContent = ip || 'Mendeteksi IP Anda...';
                infoGrid.innerHTML = '';
                
                try {
                  
                    if (!ip) {
                        const response = await fetch('https://api.ipify.org?format=json');
                        const data = await response.json();
                        ip = data.ip;
                    }
                    
                 
                    ipValue.textContent = ip;
                    
                   
                    fetchIPDetails(ip);
                } catch (error) {
                    console.error('Error mengambil IP:', error);
                    ipValue.textContent = 'Gagal mengambil informasi IP';
                    loadingIndicator.style.display = 'none';
                }
            }
            
            
            async function fetchIPDetails(ip) {
                try {
                   
                    const response = await fetch(`https://ipapi.co/${ip}/json/`);
                    const data = await response.json();
                    
                    
                    displayIPInfo(data);
                } catch (error) {
                    console.error('Error mengambil detail IP:', error);
                    
                    
                    try {
                        const response = await fetch(`https://ipapi.co/json/`);
                        const data = await response.json();
                        displayIPInfo(data);
                    } catch (fallbackError) {
                        console.error('Fallback juga gagal:', fallbackError);
                        displayBasicInfo(ip);
                    }
                }
            }
            
           
            function displayIPInfo(data) {
                infoGrid.innerHTML = '';
                
               
                let mapsLink = '';
                if (data.latitude && data.longitude) {
                    mapsLink = `<a href="https://www.google.com/maps?q=${data.latitude},${data.longitude}" target="_blank" class="maps-link"><i class="fas fa-map-marked-alt"></i> Lihat di Google Maps</a>`;
                }
                
                const infoItems = [
                    { icon: 'fa-network-wired', label: 'Jenis IP', value: data.version || (data.ip && data.ip.includes(':') ? 'IPv6' : 'IPv4') },
                    { icon: 'fa-city', label: 'Kota', value: data.city || 'Tidak tersedia' },
                    { icon: 'fa-map', label: 'Wilayah', value: data.region || 'Tidak tersedia' },
                    { icon: 'fa-flag', label: 'Negara', value: data.country_name || 'Tidak tersedia' },
                    { icon: 'fa-globe', label: 'Kode Negara', value: data.country_code || 'Tidak tersedia' },
                    { icon: 'fa-clock', label: 'Zona Waktu', value: data.timezone || 'Tidak tersedia' },
                    { icon: 'fa-server', label: 'Penyedia Layanan', value: data.org || data.isp || 'Tidak tersedia' },
                    { icon: 'fa-mail-bulk', label: 'Kode Pos', value: data.postal || 'Tidak tersedia' },
                    { icon: 'fa-map-marker-alt', label: 'Lokasi', value: (data.latitude && data.longitude) ? `${data.latitude}, ${data.longitude}` : 'Tidak tersedia', extra: mapsLink }
                ];
                
                infoItems.forEach(item => {
                    const infoCard = document.createElement('div');
                    infoCard.className = 'info-card';
                    
                    infoCard.innerHTML = `
                        <i class="fas ${item.icon}"></i>
                        <h3>${item.label}</h3>
                        <p>${item.value}</p>
                        ${item.extra || ''}
                    `;
                    
                    infoGrid.appendChild(infoCard);
                });
                
                loadingIndicator.style.display = 'none';
            }
            
            
            function displayBasicInfo(ip) {
                infoGrid.innerHTML = '';
                
                const infoCard = document.createElement('div');
                infoCard.className = 'info-card';
                infoCard.innerHTML = `
                    <i class="fas fa-network-wired"></i>
                    <h3>Jenis IP</h3>
                    <p>${ip.includes(':') ? 'IPv6' : 'IPv4'}</p>
                `;
                
                infoGrid.appendChild(infoCard);
                loadingIndicator.style.display = 'none';
            }
            
            function copyToClipboard(text) {
                navigator.clipboard.writeText(text).then(() => {
                   
                    const originalText = copyIpBtn.innerHTML;
                    copyIpBtn.innerHTML = '<i class="fas fa-check"></i> Disalin!';
                    setTimeout(() => {
                        copyIpBtn.innerHTML = originalText;
                    }, 2000);
                });
            }
            
            
            function copyAllInfo() {
                let allInfo = `Informasi IP: ${ipValue.textContent}\n\n`;
                const infoCards = document.querySelectorAll('.info-card');
                
                infoCards.forEach(card => {
                    const label = card.querySelector('h3').textContent;
                    const value = card.querySelector('p').textContent;
                    allInfo += `${label}: ${value}\n`;
                });
                
                copyToClipboard(allInfo);
                
                
                const originalText = copyAllBtn.innerHTML;
                copyAllBtn.innerHTML = '<i class="fas fa-check"></i> Semua Info Disalin!';
                setTimeout(() => {
                    copyAllBtn.innerHTML = originalText;
                }, 2000);
            }
            
            
            trackBtn.addEventListener('click', () => {
                const ip = ipInput.value.trim();
                fetchIPData(ip);
            });
            

            ipInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    const ip = ipInput.value.trim();
                    fetchIPData(ip);
                }
            });
            
            
            refreshBtn.addEventListener('click', () => {
                const ip = ipInput.value.trim();
                fetchIPData(ip || '');
            });
            
            copyIpBtn.addEventListener('click', () => {
                copyToClipboard(ipValue.textContent);
            });
            
           
            copyAllBtn.addEventListener('click', copyAllInfo);
            
          
            fetchIPData();
        });
    </script>
</body>
</html>
