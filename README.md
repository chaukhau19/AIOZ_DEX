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
#Jenkins run on 1h sáng
on Jenkins server: /var/lib/jenkins/workspace/Automation_AIOZ_Finance_main/AIOZ_Finance.sh
#Result Jenkins:
on ??
############
# Git run on 3h sáng
on Run Playwright tests: use CMD
#Result Git:
on ??
############
#Local run on 5h sáng
on Jenkins server: /var/lib/jenkins/workspace/Automation/AIOZ_Finance_Auto/run_on_remote_windows.sh
#Result Local: 
on Local
```

#######################################################################################

### Part 2 - Installation Library Yarn (New User) 

```bash
########## 1. System Requirements ##########
# Install Node.js and Yarn (if not already installed)
npm install -g yarn
# For Linux (Ubuntu/Debian-based)
# sudo apt-get update
# sudo apt-get install -y nodejs npm yarn

########## 2. Install Project Dependencies ##########
yarn install
# Install Playwright browsers
yarn playwright install
# Add main libraries
apt-get install -y nodejs
yarn add @playwright/test@latest @tenkeylabs/dappwright
npm install playwright axios

########## 2. (Optional) Java JDK for Allure ##########
# For Windows (PowerShell)
winget install --id Oracle.JDK.17
$env:JAVA_HOME="C:\Program Files\Java\jdk-17"
$env:Path += ";$env:JAVA_HOME\bin"
java -version

########## 3. Allure Report (Optional) ##########
npm install -D allure-playwright
npm install -g allure-commandline
npm install -D @playwright/test allure-playwright

########## 4. View Allure Report ##########
npx allure generate allure-results --clean
npx allure open
```

#######################################################################################

### Part 3 - Installation Library Yarn (Old User)

```bash
########## 1. Check Versions ##########
node -v
npm -v
yarn -v
yarn playwright --version
npm playwright --version

########## 2. Uninstall All Dependencies ##########
# FOR LINUX / MAC / GIT BASH
rm -rf node_modules package-lock.json yarn.lock playwright-report test-results
# FOR WINDOWS PowerShell (Run one at a time)
Remove-Item -Recurse -Force node_modules
Remove-Item -Force package-lock.json, yarn.lock
Remove-Item -Recurse -Force playwright-report, test-results

########## 3. Fix esbuild (if needed) ##########
npm install
npm install esbuild --force
ls -l node_modules/esbuild/bin/

########## 4. Remove Old Playwright & Dappwright ##########
yarn remove playwright @playwright/test @tenkeylabs/dappwright
npm uninstall playwright @playwright/test @tenkeylabs/dappwright

########## 5. Reinstall Core Tools ##########
npm install -g yarn
yarn install
npm install esbuild --force  # Fix esbuild issues

########## 6. Reinstall Playwright & Dappwright ##########
yarn playwright install
yarn playwright install --with-deps
yarn add @playwright/test@latest @tenkeylabs/dappwright
yarn add @playwright/testt@1.48.2 @tenkeylabs/dappwright #If need test 1.48.2
```

#######################################################################################

### Part 4 - Running the dApp

```bash
yarn test:All

yarn test:ConnectMetaMask
yarn test:ConnectCoinBase  
yarn test:ConnectMetaMask && yarn test:ConnectCoinBase

yarn test:ConnectMetaMask --headed
yarn test:ConnectMetaMask --debug
yarn test:ConnectMetaMask --worker=1

yarn dev # first terminal
yarn chain # second terminal
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
# Auto folder on Jenkins server
cd /var/lib/jenkins/workspace/Automation_AIOZ_Finance_main
cd /var/lib/jenkins/.cache/ms-playwright

# Check auto folder on Jenkins server
ls -lah /var/lib/jenkins/workspace/

# Find file Jenkinsfile
find / -type f -name "Jenkinsfile" 2>/dev/null
du -ah ~ | grep "Jenkinsfile"

# Install Node.js 18
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

########################################################################
# Install ethers
yarn add ethers #yarn
npm install ethers #npm

# Install Xvfb
sudo apt-get install -y xvfb

# Uninstall Xvfb
sudo apt-get remove --purge -y xvfb
sudo apt-get autoremove -y
sudo apt-get clean

# Check status Xvfb
ps aux | grep Xvfb

########################################################################
#Trong Jenkinsfile, cập nhật command để chạy test như sau:
xvfb-run --auto-servernum yarn test

# Kiểm tra log hệ thống của Jenkins
sudo journalctl -u jenkins --no-pager | tail -n 50

# Kiểm tra logs trong thư mục Jenkins
cat /var/log/jenkins/jenkins.log | tail -n 50

########################################################################
#Cài đặt Chromium vào thư mục cụ thể
mkdir -p /var/lib/jenkins/.cache/ms-playwright/chromium-1148/
cd /var/lib/jenkins/.cache/ms-playwright/chromium-1148/
wget https://playwright.azureedge.net/builds/chromium/1148/chromium-linux.zip

unzip chromium-linux.zip
mv chrome-linux /var/lib/jenkins/.cache/ms-playwright/chromium-1148/

chmod -R 755 /var/lib/jenkins/.cache/ms-playwright/
chown -R jenkins:jenkins /var/lib/jenkins/.cache/ms-playwright/
chmod +x /var/lib/jenkins/.cache/ms-playwright/chromium-1148/chrome-linux/chrome

# This will link old Chromium version to a new version path
ln -s chromium-1148/ chromium-1150
```

#######################################################################################

### Part 7 - Error Jenkins and Fix
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


