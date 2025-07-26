# Oqtane Module Request - ToDo List

## MODULE DETAILS:
**Name:** ToDo
**Owner/Namespace:** MyCompany
**Description:** A feature-rich todo list module that allows users to create, manage, and track tasks with categories, due dates, and completion status

## FUNCTIONALITY:
- **Task Management:**
  - Create new tasks with title, description, due date, and priority
  - Edit existing tasks
  - Mark tasks as complete/incomplete
  - Delete tasks with confirmation
  - Bulk operations (mark multiple as complete, delete selected)

- **Organization Features:**
  - Task categories/tags (Work, Personal, Shopping, etc.)
  - Priority levels (High, Medium, Low)
  - Filter tasks by status (All, Active, Completed)
  - Sort by due date, priority, or creation date

- **User Experience:**
  - Responsive design for mobile/desktop
  - Real-time updates without page refresh
  - Progress indicators showing completion percentage
  - Overdue task highlighting
  - Search functionality to find specific tasks

## DATABASE REQUIREMENTS:
**Primary Entity - Task:**
- TaskId (int, primary key)
- ModuleId (int, foreign key to Oqtane Module)
- Title (string, required, max 200 chars)
- Description (text, optional)
- DueDate (datetime, optional)
- Priority (enum: Low=1, Medium=2, High=3)
- IsCompleted (bool, default false)
- CompletedOn (datetime, nullable)
- CreatedBy/CreatedOn/ModifiedBy/ModifiedOn (IAuditable)

**Secondary Entity - Category:**
- CategoryId (int, primary key)
- ModuleId (int, foreign key)
- Name (string, required, max 50 chars)
- Color (string, hex color code)
- CreatedBy/CreatedOn/ModifiedBy/ModifiedOn (IAuditable)

**Junction Entity - TaskCategory:**
- TaskId (int, foreign key)
- CategoryId (int, foreign key)
- Composite primary key

## USER INTERFACE:
**Main View (Index.razor):**
- Task summary dashboard (total, completed, overdue counts)
- Filter/sort controls (dropdown menus, search box)
- Task list with checkboxes, titles, due dates, priority indicators
- "Add Task" button
- Bulk action toolbar when items selected

**Add/Edit Form (Edit.razor):**
- Task title (required field with validation)
- Description (rich text area)
- Due date picker
- Priority selector (radio buttons or dropdown)
- Category multi-select with color indicators
- Save/Cancel buttons with form validation

**Settings Page (Settings.razor):**
- Default view preferences (filter, sort order)
- Category management (add/edit/delete categories)
- Task auto-cleanup settings (delete completed tasks after X days)
- Email notification preferences

## EXAMPLES:
Use these patterns from the examples/ folder (based on the Oqtane module template):
- **Client/Modules/[Owner].Module.[Module]/Index.razor** - For the main task list display with Pager component and ActionLink patterns
- **Client/Modules/[Owner].Module.[Module]/Edit.razor** - For the task creation/editing form with validation and ModuleBase inheritance
- **Client/Services/[Module]Service.cs** - For client-side service patterns with HTTP calls and authorization policy URLs
- **Server/Controllers/[Module]Controller.cs** - For REST API endpoints with proper ModuleControllerBase inheritance and authorization
- **Server/Repository/[Module]Repository.cs** - For data access patterns with Entity Framework and IDbContextFactory
- **Server/Repository/[Module]Context.cs** - For DbContext setup with multi-database support
- **Server/Migrations/01000000_InitializeModule.cs** - For database migration structure using MultiDatabaseMigration
- **Server/Migrations/EntityBuilders/[Module]EntityBuilder.cs** - For entity builder patterns with proper foreign keys and auditing
- **Shared/Models/[Module].cs** - For entity models implementing IAuditable with proper table attributes

## OQTANE SPECIFIC REQUIREMENTS:
- **Security Level:** Edit (users can manage their own tasks, module editors can manage all tasks)
- **Localization:** English (en), Spanish (es), French (fr)
- **Module Settings:** 
  - Default task view (All/Active/Completed)
  - Tasks per page (10/25/50)
  - Enable/disable categories feature
  - Auto-delete completed tasks after X days
- **Permissions:** 
  - View tasks (all authenticated users)
  - Add/Edit own tasks (authenticated users)
  - Manage all tasks (module editors)
  - Manage categories (module editors)

## OTHER CONSIDERATIONS:
**Performance:**
- Implement pagination for large task lists (use Oqtane Pager component)
- Add database indexes on commonly queried fields (ModuleId, IsCompleted, DueDate)
- Use async/await for all database operations

**User Experience:**
- Show loading indicators during CRUD operations
- Implement optimistic UI updates (mark complete immediately, rollback on error)
- Add keyboard shortcuts (Enter to quick-add task, Escape to cancel)
- Use Oqtane's built-in notification system for success/error messages

**Common AI Assistant Pitfalls to Avoid:**
- Don't forget to implement IAuditable on all entities
- Ensure all API endpoints have proper authorization attributes
- Include ModuleId checks in all repository methods for security
- Remember to add migration entity builders for proper database creation
- Don't skip localization resource files (.resx) - they're required for Oqtane modules
- Implement proper disposal of DbContext in repositories
- Use Oqtane's built-in ModuleBase and ServiceBase classes, don't create custom base classes

**Third-Party Integrations:**
- Consider adding calendar integration (export to ICS format)
- Optional: Email reminders for overdue tasks (using Oqtane's notification system)
- Optional: Import/export functionality (CSV, JSON formats)

**Browser Compatibility:**
- Ensure date pickers work across all modern browsers
- Test drag-and-drop functionality on touch devices
- Verify real-time updates work with SignalR (if implemented)

**Testing Requirements:**
- Unit tests for all repository methods
- Integration tests for API controllers
- Blazor component tests for key user interactions
- Database migration tests to ensure clean up/down operations