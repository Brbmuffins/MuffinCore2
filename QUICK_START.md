# QUICK START - Muffin Companions Installation
**Version:** 2.0.1 (Fixed & Ready)

---

## 30-Second TL;DR

```bash
# 1. Extract to modules folder
unzip muffin-companions-2.0.1-fixed.zip
cd modules/muffin-companions

# 2. Verify package
./verify.sh

# 3. Build (from AzerothCore root)
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

# 4. Run server
./worldserver

# 5. Test in game
.mbot add tank          # Spawn tank bot
.mbot add healer        # Spawn healer bot
.mbot remove all        # Dismiss all
```

---

## Installation Steps

### 1️⃣ Extract Files
```bash
cd /path/to/azerothcore/modules
unzip muffin-companions-2.0.1-fixed.zip
cd muffin-companions
ls -la
# Should see: CMakeLists.txt  FIXES_APPLIED.md  README.md  src/  verify.sh
```

### 2️⃣ Verify Package
```bash
./verify.sh
```
Expected output:
```
=========================================
  MUFFIN COMPANIONS - Verification
=========================================

Checking files...
  ✓ README.md
  ✓ INSTALL.md
  ✓ CMakeLists.txt
  ✓ src/BotAI.cpp
  ✓ src/BotAI.h
  ✓ src/BotCombatSystem.cpp
  ... (more checks)

✅ ALL CHECKS PASSED!
```

### 3️⃣ Build
```bash
# Go to AzerothCore root
cd /path/to/azerothcore

# Create build directory
mkdir -p build
cd build

# Configure
cmake .. -DCMAKE_BUILD_TYPE=Release

# Compile
make -j$(nproc)  # Uses all CPU cores
```

### 4️⃣ Install
```bash
# From build directory
make install

# Server executable will be in bin/
cd ../bin
```

### 5️⃣ Run Server
```bash
./worldserver
```

You should see:
```
========================================
  MUFFIN COMPANIONS - Bot AI Module
  Version 2.0.1 - Production Ready
========================================
```

---

## Test It

### Login to Game
1. Start server (see above)
2. Connect with your game client
3. Create/login to character

### Spawn a Bot
```
.mbot add tank
```
Output in chat:
```
✓ Bot 'Ironforge' spawned successfully with FULL AI SUITE
```

### Control Your Bot
- **Follow**: Bots automatically follow you
- **Combat**: Bots engage enemies you attack
- **Healing**: Healer bots heal you automatically
- **Formation**: Bots arrange in semicircle behind you

### Dismiss All
```
.mbot remove all
```

---

## Commands Reference

| Command | Effect |
|---------|--------|
| `.mbot add tank` | Spawn random tank bot |
| `.mbot add healer` | Spawn random healer bot |
| `.mbot add dps` | Spawn random DPS bot |
| `.mbot add brule` | Spawn Dr Steve Brule (special!) |
| `.mbot group dungeon` | Spawn 5-man group (1T, 1H, 3D) |
| `.mbot group raid` | Spawn 25-man raid |
| `.mbot remove all` | Dismiss all your bots |
| `.mbot list` | Show your active bots |
| `.mbot status` | Show bot AI status |

---

## What's Fixed in v2.0.1

✅ **Directory Structure** - Files now in `src/` as expected  
✅ **CreatureTemplate Mutation** - Removed dangerous const_cast  
✅ **Cleanup Hooks** - Added creature destruction cleanup  
✅ **Logout Integration** - Bots properly cleaned up on logout  
✅ **Build System** - Now works first time  
✅ **Verification Script** - All checks pass  

---

## Troubleshooting

### "CMake Error: Cannot find module"
```
Solution: Make sure you're in AzerothCore root directory
$ pwd
/path/to/azerothcore/
$ mkdir build && cd build
$ cmake .. -DCMAKE_BUILD_TYPE=Release
```

### "File not found: src/BotAI.cpp"
```
Solution: Verify you extracted to correct location
$ cd modules/muffin-companions
$ ls src/BotAI.cpp
# Should show the file exists

If missing, re-extract the zip file
```

### "Compilation errors"
```
Solution: Check C++ version (needs C++17+)
$ g++ --version
# Should show C++17 or later

Update compiler if needed
```

### Server won't start / crashes
```
Solution: Check module loads in logs
$ grep -i "muffin\|botai" worldserver.log

If not loading, verify CMake output
$ cmake .. -DCMAKE_BUILD_TYPE=Release 2>&1 | grep -i muffin
```

### Bots don't spawn
```
Solution: Make sure you're logged in as GM
.account set gmlevel admin 3

Test spawn again:
.mbot add tank
```

---

## Next Steps After Installation

1. **Test on dev realm** - Spawn bots, run dungeons, verify stability
2. **Check logs** - Monitor for any errors or warnings
3. **Stress test** - Spawn multiple bots, see performance
4. **Document issues** - If you find problems, report with logs
5. **Plan upgrades** - Phase 2 features (routes, factories, etc.)

---

## Key Files

- **FIXES_APPLIED.md** - Detailed list of critical fixes
- **README.md** - Full documentation
- **INSTALL.md** - Detailed installation guide
- **QUICK_REFERENCE.md** - Command cheat sheet
- **CHANGELOG.md** - Version history

---

## Getting Help

If installation fails:

1. Check this guide first
2. Read **INSTALL.md** for detailed steps
3. Verify all files are present: `./verify.sh`
4. Check CMake output for module detection
5. Review **FIXES_APPLIED.md** for known changes

---

## Success Indicators

After successful installation, you should see:

✅ Server starts without crashes  
✅ Module logs show during startup  
✅ `.mbot add tank` spawns a bot  
✅ Bot follows you around  
✅ Bot engages enemies  
✅ Logout cleans up bots properly  

---

**Status:** ✅ Ready to Install  
**Version:** 2.0.1  
**Date:** February 20, 2026
