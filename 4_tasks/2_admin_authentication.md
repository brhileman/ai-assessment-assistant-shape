# Task 2: Admin Authentication System

**Prerequisites:** Task 1 (Generate Application) must be completed

## Task Overview
Implement passwordless authentication for administrators using Devise and magic links. Admins will receive email links to log in without passwords, with a manual allowlist approach for security.

## Reference Documentation
- **User Story 1**: Admin Authentication in `../2_user-stories/`
- **Design System**: Light theme styling for admin pages in `../3_design-system/`
- **Technical Requirements**: Authentication section in `../1_big-picture/`

## Tasks

- [ ] 1.0 Configure Devise with Passwordless Extension
  - [ ] 1.1 Generate Devise configuration: `rails generate devise:install`
  - [ ] 1.2 Configure ActionMailer for development and production
  - [ ] 1.3 Add Devise views and customize for LaunchPad Lab branding
  - [ ] 1.4 Generate Admin model: `rails generate devise Admin email:string`
  - [ ] 1.5 Configure passwordless authentication in Admin model
  - [ ] 1.6 Run migration: `rails db:migrate`

- [ ] 2.0 Set up Magic Link Email System
  - [ ] 2.1 Configure SendGrid for production email delivery
  - [ ] 2.2 Create email templates for magic links using design system
  - [ ] 2.3 Customize Devise mailer views with LaunchPad Lab branding
  - [ ] 2.4 Test email delivery in development environment
  - [ ] 2.5 Add email configuration for different environments

- [ ] 3.0 Create Admin Login Flow
  - [ ] 3.1 Create admin login page with email input form
  - [ ] 3.2 Style login page using light theme design system
  - [ ] 3.3 Add LaunchPad Lab logo and branding elements
  - [ ] 3.4 Implement magic link request functionality
  - [ ] 3.5 Create success page after magic link is sent
  - [ ] 3.6 Handle magic link verification and login

- [ ] 4.0 Implement Admin Authorization
  - [ ] 4.1 Add before_action filters to protect admin routes
  - [ ] 4.2 Create admin-only navigation partial
  - [ ] 4.3 Add admin logout functionality
  - [ ] 4.4 Redirect unauthenticated users to login
  - [ ] 4.5 Set up admin layout distinct from public pages

- [ ] 5.0 Create Admin Allowlist System
  - [ ] 5.1 Create seeds file with initial admin email addresses
  - [ ] 5.2 Add validation to prevent non-allowlisted email registration
  - [ ] 5.3 Create rake task for adding new admin emails
  - [ ] 5.4 Document admin management process
  - [ ] 5.5 Test allowlist enforcement

- [ ] 6.0 Testing and Security
  - [ ] 6.1 Write unit tests for Admin model
  - [ ] 6.2 Write controller tests for authentication flow
  - [ ] 6.3 Create system tests for complete login flow
  - [ ] 6.4 Test magic link expiration
  - [ ] 6.5 Test admin authorization on protected routes
  - [ ] 6.6 Verify email delivery in test environment

## Implementation Details

### Admin Model Configuration
```ruby
class Admin < ApplicationRecord
  devise :magic_link_authenticatable, :trackable
  
  validates :email, presence: true, uniqueness: true
  validates :email, inclusion: { 
    in: Rails.application.credentials.admin_allowlist || [],
    message: "is not authorized for admin access"
  }
  
  def send_magic_link
    # Custom magic link delivery logic
  end
end
```

### Allowlist Management
```ruby
# db/seeds.rb
admin_emails = [
  'admin@launchpadlab.com',
  'assessment@launchpadlab.com'
]

admin_emails.each do |email|
  Admin.find_or_create_by(email: email)
end
```

### Routes Configuration
```ruby
# config/routes.rb
devise_for :admins, controllers: {
  magic_links: 'admins/magic_links'
}

namespace :admin do
  root 'dashboard#index'
  # Additional admin routes will be added in later tasks
end
```

## File Tracking

### Files to Create
| File Path | Purpose | Task Ref | Status |
|-----------|---------|----------|--------|
| `app/models/admin.rb` | Admin model with passwordless auth | 1.4 | ⏳ |
| `db/migrate/*_devise_create_admins.rb` | Admin table migration | 1.4 | ⏳ |
| `app/views/admins/magic_links/new.html.erb` | Login form | 3.1 | ⏳ |
| `app/views/admins/magic_links/show.html.erb` | Magic link sent page | 3.5 | ⏳ |
| `app/views/shared/_admin_nav.html.erb` | Admin navigation | 4.2 | ⏳ |
| `app/views/layouts/admin.html.erb` | Admin layout | 4.5 | ⏳ |
| `db/seeds.rb` | Admin allowlist setup | 5.1 | ⏳ |
| `lib/tasks/admin.rake` | Admin management tasks | 5.3 | ⏳ |
| `spec/models/admin_spec.rb` | Admin model tests | 6.1 | ⏳ |
| `spec/system/admin_authentication_spec.rb` | Login flow tests | 6.3 | ⏳ |

### Files to Modify
| File Path | Changes | Task Ref | Status |
|-----------|---------|----------|--------|
| `config/environments/development.rb` | ActionMailer configuration | 1.2 | ⏳ |
| `config/environments/production.rb` | SendGrid configuration | 2.1 | ⏳ |
| `config/routes.rb` | Devise and admin routes | 1.4, 4.4 | ⏳ |
| `config/application.rb` | Devise configuration | 1.1 | ⏳ |

## Success Criteria

- [ ] Admin can request magic link via email
- [ ] Magic link email is delivered and branded correctly
- [ ] Magic link allows successful authentication
- [ ] Only allowlisted emails can receive magic links
- [ ] Admin routes are protected from unauthenticated access
- [ ] Admin can log out successfully
- [ ] All tests pass including system tests
- [ ] Email delivery works in both development and production

## Security Considerations

- **Magic Link Expiration**: Links expire after 1 hour
- **Single Use**: Magic links can only be used once
- **Email Validation**: Only allowlisted email addresses accepted
- **CSRF Protection**: All forms include CSRF tokens
- **Secure Headers**: Add security headers for admin pages

## Next Steps

After Task 2 completion:
- Task 3: Create database models for Companies, Stakeholders, and Assessments
- Task 4: Build admin dashboard with company management interface
- The authentication foundation enables all subsequent admin functionality 