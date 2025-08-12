# Playwright

```bash
This is a test dApp that shows the different ways you can integrate [dAppwright](https://github.com/TenKeyLabs/dappwright) into your test suite.
You can find the different configurations in the [tests folder](https://github.com/TenKeyLabs/dappwright-examples/tree/main/tests).
git clone https://github.com/TenKeyLabs/dappwright-examples.git
cd dappwright-examples
```

#######################################################################################

### Part 1 - RUN 

```bash
#Jenkins run on 1h 
on Jenkins server: /var/lib/jenkins/workspace/Automation_AIOZ_Finance_main/AIOZ_Finance.sh
#Result Jenkins:
on ??
############
# Git run on 3h 
on Run Playwright tests: use CMD
#Result Git:
on ??
############
#Local run on 5h 
on Jenkins server: /var/lib/jenkins/workspace/Automation/AIOZ_Finance_Auto/run_on_remote_windows.sh
#Result Local: 
on Local
```

#######################################################################################

### Part 2 - Installation Library Yarn (New User) 

```bash
########## 1. System Requirements ##########
# Install Yarn globally (requires Node.js already installed)
npm install -g yarn
# For Linux (Ubuntu/Debian-based) - install Node.js, npm, and Yarn
# sudo apt-get update
# sudo apt-get install -y nodejs npm yarn
```
```bash
########## 2. Install Project Dependencies ##########
yarn install                               # Install all dependencies listed in package.json
yarn playwright install                    # Install Playwright browsers (Chromium, Firefox, WebKit)
apt-get install -y nodejs                  # Ensure Node.js is installed (for Linux environments)
yarn add @playwright/test@latest @tenkeylabs/dappwright   # Add latest Playwright Test + Dappwright to project
npm install playwright axios               # Install Playwright + Axios via npm (alternative if needed)
```
```bash
########## 2. (Optional) Java JDK for Allure ##########
# For Windows (PowerShell) - install Java 17
winget install --id Oracle.JDK.17
# Set JAVA_HOME environment variable
$env:JAVA_HOME="C:\Program Files\Java\jdk-17"
$env:Path += ";$env:JAVA_HOME\bin"
java -version   # Verify Java installation
```
```bash
########## 3. Allure Report (Optional) ##########
npm install -D allure-playwright                    # Install Allure reporter for Playwright
npm install -g allure-commandline                   # Install Allure CLI globally
npm install -D @playwright/test allure-playwright   # Ensure Playwright + Allure reporter in devDependencies
```
```bash
########## 4. View Allure Report ##########
npx allure generate allure-results --clean   # Generate report from latest test results
npx allure open                              # Open Allure report in browser
```

#######################################################################################

### Part 3 - Installation Library Yarn (Old User)

```bash
########## 1. Check Versions ##########
node -v   # Show Node.js version
npm -v    # Show npm version
yarn -v   # Show Yarn version
yarn playwright --version   # Show Playwright version via Yarn
npm playwright --version    # Show Playwright version via npm
```
```bash
########## 2. Uninstall All Dependencies ##########
# FOR LINUX / MAC / GIT BASH - remove old dependencies and reports
rm -rf node_modules package-lock.json yarn.lock playwright-report test-results
# FOR WINDOWS PowerShell - run these one by one
Remove-Item -Recurse -Force node_modules
Remove-Item -Force package-lock.json, yarn.lock
Remove-Item -Recurse -Force playwright-report, test-results
```
```bash
########## 3. Fix esbuild (if needed) ##########
npm install                   # Reinstall dependencies
npm install esbuild --force   # Force install correct esbuild version
ls -l node_modules/esbuild/bin/   # Verify esbuild binary exists
```
```bash
########## 4. Remove Old Playwright & Dappwright ##########
yarn remove playwright @playwright/test @tenkeylabs/dappwright   # Remove via Yarn
npm uninstall playwright @playwright/test @tenkeylabs/dappwright # Remove via npm
```
```bash
########## 5. Reinstall Core Tools ##########
npm install -g yarn           # Install/Update Yarn globally
yarn install                  # Reinstall dependencies from package.json
npm install esbuild --force   # Fix esbuild issues
```
```bash
########## 6. Reinstall Playwright & Dappwright ##########
yarn playwright install             # Install browsers only
yarn playwright install --with-deps # Install browsers + system dependencies
yarn add @playwright/test@latest @tenkeylabs/dappwright   # Add latest Playwright Test + Dappwright
yarn add @playwright/testt@1.48.2 @tenkeylabs/dappwright   # Install specific version if needed
```

#######################################################################################

### Part 4 - Running the dApp

```bash
yarn test:All   # Run all automated tests

yarn test:ConnectMetaMask   # Run MetaMask connection tests
yarn test:ConnectCoinBase   # Run Coinbase connection tests
yarn test:ConnectMetaMask && yarn test:ConnectCoinBase   # Run both tests sequentially

yarn test:ConnectMetaMask --headed   # Run MetaMask test with browser UI visible
yarn test:ConnectMetaMask --debug    # Run MetaMask test in debug mode (slow-mo, verbose logs)
yarn test:ConnectMetaMask --worker=1 # Run MetaMask test in a single-threaded mode

yarn dev    # Start development server (First terminal)
yarn chain  # Start blockchain network (Second terminal)
```

#######################################################################################

### Part 5 - Additional Information Auto Local

```bash
C:\Worker KhauNTC\Github\Playwright_AIOZ\playwright-report
C:\Users\aioz\AppData\Local\Temp\dappwright
```
```bash
All trading pairs follow a cyclic token swap process.
Start with a balance of 500 of each type, execute trades to reach a limit state (1000/0 or 0/1000), then return to the initial state.
Verify that the system processes the transaction logic correctly and that the balance reflects correctly after each step
```

#######################################################################################

### Part 6 - Additional Information Automation Source on Jenkins 

```bash
# Navigate to the Jenkins job workspace directory
cd /var/lib/jenkins/workspace/Automation_AIOZ_Finance_main

# Navigate to Playwright browser cache folder on Jenkins
cd /var/lib/jenkins/.cache/ms-playwright

# List all Jenkins job workspaces with detailed info (size, permissions, owner, etc.)
ls -lah /var/lib/jenkins/workspace/

# Find Jenkinsfile location across the entire server
find / -type f -name "Jenkinsfile" 2>/dev/null    # Search silently (ignore permission errors)
du -ah ~ | grep "Jenkinsfile"                     # Search in the home directory

# Install Node.js 18 (needed for Playwright & modern JS features)
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```
```bash
# Install ethers.js library
yarn add ethers    # Install with Yarn (recommended if project uses Yarn)
npm install ethers # Install with npm (alternative)

# Install Xvfb (X Virtual Framebuffer) - allows headless browsers to run in virtual display
sudo apt-get install -y xvfb

# Uninstall Xvfb completely
sudo apt-get remove --purge -y xvfb
sudo apt-get autoremove -y   # Remove unused packages
sudo apt-get clean           # Clear package cache

# Check if Xvfb is currently running
ps aux | grep Xvfb
```
```bash
# In Jenkinsfile, update the test command to run with a virtual display
xvfb-run --auto-servernum yarn test

# View Jenkins system logs (last 50 lines)
sudo journalctl -u jenkins --no-pager | tail -n 50

# View the last 50 lines of Jenkins log file
cat /var/log/jenkins/jenkins.log | tail -n 50
```
```bash
# Install a specific Chromium build in a custom location for Playwright
mkdir -p /var/lib/jenkins/.cache/ms-playwright/chromium-1148/
cd /var/lib/jenkins/.cache/ms-playwright/chromium-1148/

# Download Chromium build 1148 from Playwright CDN
wget https://playwright.azureedge.net/builds/chromium/1148/chromium-linux.zip

# Extract the downloaded zip
unzip chromium-linux.zip

# Move extracted Chromium to the correct cache folder
mv chrome-linux /var/lib/jenkins/.cache/ms-playwright/chromium-1148/

# Set correct permissions so Jenkins can execute it
chmod -R 755 /var/lib/jenkins/.cache/ms-playwright/
chown -R jenkins:jenkins /var/lib/jenkins/.cache/ms-playwright/
chmod +x /var/lib/jenkins/.cache/ms-playwright/chromium-1148/chrome-linux/chrome

# Link old Chromium version to a new version path (symlink)
ln -s chromium-1148/ chromium-1150
```

#######################################################################################

### Part 7 - Source Folder

```bash 
AIOZ-DEX/
│
├── Data/                         # Test data
│   ├── Assets_Config.js
│   ├── Explore_Config.js
│   ├── Farm_Config.js
│   ├── Position_Config.js
│   ├── Swap_Config.js
│
├── Pages/                     # API handler functions for each module
│   ├── 1_Swap/
│   │   ├── 01_Valid_Swap
│   │   │  ├── Swap.js
│   │   ├── 02_Invalid_Swap
│   │   │  ├── Swap.js
│   ├── 2_Position/
│   │   ├── 01_Valid_Position
│   │   │  ├── Position.js
│   │   ├── 02_Invalid_Position
│   │   │  ├── Position.js
│   ├── 3_Assets/
│   │   ├── 01_Valid_Assets
│   │   │  ├── Your_Assets.js
│   │   ├── 02_Invalid_Assets
│   │   │  ├── Your_Assets.js
│   ├── 4_Farm/
│   │   ├── 01_Valid_Farm
│   │   │  ├── Farm.js
│   │   ├── 02_Invalid_Farm
│   │   │  ├── Farm.js
│   ├── 5_Explore/
│   │   ├── 01_Valid_Explore
│   │   │  ├── Explore.js
│   │   ├── 02_Invalid_Explore
│   │   │  ├── Explore.js
│   ├── 6_Dapps/
│   │   ├── 01_CoinBase
│   │   │  ├── CoinBase.js
│   │   ├── 02_MetaMask
│   │   │  ├── MetaMask.js
│   │   ├── SetupCoinBase.js
│   │   ├── SetupMetaMask.js
│   ├── Functions.js
│
├── Tests/                        # Test cases
│   ├── 1_Swap/
│   │   ├── 01_Valid_Swap
│   │   │  ├── Swap.spec.js
│   │   ├── 02_Invalid_Swap
│   │   │  ├── Swap.spec.js
│   ├── 2_Position/
│   │   ├── 01_Valid_Position
│   │   │  ├── Position.spec.js
│   │   ├── 02_Invalid_Position
│   │   │  ├── Position.spec.js
│   ├── 3_Assets/
│   │   ├── 01_Valid_Assets
│   │   │  ├── Your_Assets.spec.js
│   │   ├── 02_Invalid_Assets
│   │   │  ├── Your_Assets.spec.js
│   ├── 4_Farm/
│   │   ├── 01_Valid_Farm
│   │   │  ├── Farm.spec.js
│   │   ├── 02_Invalid_Farm
│   │   │  ├── Farm.spec.js
│   ├── 5_Explore/
│   │   ├── 01_Valid_Explore
│   │   │  ├── Explore.spec.js
│   │   ├── 02_Invalid_Explore
│   │   │  ├── Explore.spec.js
│   ├── 6_Dapps/
│   │   ├── 01_CoinBase
│   │   │  ├── CoinBase.spec.js
│   │   ├── 02_MetaMask
│   │   │  ├── MetaMask.spec.js
│   
├── SendEmail.spec.js         # Calls email sending function from CustomLibs
├── AIOZ_DEX.bat               # Quick launch script for Windows
├── playwright.config.js           # Playwright configuration file
├── package.json
└── README.md
```
```bash 
AIOZ-DEX/
├── Data/                    # Contains all test data for each module
│   ├── SwapData.js          # Test data for Swap module
│   ├── PositionData.js      # Test data for Position module
│   ├── AssetsData.js        # Test data for Assets module
│   ├── FarmData.js          # Test data for Farm module
│   ├── ExploreData.js       # Test data for Explore module
│
├── Pages/                   # Page Objects / API request handlers
│   ├── Swap.js              # Swap-related actions
│   ├── Position.js          # Position-related actions
│   ├── Assets.js            # Assets-related actions
│   ├── Farm.js              # Farm-related actions
│   ├── Explore.js           # Explore-related actions
│   ├── Dapps/               # Decentralized application integrations
│   │   ├── CoinBase.js      # Coinbase connection methods
│   │   ├── MetaMask.js      # MetaMask connection methods
│   │   ├── SetupCoinBase.js # Coinbase setup process
│   │   ├── SetupMetaMask.js # MetaMask setup process
│
├── Tests/                   # Automated test cases
│   ├── Swap/
│   │   ├── SwapValid.spec.js    # Swap tests with valid data
│   │   ├── SwapInvalid.spec.js  # Swap tests with invalid data
│   ├── Position/
│   │   ├── PositionValid.spec.js
│   │   ├── PositionInvalid.spec.js
│   ├── Assets/
│   │   ├── AssetsValid.spec.js
│   │   ├── AssetsInvalid.spec.js
│   ├── Farm/
│   │   ├── FarmValid.spec.js
│   │   ├── FarmInvalid.spec.js
│   ├── Explore/
│   │   ├── ExploreValid.spec.js
│   │   ├── ExploreInvalid.spec.js
│   ├── Dapps/
│   │   ├── CoinBase.spec.js     # Coinbase integration tests
│   │   ├── MetaMask.spec.js     # MetaMask integration tests
│
├── Libs/                    # Common libraries and helper functions
│   ├── Csv.js               # CSV file operations
│   ├── Excel.js             # Excel file operations
│   ├── ReadDataExcel.js     # Read Excel data utility
│   ├── SendEmail.js         # Email sending utility
│
├── SendEmail.spec.js        # Test for email sending feature
├── AIOZ_DEX.bat              # Batch file to run the project
├── playwright.config.js      # Playwright configuration file
├── package.json              # Project dependencies and scripts
└── README.md                 # Project documentation
```

#######################################################################################

### Part 8 - Error Jenkins and Fix

```bash
# ERROR:
# stderr: error: unable to unlink old 'dist/assets/index-b6bb3e45.js': Permission denied
# error: unable to unlink old 'dist/assets/index-dfec0afb.css': Permission denied

---> 
sudo chown -R jenkins:jenkins /var/lib/jenkins/workspace/Automation_AIOZ_Finance_main
sudo chmod -R 755 /var/lib/jenkins/workspace/Automation_AIOZ_Finance_main
git reset --hard HEAD
git clean -fd
#######
OR DELETE Automation_AIOZ_Finance_main
<---

########################################################################
# ERROR:
# TimeoutError: browserContext.waitForEvent: Timeout 30000ms exceeded while waiting for event "page"
#> |   await wallet.approve();

---> 
sudo apt-get install -y xvfb
<---

########################################################################
# ERROR:
# Error: Playwright Test did not expect test.beforeAll() to be called here.
# Most common reasons include:
# - You are calling test.beforeAll() in a configuration file.
# - You are calling test.beforeAll() in a file that is imported by the configuration file.
# - You have two different versions of @playwright/test. This usually happens
#   when one of the dependencies in your package.json depends on @playwright/test.
# > 16 | test.beforeAll(async ({ page, wallet }) => {
#      |      ^

---> Go to workflow add:
rm -rf node_modules package-lock.json yarn.lock 
    run: |
          rm -rf node_modules package-lock.json yarn.lock
          npm install -g yarn
          yarn install
          npx playwright install --with-deps
          yarn add @playwright/test@latest @tenkeylabs/dappwright
          npm dedupe
    run: |
          node -v
          npm -v
          yarn -v
          npm playwright --version
          yarn playwright --version
          npx playwright --version
          npm list @playwright/test
<---

########################################################################
# ERROR:
#Executable doesn't exist at /var/lib/jenkins/.cache/ms-playwright/chromium-1148/chrome-linux/chrome

---> 
ln -s chromium-1148/ chromium-1150
mv /var/lib/jenkins/.cache/ms-playwright/chromium-1155 /var/lib/jenkins/.cache/ms-playwright/chromium-1148
<---

########################################################################
# ERROR:
#Error: EACCES: permission denied, scandir '/tmp/dappwright/session/metamask/0'
#Error: EACCES: permission denied, scandir '/tmp/dappwright/session/metamask/1'

---> 
sudo chmod -R 777 /tmp/dappwright/session/
sudo chmod -R 777 /tmp/dappwright/session/metamask

chmod -R 777 /tmp/dappwright/session/
chmod -R 777 /tmp/dappwright/session/metamask
<---

########################################################################
# ERROR:
#npm error [Error: EACCES: permission denied, rename '/usr/lib/node_modules/yarn' -> '/usr/lib/node_modules/.yarn-LH7MXRbz'] 

---> 
...
<---

########################################################################
# ERROR:
#Error: browserContext.newPage: Target page, context or browser has been closed
#Call log:
#   [2m  - navigating to "chrome-extension://gadekpdjmpjjnnemgnhkbjgnjpdaakgh/home.html", waiting until "load"[22m

---> 
//sudo apt-get update && sudo apt-get install -y x11-utils
// Xvfb :99 -screen 0 1920x1080x24 &
// export DISPLAY=:99
// xdpyinfo -display :99 || (echo " Xvfb failed to start" && exit 1)
<---

########################################################################
# ERROR:
# TimeoutError: browserContext.waitForEvent: Timeout 30000ms exceeded while waiting for event "page"
#    > |             await wallet.reject();
#    > |             await wallet.confirmTransaction();

---> 
changed headless: true ===> headless: false on setup metamask
<---

########################################################################
# ERROR:
#-bash: ./AIOZ_Finance.sh: Permission denied

---> 
chmod +x AIOZ_Finance.sh
<---

########################################################################
# ERROR:
# src/walletExtension.ts:2:43 - error TS2307: Cannot find module 'ethers/types/providers' or its corresponding type declarations.
# 2 import { Eip1193Provider, Provider } from "ethers/types/providers";

---> Mở file src/walletExtension.ts, tìm dòng:
import { Eip1193Provider, Provider } from "ethers/types/providers";
Cách sửa đúng trong ethers v6:
Thay thế bằng: import { BrowserProvider, Eip1193Provider } from "ethers";
<---

########################################################################
# ERROR:
# Looks like you launched a headed browser without having a XServer running.                     
# Set either 'headless: true' or use 'xvfb-run <your-playwright-app>' before running Playwright.

---> 
...
<---

########################################################################
# ERROR:
# libEGL warning: failed to open /dev/dri/card0: Permission denied

---> 
./AIOZ_Finance.sh --disable-gpu
export DISPLAY=:0
<---

########################################################################
# ERROR:
# Error: EBUSY: resource busy or locked, unlink 'C:\Users\BVSSH_~1\AppData\Local\Temp\dappwright\session\metamask\1\Default\Affiliation Database'

---> 
Restart PC
<---

########################################################################
# Error: EACCES: permission denied, unlink '/var/lib/jenkins/workspace/Automation_AIOZ_Finance_main/test-results/Swap-Invalid_Swap-AIOZ_to_-6a5e2-ked-token-spending-approval-chrome/trace.zip'

########################################################################
# ERROR:
# PS C:\Worker_KhauNTC\Github\AIOZ-PIN-NETWORK> npm run test:ConnectMetaMask
# npm : File C:\nvm4w\nodejs\npm.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at 
# https:/go.microsoft.com/fwlink/?LinkID=135170.
# At line:1 char:1
# + npm run test:ConnectMetaMask
# + ~~~
#     + CategoryInfo          : SecurityError: (:) [], PSSecurityException
#     + FullyQualifiedErrorId : UnauthorizedAccess
# PS C:\Worker_KhauNTC\Github\AIOZ-PIN-NETWORK>

---> 
Chạy PowerShell với quyền Administrator
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
<---

########################################################################
# ERROR:
# Error: ENOENT: no such file or directory, mkdir ''

#        at ..\Pages\1_Dapps\SetupMetaMask.js:10

#        8 |       if (!sharedContext) {
#        9 |         try {
#     > 10 |           const [wallet, _, context] = await Promise.race([
#          |                                        ^

---> 
npx playwright install 
<---
```

#######################################################################################


