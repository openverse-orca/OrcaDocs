# How to switch between different login accounts?

## Question
I have registered multiple OrcaLab accounts, or I use OrcaLab on a shared computer. How can I switch between different login accounts?

## Answer

The login state for the OrcaLab Asset Library is typically at the browser level. If you need to switch login accounts, the most direct approach is to first log out of the current account, then log back in with the new account credentials.

## 📋 Login Account Switching Process

### Step 1: Access the OrcaLab Asset Library Page

Open your web browser and visit the OrcaLab Asset Library page:

[https://simassets.orca3d.cn/](https://simassets.orca3d.cn/)

### Step 2: Log Out of the Current Account

1.  **Go to "Account Management" or "Personal Center"**:
    -   After logging in, click your "Account Name" or the "Personal Center" entry in the upper-right corner or sidebar of the Asset Library page.
2.  **Find the "Log Out" Option**:
    -   On the "Account Management" page, find and click the "Log Out" button. This button is typically very prominent.

### Step 3: Log In with the New Account

1.  **Return to the Login Page**: After clicking "Log Out," the browser will redirect back to the OrcaLab login page.
2.  **Enter New Account Credentials**:
    -   Log in using the **phone number / email / username** and corresponding **password** of the new account you wish to switch to.
    -   If you previously linked a third-party account (WeChat/GitHub), you can also directly click the corresponding icon for quick login.

## 💡 Recommendations for Shared Computer Use

### 1. **Use Browser Privacy/Incognito Mode**
- **Purpose**: When using the OrcaLab Asset Library on a shared computer, avoid leaving login traces or affecting other users' login states.
- **How to**:
  - In Chrome: `Ctrl + Shift + N`.
  - In Firefox: `Ctrl + Shift + P`.
  - In Safari: `Command + Shift + N`.
- **Advantages**: After closing the privacy mode window, all browsing history, cookies, cache, etc., are cleared and won't affect other users.

### 2. **Use Different Browsers**
- **Purpose**: Isolate login states of different accounts.
- **How to**: Install and use different browsers on the shared computer (e.g., log into one account on Chrome and another on Firefox).

### 3. **Create System User Accounts for Different Users**
- **Purpose**: This is the most secure and recommended approach — create independent operating system user accounts for each user.
- **Advantages**:
  - Each user has an independent system environment, browser configuration, file storage space, and OrcaLab local client installation.
  - Completely isolates user data and privacy.
- **How to**:
  - In Ubuntu: `Settings` -> `Users` -> `Add User`.

## ⚠️ Important Notes

### 1. **Account Sync with the Local OrcaLab Client**
- The login state of the OrcaLab client (desktop application) is linked to the Asset Library (web page).
- After switching accounts on the Asset Library webpage, you need to **close and restart the OrcaLab client** for the client to sync to the new login account and download/update assets subscribed to by the new account.

### 2. **Asset Package Isolation**
- Asset packages subscribed to by each login account are independent.
- After switching accounts, the OrcaLab client will download assets subscribed to by the new account and may hide local assets subscribed to by the old account but not the new one.

### 3. **Account Security**
- On shared computers, be sure to log out of your OrcaLab account when leaving to protect your privacy and asset security.

## 📝 Summary

The conventional method to switch OrcaLab login accounts is to first "Log Out" of the current account, then "Log Back In" with the new account. When using on a shared computer, it is recommended to combine browser privacy mode or create independent system user accounts to enhance isolation and security.

## Related Links
- [User Registration & Management](environment-setup/user-registration-and-management.md)
- [How to register an OrcaLab account?](FAQ-list/036-how-to-register-an-orcalab-account.md)
- [What to do if you forget your password?](FAQ-list/039-what-to-do-if-you-forget-your-password.md)