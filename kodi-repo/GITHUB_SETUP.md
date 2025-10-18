# HBO Max Skin Repository - GitHub Setup Guide

## ✅ Repository Created!

Your Kodi repository is ready. Now let's put it on GitHub so you can install it on your streaming box.

## Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `kodi-repo`
3. Description: `HBO Max Skin Repository for Kodi`
4. Make it **Public** (so your streaming box can access it)
5. Don't add README, .gitignore, or license
6. Click "Create repository"

## Step 2: Upload to GitHub

### Option A: Using GitHub Website (Easiest)

1. On your new repo page, click "uploading an existing file"
2. Drag and drop these files/folders:
   - `addons.xml`
   - `addons.xml.md5`
   - `zips/` (entire folder)
   - `repository.hbomax/` folder

3. Commit changes

### Option B: Using Git Command Line

```bash
cd /Users/michaelhernandez/kodi-repo

# Initialize git
git init

# Add files
git add .

# Commit
git commit -m "Initial HBO Max skin repository"

# Add your GitHub repo (replace YOURUSERNAME)
git remote add origin https://github.com/YOURUSERNAME/kodi-repo.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 3: Update Repository URLs

After uploading, you need to update the URLs in your files:

### Update `repository.hbomax/addon.xml`:

Replace `YOURUSERNAME` with your actual GitHub username:

```xml
<info compressed="false">https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/addons.xml</info>
<checksum>https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/addons.xml.md5</checksum>
<datadir zip="true">https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/zips/</datadir>
```

### Update `addons.xml`:

Same thing - replace `YOURUSERNAME` in the repository addon section.

### Re-create the repository zip:

```bash
cd /Users/michaelhernandez/kodi-repo/repository.hbomax
zip -r ../zips/repository.hbomax/repository.hbomax-1.0.0.zip .
```

### Push the changes:

```bash
cd /Users/michaelhernandez/kodi-repo
git add .
git commit -m "Update URLs with GitHub username"
git push
```

## Step 4: Install on Your Streaming Box

### Method 1: Direct Repository Install (Easiest)

1. On your streaming box, open Kodi
2. Go to: **Settings > File Manager**
3. Click "Add source"
4. Enter this URL (replace YOURUSERNAME):
   ```
   https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/zips/repository.hbomax/
   ```
5. Name it: `HBO Max Repo`
6. Click OK

7. Go to: **Settings > Add-ons > Install from zip file**
8. Select "HBO Max Repo"
9. Select `repository.hbomax-1.0.0.zip`
10. Wait for "Add-on installed" notification

11. Go to: **Settings > Add-ons > Install from repository**
12. Select "HBO Max Repository"
13. Go to "Look and feel" > "Skin"
14. Select "HBO Max"
15. Click Install

16. Activate skin:
    **Settings > Interface > Skin > HBO Max**

### Method 2: Download Zip Manually

If Method 1 doesn't work:

1. On a computer, download:
   ```
   https://github.com/YOURUSERNAME/kodi-repo/raw/main/zips/repository.hbomax/repository.hbomax-1.0.0.zip
   ```

2. Transfer to streaming box via:
   - USB drive
   - Network share
   - Cloud storage app

3. In Kodi:
   - Settings > Add-ons > Install from zip file
   - Browse to the zip file
   - Install

4. Then install skin from repository (steps 11-16 above)

## Troubleshooting

### "Unable to connect"
- Check GitHub repo is public
- Check URLs have correct username
- Check internet connection on streaming box

### "Dependency not met"
- Install TMDbHelper first (optional but recommended)
- Go to: Settings > Add-ons > Install from repository > Kodi Add-on repository > Program add-ons > TMDb Helper

### "Skin won't load"
- Make sure you have content in your video addon
- Check Kodi version (needs 19+)

## Repository Structure

```
kodi-repo/
├── addons.xml                          # Master addon list
├── addons.xml.md5                      # Checksum
├── repository.hbomax/
│   └── addon.xml                       # Repository addon definition
└── zips/
    ├── repository.hbomax/
    │   ├── addon.xml                   # Copy of repo addon.xml
    │   └── repository.hbomax-1.0.0.zip # Repository installer
    └── skin.hbomax/
        ├── addon.xml                   # Copy of skin addon.xml
        └── skin.hbomax-1.0.0.zip      # Your skin!
```

## URLs You'll Need

Replace `YOURUSERNAME` with your GitHub username:

**Repository installer:**
```
https://github.com/YOURUSERNAME/kodi-repo/raw/main/zips/repository.hbomax/repository.hbomax-1.0.0.zip
```

**For file manager source:**
```
https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/zips/repository.hbomax/
```

**Addons.xml:**
```
https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/addons.xml
```

## Quick Install Command for Streaming Box

Tell people to:

1. Add source: `https://raw.githubusercontent.com/YOURUSERNAME/kodi-repo/main/zips/repository.hbomax/`
2. Install from zip: `repository.hbomax-1.0.0.zip`
3. Install from repository: HBO Max Repository > Skin > HBO Max
4. Activate: Settings > Interface > Skin > HBO Max

Done! 🎉
