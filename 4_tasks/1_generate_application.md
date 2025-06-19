# Task 1: Generate AI Assessment Assistant Rails Application

## Task Overview
Generate the Rails 8 foundation for the AI Assessment Assistant with PostgreSQL, Tailwind CSS, OpenAI integration, authentication gems, and testing frameworks.

## Prerequisites
- Review PRD and technical requirements in ../1_big-picture/
- Ensure development environment has Ruby, Rails 8, and PostgreSQL installed
- Review design system guidelines in ../3_design-system/

## Tasks

- [ ] 1.0 Create Rails Application & Initialize Git
  - [ ] 1.1 Generate Rails app: `rails _8.0.2_ new app_name --database=postgresql --css=tailwind`
  - [ ] 1.2 Navigate to app directory: `cd app_name`
  - [ ] 1.3 Initialize git repository: `git init`
  - [ ] 1.4 Initial commit: `git add . && git commit -m "Initial commit: New Rails app"`
  - [ ] 1.5 Install Tailwind: `bundle exec rails tailwindcss:install`
  - [ ] 1.6 Setup database: `bundle exec rails db:create db:migrate`
  - [ ] 1.7 Install RSpec: `bundle exec rails generate rspec:install`
  - [ ] 1.8 Verify RSpec works: `bundle exec rspec`

- [ ] 2.0 Set up Core Gems for AI Assessment Assistant
  - [ ] 2.1 Add authentication gems: `gem 'devise'`, `gem 'devise-passwordless'`
  - [ ] 2.2 Add email integration: `gem 'sendgrid-ruby'`
  - [ ] 2.3 Add OpenAI integration: `gem 'ruby-openai'`
  - [ ] 2.4 Add testing gems: `factory_bot_rails`, `faker`, `capybara`, `selenium-webdriver`, `shoulda-matchers`, `rspec-rails`
  - [ ] 2.5 Add production gems: `redis`, `sidekiq`, `sentry-ruby`, `sentry-rails`
  - [ ] 2.6 Run bundle install: `bundle install`
  - [ ] 2.7 Add platform compatibility: `bundle lock --add-platform x86_64-linux`

- [ ] 3.0 Set up Flowbite for UI Components
  - [ ] 3.1 Add Flowbite to importmap: `config/importmap.rb`
  - [ ] 3.2 Import Flowbite in application.js
  - [ ] 3.3 Verify Flowbite loads correctly

- [ ] 4.0 Create Welcome Page for AI Assessment Assistant
  - [ ] 4.1 Generate controller: `rails generate controller Pages welcome`
  - [ ] 4.2 Create route for welcome page as root
  - [ ] 4.3 Style page with Tailwind CSS using LaunchPad Lab design system
  - [ ] 4.4 Add LaunchPad Lab logo and basic branding
  - [ ] 4.5 Add navigation placeholder for admin login
  - [ ] 4.6 Verify page loads at `http://localhost:3000`

- [ ] 5.0 Set up Capybara for E2E Testing
  - [ ] 5.1 Configure Capybara in `spec/rails_helper.rb`
  - [ ] 5.2 Create simple system test for welcome page in `spec/system/welcome_page_spec.rb`
  - [ ] 5.3 Test that LaunchPad Lab logo displays correctly
  - [ ] 5.4 Test navigation elements are present
  - [ ] 5.5 Verify tests run: `bundle exec rspec spec/system`

- [ ] 6.0 Final Setup & Verification
  - [ ] 6.1 Verify all tests pass (RSpec including system tests)
  - [ ] 6.2 Verify server starts cleanly: `bin/dev`
  - [ ] 6.3 Create git commit for baseline setup

## File Tracking

### Files to Create
| File Path | Purpose | Task Ref | Status |
|-----------|---------|----------|--------|
| `Gemfile` | Ruby dependencies with AI/auth gems | 2.1-2.5 | ⏳ |
| `config/importmap.rb` | JavaScript imports | 3.1 | ⏳ |
| `app/javascript/application.js` | JS entry point | 3.2 | ⏳ |
| `app/controllers/pages_controller.rb` | Static pages controller | 4.1 | ⏳ |
| `app/views/pages/welcome.html.erb` | Welcome page view | 4.3 | ⏳ |
| `spec/system/welcome_page_spec.rb` | Welcome page system test | 5.2 | ⏳ |

### Files to Modify
| File Path | Changes | Task Ref | Status |
|-----------|---------|----------|--------|
| `config/routes.rb` | Set welcome as root route | 4.2 | ⏳ |
| `spec/rails_helper.rb` | Configure Capybara | 5.1 | ⏳ |

## Notes
- Follow Tailwind v4 documentation as many conventions have changed from v3
- Ensure PostgreSQL is running before database creation
- This sets up the foundation for all subsequent development tasks
- Refer to design system in ../3_design-system/ for styling consistency 