# Generate Rails Application

## Task Overview
In the code/ directory generate a Rails 8 application with PostgreSQL, Tailwind CSS, Rspec, Flowbite, and Capybara to serve as the foundation for the project.

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

- [ ] 2.0 Set up Core Gems
  - [ ] 2.1 Add production gems to Gemfile (figaro, decanter)
  - [ ] 2.2 Add testing gems to Gemfile (factory_bot_rails, faker, database_cleaner-active_record, shoulda-matchers, capybara, simplecov)
  - [ ] 2.3 Add production gems (redis, sidekiq, sentry-ruby, sentry-rails, aws-sdk-s3)
  - [ ] 2.4 Run bundle install: `bundle install`
  - [ ] 2.5 Add platform compatibility: `bundle lock --add-platform x86_64-linux`

- [ ] 3.0 Set up Flowbite for UI Components
  - [ ] 3.1 Add Flowbite to importmap: `config/importmap.rb`
  - [ ] 3.2 Import Flowbite in application.js
  - [ ] 3.3 Verify Flowbite loads correctly

- [ ] 4.0 Create Hello World Page
  - [ ] 4.1 Generate controller: `rails generate controller Pages hello`
  - [ ] 4.2 Create route for hello page
  - [ ] 4.3 Style page with Tailwind CSS
  - [ ] 4.4 Add Flowbite tooltip component to test integration
  - [ ] 4.5 Verify page loads at `http://localhost:3000/hello`

- [ ] 5.0 Set up Capybara for E2E Testing
  - [ ] 5.1 Configure Capybara in `spec/rails_helper.rb`
  - [ ] 5.2 Create simple system test for Hello World page in `spec/system/hello_world_spec.rb`
  - [ ] 5.3 Add selenium-webdriver to Gemfile if not present: `bundle add selenium-webdriver --group test`
  - [ ] 5.4 Verify tests run: `bundle exec rspec spec/system`

- [ ] 6.0 Final Setup & Verification
  - [ ] 6.1 Verify all tests pass (RSpec including system tests)
  - [ ] 6.2 Verify server starts cleanly: `bin/dev`
  - [ ] 6.3 Create git commit for baseline setup

## File Tracking

### Files to Create
| File Path | Purpose | Task Ref | Status |
|-----------|---------|----------|--------|
| `Gemfile` | Ruby dependencies | 2.1-2.3 | ⏳ |
| `config/importmap.rb` | JavaScript imports | 3.1 | ⏳ |
| `app/javascript/application.js` | JS entry point | 3.2 | ⏳ |
| `app/controllers/pages_controller.rb` | Static pages controller | 4.1 | ⏳ |
| `app/views/pages/hello.html.erb` | Hello world view | 4.3 | ⏳ |
| `spec/system/hello_world_spec.rb` | System test | 5.2 | ⏳ |

### Files to Modify
| File Path | Changes | Task Ref | Status |
|-----------|---------|----------|--------|
| `config/routes.rb` | Add hello route | 4.2 | ⏳ |
| `spec/rails_helper.rb` | Configure Capybara | 5.1 | ⏳ |

## Notes
- Follow Tailwind v4 documentation as many conventions have changed from v3
- Ensure PostgreSQL is running before database creation
- This sets up the foundation for all subsequent development tasks
- Refer to design system in ../3_design-system/ for styling consistency 