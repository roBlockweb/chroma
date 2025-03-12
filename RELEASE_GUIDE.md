
# ChromaTrack Pro: Release Guide

This guide provides the exact steps to release ChromaTrack Pro to GitHub and the Google Play Store.

## Part 1: GitHub Release

### Step 1: Update Version
1. Update version in `package.json`:
   ```bash
   npm version 1.0.0
   ```
2. Update Android version in `android/app/build.gradle`:
   ```
   versionCode 1
   versionName "1.0.0"
   ```

### Step 2: Build for Production
1. Build web version:
   ```bash
   npm run build
   ```
2. Build Android version:
   ```bash
   cd android
   ./gradlew assembleRelease
   ```

### Step 3: Create GitHub Release
1. Create a git tag:
   ```bash
   git tag -a v1.0.0 -m "Version 1.0.0"
   ```
2. Push the code and tags:
   ```bash
   git push origin main --tags
   ```
3. Go to GitHub repository → Releases → Create a new release
4. Select the tag v1.0.0
5. Title: "ChromaTrack Pro v1.0.0"
6. Description: Include key features and changes
7. Upload APK from `android/app/build/outputs/apk/release/app-release.apk`
8. Publish the release

## Part 2: Google Play Store Release

### Step 1: Google Play Console Setup
1. Go to [play.google.com/apps/publish](https://play.google.com/apps/publish)
2. Click "Create app"
3. Enter app details:
   - Name: ChromaTrack Pro
   - Default language: English (United States)
   - App or game: App
   - Free or paid: Free (with in-app purchases)
   - Click "Create app"

### Step 2: Store Listing
1. Store listing section:
   - Add short description (80 chars max)
   - Add full description
   - Add screenshots (min 3)
   - Add feature graphic (1024x500)
   - Add app icon (512x512)
   - Add privacy policy URL
2. Click "Save draft"

### Step 3: Content Rating
1. Go to "Content rating" section
2. Complete the rating questionnaire
3. Submit for rating

### Step 4: Pricing & Distribution
1. Choose countries for distribution
2. Set app as free
3. Check "Contains ads"
4. Check "Allow in-app purchases"
5. Agree to all compliance declarations
6. Click "Save draft"

### Step 5: App Release
1. Go to "Production" track
2. Click "Create release"
3. Upload the signed APK
4. Add release notes
5. Click "Review release"
6. Start rollout (can start with 10% for testing)

### Step 6: In-App Products
1. Go to "In-app products" section
2. Click "Create managed product"
3. Product ID: premium_upgrade
4. Name: Premium Upgrade
5. Description: Remove ads and unlock all premium features
6. Price: $9.99
7. Click "Active" and save

### Step 7: Submit for Review
1. Go back to App releases
2. Verify all requirements are met
3. Click "Start rollout to production"
4. Wait for Google's review (1-3 days typically)

## Troubleshooting

### GitHub Issues
- If push fails, try `git pull --rebase` first
- If tag already exists: `git tag -d v1.0.0` then recreate

### Google Play Issues
- Rejected for policy violation: Address the specific issues mentioned in the rejection email
- APK signing issues: Verify the keystore is correct and signing configuration matches
- Rating issue: Ensure app content matches declared content rating

## Post-Release
1. Monitor ratings and reviews
2. Check crash reports
3. Track user acquisition
4. Collect user feedback for next version
