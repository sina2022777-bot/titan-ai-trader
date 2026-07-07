# Titan AI Trader v1.1 Telegram

ربات تحلیل تکنیکال کریپتو با کنترل تلگرام و حالت امن Paper Trading.

## مهم
- پیش‌فرض: `LIVE_TRADING=false` و `SANDBOX=true`
- این نسخه برای تست است، نه سود تضمینی.
- تا چند هفته اول API واقعی پول‌دار وصل نکن.

## دستورهای تلگرام
- `/start` شروع
- `/status` وضعیت ربات
- `/scan` اسکن بازار و نمایش سیگنال
- `/help` راهنما

## دیپلوی رایگان روی Render
1. فایل ZIP را در GitHub آپلود کن یا پروژه را از ZIP در ریپازیتوری بگذار.
2. وارد Render.com شو و New → Web Service را بزن.
3. ریپازیتوری را وصل کن.
4. Build Command:
   `pip install -r requirements.txt`
5. Start Command:
   `uvicorn titan_ai_trader.telegram_app:app --host 0.0.0.0 --port $PORT`
6. Environment Variables را وارد کن:
   - `TELEGRAM_BOT_TOKEN` توکن ربات از BotFather
   - `TELEGRAM_ALLOWED_USER_ID` آیدی عددی تلگرام خودت
   - `LIVE_TRADING=false`
   - `SANDBOX=true`
   - `EXCHANGE=bybit`
7. بعد از Deploy، آدرس سرویس Render را بردار. مثل:
   `https://titan-ai-trader.onrender.com`
8. در مرورگر باز کن:
   `https://YOUR-RENDER-URL/set-webhook?url=https://YOUR-RENDER-URL`
9. حالا در تلگرام به رباتت پیام بده: `/start`

## اجرای محلی برای تست
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
uvicorn titan_ai_trader.telegram_app:app --reload
```

## ساخت BotFather
در تلگرام به `@BotFather` برو:
1. `/newbot`
2. اسم بده
3. username بده که آخرش bot باشد
4. توکن را در Render داخل `TELEGRAM_BOT_TOKEN` قرار بده.

## گرفتن Telegram User ID
به ربات `@userinfobot` پیام بده و عدد ID را در `TELEGRAM_ALLOWED_USER_ID` قرار بده.
