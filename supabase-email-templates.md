# Supabase Auth Email Templates

Paste these into **Supabase Dashboard → Authentication → Email Templates**.
Uses Keystone branding: arch logo, Instrument Serif (Georgia fallback), Ember palette.

---

## Confirm Signup

**Subject:** `Confirm your Keystone account`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body style="margin:0;padding:0;background:#F6F5F2;font-family:'DM Sans',-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,'Helvetica Neue',Arial,sans-serif;-webkit-font-smoothing:antialiased;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="background:#F6F5F2;">
    <tr>
      <td align="center" style="padding:40px 16px;">
        <table role="presentation" width="600" cellpadding="0" cellspacing="0" style="max-width:600px;width:100%;">
          <!-- Logo header -->
          <tr>
            <td style="padding:24px 32px;background:#FFFFFF;border:1px solid #DDDAD3;border-bottom:none;border-radius:10px 10px 0 0;">
              <table role="presentation" cellpadding="0" cellspacing="0">
                <tr>
                  <td style="padding-right:10px;vertical-align:middle;">
                    <img src="https://keystn.com/logo.png" alt="" width="28" height="28" style="display:block;border:0;" />
                  </td>
                  <td>
                    <span style="font-family:Georgia,'Times New Roman',serif;font-size:20px;font-weight:400;color:#1B1A17;letter-spacing:-0.3px;">Keystone</span>
                  </td>
                </tr>
              </table>
            </td>
          </tr>
          <!-- Accent bar -->
          <tr>
            <td style="height:3px;background:#B5420A;font-size:0;line-height:0;">&nbsp;</td>
          </tr>
          <!-- Content -->
          <tr>
            <td style="padding:36px 32px 32px 32px;background:#FFFFFF;border-left:1px solid #DDDAD3;border-right:1px solid #DDDAD3;">
              <h1 style="font-family:Georgia,'Times New Roman',serif;font-size:22px;font-weight:400;color:#1B1A17;margin:0 0 12px 0;">Confirm your email</h1>
              <p style="font-size:15px;color:#65605A;line-height:1.6;margin:0 0 28px 0;">
                Thanks for signing up for Keystone. Click the button below to confirm your email and get started.
              </p>
              <table role="presentation" cellpadding="0" cellspacing="0" style="margin:0 auto 28px auto;">
                <tr>
                  <td style="background:#B5420A;border-radius:6px;">
                    <a href="{{ .ConfirmationURL }}" style="display:inline-block;padding:13px 32px;color:#FFFFFF;text-decoration:none;font-family:'DM Sans',-apple-system,sans-serif;font-size:14px;font-weight:600;letter-spacing:-0.2px;">
                      Confirm Email
                    </a>
                  </td>
                </tr>
              </table>
              <p style="font-size:13px;color:#9B968F;line-height:1.5;margin:0;">
                If you didn't create an account, you can safely ignore this email.
              </p>
            </td>
          </tr>
          <!-- Footer -->
          <tr>
            <td style="padding:24px 32px;background:#FEF1E8;border:1px solid #DDDAD3;border-top:none;border-radius:0 0 10px 10px;">
              <p style="font-family:Georgia,'Times New Roman',serif;font-size:13px;font-style:italic;color:#65605A;margin:0 0 8px 0;">
                The foundation your brokerage is built on.
              </p>
              <p style="font-size:12px;color:#9B968F;margin:0;">
                <a href="https://keystn.com" style="color:#B5420A;text-decoration:none;">keystn.com</a>
              </p>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

---

## Magic Link

**Subject:** `Your Keystone login link`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body style="margin:0;padding:0;background:#F6F5F2;font-family:'DM Sans',-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,'Helvetica Neue',Arial,sans-serif;-webkit-font-smoothing:antialiased;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="background:#F6F5F2;">
    <tr>
      <td align="center" style="padding:40px 16px;">
        <table role="presentation" width="600" cellpadding="0" cellspacing="0" style="max-width:600px;width:100%;">
          <tr>
            <td style="padding:24px 32px;background:#FFFFFF;border:1px solid #DDDAD3;border-bottom:none;border-radius:10px 10px 0 0;">
              <table role="presentation" cellpadding="0" cellspacing="0">
                <tr>
                  <td style="padding-right:10px;vertical-align:middle;">
                    <img src="https://keystn.com/logo.png" alt="" width="28" height="28" style="display:block;border:0;" />
                  </td>
                  <td><span style="font-family:Georgia,'Times New Roman',serif;font-size:20px;font-weight:400;color:#1B1A17;letter-spacing:-0.3px;">Keystone</span></td>
                </tr>
              </table>
            </td>
          </tr>
          <tr><td style="height:3px;background:#B5420A;font-size:0;line-height:0;">&nbsp;</td></tr>
          <tr>
            <td style="padding:36px 32px 32px 32px;background:#FFFFFF;border-left:1px solid #DDDAD3;border-right:1px solid #DDDAD3;">
              <h1 style="font-family:Georgia,'Times New Roman',serif;font-size:22px;font-weight:400;color:#1B1A17;margin:0 0 12px 0;">Your login link</h1>
              <p style="font-size:15px;color:#65605A;line-height:1.6;margin:0 0 28px 0;">
                Click the button below to log in to Keystone. This link expires in 24 hours.
              </p>
              <table role="presentation" cellpadding="0" cellspacing="0" style="margin:0 auto 28px auto;">
                <tr>
                  <td style="background:#B5420A;border-radius:6px;">
                    <a href="{{ .ConfirmationURL }}" style="display:inline-block;padding:13px 32px;color:#FFFFFF;text-decoration:none;font-family:'DM Sans',-apple-system,sans-serif;font-size:14px;font-weight:600;letter-spacing:-0.2px;">Log In to Keystone</a>
                  </td>
                </tr>
              </table>
              <p style="font-size:13px;color:#9B968F;line-height:1.5;margin:0;">If you didn't request this link, you can safely ignore this email.</p>
            </td>
          </tr>
          <tr>
            <td style="padding:24px 32px;background:#FEF1E8;border:1px solid #DDDAD3;border-top:none;border-radius:0 0 10px 10px;">
              <p style="font-family:Georgia,'Times New Roman',serif;font-size:13px;font-style:italic;color:#65605A;margin:0 0 8px 0;">The foundation your brokerage is built on.</p>
              <p style="font-size:12px;color:#9B968F;margin:0;"><a href="https://keystn.com" style="color:#B5420A;text-decoration:none;">keystn.com</a></p>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

---

## Invite User

**Subject:** `You've been invited to Keystone`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body style="margin:0;padding:0;background:#F6F5F2;font-family:'DM Sans',-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,'Helvetica Neue',Arial,sans-serif;-webkit-font-smoothing:antialiased;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="background:#F6F5F2;">
    <tr>
      <td align="center" style="padding:40px 16px;">
        <table role="presentation" width="600" cellpadding="0" cellspacing="0" style="max-width:600px;width:100%;">
          <tr>
            <td style="padding:24px 32px;background:#FFFFFF;border:1px solid #DDDAD3;border-bottom:none;border-radius:10px 10px 0 0;">
              <table role="presentation" cellpadding="0" cellspacing="0">
                <tr>
                  <td style="padding-right:10px;vertical-align:middle;">
                    <img src="https://keystn.com/logo.png" alt="" width="28" height="28" style="display:block;border:0;" />
                  </td>
                  <td><span style="font-family:Georgia,'Times New Roman',serif;font-size:20px;font-weight:400;color:#1B1A17;letter-spacing:-0.3px;">Keystone</span></td>
                </tr>
              </table>
            </td>
          </tr>
          <tr><td style="height:3px;background:#B5420A;font-size:0;line-height:0;">&nbsp;</td></tr>
          <tr>
            <td style="padding:36px 32px 32px 32px;background:#FFFFFF;border-left:1px solid #DDDAD3;border-right:1px solid #DDDAD3;">
              <h1 style="font-family:Georgia,'Times New Roman',serif;font-size:22px;font-weight:400;color:#1B1A17;margin:0 0 12px 0;">You're invited</h1>
              <p style="font-size:15px;color:#65605A;line-height:1.6;margin:0 0 28px 0;">
                You've been invited to join your team on Keystone. Click below to set up your account and get started.
              </p>
              <table role="presentation" cellpadding="0" cellspacing="0" style="margin:0 auto 28px auto;">
                <tr>
                  <td style="background:#B5420A;border-radius:6px;">
                    <a href="{{ .ConfirmationURL }}" style="display:inline-block;padding:13px 32px;color:#FFFFFF;text-decoration:none;font-family:'DM Sans',-apple-system,sans-serif;font-size:14px;font-weight:600;letter-spacing:-0.2px;">Accept Invitation</a>
                  </td>
                </tr>
              </table>
              <p style="font-size:13px;color:#9B968F;line-height:1.5;margin:0;">If you weren't expecting this invitation, you can safely ignore this email.</p>
            </td>
          </tr>
          <tr>
            <td style="padding:24px 32px;background:#FEF1E8;border:1px solid #DDDAD3;border-top:none;border-radius:0 0 10px 10px;">
              <p style="font-family:Georgia,'Times New Roman',serif;font-size:13px;font-style:italic;color:#65605A;margin:0 0 8px 0;">The foundation your brokerage is built on.</p>
              <p style="font-size:12px;color:#9B968F;margin:0;"><a href="https://keystn.com" style="color:#B5420A;text-decoration:none;">keystn.com</a></p>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

---

## Reset Password

**Subject:** `Reset your Keystone password`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body style="margin:0;padding:0;background:#F6F5F2;font-family:'DM Sans',-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,'Helvetica Neue',Arial,sans-serif;-webkit-font-smoothing:antialiased;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="background:#F6F5F2;">
    <tr>
      <td align="center" style="padding:40px 16px;">
        <table role="presentation" width="600" cellpadding="0" cellspacing="0" style="max-width:600px;width:100%;">
          <tr>
            <td style="padding:24px 32px;background:#FFFFFF;border:1px solid #DDDAD3;border-bottom:none;border-radius:10px 10px 0 0;">
              <table role="presentation" cellpadding="0" cellspacing="0">
                <tr>
                  <td style="padding-right:10px;vertical-align:middle;">
                    <img src="https://keystn.com/logo.png" alt="" width="28" height="28" style="display:block;border:0;" />
                  </td>
                  <td><span style="font-family:Georgia,'Times New Roman',serif;font-size:20px;font-weight:400;color:#1B1A17;letter-spacing:-0.3px;">Keystone</span></td>
                </tr>
              </table>
            </td>
          </tr>
          <tr><td style="height:3px;background:#B5420A;font-size:0;line-height:0;">&nbsp;</td></tr>
          <tr>
            <td style="padding:36px 32px 32px 32px;background:#FFFFFF;border-left:1px solid #DDDAD3;border-right:1px solid #DDDAD3;">
              <h1 style="font-family:Georgia,'Times New Roman',serif;font-size:22px;font-weight:400;color:#1B1A17;margin:0 0 12px 0;">Reset your password</h1>
              <p style="font-size:15px;color:#65605A;line-height:1.6;margin:0 0 28px 0;">
                We received a request to reset your Keystone password. Click the button below to choose a new one.
              </p>
              <table role="presentation" cellpadding="0" cellspacing="0" style="margin:0 auto 28px auto;">
                <tr>
                  <td style="background:#B5420A;border-radius:6px;">
                    <a href="{{ .ConfirmationURL }}" style="display:inline-block;padding:13px 32px;color:#FFFFFF;text-decoration:none;font-family:'DM Sans',-apple-system,sans-serif;font-size:14px;font-weight:600;letter-spacing:-0.2px;">Reset Password</a>
                  </td>
                </tr>
              </table>
              <p style="font-size:13px;color:#9B968F;line-height:1.5;margin:0;">If you didn't request a password reset, you can safely ignore this email. Your password won't change.</p>
            </td>
          </tr>
          <tr>
            <td style="padding:24px 32px;background:#FEF1E8;border:1px solid #DDDAD3;border-top:none;border-radius:0 0 10px 10px;">
              <p style="font-family:Georgia,'Times New Roman',serif;font-size:13px;font-style:italic;color:#65605A;margin:0 0 8px 0;">The foundation your brokerage is built on.</p>
              <p style="font-size:12px;color:#9B968F;margin:0;"><a href="https://keystn.com" style="color:#B5420A;text-decoration:none;">keystn.com</a></p>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

---

## Change Email Address

**Subject:** `Confirm your new email address`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body style="margin:0;padding:0;background:#F6F5F2;font-family:'DM Sans',-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,'Helvetica Neue',Arial,sans-serif;-webkit-font-smoothing:antialiased;">
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0" style="background:#F6F5F2;">
    <tr>
      <td align="center" style="padding:40px 16px;">
        <table role="presentation" width="600" cellpadding="0" cellspacing="0" style="max-width:600px;width:100%;">
          <tr>
            <td style="padding:24px 32px;background:#FFFFFF;border:1px solid #DDDAD3;border-bottom:none;border-radius:10px 10px 0 0;">
              <table role="presentation" cellpadding="0" cellspacing="0">
                <tr>
                  <td style="padding-right:10px;vertical-align:middle;">
                    <img src="https://keystn.com/logo.png" alt="" width="28" height="28" style="display:block;border:0;" />
                  </td>
                  <td><span style="font-family:Georgia,'Times New Roman',serif;font-size:20px;font-weight:400;color:#1B1A17;letter-spacing:-0.3px;">Keystone</span></td>
                </tr>
              </table>
            </td>
          </tr>
          <tr><td style="height:3px;background:#B5420A;font-size:0;line-height:0;">&nbsp;</td></tr>
          <tr>
            <td style="padding:36px 32px 32px 32px;background:#FFFFFF;border-left:1px solid #DDDAD3;border-right:1px solid #DDDAD3;">
              <h1 style="font-family:Georgia,'Times New Roman',serif;font-size:22px;font-weight:400;color:#1B1A17;margin:0 0 12px 0;">Confirm your new email</h1>
              <p style="font-size:15px;color:#65605A;line-height:1.6;margin:0 0 28px 0;">
                Click the button below to confirm your new email address on Keystone.
              </p>
              <table role="presentation" cellpadding="0" cellspacing="0" style="margin:0 auto 28px auto;">
                <tr>
                  <td style="background:#B5420A;border-radius:6px;">
                    <a href="{{ .ConfirmationURL }}" style="display:inline-block;padding:13px 32px;color:#FFFFFF;text-decoration:none;font-family:'DM Sans',-apple-system,sans-serif;font-size:14px;font-weight:600;letter-spacing:-0.2px;">Confirm Email Change</a>
                  </td>
                </tr>
              </table>
              <p style="font-size:13px;color:#9B968F;line-height:1.5;margin:0;">If you didn't request this change, please contact your admin immediately.</p>
            </td>
          </tr>
          <tr>
            <td style="padding:24px 32px;background:#FEF1E8;border:1px solid #DDDAD3;border-top:none;border-radius:0 0 10px 10px;">
              <p style="font-family:Georgia,'Times New Roman',serif;font-size:13px;font-style:italic;color:#65605A;margin:0 0 8px 0;">The foundation your brokerage is built on.</p>
              <p style="font-size:12px;color:#9B968F;margin:0;"><a href="https://keystn.com" style="color:#B5420A;text-decoration:none;">keystn.com</a></p>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```
