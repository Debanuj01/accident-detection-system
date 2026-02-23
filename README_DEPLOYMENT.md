# 🚀 Deployment Guide - Free Options

## Option 1: Streamlit Cloud (Recommended - FREE)

### Steps:
1. **Push to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

2. **Deploy on Streamlit Cloud:**
   - Go to [share.streamlit.io](https://share.streamlit.io)
   - Sign in with GitHub
   - Click "New app"
   - Select your repository
   - Set main file path: `app.py`
   - Click "Deploy"

3. **Your app will be live at:** `https://YOUR_APP.streamlit.app`

### Important Notes:
- Model file `best.pt` must be < 100MB (GitHub limit)
- If larger, use Git LFS or host model separately
- Free tier: 1GB RAM, limited resources

---

## Option 2: Hugging Face Spaces (FREE)

### Steps:
1. **Create Space:**
   - Go to [huggingface.co/spaces](https://huggingface.co/spaces)
   - Click "Create new Space"
   - Choose "Streamlit" as SDK
   - Name your space

2. **Upload Files:**
   ```bash
   git clone https://huggingface.co/spaces/YOUR_USERNAME/YOUR_SPACE
   cd YOUR_SPACE
   # Copy app.py, requirements.txt, best.pt, coco1.txt
   git add .
   git commit -m "Deploy accident detection"
   git push
   ```

3. **Your app will be at:** `https://huggingface.co/spaces/YOUR_USERNAME/YOUR_SPACE`

### Advantages:
- Better GPU support (optional)
- No file size limits
- Community visibility

---

## Option 3: Railway (FREE with limits)

### Steps:
1. **Install Railway CLI:**
   ```bash
   npm i -g @railway/cli
   railway login
   ```

2. **Deploy:**
   ```bash
   railway init
   railway up
   ```

3. **Add Procfile:**
   ```
   web: streamlit run app.py --server.port=$PORT
   ```

---

## Option 4: Render (FREE)

### Steps:
1. **Create Web Service:**
   - Go to [render.com](https://render.com)
   - Connect GitHub repo
   - Select "Web Service"

2. **Configuration:**
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `streamlit run app.py --server.port=$PORT --server.address=0.0.0.0`

---

## Option 5: Package as Desktop App (Distribution)

### Using PyInstaller:
```bash
pip install pyinstaller
pyinstaller --onefile --windowed --add-data "best.pt;." --add-data "coco1.txt;." main.py
```

Your executable will be in `dist/` folder.

### Using Auto-PY-to-EXE (GUI):
```bash
pip install auto-py-to-exe
auto-py-to-exe
```

---

## 📦 Pre-Deployment Checklist

- [ ] Ensure `best.pt` model file is included
- [ ] Verify `coco1.txt` class list exists
- [ ] Test locally: `streamlit run app.py`
- [ ] Check requirements.txt is complete
- [ ] Remove sensitive data (API keys, tokens)
- [ ] Add .gitignore for large files
- [ ] Test with different confidence thresholds

---

## 🔧 Environment Variables (if using notifications)

For Streamlit Cloud, add in Settings > Secrets:
```toml
TWILIO_ACCOUNT_SID = "your_sid"
TWILIO_AUTH_TOKEN = "your_token"
TWILIO_PHONE = "+1234567890"
RECIPIENT_PHONE = "+1234567890"
```

Access in code:
```python
import streamlit as st
twilio_sid = st.secrets["TWILIO_ACCOUNT_SID"]
```

---

## 💡 Tips for Free Deployment

1. **Optimize Model:** Use lighter YOLO models (yolov8n.pt) for faster inference
2. **Resource Limits:** Free tiers have CPU/memory limits - optimize code
3. **File Size:** Keep total repo < 100MB for GitHub, or use Git LFS
4. **Cold Starts:** Free services may sleep - first load will be slow
5. **Monitoring:** Add error tracking with Sentry (free tier)

---

## 🎯 Recommended: Streamlit Cloud

**Best for this project because:**
- ✅ Easy deployment (click-based)
- ✅ Auto-updates from GitHub
- ✅ Free HTTPS
- ✅ Built for ML/CV apps
- ✅ Share with link instantly

**Start here:** Run `streamlit run app.py` locally first!
