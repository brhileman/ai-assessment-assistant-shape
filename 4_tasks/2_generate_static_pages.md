# Generate Static Pages

Prerequisites: Task 1 (Generate Application) must be completed

## Task Overview
Create the actual application pages (with hardcoded data initially) in the code/ directory. These pages will serve as the foundation for the live application - proper routes, controllers, and views that will be enhanced with dynamic functionality later.

## Prerequisites
- Rails application is set up and running (Task 1 completed)
- Design system is defined in ../3_design-system/
- User stories and flowchart define required pages
- Tailwind CSS and Flowbite are configured

## Important Note
These are NOT throwaway prototype pages. Create production-ready routes, controllers, and views that will be used in the final application. Only the data is hardcoded initially.

## Implementation Strategy
**Start with the core of the application first** (e.g., main dashboard, primary user interface, or key feature page). Create this core page completely, then **STOP and let the user review the experience**. Users will likely want to iterate on this core page multiple times before moving to supporting pages. This iterative approach ensures the most important user experience is refined before building out the rest of the application.

## Tasks

- [ ] 1.0 Plan Application Structure
  - [ ] 1.1 Review flowchart in ../1_big-picture/flowchart.md for page requirements
  - [ ] 1.2 Review user stories in ../2_user-stories/ for page-specific needs
  - [ ] 1.3 Review design system in ../3_design-system/ for styling guidelines
  - [ ] 1.4 Identify the CORE page/feature of the application (dashboard, main interface, etc.)
  - [ ] 1.5 Create list of supporting pages needed
  - [ ] 1.6 Plan RESTful routes and controller structure

- [ ] 2.0 Generate Core Controller and Routes FIRST
  - [ ] 2.1 Generate controller for core feature (e.g., `rails g controller Dashboard index`)
  - [ ] 2.2 Set up routes for core feature in `config/routes.rb`
  - [ ] 2.3 **Create only the core routes initially - hold off on other pages**
  - [ ] 2.4 Ensure core routes follow Rails conventions
  - [ ] 2.5 Test that core routes are working

- [ ] 3.0 Create Application Layout for Core Experience
  - [ ] 3.1 Update `app/views/layouts/application.html.erb` with main structure
  - [ ] 3.2 Create minimal navigation (just enough for core page)
  - [ ] 3.3 Focus on the core page's specific layout needs
  - [ ] 3.4 Implement responsive design for core page
  - [ ] 3.5 Add any core-specific meta tags

- [ ] 4.0 Implement Core Page COMPLETELY
  - [ ] 4.1 Create the main view file (e.g., `app/views/dashboard/index.html.erb`)
  - [ ] 4.2 Add all hardcoded data needed for realistic experience
  - [ ] 4.3 Implement all UI components for this page
  - [ ] 4.4 Add interactive elements (dropdowns, modals, etc.)
  - [ ] 4.5 Ensure responsive design works perfectly
  - [ ] 4.6 Polish with transitions and hover states
  - [ ] 4.7 **STOP HERE - Let user review and iterate**

**🛑 PAUSE POINT: After completing the core page, stop and let the user review. They will likely want to iterate on styling, layout, and functionality before proceeding.**

- [ ] 5.0 After Core Page Approval - Generate Supporting Controllers
  - [ ] 5.1 Generate PagesController for static pages: `rails g controller Pages home about contact`
  - [ ] 5.2 Generate other resource controllers based on flowchart
  - [ ] 5.3 Set up remaining routes in `config/routes.rb`
  - [ ] 5.4 Ensure all routes follow Rails conventions
  - [ ] 5.5 Test all routes are working

- [ ] 6.0 Expand Navigation and Layout
  - [ ] 6.1 Create full navigation partial: `app/views/shared/_navigation.html.erb`
  - [ ] 6.2 Create footer partial: `app/views/shared/_footer.html.erb`
  - [ ] 6.3 Update layout to work for all pages
  - [ ] 6.4 Ensure navigation highlights current page
  - [ ] 6.5 Add mobile menu functionality

- [ ] 7.0 Implement Supporting Pages
  - [ ] 7.1 Create homepage if not the core page
  - [ ] 7.2 Create about page
  - [ ] 7.3 Create contact page
  - [ ] 7.4 Create other resource views (index, show)
  - [ ] 7.5 Ensure consistent styling across all pages

- [ ] 8.0 Define Structs and Add Sample Data
  - [ ] 8.1 Define Structs for all data types at top of controllers
  - [ ] 8.2 Create realistic sample data arrays
  - [ ] 8.3 Implement show actions with find logic
  - [ ] 8.4 Add methods to Structs that mimic ActiveRecord
  - [ ] 8.5 Document all Struct attributes

  ```ruby
  # Example Struct definition
  Product = Struct.new(:id, :name, :slug, :price, :description, 
                      :image_url, :category, :in_stock, :created_at, 
                      keyword_init: true) do
    def to_param
      slug
    end
    
    def formatted_price
      "$%.2f" % price
    end
  end
  ```

- [ ] 9.0 Create Reusable Components
  - [ ] 9.1 Extract repeated UI into partials
  - [ ] 9.2 Create card partial: `app/views/shared/_card.html.erb`
  - [ ] 9.3 Create button components
  - [ ] 9.4 Create form components
  - [ ] 9.5 Document component usage

- [ ] 10.0 Testing and Validation
  - [ ] 10.1 Write controller tests
  - [ ] 10.2 Create system tests for user flows
  - [ ] 10.3 Add E2E tests with Capybara
  - [ ] 10.4 Test all responsive breakpoints
  - [ ] 10.5 Validate accessibility

- [ ] 11.0 Prepare for Dynamic Data
  - [ ] 11.1 Add TODO comments for database queries
  - [ ] 11.2 Create seed file matching Struct data
  - [ ] 11.3 Document data relationships
  - [ ] 11.4 Plan model structure
  - [ ] 11.5 Note where authentication will be added

## File Tracking

### Core Page Files (Create First)
| File Path | Purpose | Task Ref | Status |
|-----------|---------|----------|--------|
| Core controller (e.g., `app/controllers/dashboard_controller.rb`) | Core feature controller | 2.1 | ⏳ |
| Core view (e.g., `app/views/dashboard/index.html.erb`) | Main application view | 4.1 | ⏳ |
| `app/views/layouts/application.html.erb` | Initial layout | 3.1 | ⏳ |

### Supporting Files (Create After Core Review)
| File Path | Purpose | Task Ref | Status |
|-----------|---------|----------|--------|
| `app/controllers/pages_controller.rb` | Static pages | 5.1 | ⏳ |
| `app/views/shared/_navigation.html.erb` | Full navigation | 6.1 | ⏳ |
| `app/views/shared/_footer.html.erb` | Footer partial | 6.2 | ⏳ |
| `app/views/pages/*.html.erb` | Supporting pages | 7.1-7.4 | ⏳ |
| `app/views/shared/_card.html.erb` | Card component | 9.2 | ⏳ |
| `spec/system/*_spec.rb` | System tests | 10.2 | ⏳ |
| `db/seeds.rb` | Seed data | 11.2 | ⏳ |

### Files to Modify
| File Path | Changes | Task Ref | Status |
|-----------|---------|----------|--------|
| `config/routes.rb` | Add routes incrementally | 2.2, 5.3 | ⏳ |

## Core-First Development Benefits

1. **User Feedback Early**: Get the most important page right before building everything else
2. **Design System Validation**: Test your design system on the most complex page first
3. **Efficient Iteration**: Changes to core page inform decisions for other pages
4. **Clear Priorities**: Focus effort where it matters most
5. **Reduced Rework**: Avoid building pages that might change based on core page decisions

## Next Steps After Static Pages Complete
- Replace Structs with ActiveRecord models
- Add authentication and authorization
- Implement forms and CRUD operations
- Add dynamic features (search, filtering)
- Enhance with real-time updates 