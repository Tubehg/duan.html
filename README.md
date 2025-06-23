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
        
        .url-container {
            margin-top: 20px;
            padding: 15px;
            background-color: #e3f2fd;
            border-radius: 8px;
            font-size: 14px;
        }
        
        .url-container a {
            color: #0d47a1;
            font-weight: 600;
            word-break: break-all;
        }
        
        .url-container button {
            margin-top: 10px;
            padding: 8px 15px;
            background-color: #0d47a1;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .url-container button:hover {
            background-color: #0b3d91;
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
            
            .controls, .parameter-form, .month-selector, .loading, .error-message {
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

            .signer-section {
                text-align: right;
                padding: 5px 30px 0px;
                font-size: 12px;
                color: #555;
            }
            .signer-text {
                margin-top: 30px;
            }
            .note-asterisk {
                text-align: right;
                padding: 0 30px 10px;
                font-size: 10px;
                color: #777;
            }

            .footer {
                padding: 5px 20px;
                font-size: 10px;
                background-color: white;
                border-top: 1px solid #bbdefb;
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
        
        <!-- Month selector -->
        <div class="month-selector">
            <div>
                <label for="month1">Tháng 1:</label>
                <select id="month1">
                    <option value="1/2024">Tháng 1/2024</option>
                    <option value="2/2024">Tháng 2/2024</option>
                    <option value="3/2024">Tháng 3/2024</option>
                    <option value="4/2024">Tháng 4/2024</option>
                    <option value="5/2024">Tháng 5/2024</option>
                    <option value="6/2024">Tháng 6/2024</option>
                    <option value="7/2024">Tháng 7/2024</option>
                    <option value="8/2024">Tháng 8/2024</option>
                    <option value="9/2024" selected>Tháng 9/2024</option>
                    <option value="10/2024">Tháng 10/2024</option>
                    <option value="11/2024">Tháng 11/2024</option>
                    <option value="12/2024">Tháng 12/2024</option>
                </select>
            </div>
            <div>
                <label for="month2">Tháng 2:</label>
                <select id="month2">
                    <option value="1/2024">Tháng 1/2024</option>
                    <option value="2/2024">Tháng 2/2024</option>
                    <option value="3/2024">Tháng 3/2024</option>
                    <option value="4/2024">Tháng 4/2024</option>
                    <option value="5/2024">Tháng 5/2024</option>
                    <option value="6/2024">Tháng 6/2024</option>
                    <option value="7/2024">Tháng 7/2024</option>
                    <option value="8/2024">Tháng 8/2024</option>
                    <option value="9/2024">Tháng 9/2024</option>
                    <option value="10/2024" selected>Tháng 10/2024</option>
                    <option value="11/2024">Tháng 11/2024</option>
                    <option value="12/2024">Tháng 12/2024</option>
                </select>
            </div>
            <div>
                <label for="month3">Tháng 3:</label>
                <select id="month3">
                    <option value="1/2024">Tháng 1/2024</option>
                    <option value="2/2024">Tháng 2/2024</option>
                    <option value="3/2024">Tháng 3/2024</option>
                    <option value="4/2024">Tháng 4/2024</option>
                    <option value="5/2024">Tháng 5/2024</option>
                    <option value="6/2024">Tháng 6/2024</option>
                    <option value="7/2024">Tháng 7/2024</option>
                    <option value="8/2024">Tháng 8/2024</option>
                    <option value="9/2024">Tháng 9/2024</option>
                    <option value="10/2024">Tháng 10/2024</option>
                    <option value="11/2024" selected>Tháng 11/2024</option>
                    <option value="12/2024">Tháng 12/2024</option>
                </select>
            </div>
            <div>
                <label for="month4">Tháng 4:</label>
                <select id="month4">
                    <option value="1/2024">Tháng 1/2024</option>
                    <option value="2/2024">Tháng 2/2024</option>
                    <option value="3/2024">Tháng 3/2024</option>
                    <option value="4/2024">Tháng 4/2024</option>
                    <option value="5/2024">Tháng 5/2024</option>
                    <option value="6/2024">Tháng 6/2024</option>
                    <option value="7/2024">Tháng 7/2024</option>
                    <option value="8/2024">Tháng 8/2024</option>
                    <option value="9/2024">Tháng 9/2024</option>
                    <option value="10/2024">Tháng 10/2024</option>
                    <option value="11/2024">Tháng 11/2024</option>
                    <option value="12/2024" selected>Tháng 12/2024</option>
                </select>
            </div>
        </div>
        
        <div id="tableContainer">
            <table>
                <thead>
                    <tr>
                        <th rowspan="2">Ngày/ Date</th>
                        <th colspan="2" id="monthHeader1">Tháng/Month<br>9/2024</th>
                        <th rowspan="2">Người TD</th>
                        <th colspan="2" id="monthHeader2">Tháng/Month<br>10/2024</th>
                        <th rowspan="2">Người TD</th>
                        <th colspan="2" id="monthHeader3">Tháng/Month<br>11/2024</th>
                        <th rowspan="2">Người TD</th>
                        <th colspan="2" id="monthHeader4">Tháng/Month<br>12/2024</th>
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
                <tbody id="dataBody">
                    <!-- Data will be populated here -->
                </tbody>
            </table>
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
                    <label for="inputPhong"><i class="fas fa-door-open"></i> Số phòng</label>
                    <input type="text" id="inputPhong" placeholder="Số phòng" value="418">
                </div>
                <div class="input-group">
                    <label for="inputNam"><i class="fas fa-calendar"></i> Năm</label>
                    <input type="text" id="inputNam" placeholder="Năm" value="2024">
                </div>
                <div class="input-group">
                    <label for="inputNhietDo"><i class="fas fa-thermometer-half"></i> Nhiệt độ</label>
                    <input type="text" id="inputNhietDo" placeholder="Nhiệt độ (21°C-26°C)" value="21°C - 26°C">
                </div>
                <div class="input-group">
                    <label for="inputDoAm"><i class="fas fa-tint"></i> Độ ẩm</label>
                    <input type="text" id="inputDoAm" placeholder="Độ ẩm (40%-70%)" value="40% - 70%">
                </div>
            </div>
            
            <div class="url-container" id="urlContainer">
                <strong><i class="fas fa-link"></i> URL đã tạo:</strong>
                <div id="generatedUrl"></div>
            </div>
        </div>
        
        <div class="controls">
            <button class="btn btn-print" onclick="window.print()">
                <i class="fas fa-print"></i> In trang
            </button>
            <button class="btn btn-generate" onclick="generateUrl()">
                <i class="fas fa-link"></i> Tạo URL tùy chỉnh
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
        let lastFetchTime = 0;
        const CACHE_DURATION = 5 * 60 * 1000; // 5 minutes

        // Hàm chuyển đổi tên tháng
        function formatMonthYear(thang_nam) {
            if (!thang_nam) return '';
            const parts = thang_nam.split(' ');
            if (parts.length < 4) return '';
            const month = parts[1];
            const year = parts[3];
            return `${month}/${year}`;
        }

        // Hàm tổ chức dữ liệu
        function organizeData(roomData) {
            organizedData = {};
            
            // Tạo cấu trúc dữ liệu theo ngày và tháng
            roomData.forEach(item => {
                // Điều chỉnh múi giờ: UTC -> UTC+7 (Việt Nam)
                const dateObj = new Date(item.ngay_theo_doi);
                const vnTime = new Date(dateObj.getTime() + 7 * 60 * 60 * 1000);
                const day = vnTime.getDate();
                
                // Lấy tháng/năm
                const monthYear = formatMonthYear(item.thang_nam);
                
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
                
                organizedData[day][monthYear] = {
                    temperature,
                    humidity,
                    person: '' // không có thông tin người
                };
            });
        }

        // Hàm cập nhật bảng với dữ liệu đã chọn
        function updateTable() {
            const tbody = document.getElementById('dataBody');
            tbody.innerHTML = '';
            
            // Lấy các tháng đã chọn
            const selectedMonths = [
                document.getElementById('month1').value,
                document.getElementById('month2').value,
                document.getElementById('month3').value,
                document.getElementById('month4').value
            ];
            
            // Cập nhật tiêu đề các tháng
            document.getElementById('monthHeader1').innerHTML = `Tháng/Month<br>${selectedMonths[0]}`;
            document.getElementById('monthHeader2').innerHTML = `Tháng/Month<br>${selectedMonths[1]}`;
            document.getElementById('monthHeader3').innerHTML = `Tháng/Month<br>${selectedMonths[2]}`;
            document.getElementById('monthHeader4').innerHTML = `Tháng/Month<br>${selectedMonths[3]}`;
            
            // Tạo hàng cho từng ngày (1-31)
            for (let day = 1; day <= 31; day++) {
                const row = document.createElement('tr');
                
                // Thêm cột ngày
                const dateCell = document.createElement('td');
                dateCell.textContent = day;
                row.appendChild(dateCell);
                
                // Thêm dữ liệu cho từng tháng (4 tháng)
                for (let i = 0; i < 4; i++) {
                    const month = selectedMonths[i];
                    
                    // Kiểm tra xem có dữ liệu cho ngày và tháng này không
                    const dataForDay = organizedData[day];
                    const monthData = dataForDay && dataForDay[month];
                    
                    // Thêm ô nhiệt độ
                    const tempCell = document.createElement('td');
                    tempCell.textContent = monthData ? monthData.temperature : '';
                    row.appendChild(tempCell);
                    
                    // Thêm ô độ ẩm
                    const humidityCell = document.createElement('td');
                    humidityCell.textContent = monthData ? monthData.humidity : '';
                    row.appendChild(humidityCell);
                    
                    // Thêm ô người theo dõi (sau mỗi 2 cột)
                    if (i < 3) {
                        const personCell = document.createElement('td');
                        personCell.textContent = monthData ? monthData.person : '';
                        row.appendChild(personCell);
                    }
                }
                
                // Thêm ô người theo dõi cho tháng cuối
                const lastMonth = selectedMonths[3];
                const lastMonthData = organizedData[day] && organizedData[day][lastMonth];
                const lastPersonCell = document.createElement('td');
                lastPersonCell.textContent = lastMonthData ? lastMonthData.person : '';
                row.appendChild(lastPersonCell);
                
                tbody.appendChild(row);
            }
            
            // Thêm hàng người xem xét
            const reviewerRow = document.createElement('tr');
            reviewerRow.className = 'reviewer-row';
            reviewerRow.innerHTML = `
                <td style="text-align: left; font-weight: bold;">Người xem xét</td>
                <td></td><td></td><td><span class="signature-line"></span></td>
                <td></td><td></td><td><span class="signature-line"></span></td>
                <td></td><td></td><td><span class="signature-line"></span></td>
                <td></td><td></td><td><span class="signature-line"></span></td>
            `;
            tbody.appendChild(reviewerRow);
        }

        // Hàm lấy dữ liệu từ URL
        async function fetchData() {
            const phong = document.getElementById('inputPhong').value;
            
            // Hiển thị loading
            const tableContainer = document.getElementById('tableContainer');
            tableContainer.innerHTML = '<div class="loading"><div class="spinner"></div></div>';
            
            // Xóa thông báo lỗi cũ
            const errorElement = document.querySelector('.error-message');
            if (errorElement) errorElement.remove();
            
            try {
                // Kiểm tra cache
                const currentTime = new Date().getTime();
                if (currentTime - lastFetchTime < CACHE_DURATION && allData.length > 0) {
                    // Sử dụng dữ liệu cache
                    console.log('Sử dụng dữ liệu cache');
                    processData(phong);
                    return;
                }
                
                const response = await fetch('https://script.google.com/macros/s/AKfycbz7fiaQeYt7brE8TBtqJ2xbXHq8H2qkHdn-VWy1HOQSbDv9o88o_3xyfG3blaKF-cqvvA/exec');
                
                if (!response.ok) {
                    throw new Error('Không thể lấy dữ liệu từ URL');
                }
                
                const data = await response.json();
                allData = data || [];
                lastFetchTime = new Date().getTime();
                
                // Xử lý dữ liệu
                processData(phong);
                
            } catch (error) {
                console.error('Lỗi khi lấy dữ liệu:', error);
                
                // Tạo thông báo lỗi
                const errorElement = document.createElement('div');
                errorElement.className = 'error-message';
                errorElement.innerHTML = `
                    <i class="fas fa-exclamation-triangle"></i> 
                    Đã xảy ra lỗi khi lấy dữ liệu: ${error.message}
                    <p>Vui lòng thử lại hoặc kiểm tra kết nối mạng</p>
                `;
                
                tableContainer.innerHTML = '';
                tableContainer.appendChild(errorElement);
            }
        }
        
        // Xử lý dữ liệu sau khi lấy về
        function processData(phong) {
            // Lọc dữ liệu cho phòng hiện tại
            const roomData = allData.filter(item => 
                item.ten_thiet_bi === `Phòng ${phong}`
            );
            
            if (roomData.length === 0) {
                const tableContainer = document.getElementById('tableContainer');
                tableContainer.innerHTML = '<div class="error-message"><i class="fas fa-exclamation-circle"></i> Không tìm thấy dữ liệu cho phòng này</div>';
                return;
            }
            
            // Tổ chức dữ liệu
            organizeData(roomData);
            
            // Cập nhật bảng
            updateTable();
            
            // Hiển thị lại bảng
            const tableContainer = document.getElementById('tableContainer');
            tableContainer.innerHTML = `
                <table>
                    <thead>
                        <tr>
                            <th rowspan="2">Ngày/ Date</th>
                            <th colspan="2" id="monthHeader1">Tháng/Month<br>9/2024</th>
                            <th rowspan="2">Người TD</th>
                            <th colspan="2" id="monthHeader2">Tháng/Month<br>10/2024</th>
                            <th rowspan="2">Người TD</th>
                            <th colspan="2" id="monthHeader3">Tháng/Month<br>11/2024</th>
                            <th rowspan="2">Người TD</th>
                            <th colspan="2" id="monthHeader4">Tháng/Month<br>12/2024</th>
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
                    <tbody id="dataBody">
                        ${document.getElementById('dataBody').innerHTML}
                    </tbody>
                </table>
            `;
        }

        // Hàm tạo URL tùy chỉnh
        function generateUrl() {
            const phong = document.getElementById('inputPhong').value;
            const nam = document.getElementById('inputNam').value;
            const nhietDo = document.getElementById('inputNhietDo').value;
            const doAm = document.getElementById('inputDoAm').value;
            
            // Cập nhật thông tin trên trang
            document.getElementById('roomNumber').textContent = phong;
            document.getElementById('year').textContent = 'Năm: ' + nam;
            document.getElementById('tempRange').textContent = nhietDo;
            document.getElementById('humidityRange').textContent = doAm;
            
            // Tạo URL
            const baseUrl = window.location.href.split('?')[0];
            const newUrl = `${baseUrl}?phong=${encodeURIComponent(phong)}&nam=${encodeURIComponent(nam)}&nhietDo=${encodeURIComponent(nhietDo)}&doAm=${encodeURIComponent(doAm)}`;
            
            document.getElementById('generatedUrl').innerHTML = `
                <a href="${newUrl}" target="_blank">${newUrl}</a>
                <button onclick="copyToClipboard('${newUrl}')"><i class="fas fa-copy"></i> Sao chép URL</button>
            `;
        }
        
        // Hàm sao chép vào clipboard
        function copyToClipboard(text) {
            navigator.clipboard.writeText(text).then(() => {
                alert('Đã sao chép URL vào clipboard!');
            });
        }
        
        // Khởi tạo khi trang được tải
        document.addEventListener('DOMContentLoaded', function() {
            // Thiết lập sự kiện cho các dropdown tháng
            document.querySelectorAll('.month-selector select').forEach(select => {
                select.addEventListener('change', updateTable);
            });
            
            // Thiết lập sự kiện cho input phòng
            document.getElementById('inputPhong').addEventListener('change', function() {
                document.getElementById('roomNumber').textContent = this.value;
                fetchData();
            });
            
            // Tải dữ liệu ban đầu
            fetchData();
            
            // Kiểm tra tham số URL khi tải trang
            const urlParams = new URLSearchParams(window.location.search);
            
            if (urlParams.has('phong')) {
                const phong = urlParams.get('phong');
                document.getElementById('roomNumber').textContent = phong;
                document.getElementById('inputPhong').value = phong;
            }
            if (urlParams.has('nam')) {
                document.getElementById('year').textContent = 'Năm: ' + urlParams.get('nam');
                document.getElementById('inputNam').value = urlParams.get('nam');
            }
            if (urlParams.has('nhietDo')) {
                document.getElementById('tempRange').textContent = urlParams.get('nhietDo');
                document.getElementById('inputNhietDo').value = urlParams.get('nhietDo');
            }
            if (urlParams.has('doAm')) {
                document.getElementById('humidityRange').textContent = urlParams.get('doAm');
                document.getElementById('inputDoAm').value = urlParams.get('doAm');
            }
        });
    </script>
</body>
</html>
