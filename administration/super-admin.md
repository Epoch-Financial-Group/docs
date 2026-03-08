# Super Admin

Super admin is the highest level of access in Keystone. While regular users operate within the context of a single company, super admins have platform-wide visibility and the ability to create and manage all companies in the system.

## What is a super admin?

A super admin is a user whose email address has been explicitly listed in the platform's configuration. Super admins can:

- Access the **Admin Panel** at `/admin`
- View dashboard statistics across all companies
- Create new companies
- Edit existing company settings
- Activate or deactivate companies
- View employee rosters for any company
- Access any company's data as if they were a member (used for support and troubleshooting)

Super admin access is not tied to any specific company. It is a platform-level privilege that exists independently of company membership.

## How access is controlled

Super admin access is controlled entirely by the `SUPER_ADMIN_EMAILS` environment variable. This variable contains a comma-separated list of email addresses that are granted super admin access.

### Configuration

The environment variable is set in your deployment configuration (e.g., `.env`, Vercel environment variables, or your hosting provider's settings):

```
SUPER_ADMIN_EMAILS=admin@yourcompany.com,cto@yourcompany.com
```

### How verification works

When a user attempts to access a super-admin-protected resource, the system:

1. Retrieves the currently authenticated user from the session.
2. Reads the `SUPER_ADMIN_EMAILS` environment variable.
3. Splits the value by commas and trims whitespace.
4. Converts both the user's email and all configured emails to lowercase.
5. Checks whether the user's email appears in the list.
6. If the email matches, access is granted. If not, the request is denied with an "Access denied" error.

### Important considerations

- **Email-based:** Access is determined solely by the user's email address. There is no database flag or role assignment -- if the email is in the environment variable, the user is a super admin.
- **Case-insensitive:** Email matching is case-insensitive. `Admin@Company.com` and `admin@company.com` are treated as the same email.
- **No UI for management:** The list of super admin emails can only be changed by updating the environment variable. There is no admin interface for adding or removing super admins. This is an intentional security measure.
- **Restart required:** Changes to the environment variable take effect based on your deployment method. In most serverless environments, changes take effect on the next function invocation. In traditional servers, a restart may be required.

## Accessing the admin panel

Super admins access the admin panel by navigating to `/admin` in their browser. This route is only accessible to authenticated users whose email appears in the `SUPER_ADMIN_EMAILS` list.

### Admin dashboard

The admin dashboard at `/admin` displays platform-wide statistics:

| Metric | Description |
|--------|-------------|
| **Total Companies** | The total number of companies registered in the platform |
| **Active Companies** | The number of companies with `isActive` set to true |
| **Total Employees** | The total number of non-archived employees across all companies |

The dashboard also shows a list of the 10 most recently created companies with their employee counts.

> ![Screenshot: Admin dashboard showing platform statistics and recent companies table](screenshots/admin-dashboard.png)

### Company management

From the admin panel, super admins can navigate to `/admin/companies` to manage all companies. See [Multi-Company Management](multi-company.md) for details.

## Super admin access within companies

In addition to the admin panel, super admin status grants access to any company's data through the normal application routes. When a user accesses a company-scoped route (e.g., `/{company}/loans`), the system checks:

1. Is the user an employee of this company? If yes, grant access.
2. If not, is the user a super admin? If yes, grant access.

This allows super admins to troubleshoot issues, review configurations, and provide support without needing an employee record in every company. When a super admin accesses a company they are not a member of, some features that require an employee ID (such as being assigned as a reviewer or note author) may have limited functionality.
