# WiFi接続用QRCode生成
[GitHubPages上で動作してます](https://rururu3.github.io/qr-wifi/)

# qr-wifi テキスト仕様
https://github.com/zxing/zxing/wiki/Barcode-Contents#wi-fi-network-config-android-ios-11

https://nakanishi.dev/posts/wifi_qrcode/

# QRCode Wifi
COPILOTの回答
(QrCodeでのWiFiを扱う仕様を教えて)
```
Wi-Fi ネットワークの設定情報を QR コードにエンコードすることで、**Wi-Fi QR コード**を作成できます。ユーザーはこの QR コードをスキャンして、自動的に Wi-Fi ネットワークに接続できます。以下は Wi-Fi QR コードの作成方法と仕様についての詳細です。

1. **QR コードの作成**:
   - Wi-Fi ネットワークの SSID（ネットワーク名）とパスワードを QR コードにエンコードします。
   - QR コードジェネレーターツールやソフトウェアを使用して、QR コードを作成します。
   - 作成した QR コードは印刷したり画面に表示したりできます。

2. **QR コードの形式**:
   - Wi-Fi QR コードの形式は、ZXing QR デコーダーによって元々考案され、文書化されました。
   - 公式な文書は存在しないため、ZXing の wiki ページに詳細が記載されています¹。
   - 以下は一般的な Wi-Fi QR コードの形式です:
     ```
     WIFI:T:WPA;S:SSID_NAME;P:PASSWORD;;
     ```
     - `T:WPA` は、パスワードベースの認証のいずれかの形式を指します（WPA1 や WPA2 など）。
     - `R:1` は「WPA2/WPA3 トランジションモード無効」を示します（対応するデバイスで理解される場合）。

3. **QR コードのサポート**:
   - 一部の QR コードスキャナーは、すべての形式をサポートしていません。古いアプリケーション（ZXing など）は、WPA3 対応デバイスでも R タグを認識しないことがあります。

Wi-Fi QR コードは、ユーザーが手動で設定を入力する手間を省き、便利な方法でネットワークに接続できるようにします²³。¹⁴⁵

ソース: Bing との会話 2024/5/13
(1) wpa - WiFi QR Code format for WPA2/WPA3 - Super User. https://superuser.com/questions/1752083/wifi-qr-code-format-for-wpa2-wpa3.
(2) What is a WiFi QR code? | SQR. https://docs.sqr.co/guides/creating-a-qr-code/wifi-qr-code/what-is-a-wifi-qr-code.
(3) Wi-Fi configuration in a QR code - cweiske.de. https://cweiske.de/tagebuch/wifi-config-qrcode.htm.
(4) Wi-Fi Easy Connect | Wi-Fi Alliance. https://www.wi-fi.org/discover-wi-fi/wi-fi-easy-connect.
(5) QR Code Standardization | QRcode.com | DENSO WAVE. https://www.qrcode.com/en/about/standards.html.
```

# qrcode.vue
https://www.npmjs.com/package/qrcode.vue

こっちのほうが機能が多いのでこちらを使用しています
https://github.com/scholtz/qrcode-vue3

