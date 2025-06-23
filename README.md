<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Theo dõi nhiệt độ - độ ẩm phòng xét nghiệm</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .hospital {
            text-align: center;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 5px;
        }
        .department {
            text-align: center;
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 15px;
        }
        .title {
            text-align: center;
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 5px;
        }
        .year {
            text-align: center;
            font-style: italic;
            margin-bottom: 10px;
        }
        .monitoring-info {
            text-align: center;
            margin-bottom: 15px;
        }
        .room {
            text-align: center;
            font-weight: bold;
            margin-bottom: 15px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 15px;
        }
        th, td {
            border: 1px solid black;
            padding: 5px;
            text-align: center;
        }
        th {
            background-color: #f2f2f2;
        }
        .note {
            font-size: 14px;
            margin-bottom: 15px;
        }
        .footer {
            display: flex;
            justify-content: space-between;
            font-size: 14px;
        }
        .editable {
            background-color: #ffffcc;
        }
    </style>
</head>
<body>
    <div class="hospital" id="hospital">BỆNH VIỆN ĐA KHOA TỈNH HÀ GIANG</div>
    <div class="department" id="department">KHOA VI SINH - SHPT</div>
    
    <div class="title">THEO DÕI NHIỆT ĐỘ - ĐỘ ẨM PHÒNG XÉT NGHIỆM</div>
    <div class="year" id="year">Năm: 2024</div>
    
    <div class="monitoring-info">
        <span><strong>Theo dõi 8h hàng ngày</strong></span>
        <span><strong>Nhiệt độ cho phép: <span id="tempRange" class="editable">21°C - 26°C</span></strong></span>
        <span><strong>Độ ẩm cho phép: <span id="humidityRange" class="editable">40% - 70%</span></strong></span>
    </div>
    
    <div class="room">Phòng: <span id="roomNumber" class="editable">418</span></div>
    
    <table>
        <thead>
            <tr>
                <th rowspan="2">Ngày/ Date</th>
                <th colspan="2">Tháng/Month<br>9/2024</th>
                <th rowspan="2">Người TD</th>
                <th colspan="2">Tháng/Month<br>10/2024</th>
                <th rowspan="2">Người TD</th>
                <th colspan="2">Tháng/Month<br>11/2024</th>
                <th rowspan="2">Người TD</th>
                <th colspan="2">Tháng/Month<br>12/2024</th>
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
            <tr><td>1</td><td>25,0</td><td>53,0</td><td>Sâm</td><td>22,0</td><td>65,0</td><td>Việt</td><td>24,0</td><td>51,0</td><td>Tú</td><td>22,0</td><td>64,0</td><td>Việt</td></tr>
            <tr><td>2</td><td>21,0</td><td>45,0</td><td>Sâm</td><td>23,0</td><td>60,0</td><td>Việt</td><td>26,0</td><td>54,0</td><td>Tú</td><td>25,0</td><td>48,0</td><td>Nam</td></tr>
            <tr><td>3</td><td>24,0</td><td>43,0</td><td>Tú</td><td>21,0</td><td>56,0</td><td>Nam</td><td>24,0</td><td>63,0</td><td>Tú</td><td>26,0</td><td>51,0</td><td>Việt</td></tr>
            <tr><td>4</td><td>24,0</td><td>47,0</td><td>Sâm</td><td>25,0</td><td>50,0</td><td>Nam</td><td>22,0</td><td>65,0</td><td>Sâm</td><td>26,0</td><td>43,0</td><td>Việt</td></tr>
            <tr><td>5</td><td>21,0</td><td>69,0</td><td>Tú</td><td>25,0</td><td>51,0</td><td>Nam</td><td>23,0</td><td>61,0</td><td>Tú</td><td>26,0</td><td>57,0</td><td>Việt</td></tr>
            <tr><td>6</td><td>21,0</td><td>56,0</td><td>Sâm</td><td>24,0</td><td>47,0</td><td>Nam</td><td>25,0</td><td>63,0</td><td>Tú</td><td>22,0</td><td>50,0</td><td>Việt</td></tr>
            <tr><td>7</td><td>21,0</td><td>52,0</td><td>Sâm</td><td>23,0</td><td>45,0</td><td>Việt</td><td>23,0</td><td>45,0</td><td>Sâm</td><td>21,0</td><td>56,0</td><td>Việt</td></tr>
            <tr><td>8</td><td>26,0</td><td>59,0</td><td>Sâm</td><td>26,0</td><td>45,0</td><td>Việt</td><td>24,0</td><td>43,0</td><td>Sâm</td><td>21,0</td><td>60,0</td><td>Nam</td></tr>
            <tr><td>9</td><td>26,0</td><td>46,0</td><td>Tú</td><td>26,0</td><td>58,0</td><td>Việt</td><td>23,0</td><td>41,0</td><td>Sâm</td><td>26,0</td><td>50,0</td><td>Nam</td></tr>
            <tr><td>10</td><td>23,0</td><td>49,0</td><td>Tú</td><td>22,0</td><td>44,0</td><td>Việt</td><td>24,0</td><td>45,0</td><td>Sâm</td><td>24,0</td><td>69,0</td><td>Nam</td></tr>
            <tr><td>11</td><td>21,0</td><td>63,0</td><td>Tú</td><td>21,0</td><td>56,0</td><td>Nam</td><td>21,0</td><td>60,0</td><td>Sâm</td><td>23,0</td><td>49,0</td><td>Nam</td></tr>
            <tr><td>12</td><td>24,0</td><td>53,0</td><td>Sâm</td><td>24,0</td><td>50,0</td><td>Việt</td><td>25,0</td><td>51,0</td><td>Sâm</td><td>23,0</td><td>60,0</td><td>Việt</td></tr>
            <tr><td>13</td><td>26,0</td><td>63,0</td><td>Sâm</td><td>26,0</td><td>54,0</td><td>Việt</td><td>26,0</td><td>47,0</td><td>Sâm</td><td>22,0</td><td>66,0</td><td>Nam</td></tr>
            <tr><td>14</td><td>23,0</td><td>62,0</td><td>Sâm</td><td>22,0</td><td>66,0</td><td>Việt</td><td>26,0</td><td>42,0</td><td>Tú</td><td>24,0</td><td>59,0</td><td>Việt</td></tr>
            <tr><td>15</td><td>24,0</td><td>54,0</td><td>Sâm</td><td>23,0</td><td>53,0</td><td>Nam</td><td>24,0</td><td>45,0</td><td>Sâm</td><td>24,0</td><td>48,0</td><td>Nam</td></tr>
            <tr><td>16</td><td>23,0</td><td>68,0</td><td>Sâm</td><td>22,0</td><td>57,0</td><td>Nam</td><td>22,0</td><td>69,0</td><td>Tú</td><td>26,0</td><td>68,0</td><td>Việt</td></tr>
            <tr><td>17</td><td>23,0</td><td>41,0</td><td>Sâm</td><td>25,0</td><td>66,0</td><td>Nam</td><td>26,0</td><td>63,0</td><td>Tú</td><td>26,0</td><td>51,0</td><td>Nam</td></tr>
            <tr><td>18</td><td>23,0</td><td>42,0</td><td>Tú</td><td>23,0</td><td>59,0</td><td>Việt</td><td>21,0</td><td>52,0</td><td>Tú</td><td>26,0</td><td>45,0</td><td>Việt</td></tr>
            <tr><td>19</td><td>24,0</td><td>50,0</td><td>Tú</td><td>24,0</td><td>41,0</td><td>Nam</td><td>26,0</td><td>53,0</td><td>Tú</td><td>25,0</td><td>53,0</td><td>Việt</td></tr>
            <tr><td>20</td><td>25,0</td><td>61,0</td><td>Sâm</td><td>24,0</td><td>68,0</td><td>Nam</td><td>21,0</td><td>57,0</td><td>Sâm</td><td>22,0</td><td>57,0</td><td>Việt</td></tr>
            <tr><td>21</td><td>26,0</td><td>53,0</td><td>Tú</td><td>25,0</td><td>68,0</td><td>Việt</td><td>23,0</td><td>49,0</td><td>Sâm</td><td>22,0</td><td>48,0</td><td>Việt</td></tr>
            <tr><td>22</td><td>26,0</td><td>41,0</td><td>Tú</td><td>26,0</td><td>41,0</td><td>Nam</td><td>21,0</td><td>63,0</td><td>Tú</td><td>21,0</td><td>52,0</td><td>Nam</td></tr>
            <tr><td>23</td><td>25,0</td><td>44,0</td><td>Tú</td><td>24,0</td><td>67,0</td><td>Nam</td><td>22,0</td><td>69,0</td><td>Sâm</td><td>24,0</td><td>57,0</td><td>Việt</td></tr>
            <tr><td>24</td><td>26,0</td><td>57,0</td><td>Tú</td><td>26,0</td><td>53,0</td><td>Nam</td><td>22,0</td><td>54,0</td><td>Sâm</td><td>21,0</td><td>50,0</td><td>Việt</td></tr>
            <tr><td>25</td><td>23,0</td><td>65,0</td><td>Tú</td><td>26,0</td><td>44,0</td><td>Việt</td><td>22,0</td><td>45,0</td><td>Sâm</td><td>23,0</td><td>61,0</td><td>Nam</td></tr>
            <tr><td>26</td><td>25,0</td><td>57,0</td><td>Tú</td><td>25,0</td><td>49,0</td><td>Nam</td><td>24,0</td><td>56,0</td><td>Sâm</td><td>23,0</td><td>68,0</td><td>Việt</td></tr>
            <tr><td>27</td><td>22,0</td><td>57,0</td><td>Sâm</td><td>21,0</td><td>46,0</td><td>Việt</td><td>25,0</td><td>44,0</td><td>Sâm</td><td>24,0</td><td>67,0</td><td>Việt</td></tr>
            <tr><td>28</td><td>21,0</td><td>55,0</td><td>Sâm</td><td>25,0</td><td>55,0</td><td>Việt</td><td>23,0</td><td>69,0</td><td>Tú</td><td>24,0</td><td>61,0</td><td>Việt</td></tr>
            <tr><td>29</td><td>22,0</td><td>62,0</td><td>Sâm</td><td>21,0</td><td>51,0</td><td>Nam</td><td>24,0</td><td>65,0</td><td>Tú</td><td>22,0</td><td>62,0</td><td>Nam</td></tr>
            <tr><td>30</td><td>23,0</td><td>51,0</td><td>Sâm</td><td>21,0</td><td>60,0</td><td>Việt</td><td>25,0</td><td>57,0</td><td>Tú</td><td>25,0</td><td>48,0</td><td>Việt</td></tr>
            <tr><td>31</td><td></td><td></td><td></td><td>21,0</td><td>54,0</td><td>Nam</td><td></td><td></td><td></td><td>22,0</td><td>68,0</td><td>Nam</td></tr>
        </tbody>
    </table>

    <div class="note">
        - : nằm trong khoảng cho phép ghi sát lề bên trái; nằm ngoài khoảng cho phép ghi sát lề bên phải
    </div>

    <div class="footer">
        <div>Mã: VS-QTQL.5.1-BM02</div>
        <div>Ngày ban hành: 03/10/2022</div>
        <div>Phiên bản: 1.0</div>
        <div>Trang 1/1</div>
    </div>

    <script>
        // Function to get URL parameters
        function getUrlParameter(name) {
            name = name.replace(/[\[\]]/g, '\\$&');
            var regex = new RegExp('[?&]' + name + '(=([^&#]*)|&|#|$)'),
                results = regex.exec(window.location.href);
            if (!results) return null;
            if (!results[2]) return '';
            return decodeURIComponent(results[2].replace(/\+/g, ' '));
        }

        // Update editable fields from URL parameters
        document.addEventListener('DOMContentLoaded', function() {
            // Get parameters from URL
            var phong = getUrlParameter('phong');
            var nam = getUrlParameter('nam');
            var nhietDo = getUrlParameter('nhietDo');
            var doAm = getUrlParameter('doAm');
            var benhVien = getUrlParameter('benhVien');
            var khoa = getUrlParameter('khoa');

            // Update fields if parameters exist
            if (phong) document.getElementById('roomNumber').textContent = phong;
            if (nam) document.getElementById('year').textContent = 'Năm: ' + nam;
            if (nhietDo) document.getElementById('tempRange').textContent = nhietDo;
            if (doAm) document.getElementById('humidityRange').textContent = doAm;
            if (benhVien) document.getElementById('hospital').textContent = benhVien;
            if (khoa) document.getElementById('department').textContent = khoa;
        });
    </script>
</body>
</html>
