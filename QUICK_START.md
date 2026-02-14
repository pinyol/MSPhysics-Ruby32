# 🚀 Quick Start Checklist

## GitHub Actions Setup - 30 Minute Version

### ✅ Before You Start

- [ ] Have a GitHub account (https://github.com/signup)
- [ ] Have this folder ready to upload

### ✅ Step 1: Create Repository (5 minutes)

1. Go to https://github.com/new
2. Name: `MSPhysics-Ruby32`
3. Public or Private (your choice)
4. ✅ Check "Add README"
5. Click "Create repository"

### ✅ Step 2: Upload Files (10 minutes)

**Using GitHub Web Interface:**

1. Click "Add file" → "Upload files"  
2. Drag and drop this ENTIRE folder
3. Click "Commit changes"

**OR using Git command line:**

```bash
cd /path/to/this/folder
git init
git add .
git commit -m "Initial commit - MSPhysics Ruby 3.2"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/MSPhysics-Ruby32.git
git push -u origin main
```

### ✅ Step 3: Run Build (5 minutes)

1. Go to your repository on GitHub
2. Click "Actions" tab
3. Click "Build MSPhysics C++ Extensions"
4. Click "Run workflow" → "Run workflow"

**The build starts automatically!**

### ✅ Step 4: Wait for Build (10-20 minutes)

- Watch the progress in Actions tab
- Three jobs will run (Windows, macOS, Package)
- All should turn green ✅

### ✅ Step 5: Download Plugin (2 minutes)

1. Click on the completed workflow (green checkmark)
2. Scroll to "Artifacts"
3. Download **`MSPhysics-v1.1.0-Ruby3.2`**
4. This is your complete .rbz file!

### ✅ Step 6: Install in SketchUp (3 minutes)

1. Open SketchUp 2024
2. Window → Extension Manager
3. Install Extension
4. Select the .rbz file
5. Restart SketchUp

### ✅ Step 7: Test It! (2 minutes)

1. Create a cube
2. Right-click → MSPhysics → Make Dynamic
3. Click Play button
4. Cube falls = SUCCESS! 🎉

---

## 🆘 If Something Goes Wrong

### Build Fails?

1. Click on the failed job
2. Read the error message
3. Check GITHUB_ACTIONS_SETUP_GUIDE.md troubleshooting section

### Plugin Won't Load?

1. Check Ruby Console (Window → Ruby Console)
2. Look for error messages
3. Verify SketchUp version is 2024+

### Still Stuck?

- Check the detailed guide: GITHUB_ACTIONS_SETUP_GUIDE.md
- Open an issue on GitHub
- Ask in SketchUp forums

---

## 💯 Success Criteria

- ✅ Repository created
- ✅ All files uploaded
- ✅ Build completed (green checkmarks)
- ✅ .rbz downloaded
- ✅ Installed in SketchUp
- ✅ Physics simulation works

**If all boxes checked: YOU DID IT! 🎉**

---

## ⏱️ Total Time

**Setup:** ~30 minutes (one time)  
**Future builds:** Just push code, builds automatically!

---

**Questions?** See GITHUB_ACTIONS_SETUP_GUIDE.md for detailed instructions.
