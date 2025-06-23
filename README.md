<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biểu mẫu theo dõi nhiệt độ - độ ẩm</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #e0f7fa, #f5f5f5);
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            overflow: hidden;
        }
        
        .hospital-info {
            text-align: left;
            padding: 20px 30px 10px;
            border-bottom: 2px solid #e0e0e0;
        }
        
        .hospital-name {
            font-size: 22px;
            font-weight: 700;
            color: #0d47a1;
            margin-bottom: 5px;
        }
        
        .department-name {
            font-size: 18px;
            font-weight: 600;
            color: #1976d2;
            margin-bottom: 15px;
            text-align: left;
        }
        
        .title {
            text-align: center;
            font-size: 24px;
            font-weight: 700;
            text-transform: uppercase;
            color: #333;
            padding: 15px 0;
            background-color: #f1f8ff;
        }
        
        .year {
            text-align: center;
            font-style: italic;
            font-size: 18px;
            color: #555;
            padding-bottom: 10px;
            background-color: #f1f8ff;
        }
        
        .monitoring-info {
            display: flex;
            justify-content: center;
            gap: 20px;
            padding: 15px 0;
            background-color: #f1f8ff;
            flex-wrap: wrap;
        }
        
        .info-item {
            padding: 8px 15px;
            background-color: #e3f2fd;
            border-radius: 8px;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .room-info {
            text-align: left;
            padding: 15px 30px;
            font-weight: 700;
            font-size: 18px;
            color: #0d47a1;
            background-color: #e3f2fd;
            border-top: 1px solid #bbdefb;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        
        th, td {
            border: 1px solid #b0bec5;
            padding: 8px;
            text-align: center;
            font-size: 14px;
        }
        
        th {
            background-color: #e3f2fd;
            font-weight: 700;
            color: #0d47a1;
        }
        
        tbody tr:nth-child(even) {
            background-color: #f5f9ff;
        }
        
        tbody tr:hover {
            background-color: #e1f5fe;
        }
        
        .note {
            padding: 15px 30px;
            font-size: 14px;
            color: #555;
            border-top: 1px dashed #b0bec5;
        }
        
        .footer {
            display: flex;
            justify-content: space-between;
            padding: 15px 30px;
            font-size: 14px;
            color: #555;
            background-color: #f1f8ff;
            border-top: 1px solid #bbdefb;
        }
        
        .controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            padding: 20px;
            background-color: #f1f8ff;
            flex-wrap: wrap;
        }
        
        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
        }
        
        .btn-print {
            background: linear-gradient(to right, #1976d2, #0d47a1);
            color: white;
            box-shadow: 0 4px 10px rgba(25, 118, 210, 0.3);
        }
        
        .btn-print:hover {
            background: linear-gradient(to right, #1565c0, #0b3d91);
            transform: translateY(-3px);
        }
        
        .btn-generate {
            background: linear-gradient(to right, #4caf50, #2e7d32);
            color: white;
            box-shadow: 0 4px 10px rgba(76, 175, 80, 0.3);
        }
        
        .btn-generate:hover {
            background: linear-gradient(to right, #388e3c, #1b5e20);
            transform: translateY(-3px);
        }
        
        .parameter-form {
            padding: 20px;
            background-color: #f5f9ff;
            border-radius: 10px;
            margin: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
        }
        
        .form-title {
            text-align: center;
            font-weight: 700;
            color: #0d47a1;
            margin-bottom: 20px;
            font-size: 20px;
        }
        
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .input-group {
            display: flex;
            flex-direction: column;
        }
        
        .input-group label {
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }
        
        .input-group input, .input-group select {
            padding: 12px;
            border: 1px solid #90caf9;
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .input-group input:focus, .input-group select:focus {
            outline: none;
            border-color: #1976d2;
            box-shadow: 0 0 0 3px rgba(25, 118, 210, 0.2);
        }
        
        .month-selector {
            display: flex;
            justify-content: center;
            gap: 10px;
            padding: 10px 0;
            background-color: #f1f8ff;
            flex-wrap: wrap;
        }
        
        .month-selector select {
            padding: 8px 12px;
            border-radius: 5px;
            border: 1px solid #90caf9;
            background-color: white;
        }
        
        .room-selector {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            padding: 15px 0;
            background-color: #f1f8ff;
            flex-wrap: wrap;
        }
        
        .room-selector label {
            font-weight: 600;
            color: #0d47a1;
        }
        
        .room-selector select {
            padding: 10px 15px;
            border-radius: 8px;
            border: 1px solid #90caf9;
            background-color: white;
            font-size: 16px;
            min-width: 200px;
        }
        
        .loading {
            display: flex;
            justify-content: center;
            padding: 20px;
        }
        
        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid #f3f3f3;
            border-top: 4px solid #1976d2;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .error-message {
            background-color: #ffebee;
            color: #c62828;
            padding: 15px;
            margin: 20px;
            border-radius: 8px;
            text-align: center;
        }

        .status-indicator {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 12px;
            margin-top: 10px;
        }

        .status-success {
            background-color: #c8e6c9;
            color: #2e7d32;
        }

        .status-error {
            background-color: #ffcdd2;
            color: #c62828;
        }
        
        .session-selector {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            padding: 15px 0;
            background-color: #f1f8ff;
            flex-wrap: wrap;
        }
        
        .session-buttons {
            display: flex;
            gap: 10px;
        }
        
        .session-btn {
            padding: 10px 20px;
            border: 2px solid #90caf9;
            border-radius: 8px;
            background-color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .session-btn.active {
            background: linear-gradient(to right, #1976d2, #0d47a1);
            color: white;
            border-color: #0d47a1;
        }
        
        .session-btn:hover {
            background-color: #e3f2fd;
        }
        
        td.out-of-range {
            background-color: #ffcdd2;
            color: #c62828;
            font-weight: bold;
        }

        /* Styles for printing */
        @media print {
            body {
                background: white;
                padding: 0;
                margin: 0;
                font-size: 12px;
            }
            
            .container {
                max-width: 100%;
                box-shadow: none;
                border-radius: 0;
            }
            
            .controls, .parameter-form, .month-selector, .room-selector, .session-selector, .loading, .error-message {
                display: none;
            }
            
            .hospital-info {
                padding: 3px 15px;
                border-bottom: 1px solid black;
                text-align: left;
            }

            .hospital-name {
                font-size: 15px;
                color: black;
                text-align: left;
                margin-bottom: 0px; 
            }
            
            .department-name {
                font-size: 13px;
                color: black;
                text-align: left;
                margin-bottom: 1px;
                padding-left: 15px;
            }
            
            .title {
                background: white;
                color: black;
                padding: 3px 0;
                font-size: 16px;
            }
            
            .year {
                background: white;
                color: black;
                padding-bottom: 2px;
                padding-top: 0px;
                font-size: 13px;
            }

            .monitoring-info {
                padding: 2px 15px;
                font-size: 11px;
                flex-wrap: nowrap;
                justify-content: flex-start;
                gap: 5px;
            }
            
            .info-item {
                background: white;
                padding: 1px 3px;
            }

            .room-info {
                padding: 2px 15px;
                font-size: 13px;
                border-top: 0;
                background-color: white;
                color: black;
                margin-bottom: 5px;
            }

            table {
                width: 100%;
                border-collapse: collapse;
                margin: 5px 0;
                table-layout: fixed;
            }
            
            th, td {
                border: 1px solid #b0bec5;
                padding: 5px 6px;
                text-align: center;
                font-size: 9.5px;
                line-height: 1.2;
            }

            th {
                background-color: white;
                color: black;
            }
            
            tbody tr:nth-child(even) {
                background-color: white;
            }
            
            tbody tr:hover {
                background-color: white;
            }

            .footer {
                padding: 5px 20px;
                font-size: 10px;
                background-color: white;
                border-top: 1px solid #bbdefb;
            }
            
            td.out-of-range {
                background-color: #ffcdd2 !important;
                color: #c62828 !important;
                font-weight: bold;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="hospital-info">
            <div class="hospital-name">
                BỆNH VIỆN ĐA KHOA TỈNH HÀ GIANG
            </div>
            <div class="department-name">
                KHOA VI SINH - SHPT
            </div>
        </div>
        
        <div class="title">
            THEO DÕI NHIỆT ĐỘ - ĐỘ ẨM PHÒNG XÉT NGHIỆM
        </div>
        
        <div class="year" id="year">Năm: 2024</div>
        
        <div class="monitoring-info">
            <div class="info-item">
                <i class="fas fa-clock"></i> Theo dõi 8h hàng ngày
            </div>
            <div class="info-item">
                <i class="fas fa-thermometer-half"></i> Nhiệt độ cho phép: <span id="tempRange">21°C - 26°C</span>
            </div>
            <div class="info-item">
                <i class="fas fa-tint"></i> Độ ẩm cho phép: <span id="humidityRange">40% - 70%</span>
            </div>
        </div>
        
        <div class="room-info">
            <i class="fas fa-door-open"></i> Phòng: <span id="roomNumber">418</span>
        </div>
        
        <!-- Session selector -->
        <div class="session-selector">
            <label><i class="fas fa-sun"></i> Chọn buổi:</label>
            <div class="session-buttons">
                <button id="sessionMorning" class="session-btn active">Buổi Sáng</button>
                <button id="sessionAfternoon" class="session-btn">Buổi Chiều</button>
            </div>
        </div>
        
        <!-- Room selector -->
        <div class="room-selector">
            <label for="roomSelect"><i class="fas fa-door-open"></i> Chọn phòng:</label>
            <select id="roomSelect">
                <option value="">Đang tải danh sách phòng...</option>
            </select>
            <div class="status-indicator" id="statusIndicator" style="display: none;"></div>
        </div>
        
        <!-- Month selector -->
        <div class="month-selector">
            <div>
                <label for="month1">Tháng 1:</label>
                <select id="month1">
                    <!-- Options will be populated by JavaScript -->
                </select>
            </div>
            <div>
                <label for="month2">Tháng 2:</label>
                <select id="month2">
                    <!-- Options will be populated by JavaScript -->
                </select>
            </div>
            <div>
                <label for="month3">Tháng 3:</label>
                <select id="month3">
                    <!-- Options will be populated by JavaScript -->
                </select>
            </div>
            <div>
                <label for="month4">Tháng 4:</label>
                <select id="month4">
                    <!-- Options will be populated by JavaScript -->
                </select>
            </div>
        </div>
        
        <div id="tableContainer">
            <div class="loading">
                <div class="spinner"></div>
                <p style="margin-left: 10px;">Đang tải dữ liệu...</p>
            </div>
        </div>
        
        <div class="note">
            <p><strong>Chú thích:</strong> * Nằm trong khoảng cho phép ghi sát lề bên trái; nằm ngoài khoảng cho phép ghi sát lề bên phải</p>
        </div>
        
        <div class="footer">
            <div>Mã: VS-QTQL.5.1-BM02</div>
            <div>Ngày ban hành: 03/10/2022</div>
            <div>Phiên bản: 1.0</div>
            <div>Trang 1/1</div>
        </div>
        
        <div class="parameter-form">
            <div class="form-title">TÙY CHỈNH THÔNG SỐ</div>
            <div class="form-grid">
                <div class="input-group">
                    <label for="inputNhietDo"><i class="fas fa-thermometer-half"></i> Nhiệt độ</label>
                    <input type="text" id="inputNhietDo" placeholder="Nhiệt độ (21°C-26°C)" value="21°C - 26°C">
                </div>
                <div class="input-group">
                    <label for="inputDoAm"><i class="fas fa-tint"></i> Độ ẩm</label>
                    <input type="text" id="inputDoAm" placeholder="Độ ẩm (40%-70%)" value="40% - 70%">
                </div>
            </div>
        </div>
        
        <div class="controls">
            <button class="btn btn-print" onclick="window.print()">
                <i class="fas fa-print"></i> In trang
            </button>
            <button class="btn btn-generate" onclick="fetchData()">
                <i class="fas fa-sync"></i> Làm mới dữ liệu
            </button>
        </div>
    </div>

    <script>
        // Biến lưu trữ dữ liệu
        let allData = [];
        let organizedData = {};
        let availableRooms = [];
        let lastFetchTime = 0;
        const CACHE_DURATION = 5 * 60 * 1000; // 5 minutes
        let currentSession = "Sáng"; // Mặc định là buổi sáng

        // Hàm tạo danh sách tháng từ 1/2024 đến 12/2025
        function generateMonthOptions() {
            const months = [];
            for (let year = 2024; year <= 2025; year++) {
                for (let month = 1; month <= 12; month++) {
                    months.push({
                        value: `Tháng ${month} năm ${year}`,
                        display: `${month}/${year}`,
                        monthNum: month,
                        year: year
                    });
                }
            }
            return months;
        }

        // Hàm khởi tạo dropdown tháng
        function initializeMonthSelectors() {
            const months = generateMonthOptions();
            const selectors = ['month1', 'month2', 'month3', 'month4'];
            
            selectors.forEach((selectorId, index) => {
                const select = document.getElementById(selectorId);
                select.innerHTML = '';
                
                months.forEach(month => {
                    const option = document.createElement('option');
                    option.value = month.value;
                    option.textContent = `Tháng ${month.display}`;
                    select.appendChild(option);
                });
                
                // Thiết lập giá trị mặc định (9/2024, 10/2024, 11/2024, 12/2024)
                const defaultMonths = ['Tháng 9 năm 2024', 'Tháng 10 năm 2024', 'Tháng 11 năm 2024', 'Tháng 12 năm 2024'];
                if (defaultMonths[index]) {
                    select.value = defaultMonths[index];
                }
            });
        }

        // Hàm trích xuất thông tin phòng từ tên thiết bị
        function extractRoomNumber(tenThietBi) {
            const match = tenThietBi.match(/Phòng (\d+)/);
            return match ? match[1] : null;
        }

        // Hàm trích xuất tên ngắn từ tên đầy đủ
        function extractShortName(fullName) {
            if (!fullName) return '';
            
            // Tách tên thành các phần
            const nameParts = fullName.split(' ');
            
            // Lấy phần tử cuối cùng (tên)
            return nameParts.length > 0 ? nameParts[nameParts.length - 1] : fullName;
        }

        // Hàm tổ chức dữ liệu
        function organizeData(roomData) {
            organizedData = {};
            
            roomData.forEach(item => {
                // Chỉ lấy dữ liệu buổi đã chọn
                if (item.buoi !== currentSession) return;
                
                // Chuyển đổi ngày từ UTC sang múi giờ Việt Nam
                const dateObj = new Date(item.ngay_theo_doi);
                const vnTime = new Date(dateObj.getTime() + 7 * 60 * 60 * 1000);
                const day = vnTime.getDate();
                
                const monthYear = item.thang_nam;
                
                if (!organizedData[day]) {
                    organizedData[day] = {};
                }
                
                // Format nhiệt độ, độ ẩm
                let temperature = '';
                let humidity = '';
                
                if (item.nhiet_do !== null && item.nhiet_do !== '' && !isNaN(item.nhiet_do)) {
                    temperature = parseFloat(item.nhiet_do).toFixed(1).replace('.', ',');
                }
                
                if (item.do_am !== null && item.do_am !== '' && !isNaN(item.do_am)) {
                    humidity = parseFloat(item.do_am).toFixed(1).replace('.', ',');
                }
                
                // Trích xuất tên ngắn
                const shortName = extractShortName(item.nguoi_theo_doi);
                
                organizedData[day][monthYear] = {
                    temperature,
                    humidity,
                    person: shortName
                };
            });
        }

        // Hàm cập nhật bảng với dữ liệu đã chọn
        function updateTable() {
            const tableContainer = document.getElementById('tableContainer');
            
            // Lấy các tháng đã chọn
            const selectedMonths = [
                document.getElementById('month1').value,
                document.getElementById('month2').value,
                document.getElementById('month3').value,
                document.getElementById('month4').value
            ];

            // Lấy ngưỡng nhiệt độ và độ ẩm
            const tempRange = document.getElementById('inputNhietDo').value;
            const humidityRange = document.getElementById('inputDoAm').value;
            
            // Tách giá trị min/max từ chuỗi
            const tempMatch = tempRange.match(/(\d+)\s*°C\s*-\s*(\d+)\s*°C/);
            const humidityMatch = humidityRange.match(/(\d+)%\s*-\s*(\d+)%/);
            
            const minTemp = tempMatch ? parseInt(tempMatch[1]) : 21;
            const maxTemp = tempMatch ? parseInt(tempMatch[2]) : 26;
            const minHumidity = humidityMatch ? parseInt(humidityMatch[1]) : 40;
            const maxHumidity = humidityMatch ? parseInt(humidityMatch[2]) : 70;

            // Tạo bảng HTML
            let tableHTML = `
                <table>
                    <thead>
                        <tr>
                            <th rowspan="2">Ngày/ Date</th>
                            <th colspan="2">${selectedMonths[0]}</th>
                            <th rowspan="2">Người TD</th>
                            <th colspan="2">${selectedMonths[1]}</th>
                            <th rowspan="2">Người TD</th>
                            <th colspan="2">${selectedMonths[2]}</th>
                            <th rowspan="2">Người TD</th>
                            <th colspan="2">${selectedMonths[3]}</th>
                            <th rowspan="2">Người TD</th>
                        </tr>
                        <tr>
                            <th>Nhiệt độ (°C)</th>
                            <th>Độ ẩm (%)</th>
                            <th>Nhiệt độ (°C)</th>
                            <th>Độ ẩm (%)</th>
                            <th>Nhiệt độ (°C)</th>
                            <th>Độ ẩm (%)</th>
                            <th>Nhiệt độ (°C)</th>
                            <th>Độ ẩm (%)</th>
                        </tr>
                    </thead>
                    <tbody>
            `;
            
            // Tạo hàng cho từng ngày (1-31)
            for (let day = 1; day <= 31; day++) {
                tableHTML += '<tr>';
                tableHTML += `<td>${day}</td>`;
                
                // Thêm dữ liệu cho từng tháng (4 tháng)
                for (let i = 0; i < 4; i++) {
                    const month = selectedMonths[i];
                    const monthData = organizedData[day] && organizedData[day][month];
                    
                    // Kiểm tra và định dạng nhiệt độ
                    let tempCell = monthData ? monthData.temperature : '';
                    let tempClass = '';
                    if (monthData && monthData.temperature) {
                        const tempValue = parseFloat(monthData.temperature.replace(',', '.'));
                        if (tempValue < minTemp || tempValue > maxTemp) {
                            tempClass = 'out-of-range';
                        }
                    }
                    
                    // Kiểm tra và định dạng độ ẩm
                    let humidityCell = monthData ? monthData.humidity : '';
                    let humidityClass = '';
                    if (monthData && monthData.humidity) {
                        const humidityValue = parseFloat(monthData.humidity.replace(',', '.'));
                        if (humidityValue < minHumidity || humidityValue > maxHumidity) {
                            humidityClass = 'out-of-range';
                        }
                    }
                    
                    // Thêm ô nhiệt độ
                    tableHTML += `<td class="${tempClass}">${tempCell}</td>`;
                    
                    // Thêm ô độ ẩm
                    tableHTML += `<td class="${humidityClass}">${humidityCell}</td>`;
                    
                    // Thêm ô người theo dõi (chỉ hiển thị tên ngắn)
                    tableHTML += `<td>${monthData ? monthData.person : ''}</td>`;
                }
                
                tableHTML += '</tr>';
            }
            
            // Thêm hàng người xem xét
            tableHTML += `
                <tr class="reviewer-row">
                    <td style="text-align: left; font-weight: bold;">Người xem xét</td>
                    <td></td><td></td><td></td>
                    <td></td><td></td><td></td>
                    <td></td><td></td><td></td>
                    <td></td><td></td><td></td>
                </tr>
            `;
            
            tableHTML += '</tbody></table>';
            tableContainer.innerHTML = tableHTML;
        }

        // Hàm cập nhật thông tin phòng và năm
        function updateDisplayInfo() {
            const selectedRoom = document.getElementById('roomSelect').value;
            const roomNumber = extractRoomNumber(selectedRoom);
            
            if (roomNumber) {
                document.getElementById('roomNumber').textContent = roomNumber;
            }

            // Lấy năm từ tháng đầu tiên được chọn
            const firstMonth = document.getElementById('month1').value;
            const yearMatch = firstMonth.match(/năm (\d{4})/);
            if (yearMatch) {
                document.getElementById('year').textContent = `Năm: ${yearMatch[1]}`;
            }

            // Cập nhật thông số nhiệt độ và độ ẩm
            document.getElementById('tempRange').textContent = document.getElementById('inputNhietDo').value;
            document.getElementById('humidityRange').textContent = document.getElementById('inputDoAm').value;
        }

        // Hàm lấy dữ liệu từ URL
        async function fetchData() {
            const statusIndicator = document.getElementById('statusIndicator');
            const tableContainer = document.getElementById('tableContainer');
            
            // Hiển thị loading
            tableContainer.innerHTML = '<div class="loading"><div class="spinner"></div><p style="margin-left: 10px;">Đang tải dữ liệu...</p></div>';
            statusIndicator.style.display = 'none';
            
            try {
                // Kiểm tra cache
                const currentTime = new Date().getTime();
                if (currentTime - lastFetchTime < CACHE_DURATION && allData.length > 0) {
                    processData();
                    return;
                }
                
                // Sử dụng URL script mới
                const response = await fetch('https://script.google.com/macros/s/AKfycbw9tQT6wEOgNb-VndUkhIE5eW4czj9_uyaQ1PNCTLLWSTwHwNOb_W1ZZJ5KbQX8HaEFmw/exec');
                
                if (!response.ok) {
                    throw new Error('Không thể lấy dữ liệu từ URL');
                }
                
                const data = await response.json();
                allData = data || [];
                lastFetchTime = new Date().getTime();
                
                // Xử lý dữ liệu
                processData();
                
                // Hiển thị trạng thái thành công
                statusIndicator.textContent = `Đã tải ${allData.length} bản ghi lúc ${new Date().toLocaleTimeString('vi-VN')}`;
                statusIndicator.className = 'status-indicator status-success';
                statusIndicator.style.display = 'inline-block';
                
            } catch (error) {
                console.error('Lỗi khi lấy dữ liệu:', error);
                
                tableContainer.innerHTML = `
                    <div class="error-message">
                        <i class="fas fa-exclamation-triangle"></i> 
                        Đã xảy ra lỗi khi lấy dữ liệu: ${error.message}
                        <p>Vui lòng thử lại hoặc kiểm tra kết nối mạng</p>
                    </div>
                `;
                
                statusIndicator.textContent = `Lỗi: ${error.message}`;
                statusIndicator.className = 'status-indicator status-error';
                statusIndicator.style.display = 'inline-block';
            }
        }
        
        // Xử lý dữ liệu sau khi lấy về
        function processData() {
            // Lấy danh sách phòng duy nhất
            const roomSet = new Set();
            allData.forEach(item => {
                if (item.ten_thiet_bi && item.ten_thiet_bi.includes('Phòng')) {
                    roomSet.add(item.ten_thiet_bi);
                }
            });
            
            availableRooms = Array.from(roomSet).sort();
            
            // Cập nhật dropdown phòng
            const roomSelect = document.getElementById('roomSelect');
            roomSelect.innerHTML = '<option value="">-- Chọn phòng --</option>';
            
            availableRooms.forEach(room => {
                const option = document.createElement('option');
                option.value = room;
                option.textContent = room;
                roomSelect.appendChild(option);
            });
            
            // Thiết lập phòng mặc định (Phòng 418 nếu có)
            const defaultRoom = availableRooms.find(room => room.includes('418'));
            if (defaultRoom) {
                roomSelect.value = defaultRoom;
            } else if (availableRooms.length > 0) {
                roomSelect.value = availableRooms[0];
            }
            
            // Lọc và hiển thị dữ liệu
            filterAndDisplayData();
        }

        // Hàm lọc và hiển thị dữ liệu
        function filterAndDisplayData() {
            const selectedRoom = document.getElementById('roomSelect').value;
            
            if (!selectedRoom) {
                document.getElementById('tableContainer').innerHTML = `
                    <div class="error-message">
                        <i class="fas fa-exclamation-circle"></i>
                        Vui lòng chọn phòng để xem dữ liệu
                    </div>
                `;
                return;
            }
            
            // Lọc dữ liệu theo phòng đã chọn
            const roomData = allData.filter(item => item.ten_thiet_bi === selectedRoom);
            
            if (roomData.length === 0) {
                document.getElementById('tableContainer').innerHTML = `
                    <div class="error-message">
                        <i class="fas fa-database"></i>
                        Không tìm thấy dữ liệu cho phòng đã chọn
                    </div>
                `;
                return;
            }
            
            // Tổ chức dữ liệu
            organizeData(roomData);
            
            // Cập nhật thông tin hiển thị
            updateDisplayInfo();
            
            // Tạo bảng
            updateTable();
        }

        // Hàm chọn buổi
        function selectSession(session) {
            currentSession = session;
            
            // Cập nhật nút active
            document.getElementById('sessionMorning').classList.remove('active');
            document.getElementById('sessionAfternoon').classList.remove('active');
            
            if (session === "Sáng") {
                document.getElementById('sessionMorning').classList.add('active');
            } else {
                document.getElementById('sessionAfternoon').classList.add('active');
            }
            
            // Cập nhật bảng nếu đã chọn phòng
            if (document.getElementById('roomSelect').value) {
                filterAndDisplayData();
            }
        }

        // Hàm khởi tạo ứng dụng
        function initializeApp() {
            // Khởi tạo dropdown tháng
            initializeMonthSelectors();
            
            // Lắng nghe sự kiện thay đổi phòng
            document.getElementById('roomSelect').addEventListener('change', () => {
                filterAndDisplayData();
            });
            
            // Lắng nghe sự kiện thay đổi tháng
            const monthSelectors = ['month1', 'month2', 'month3', 'month4'];
            monthSelectors.forEach(id => {
                document.getElementById(id).addEventListener('change', () => {
                    updateDisplayInfo();
                    updateTable();
                });
            });
            
            // Lắng nghe sự kiện thay đổi thông số
            document.getElementById('inputNhietDo').addEventListener('change', function() {
                document.getElementById('tempRange').textContent = this.value;
                updateTable();
            });
            
            document.getElementById('inputDoAm').addEventListener('change', function() {
                document.getElementById('humidityRange').textContent = this.value;
                updateTable();
            });
            
            // Lắng nghe sự kiện chọn buổi
            document.getElementById('sessionMorning').addEventListener('click', () => {
                selectSession("Sáng");
            });
            
            document.getElementById('sessionAfternoon').addEventListener('click', () => {
                selectSession("Chiều");
            });
            
            // Tải dữ liệu ban đầu
            fetchData();
        }

        // Khởi chạy ứng dụng khi trang tải xong
        document.addEventListener('DOMContentLoaded', initializeApp);
    </script>
</body>
</html>
