# missiya.neticeler
<!DOCTYPE html>
<html lang="az">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Missiya İmtahan Nəticəsi Sistemi</title>

    <style>
        /* --- Ümumi və Səhifə Stilləri --- */
        body {
            font-family: Tahoma, sans-serif;
            background-color: #f7f7f7; /* Ümumi arxa fon */
            margin: 0;
            padding: 0;
        }

        /* --- 1. Giriş Forması Stilləri --- */
        #input-page {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
        }

        #input-page h1 {
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        #jobNumberInput {
            padding: 10px 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
            width: 250px;
            margin-right: 10px;
        }

        .blue-button {
            background-color: #007aff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .blue-button:hover {
            background-color: #005bb5;
        }

        /* --- 2. Nəticə Vərəqəsi (Result Page) Stilləri --- */
        #result-page {
            display: none; /* Başlanğıcda gizli saxlayırıq */
            padding: 20px 0;
        }

        .page-container {
            width: 800px; /* Nəticə vərəqəsinin eni */
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            border: 1px solid #ccc;
        }
        /* Başlıq və Loqo */
        .header-section {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 15px;
        }
        .result-title-box {
            font-size: 16px;
            font-weight: bold;
            color: #333;
            padding-top: 5px; 
        }
        .logo-box {
            text-align: center;
            font-weight: bold;
            line-height: 1.1;
            font-size: 12px;
        }
        .logo-box img {
            max-width: 80px;
            height: auto;
            display: block;
            margin: 0 auto 5px auto;
        }
        .logo-box p {
            margin: 0;
            font-size: 11px;
        }
        /* Şagird Məlumat Cədvəli */
        .info-table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 15px;
            font-size: 12px;
        }
        .info-table td {
            border: 1px solid #000;
            padding: 3px 6px;
        }
        .info-table .label {
            background-color: #e6e6e6; 
            font-weight: bold;
            width: 15%; 
        }
        /* Fənn Bölmələri */
        .subject-box {
            margin-bottom: 15px;
        }
        .subject-name-row {
            background-color: #e6e6e6;
            padding: 3px 6px;
            font-weight: bold;
            font-size: 13px;
            border: 1px solid #000;
            margin-bottom: -1px; 
        }
        /* Ümumi Göstəricilər Cədvəli */
        .summary-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 11px;
            margin-bottom: 1px;
        }
        .summary-table td {
            border: 1px solid #000;
            padding: 4px;
            font-weight: bold;
            text-align: center;
        }
        .summary-table .highlight-label {
            background-color: #f0f0f0;
            width: 8%; 
        }
        /* Bal Cədvəli (Sual/Cavab) */
        .score-table {
            width: 100%;
            border-collapse: collapse;
            text-align: center;
            font-size: 9px;
            table-layout: fixed; 
        }
        .score-table td {
            border: 1px solid #000;
            padding: 2px 0;
            white-space: nowrap;
        }
        .score-table .q-label {
             background-color: #e6e6e6;
             font-weight: bold;
        }
        .q-small { width: 2.2%; }
        .q-large { width: 6.5%; }
        .c_bold { font-weight: bold; }
        .c_no_answer { color: #888; }
    </style>
</head>
<body>

    <div id="input-page">
        <div class="input-container">
            <h1>İş nömrəsi</h1>
            <input type="text" id="jobNumberInput" placeholder="bura daxil edin" required>
            <button type="button" class="blue-button" onclick="checkJobNumber()">Nəticəni göstər</button>
        </div>
    </div>

    <div id="result-page">
        <div class="page-container">
            
            <div class="header-section">
                <div class="result-title-box">
                    İMTAHAN NƏTİCƏ VƏRƏQƏSİ
                </div>
                <div class="logo-box">
                    <img src="missiya_logo.png" alt="MİSSİYA TƏHSİL ŞİRKƏTİ Loqosu"> 
                    <p>MİSSİYA</p>
                    <p>TƏHSİL ŞİRKƏTİ</p>
                </div>
            </div>

            <table class="info-table">
                <tr><td class="label">İmtahan Bloku</td><td class="value"></td><td class="label">Adı</td><td class="value">ABDULLAZADƏ</td></tr>
                <tr><td class="label">Keçirilmə tarixi</td><td class="value">2025-11-30</td><td class="label">Soyadı</td><td class="value">ABDULLAZADƏ</td></tr>
                <tr><td class="label">İş nömrəsi</td><td class="value">54979</td><td class="label">Sinif</td><td class="value">10</td></tr>
                <tr><td class="label">Bölmə</td><td class="value">Azərbaycan</td><td class="label">Variant</td><td class="value">A</td></tr>
                <tr><td class="label">Blok</td><td class="value">4 #</td><td class="label">Bal</td><td class="value">259.94</td></tr>
                <tr><td class="label">Faiz</td><td class="value">65%</td><td class="label">Doğru</td><td class="value">56.0</td></tr>
                <tr><td class="label">Yanlış</td><td class="value">26.0</td><td class="label">Cavabsız</td><td class="value">5.0</td></tr>
            </table>

            <div class="subject-box">
                <div class="subject-name-row">Biologiya (1-30)</div>
                <table class="summary-table">
                    <tr>
                        <td class="highlight-label">Bal</td><td style="width:17%">93.18</td>
                        <td class="highlight-label">Faiz</td><td style="width:17%">66.67%</td>
                        <td class="highlight-label">Doğru</td><td style="width:15%">20.0</td>
                        <td class="highlight-label">Yanlış</td><td style="width:15%">10.0</td>
                        <td class="highlight-label">Cavabsız</td><td style="width:15%">0.0</td>
                    </tr>
                </table>
                <table class="score-table">
                    <colgroup>
                        <col class="q-small" span="22">
                        <col class="q-large"><col class="q-small"><col class="q-large"><col class="q-small"><col class="q-large"><col class="q-small"><col class="q-small"><col class="q-small">
                    </colgroup>
                    <tr><td class="q-label">Sual N.</td>
                        <td colspan="22">1 &nbsp; 2 &nbsp; 3 &nbsp; 4 &nbsp; 5 &nbsp; 6 &nbsp; 7 &nbsp; 8 &nbsp; 9 &nbsp; 10 &nbsp; 11 &nbsp; 12 &nbsp; 13 &nbsp; 14 &nbsp; 15 &nbsp; 16 &nbsp; 17 &nbsp; 18 &nbsp; 19 &nbsp; 20 &nbsp; 21 &nbsp; 22</td>
                        <td class="q-label">23</td><td class="q-label">24</td><td class="q-label">25</td><td class="q-label">26</td><td class="q-label">27</td><td class="q-label">28</td><td class="q-label">29</td><td class="q-label">30</td>
                    </tr>
                    <tr><td class="q-label">Doğrular</td>
                        <td>C</td><td>E</td><td>A</td><td>E</td><td>D</td><td>D</td><td>C</td><td>E</td><td>A</td><td>C</td><td>B</td><td>A</td><td>C</td><td>D</td><td>B</td><td>E</td><td>C</td><td>D</td><td>E</td><td>B</td><td>A</td><td>C</td>
                        <td>13S####</td><td>82###</td><td>14####</td><td>8#</td><td>182DE3AC</td><td>8#</td><td>1/2</td><td>1/2</td>
                    </tr>
                     <tr><td class="q-label">Cavablar</td>
                        <td class="c_bold">C</td><td class="c_bold">B</td><td class="c_bold">A</td><td class="c_bold">E</td><td class="c_bold">D</td><td class="c_bold">D</td><td class="c_bold">A</td><td class="c_bold">A</td><td class="c_bold">A</td><td class="c_bold">C</td><td class="c_bold">E</td><td class="c_bold">E</td><td class="c_bold">C</td><td class="c_bold">D</td><td class="c_bold">E</td><td class="c_bold">E</td><td class="c_bold">C</td><td class="c_bold">A</td><td class="c_bold">E</td><td class="c_bold">D</td><td class="c_bold">A</td><td class="c_bold">B</td>
                        <td class="c_bold">13S####</td><td class="c_bold">82###</td><td class="c_bold">14####</td><td class="c_bold">8#</td><td class="c_bold">182DE3AC</td><td class="c_bold">12#</td><td class="c_bold">1/2</td><td class="c_bold">1</td>
                    </tr>
                     <tr><td class="q-label">Nəticələr</td>
                        <td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td>
                        <td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td>
                    </tr>
                </table>
            </div>
            
            <div class="subject-box">
                <div class="subject-name-row">Kimya (31-60)</div>
                <table class="summary-table">
                    <tr>
                        <td class="highlight-label">Bal</td><td>102.27</td>
                        <td class="highlight-label">Faiz</td><td>73.33%</td>
                        <td class="highlight-label">Doğru</td><td style="width:15%">22.0</td>
                        <td class="highlight-label">Yanlış</td><td style="width:15%">8.0</td>
                        <td class="highlight-label">Cavabsız</td><td style="width:15%">0.0</td>
                    </tr>
                </table>
                 <table class="score-table">
                    <colgroup>
                        <col class="q-small" span="22">
                        <col class="q-large"><col class="q-small"><col class="q-large"><col class="q-small"><col class="q-large"><col class="q-small"><col class="q-small"><col class="q-small">
                    </colgroup>
                    <tr><td class="q-label">Sual N.</td>
                        <td colspan="22">31 &nbsp; 32 &nbsp; 33 &nbsp; 34 &nbsp; 35 &nbsp; 36 &nbsp; 37 &nbsp; 38 &nbsp; 39 &nbsp; 40 &nbsp; 41 &nbsp; 42 &nbsp; 43 &nbsp; 44 &nbsp; 45 &nbsp; 46 &nbsp; 47 &nbsp; 48 &nbsp; 49 &nbsp; 50 &nbsp; 51 &nbsp; 52</td>
                        <td class="q-label">53</td><td class="q-label">54</td><td class="q-label">55</td><td class="q-label">56</td><td class="q-label">57</td><td class="q-label">58</td><td class="q-label">59</td><td class="q-label">60</td>
                    </tr>
                    <tr><td class="q-label">Doğrular</td>
                        <td>B</td><td>D</td><td>D</td><td>C</td><td>E</td><td>A</td><td>D</td><td>B</td><td>A</td><td>C</td><td>D</td><td>A</td><td>C</td><td>C</td><td>D</td><td>A</td><td>C</td><td>E</td><td>A</td><td>B</td><td>D</td>
                        <td>82###</td><td>1#</td><td>14####</td><td>1#</td><td>1AD2B3E</td><td>1#</td><td>1</td><td>1/9</td>
                    </tr>
                     <tr><td class="q-label">Cavablar</td>
                        <td class="c_bold">B</td><td class="c_bold">B</td><td class="c_bold">D</td><td class="c_bold">E</td><td class="c_bold">E</td><td class="c_bold">A</td><td class="c_bold">D</td><td class="c_bold">E</td><td class="c_bold">A</td><td class="c_bold">D</td><td class="c_bold">B</td><td class="c_bold">C</td><td class="c_bold">D</td><td class="c_bold">A</td><td class="c_bold">C</td><td class="c_bold">D</td><td class="c_bold">A</td><td class="c_bold">C</td><td class="c_bold">E</td><td class="c_bold">B</td>
                        <td class="c_bold">82###</td><td class="c_bold">8###</td><td class="c_bold">14####</td><td class="c_bold">4###</td><td class="c_bold">1AD2B3E</td><td class="c_bold">1#</td><td class="c_bold">1</td><td class="c_bold">1/9</td>
                    </tr>
                     <tr><td class="q-label">Nəticələr</td>
                        <td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td>
                        <td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td>
                    </tr>
                </table>
            </div>

            <div class="subject-box">
                <div class="subject-name-row">Fizika (61-90)</div>
                <table class="summary-table">
                    <tr>
                        <td class="highlight-label">Bal</td><td>48.48</td>
                        <td class="highlight-label">Faiz</td><td>56.67%</td>
                        <td class="highlight-label">Doğru</td><td>17.0</td>
                        <td class="highlight-label">Yanlış</td><td>8.0</td>
                        <td class="highlight-label">Cavabsız</td><td>5.0</td>
                    </tr>
                </table>
                <table class="score-table">
                    <colgroup>
                        <col class="q-small" span="22">
                        <col class="q-large"><col class="q-small"><col class="q-large"><col class="q-small"><col class="q-small"><col class="q-small">
                    </colgroup>
                    <tr><td class="q-label">Sual N.</td>
                        <td colspan="22">61 &nbsp; 62 &nbsp; 63 &nbsp; 64 &nbsp; 65 &nbsp; 66 &nbsp; 67 &nbsp; 68 &nbsp; 69 &nbsp; 70 &nbsp; 71 &nbsp; 72 &nbsp; 73 &nbsp; 74 &nbsp; 75 &nbsp; 76 &nbsp; 77 &nbsp; 78 &nbsp; 79 &nbsp; 80 &nbsp; 81 &nbsp; 82</td>
                        <td class="q-label">83</td><td class="q-label">84</td><td class="q-label">85</td><td class="q-label">86</td><td class="q-label">87</td><td class="q-label">88</td><td class="q-label">89</td><td class="q-label">90</td>
                    </tr>
                    <tr><td class="q-label">Doğrular</td>
                        <td>D</td><td>C</td><td>B</td><td>C</td><td>D</td><td>E</td><td>A</td><td>B</td><td>A</td><td>B</td><td>C</td><td>D</td><td>E</td><td>A</td><td>D</td><td>B</td><td>D</td><td>F</td><td>A</td><td>B</td><td>D</td><td>B</td>
                        <td>8#</td><td>10####</td><td>5#</td><td>6.2500</td><td>1AD2CE3B</td><td>#</td><td>#</td><td>#</td>
                    </tr>
                     <tr><td class="q-label">Cavablar</td>
                        <td class="c_bold">D</td><td class="c_bold">B</td><td class="c_bold">C</td><td class="c_bold">B</td><td class="c_bold">D</td><td class="c_bold">C</td><td class="c_bold">E</td><td class="c_bold">A</td><td class="c_bold">A</td><td class="c_bold">E</td><td class="c_bold">D</td><td class="c_bold">D</td><td class="c_bold">B</td><td class="c_bold">A</td><td class="c_bold">D</td><td class="c_bold">F</td><td class="c_bold">A</td><td class="c_bold">B</td><td class="c_bold">D</td><td class="c_bold">B</td><td class="c_bold">E</td><td class="c_bold">K</td>
                        <td class="c_no_answer"></td><td class="c_no_answer"></td><td class="c_bold">8###</td><td class="c_bold">12.5#</td><td class="c_no_answer"></td><td class="c_no_answer"></td><td class="c_no_answer"></td><td class="c_no_answer"></td>
                    </tr>
                     <tr><td class="q-label">Nəticələr</td>
                        <td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">+</div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td>
                        <td><div class="c_no_answer"></div></td><td><div class="c_no_answer"></div></td><td><div class="c_bold">-</div></td><td><div class="c_bold">-</div></td><td><div class="c_no_answer"></div></td><td><div class="c_no_answer"></div></td><td><div class="c_no_answer"></div></td><td><div class="c_no_answer"></div></td>
                    </tr>
                </table>
            </div>

        </div>
    </div>

    <script>
        function checkJobNumber() {
            const inputNumber = document.getElementById('jobNumberInput').value.trim();
            const inputPage = document.getElementById('input-page');
            const resultPage = document.getElementById('result-page');

            // JavaScript yalnız "54979" nömrəsini qəbul edir
            if (inputNumber === '54979') {
                // Giriş səhifəsini gizlədir, nəticəni göstərir
                inputPage.style.display = 'none';
                resultPage.style.display = 'block';
                window.scrollTo(0, 0); 

            } else {
                // Başqa nömrə daxil edilərsə yeni xəta mesajı
                alert('Nəticə tapılmadı.');
            }
        }
    </script>
</body>
</html>
