# Вывод изображений и текстовое поле
<style>
    /* --- Ümumi Stillər --- */
    body {
        font-family: Tahoma, sans-serif;
        background-color: #ffffff;
        margin: 0;
        padding: 0;
    }

    /* --- Giriş Forması Stilləri --- */
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

    /* --- Nəticə Vərəqəsi Stilləri --- */
    #result-page {
        display: none; /* Başlanğıcda gizli saxlayırıq */
        padding: 20px;
    }

    .page-container {
        width: 900px;
        margin: 0 auto;
        background-color: white;
        padding: 30px;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    /* Başlıq və Loqo */
    .header-section {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        margin-bottom: 20px;
    }

    .result-title-box {
        background-color: #f0f0f0;
        padding: 8px;
        font-size: 16px;
        font-weight: bold;
        text-align: center;
        border: 1px solid #ccc;
        width: 50%;
    }

    .logo-box {
        text-align: center;
        font-weight: bold;
        line-height: 1.1;
    }

    .logo-box p {
        margin: 0;
        font-size: 14px;
    }

    /* Şagird Məlumat Cədvəli */
    .info-table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 20px;
    }

    .info-table td {
        border: 1px solid #000;
        padding: 5px 10px;
        font-size: 12px;
    }

    .info-table .label {
        background-color: #f0f0f0;
        font-weight: bold;
        width: 15%;
    }

    /* Fənn Hissəsi */
    .subject-box {
        margin-bottom: 20px;
        border: 1px solid #ccc;
        padding: 5px;
    }

    .subject-name {
        background-color: #f0f0f0;
        padding: 5px;
        font-weight: bold;
        font-size: 14px;
        margin-bottom: 5px;
        border-bottom: 1px solid #ccc;
    }

    /* Bal Cədvəli (Sual/Cavab) */
    .score-table {
        width: 100%;
        border-collapse: collapse;
        text-align: center;
        font-size: 10px;
        margin-bottom: 5px;
    }

    .score-table td {
        border: 1px solid #ccc;
        padding: 3px;
        white-space: nowrap;
    }

    .score-table thead td {
        background-color: #e0e0e0;
        font-weight: bold;
    }

    .score-table .correct {
        color: green;
        font-weight: bold;
    }

    .score-table .wrong {
        color: red;
        font-weight: bold;
    }

    /* Fənnin Ümumi Göstəriciləri Cədvəli */
    .summary-table {
        width: 100%;
        border-collapse: collapse;
        font-size: 12px;
    }

    .summary-table td {
        border: 1px solid #000;
        padding: 5px;
        font-weight: bold;
        text-align: center;
    }

    .summary-table .highlight-value {
        background-color: #f0f0f0;
    }
</style>
