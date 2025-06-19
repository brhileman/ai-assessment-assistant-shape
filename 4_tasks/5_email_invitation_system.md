# Task 5: SendGrid Email Invitation System

**Prerequisites:** Task 4 (Admin Dashboard) must be completed

## Task Overview
Implement the complete email invitation system using SendGrid for stakeholder invitations, admin magic links, and assessment completion notifications. This includes email template design, delivery management, and integration with the admin interface.

## Reference Documentation
- **User Story 3**: Stakeholder Invitation Management in `../2_user-stories/`
- **User Story 5**: Assessment Invitation Response in `../2_user-stories/`
- **Email Requirements**: SendGrid integration from `../1_big-picture/`

## Tasks

- [ ] 1.0 Configure SendGrid Integration
  - [ ] 1.1 Add SendGrid API key to Rails credentials
  - [ ] 1.2 Configure ActionMailer for SendGrid in production
  - [ ] 1.3 Set up development email configuration
  - [ ] 1.4 Test basic email delivery functionality
  - [ ] 1.5 Add error handling for email delivery failures
  - [ ] 1.6 Configure email logging and monitoring

- [ ] 2.0 Create Assessment Invitation Mailer
  - [ ] 2.1 Generate AssessmentMailer: `rails generate mailer AssessmentMailer`
  - [ ] 2.2 Create stakeholder_invitation method
  - [ ] 2.3 Add assessment_completed method for thank you emails
  - [ ] 2.4 Set up from address and reply-to configuration
  - [ ] 2.5 Add email subject line templates
  - [ ] 2.6 Test mailer methods in development

- [ ] 3.0 Design Email Templates with LaunchPad Lab Branding
  - [ ] 3.1 Create HTML layout for all emails
  - [ ] 3.2 Add LaunchPad Lab logo and color scheme
  - [ ] 3.3 Design stakeholder invitation email template
  - [ ] 3.4 Create assessment completion thank you template
  - [ ] 3.5 Add mobile-responsive email design
  - [ ] 3.6 Include clear call-to-action buttons
  - [ ] 3.7 Test email rendering across email clients

- [ ] 4.0 Implement Invitation Email Content
  - [ ] 4.1 Create personalized greeting with stakeholder name
  - [ ] 4.2 Include company context and custom instructions
  - [ ] 4.3 Add clear assessment instructions and expectations
  - [ ] 4.4 Include prominent "Start Assessment" button with UUID link
  - [ ] 4.5 Add LaunchPad Lab contact information
  - [ ] 4.6 Include privacy and data usage information
  - [ ] 4.7 Test email content with real company data

- [ ] 5.0 Create Invitation Management Interface
  - [ ] 5.1 Add "Invite Stakeholder" functionality to admin company view
  - [ ] 5.2 Create invitation form with name and email fields
  - [ ] 5.3 Add bulk invitation functionality for multiple stakeholders
  - [ ] 5.4 Implement "Resend Invitation" feature
  - [ ] 5.5 Add invitation status tracking (sent, opened, clicked)
  - [ ] 5.6 Create invitation history and audit trail
  - [ ] 5.7 Test invitation workflow from admin interface

- [ ] 6.0 Handle Email Delivery States and Errors
  - [ ] 6.1 Add email delivery status tracking
  - [ ] 6.2 Implement retry logic for failed deliveries
  - [ ] 6.3 Handle bounce and spam notifications from SendGrid
  - [ ] 6.4 Add email validation before sending
  - [ ] 6.5 Create admin notifications for delivery failures
  - [ ] 6.6 Log all email events for debugging
  - [ ] 6.7 Test error scenarios and recovery

- [ ] 7.0 Create Assessment Completion Emails
  - [ ] 7.1 Design thank you email template
  - [ ] 7.2 Include assessment summary information
  - [ ] 7.3 Add next steps and contact information
  - [ ] 7.4 Implement automatic sending after assessment completion
  - [ ] 7.5 Add option for custom thank you messages per company
  - [ ] 7.6 Test completion email delivery
  - [ ] 7.7 Ensure emails reflect company branding context

- [ ] 8.0 Add Email Analytics and Tracking
  - [ ] 8.1 Implement SendGrid event webhooks
  - [ ] 8.2 Track email opens, clicks, and bounces
  - [ ] 8.3 Add analytics dashboard for email performance
  - [ ] 8.4 Create reports for invitation effectiveness
  - [ ] 8.5 Add admin alerts for high bounce rates
  - [ ] 8.6 Test webhook processing and data storage
  - [ ] 8.7 Validate analytics accuracy

- [ ] 9.0 Testing and Security
  - [ ] 9.1 Write unit tests for all mailer methods
  - [ ] 9.2 Create integration tests for email delivery
  - [ ] 9.3 Test email templates across multiple clients
  - [ ] 9.4 Verify invitation token security and uniqueness
  - [ ] 9.5 Test bulk invitation performance
  - [ ] 9.6 Validate email content filtering and security
  - [ ] 9.7 Test production email configuration

## Email Templates

### Stakeholder Invitation Email
```erb
<% content_for :title, "You're invited to complete an AI Assessment" %>

<div class="email-container">
  <header class="email-header">
    <%= image_tag "Blue-Horizontal-LPL-Logo.svg", alt: "LaunchPad Lab" %>
  </header>
  
  <main class="email-content">
    <h1>Hi <%= @stakeholder.name %>,</h1>
    
    <p>You've been invited by <strong><%= @company.name %></strong> to participate in an AI readiness assessment.</p>
    
    <div class="company-context">
      <%= simple_format(@company.custom_instructions) if @company.custom_instructions.present? %>
    </div>
    
    <div class="cta-section">
      <%= link_to "Start Assessment", assessment_url(@stakeholder.invitation_token), 
          class: "btn btn-primary email-cta" %>
    </div>
    
    <p class="assessment-info">
      The assessment takes approximately 10-15 minutes and consists of a conversational AI interview about your role, technology usage, and AI readiness.
    </p>
  </main>
  
  <footer class="email-footer">
    <p>Questions? Contact us at <a href="mailto:assessment@launchpadlab.com">assessment@launchpadlab.com</a></p>
  </footer>
</div>
```

### Assessment Completion Email
```erb
<% content_for :title, "Thank you for completing your AI Assessment" %>

<div class="email-container">
  <header class="email-header">
    <%= image_tag "Blue-Horizontal-LPL-Logo.svg", alt: "LaunchPad Lab" %>
  </header>
  
  <main class="email-content">
    <h1>Thank you, <%= @stakeholder.name %>!</h1>
    
    <p>You've successfully completed the AI readiness assessment for <strong><%= @company.name %></strong>.</p>
    
    <div class="assessment-summary">
      <p><strong>Assessment completed:</strong> <%= @assessment.completed_at.strftime("%B %d, %Y at %I:%M %p") %></p>
      <p><strong>Duration:</strong> <%= @assessment.duration_minutes %> minutes</p>
    </div>
    
    <p>Your insights will help <%= @company.name %> better understand their AI readiness and opportunities. The LaunchPad Lab team will analyze all responses and provide comprehensive recommendations.</p>
  </main>
  
  <footer class="email-footer">
    <p>Questions about your assessment? Contact us at <a href="mailto:assessment@launchpadlab.com">assessment@launchpadlab.com</a></p>
  </footer>
</div>
```

## File Tracking

### Files to Create
| File Path | Purpose | Task Ref | Status |
|-----------|---------|----------|--------|
| `app/mailers/assessment_mailer.rb` | Email delivery logic | 2.1 | ⏳ |
| `app/views/assessment_mailer/stakeholder_invitation.html.erb` | Invitation email HTML | 3.3 | ⏳ |
| `app/views/assessment_mailer/stakeholder_invitation.text.erb` | Invitation email text | 3.3 | ⏳ |
| `app/views/assessment_mailer/assessment_completed.html.erb` | Thank you email HTML | 3.4 | ⏳ |
| `app/views/assessment_mailer/assessment_completed.text.erb` | Thank you email text | 3.4 | ⏳ |
| `app/views/layouts/mailer.html.erb` | Email layout template | 3.1 | ⏳ |
| `app/controllers/admin/invitations_controller.rb` | Invitation management | 5.1 | ⏳ |
| `app/models/concerns/email_trackable.rb` | Email tracking module | 8.1 | ⏳ |
| `app/controllers/webhooks/sendgrid_controller.rb` | SendGrid webhooks | 8.1 | ⏳ |
| `spec/mailers/assessment_mailer_spec.rb` | Mailer tests | 9.1 | ⏳ |
| `spec/system/admin/invitation_management_spec.rb` | Invitation workflow tests | 9.2 | ⏳ |

### Files to Modify
| File Path | Changes | Task Ref | Status |
|-----------|---------|----------|--------|
| `config/environments/production.rb` | SendGrid configuration | 1.2 | ⏳ |
| `config/environments/development.rb` | Development email config | 1.3 | ⏳ |
| `config/routes.rb` | Webhook and invitation routes | 5.1, 8.1 | ⏳ |
| `app/models/stakeholder.rb` | Add invitation methods | 5.2 | ⏳ |
| `app/views/admin/companies/show.html.erb` | Add invitation interface | 5.1 | ⏳ |

## SendGrid Configuration

```ruby
# config/environments/production.rb
config.action_mailer.delivery_method = :smtp
config.action_mailer.smtp_settings = {
  user_name: 'apikey',
  password: Rails.application.credentials.sendgrid[:api_key],
  domain: 'launchpadlab.com',
  address: 'smtp.sendgrid.net',
  port: 587,
  authentication: :plain,
  enable_starttls_auto: true
}
```

## Success Criteria

- [ ] Stakeholder invitation emails deliver successfully
- [ ] Email templates render correctly across email clients
- [ ] Assessment completion emails send automatically
- [ ] Admin interface manages invitations efficiently
- [ ] Email delivery failures are handled gracefully
- [ ] Email analytics provide useful insights
- [ ] All tests pass including integration tests
- [ ] Production email configuration works reliably

## Security Considerations

- **Token Security**: UUID tokens are cryptographically secure and unique
- **Rate Limiting**: Prevent spam by limiting invitation frequency
- **Email Validation**: Validate email addresses before sending
- **Unsubscribe**: Include unsubscribe links where required
- **Data Privacy**: Only include necessary information in emails

## Next Steps

After Task 5 completion:
- Task 6: Create stakeholder landing pages for assessment entry
- Task 7: Implement the voice assessment interface
- Email system enables stakeholder engagement and communication flow 