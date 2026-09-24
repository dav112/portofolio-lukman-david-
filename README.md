# AI Crypto Futures Bot — PAPER default, LIVE optional (Binance Futures)

Production-oriented, 5 models + Meta, walk-forward, LIVE safety-guarded.

## Quick Start PAPER (default aman)
```bash
cd ai-crypto-trading-bot
python3.10 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env  # TRADING_MODE=PAPER
uvicorn api.main:app --host 127.0.0.1 --port 8000  # /docs
python3 -m http.server 3001 --directory dashboard  # http://127.0.0.1:3001/index.html
pytest -q  # 46 passed
```

## TESTNET
```env
TRADING_MODE=TESTNET
BINANCE_API_KEY=...
BINANCE_API_SECRET=...
BINANCE_TESTNET=true
```
`POST /exchange/test-connection` → CONNECTED.

## LIVE_DRY_RUN (production data tanpa order)
```env
TRADING_MODE=LIVE
BINANCE_API_KEY=...
BINANCE_API_SECRET=...
LIVE_DRY_RUN=true
```
Run `python -c "from bot.execution.executor import execute"` → `dry_run` intended.

## LIVE (real money) — butuh arm
```env
TRADING_MODE=LIVE
BINANCE_API_KEY=...
BINANCE_API_SECRET=...
BINANCE_TESTNET=false
LIVE_DRY_RUN=false
DASHBOARD_TOKEN=secret123
MAX_LEVERAGE=5 RISK_PER_TRADE=0.01 etc
```
Checklist: `GET /trading/mode` `GET /exchange/permissions` (key ****ABCD, withdrawal false) `GET /health`.
Arm: `POST /trading/arm?confirmation=ENABLE%20LIVE%20TRADING` (Bearer DASHBOARD_TOKEN jika set).
Emergency: `POST /bot/emergency-stop` → cancel all, live_state EMERGENCY, manual re-arm.

## Docs
docs/LIVE_TRADING_AUDIT.md, BINANCE_SETUP.md, LIVE_TRADING.md, SECURITY.md, ORDER_EXECUTION.md, FAILURE_RECOVERY.md
# Porto-Lukman-David
# portofolio-lukman-david-
