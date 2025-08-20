# AutoReel Maker - Hostinger Deployment Guide

## Step-by-Step Hostinger Deployment

### Prerequisites
- Hostinger hosting account with Node.js support
- Domain configured in Hostinger
- OpenAI API key

### Step 1: Upload Files to Hostinger

1. **Download the deployment zip file** from this Replit project
2. **Log into Hostinger hPanel**
3. **Go to File Manager**
4. **Navigate to public_html folder** (or your domain's folder)
5. **Upload the zip file** and extract it
6. **Move all files** from the extracted folder to your domain root

### Step 2: Configure Environment Variables

1. **Create .env file** in your domain root:
```
OPENAI_API_KEY=your_openai_api_key_here
NODE_ENV=production
PORT=3000
```

2. **In Hostinger hPanel**, go to **Advanced → Node.js**
3. **Select your domain**
4. **Set the startup file** to: `server/index.js`
5. **Add environment variables** in the Node.js app settings

### Step 3: Install Dependencies

1. **In File Manager**, open **Terminal** (if available)
2. **Navigate to your domain folder**:
   ```bash
   cd public_html
   ```
3. **Install dependencies**:
   ```bash
   npm install --production
   ```

### Step 4: Build the Application

```bash
npm run build
```

### Step 5: Configure Node.js App

1. **In hPanel**, go to **Advanced → Node.js**
2. **Create new Node.js app**:
   - **Node.js version**: 18.x or latest
   - **Application root**: your domain folder
   - **Application startup file**: `dist/server/index.js`
   - **Application URL**: your domain

### Step 6: Set up File Permissions

```bash
chmod 755 uploads
chmod 755 clips
chmod 755 dist
```

### Step 7: Start the Application

1. **In Node.js app settings**, click **Start/Restart**
2. **Monitor logs** for any errors
3. **Visit your domain** to test

## Important Notes for Hostinger

### Limitations
- **No FFmpeg**: Hostinger shared hosting doesn't support FFmpeg
- **Memory limits**: Shared hosting has memory restrictions
- **File upload size**: Limited by hosting plan

### Workarounds
1. **Use a VPS instead** of shared hosting for full functionality
2. **Consider Hostinger VPS** for FFmpeg support
3. **Use external video processing service** as fallback

### File Structure on Hostinger
```
public_html/
├── dist/               # Built application
├── uploads/           # Upload directory
├── clips/             # Generated clips
├── .env              # Environment variables
└── package.json      # Dependencies
```

### Troubleshooting

**If the app doesn't start:**
1. Check Node.js logs in hPanel
2. Verify environment variables
3. Ensure all dependencies installed
4. Check file permissions

**If uploads fail:**
1. Verify uploads folder exists and writable
2. Check file size limits in hosting plan
3. Review error logs

**For video processing issues:**
1. FFmpeg not available on shared hosting
2. Consider upgrading to VPS
3. Use external processing service

### Performance Optimization

1. **Enable gzip compression** in .htaccess
2. **Use CDN** for static assets
3. **Optimize images** and reduce file sizes
4. **Monitor resource usage** in hPanel

### Security Recommendations

1. **Use HTTPS** (enable in hPanel)
2. **Set strong passwords**
3. **Regular backups**
4. **Keep dependencies updated**

## Alternative: Hostinger VPS

For full functionality with FFmpeg:

1. **Order Hostinger VPS**
2. **Install Node.js and FFmpeg**
3. **Use Docker deployment** from the main guide
4. **Configure reverse proxy** (Nginx)

This provides complete video processing capabilities without shared hosting limitations.