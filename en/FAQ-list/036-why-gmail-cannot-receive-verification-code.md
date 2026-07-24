# Why can't Gmail receive the verification code?

## Question
When registering an OrcaLab account with a Gmail address, the verification code cannot be received. What causes this? How should I resolve this issue?

## Answer

When registering for OrcaLab with a Gmail address, you may indeed encounter issues receiving the verification code. This is typically not a problem with the OrcaLab system itself, but is related to Google's email security policies and mail server configuration.

## 📋 Cause: Google's Email Security Policies

Since **November 2022**, Google has strengthened requirements for senders, especially for services that send bulk email. Specifically, Google requires senders delivering email to Gmail addresses to configure one or more of the following **email authentication mechanisms**:

1.  **SPF (Sender Policy Framework)**: Verifies that the email was sent by an authorized IP address.
2.  **DKIM (DomainKeys Identified Mail)**: Uses digital signatures to verify that email content has not been tampered with.
3.  **DMARC (Domain-based Message Authentication, Reporting, and Conformance)**: A combination of SPF and DKIM, providing more comprehensive verification and reporting mechanisms.

**If the sending server has not properly configured these authentication mechanisms, Gmail's receiving server may reject the email or place it in the spam folder.** OrcaLab's registration system may also be affected by these policy updates.

### Common Error Message
You may see an error prompt similar to the following on the OrcaLab registration page (or in the sender's logs):
```
The recipient server rejected your email, possibly due to SPF verification failure
```

## 🛠️ Solutions

### 1. **Use a Non-Gmail Email to Register (Recommended)**

This is the most direct and recommended solution. Try registering with an email address from another mainstream email service provider, such as:
- **QQ Mail** (`@qq.com`)
- **163 Mail** (`@163.com`)
- **Outlook Mail** (`@outlook.com`)
- Other corporate or personal domain email addresses

### 2. **Check the Spam/Junk Folder**

Sometimes verification code emails may be mistakenly classified as spam. Log into your Gmail account and carefully check the **Spam** or **Junk** folder. If found, you can mark it as "Not Spam" and add it to your whitelist to ensure normal receipt in the future.

### 3. **Contact Technical Support**

If none of the above methods resolve the issue, you can contact the OrcaLab technical support team. They may need:
- Your Gmail address.
- The time when you attempted to register.
- They can check the mail server's sending logs to confirm whether the email was successfully sent and whether Gmail provided a rejection reason.
- The technical support team may need to contact their email service provider to update SPF/DKIM records.

### 4. **Third-Party Account Registration**

As an alternative, you can use the **third-party account registration** methods provided by OrcaLab, such as **WeChat** or **GitHub**. After successful registration, the system will guide you to bind an email address, at which point you can try binding a non-Gmail address.

### 5. **Configure SPF/DKIM Records (For Senders)**

If you are an OrcaLab system administrator or email service provider, you need to ensure your mail server has SPF/DKIM records correctly configured. Below is an example SPF record:

```
v=spf1 include:spf.163.com -all
```
This record indicates that `spf.163.com` (for example, if using NetEase's corporate email service) is authorized as a sender. The specific configuration depends on your email service provider.

## 📝 Summary

The primary reason Gmail cannot receive OrcaLab verification codes is Google's email security policies. The best way to resolve this issue is to **switch to a non-Gmail email address for registration**. If the problem persists, contact OrcaLab technical support for assistance.

## Related Links
- [User Registration & Management](environment-setup/user-registration-and-management.md)
- [How to register an OrcaLab account?](FAQ-list/034-how-to-register-an-orcalab-account.md)
- [What registration methods are supported?](FAQ-list/035-what-registration-methods-are-supported.md)