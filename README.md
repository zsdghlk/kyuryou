
# Salary Calculator / 給料計算ツール

**A simple and convenient web app to calculate and save monthly salary in JPY or USD.**  
**シンプルで便利！月ごとの給与を日本円／ドルのどちらでも計算・保存できる Web アプリケーション**

---

## 📌 Overview / 概要

- Calculate monthly salary based on **working days**, **hours per day**, **hourly wage**, and **extra payments**  
- Choose between **JPY** and **USD**  
- Save results per month and get **annual totals**  
- Export as **CSV** or **Print/PDF**  
- UI available in **Japanese** and **English**  

---

- 月ごとの「勤務日数」「勤務時間」「時給」「追加支給」を指定して給与を計算  
- 通貨を **日本円 (JPY)** と **米ドル (USD)** から選択可能  
- 各月のデータを保存し、年間合計を自動計算  
- CSV 出力や印刷（PDF 保存）に対応  
- 日本語・英語の UI 切替対応  

🔗 Demo: [https://zsdghlk.github.io/kyuryou/](https://zsdghlk.github.io/kyuryou/)

---

## ✨ Features / 主な機能

- **Independent salary settings per currency**  
  Hourly wage and extra steps are managed separately for JPY and USD.  

- **Save & edit monthly data**  
  Store calculated salaries per month and adjust later if needed.  

- **Annual total calculation**  
  Automatically calculates yearly totals from saved months.  

- **CSV export / Print PDF**  
  Export salary data for reporting or printing.  

- **Multi-language support**  
  Switch UI between Japanese and English easily.  

---

- **通貨ごとに独立した給与設定**  
  JPY と USD の「時給」「追加金額ステップ」をそれぞれ設定可能。  

- **月別データの保存・編集**  
  各月に金額を保存し、編集や確認が可能。  

- **年間合計の自動計算**  
  保存した月の合計を自動で算出。  

- **CSV ダウンロード / PDF 印刷**  
  データをエクスポート可能。  

- **多言語対応**  
  日本語と英語で UI 切替が可能。  

---

## 🖥️ Usage / 使い方

1. Select **Language** and **Currency**  
2. Set the **Hourly Wage** for JPY / USD  
3. Enter working **days** and **hours per day**  
4. Adjust **extra payments** with + / − buttons  
5. Click **Save this amount** to record monthly data  
6. View or edit **annual total**  
7. Export as **CSV** or **Print/PDF**  

---

1. 「言語」と「通貨」を選択  
2. 「時給」を JPY / USD で設定  
3. 勤務日数と勤務時間を入力  
4. 追加支給があればステップで調整（＋／−）  
5. 「この金額を保存」で月ごとに保存  
6. 年間合計を確認、必要に応じて編集  
7. CSV 出力または PDF 印刷が可能  

---

## 🔧 Implementation Notes / 実装ポイント

- Data persistence using **localStorage**  
- Independent handling of JPY and USD (no exchange rate needed)  
- Dynamic UI rendering depending on the selected currency  
- Backward compatibility with older data storage format  

---

- `localStorage` によるデータ保存でブラウザ間の持続性を確保  
- 通貨ごとに独立した値を保持（レート換算不要）  
- UI は選択中の通貨に応じて動的に切替  
- 旧バージョンからのデータマイグレーションに対応  

---

## 📂 File Structure / ファイル構成
├── index.html # Main application (HTML + CSS + JS in one file)
├── README.md # Project documentation

---

## 📜 License / ライセンス

This project is licensed under the **MIT License**.  
Feel free to use, modify, and distribute.  

このプロジェクトは **MIT License** で公開されています。  
自由に利用・改変・配布可能です。  

