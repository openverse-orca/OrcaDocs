# OrcaLab User Registration
Welcome to `OrcaLab`! Registering an account is the key step to unlocking exclusive services and full features. Let us bring you a secure and personalized user experience.


## 1. User Registration Guide

### 1.1 User Registration & Login
Open the Asset Library page at https://simassets.orca3d.cn/. Registered users can log in directly, while unregistered users must complete registration before use.

 **Method 1: Phone/Email Registration**:

   - Click the Register button
   - Enter your phone number
   - Enter the verification code
   - Submit registration

   - Complete account information:
     - First Name
     - Last Name
     - Username
     - Password
     - Confirm Password
     - Organization Name
     - Check "I have read and accept" (User Agreement, Privacy Policy)
     - Confirm and Submit

 **Method 2: Third-Party Account Registration**: Supports WeChat and GitHub third-party account registration
   - Click the third-party registration option
     - Follow the prompts to scan the WeChat QR code or enter your GitHub account email
   - Proceed to the next step to bind your phone number
   - Enter the verification code
   - Confirm

   - Complete account information:
     - First Name
     - Last Name
     - Username
     - Password
     - Confirm Password
     - Organization Name
     - Check "I have read and accept" (User Agreement, Privacy Policy)
     - Confirm and Submit

### 1.2 Automatic Login After Registration
After successful registration, you will be automatically logged in and the Asset Library interface will appear.

 ![](../img/register/assets.png)
---

## 2. Common Registration Issues
#### 2.1 Email Verification Code Issues

**⚠️ Known Gmail Issue**:

If you use a Gmail address to register, you may encounter the following issue:

```
The recipient server rejected your email, possibly due to SPF verification failure
```

**Cause**: Since November 2022, Google requires senders delivering email to Gmail addresses to have SPF or DKIM records configured.

**Solution**:

- Use a non-Gmail email address to register
- Or contact your system administrator to configure SPF/DKIM records

**SPF Record Example**:

```
v=spf1 include:spf.163.com -all
```

---

## 3. Technical Support

If you encounter issues, please:

1. Refer to the "Common Troubleshooting" section of this document
2. Check terminal error messages
3. Scan the QR code to contact the technical support team

![](../img/install/chat_scode.png)

---