1. Ruby Style Guide Compliance
  General Rule: Follow the Ruby Style Guide by default. This includes guidelines on syntax, naming, and structure.
  Indentation: Use two spaces per indentation level (no tabs).
  Line Length: Keep lines to a maximum of 80 characters where possible.
  Spaces: Use spaces around operators, after commas, colons and semicolons, around { and before }.

2. Rails-Specific Conventions
  Naming Conventions:
  - Classes and Modules: Use CamelCase for classes and modules. For example, InvoiceItem.
  - Database Tables: Use snake_case and pluralize table names. For example, invoice_items.
  - Model Names: Singular with the first letter capitalized. For example, InvoiceItem.
  - Controller Names: Pluralized, since they typically manage multiple instances of a model. For example, InvoiceItemsController.
  - Routing: Use RESTful routes where applicable.

3. Models
  - Validations: Group validations in your model and keep them at the top.
    ```ruby
    class User < ApplicationRecord
     validates :name, presence: true
     validates :email, presence: true, uniqueness: true
    end
    ```
  - Associations: Place ActiveRecord associations right after validations.
    ```ruby
    has_many :orders
    belongs_to :account
    ```

4. Controllers
  - Thin Controllers: Keep logic out of controllers as much as possible. Aim for thin controllers and thick models.
  - Actions: Follow the standard CRUD actions sequence: index, show, new, edit, create, update, destroy.

5. Views
  - Using Partials: Refactor repeated view code into partials.
  - Helpers: Use helpers for complex logic instead of cluttering your views.

6. Tests
  - DRY (Don't Repeat Yourself): Use before actions and factories to set up common contexts.
  - Naming: Name the test files corresponding to their tested files. For instance, `models/user_test.rb` for `models/user.rb`.

7. Database Migrations
  - Reversible Migrations: Ensure migrations are reversible. Use `change` method when possible over `up` and `down`.
  - Indices: Add database indices for foreign keys and frequently queried fields.

8. File Structure
  - Logical Organization: Organize files logically and keep related files close in the directory structure.
  - Load Paths: Be mindful of autoload paths and eager load paths in `config/application.rb`.

9. Security
  - Parameter Sanitization: Use strong parameters to avoid mass-assignment vulnerabilities.
    ```ruby
    private
    def user_params
     params.require(:user).permit(:name, :email)
    end
    ```
  - Session Security: Treat session data cautiously, avoid storing sensitive data.

10. Git Usage
   - Commits: Make small, frequent commits that reflect a single cohesive feature or fix.
   - Branching: Use feature branches for development and merge them into the main branch upon completion.

This cheat sheet covers essential guidelines that Rails developers should adhere to for maintaining a clean, efficient, and secure codebase. Always keep up to date with the latest Rails versions and community best practices for optimal development.