# Comprehensive Storybook Codebase with Accessibility-First Design, Multiple Themes, AG Grid, Tailwind CSS, and Design Tokens Managed by Style Dictionary

**Context:**  
You are a senior front-end developer tasked with building a complete, production-ready codebase. This project must include a Storybook instance that serves as a gallery for **all Mantine UI components** (from `@mantine/core`), along with an AG Grid example. The design must follow accessibility-first principles (WCAG 2.2 compliant) as accessibility is the primary design principle in our organization. In addition, the project must include:

- An **enhanced skip navigation** (skip-nav) component based on [PayPal’s SkipTo](https://github.com/paypal/skipto).
- Support for **multiple themes**: light, dark, solarized-light, solarized-dark, monokai, dracula, and tomorrow; these themes will be managed via design tokens using Style Dictionary.
- An **accessibility settings** component that allows users to adjust text size, spacing, font-family (for headings and paragraphs), line-height, and paragraph spacing.
- Integration of **Tailwind CSS** for styling.
- **Component tests using Cypress** (with plugins like `cypress-axe` for automated accessibility audits).

Below is a detailed, step-by-step task list that an AI coding agent can follow to implement this project. Each task includes checkboxes for individual substeps along with detailed instructions for Storybook story states and Cypress tests.

---

1. **Set Up the Project Structure**
   - [ ] **Create the Root Project Directory.**
   - [ ] **Create the Following Folders and Files:**
     - [ ] **`.storybook/` Folder:**
       - [ ] Create `main.js`
       - [ ] Create `preview.js`
     - [ ] **`src/` Folder:**
       - [ ] Create `components/` folder  
         *(This folder will contain all React component files including Mantine UI components, AG Grid, SkipNav, and AccessibilitySettings.)*
       - [ ] Create `stories/` folder  
         *(This folder will contain all Storybook story files for each component.)*
       - [ ] Create `theme/` folder:
         - [ ] Create `tokens.json` *(or multiple theme token files like `light.json`, `dark.json`, etc.)*
         - [ ] Create `style-dictionary.config.js`
     - [ ] **Root-Level Configuration Files:**
       - [ ] Create `tailwind.config.js`
       - [ ] Create `postcss.config.js`
       - [ ] Create `package.json`

2. **Configure Storybook**
   - [ ] **Configure `.storybook/main.js`:**
     - [ ] Set the stories glob pattern to load files from `src/stories/**/*.stories.jsx`.
     - [ ] Include necessary addons (e.g., accessibility addon, controls addon).
   - [ ] **Configure `.storybook/preview.js`:**
     - [ ] Import the global CSS (including Tailwind CSS output).
     - [ ] Set up global decorators to apply themes and accessibility contexts if needed.
     - [ ] Ensure the preview supports switching between multiple themes via design tokens.

3. **Implement Design Tokens and Multiple Themes via Style Dictionary**
   - [ ] **Create Theme Token Files in `src/theme/`:**
     - [ ] Define tokens for each theme:
       - light
       - dark
       - solarized-light
       - solarized-dark
       - monokai
       - dracula
       - tomorrow
     - [ ] *Each token file or section in `tokens.json` should include:*
       - Color palette definitions (primary, secondary, background, text, etc.)
       - Typography settings (font families, font sizes, line-heights)
       - Spacing values (margins, paddings)
       - Any other variables needed for accessible, high-contrast interfaces
   - [ ] **Create `src/theme/style-dictionary.config.js`:**
     - [ ] Configure Style Dictionary to process the tokens.
     - [ ] Generate CSS variables for each theme that can be consumed by Tailwind CSS.
     - [ ] Organize the output (e.g., separate CSS files or a single file with theme-specific variable sets).

4. **Integrate Tailwind CSS**
   - [ ] **Create `tailwind.config.js`:**
     - [ ] Extend the default theme to include custom colors, fonts, and spacing from the design tokens.
     - [ ] Configure variants for focus and hover states to support accessibility.
   - [ ] **Create `postcss.config.js`:**
     - [ ] Set up PostCSS with the Tailwind CSS plugin and autoprefixer.

5. **Develop Comprehensive Mantine UI Components and Their Stories (Accessibility-First)**
   
   **Basic Controls:**
   1. **Button Component**
      - [ ] Create `src/components/Button.jsx` using `@mantine/core`'s Button.
      - [ ] Ensure the button uses semantic HTML and includes ARIA labels where applicable.
      - [ ] Create `src/stories/Button.stories.jsx` with these states:
        - [ ] **Default State:** Render a button labeled "Default Button".
        - [ ] **Primary State:** Render a button with primary styling (using the primary color from design tokens).
        - [ ] **Disabled State:** Render a button with the `disabled` attribute.
        - [ ] **Loading State:** Render a button with a loading spinner and the label "Loading...".
      - [ ] **Cypress Tests for Button:**
        - [ ] Write Cypress tests to verify button accessibility, ARIA attributes, and keyboard navigability.
        - [ ] Use `cypress-axe` to run an automated accessibility audit.
   
   2. **TextInput Component**
      - [ ] Create `src/components/TextInput.jsx` using `@mantine/core`'s TextInput.
      - [ ] Include proper labeling and error message handling (with ARIA attributes for error states).
      - [ ] Create `src/stories/TextInput.stories.jsx` with these states:
        - [ ] **Empty State:** Render with a placeholder "Enter text...".
        - [ ] **Filled State:** Render with a default value "Sample text".
        - [ ] **Error State:** Render with an error message ("Invalid input") and error styling.
      - [ ] **Cypress Tests for TextInput:**
        - [ ] Verify the input’s ARIA attributes and error state messaging using Cypress and `cypress-axe`.

   3. **Checkbox Component**
      - [ ] Create `src/components/Checkbox.jsx` using `@mantine/core`'s Checkbox.
      - [ ] Ensure proper labeling for screen readers.
      - [ ] Create `src/stories/Checkbox.stories.jsx` with these states:
        - [ ] **Unchecked State:** Render as default (unchecked).
        - [ ] **Checked State:** Render as pre-checked.
        - [ ] **Disabled State:** Render with the disabled attribute.
      - [ ] **Cypress Tests for Checkbox:**
        - [ ] Test keyboard navigability and label association.

   4. **Radio Component**
      - [ ] Create `src/components/Radio.jsx` using `@mantine/core`'s Radio.
      - [ ] Implement a single radio and a group with one pre-selected option.
      - [ ] Create `src/stories/Radio.stories.jsx` with these states:
        - [ ] **Default State:** Render a single unselected radio.
        - [ ] **Grouped State:** Render a group with one option selected.
      - [ ] **Cypress Tests for Radio:**
        - [ ] Verify group behavior and accessibility (e.g., proper use of ARIA roles).

   5. **Select Component**
      - [ ] Create `src/components/Select.jsx` using `@mantine/core`'s Select.
      - [ ] Ensure options are accessible (with appropriate ARIA attributes).
      - [ ] Create `src/stories/Select.stories.jsx` with these states:
        - [ ] **Default State:** Render with a list of options (e.g., "Option 1", "Option 2", "Option 3").
        - [ ] **Pre-selected State:** Render with one of the options selected by default.
      - [ ] **Cypress Tests for Select:**
        - [ ] Test dropdown behavior and option accessibility.

   **Display Components:**
   6. **Badge Component**
      - [ ] Create `src/components/Badge.jsx` using `@mantine/core`'s Badge.
      - [ ] Create `src/stories/Badge.stories.jsx` with these states:
        - [ ] **Default Badge:** Render a badge with text "New".
        - [ ] **Colored Badge:** Render a badge styled with a secondary color.
      - [ ] **Cypress Tests for Badge:**
        - [ ] Confirm text contrast and accessibility.
   
   7. **Avatar Component**
      - [ ] Create `src/components/Avatar.jsx` using `@mantine/core`'s Avatar.
      - [ ] Create `src/stories/Avatar.stories.jsx` with these states:
        - [ ] **Image Avatar:** Render an avatar displaying an image.
        - [ ] **Initials Avatar:** Render an avatar displaying initials (e.g., "AB") when no image is provided.
      - [ ] **Cypress Tests for Avatar:**
        - [ ] Verify that alt text or ARIA labels are provided for images.
   
   8. **Loader Component**
      - [ ] Create `src/components/Loader.jsx` using `@mantine/core`'s Loader.
      - [ ] Create `src/stories/Loader.stories.jsx` with these states:
        - [ ] **Default Loader:** Render with default size.
        - [ ] **Size Variations:** Render with small, medium, and large sizes.
      - [ ] **Cypress Tests for Loader:**
        - [ ] Ensure loader is announced appropriately (e.g., via ARIA-live regions if applicable).

   **Layout Components:**
   9. **Grid Component**
      - [ ] Create `src/components/Grid.jsx` using `@mantine/core`'s Grid.
      - [ ] Create `src/stories/Grid.stories.jsx` with these states:
        - [ ] **Responsive Layout:** Render a grid with several items that adjust based on viewport size.
      - [ ] **Cypress Tests for Grid:**
        - [ ] Verify that the grid layout is accessible and responsive.
   
   10. **Group Component**
       - [ ] Create `src/components/Group.jsx` using `@mantine/core`'s Group.
       - [ ] Create `src/stories/Group.stories.jsx` with these states:
         - [ ] **Aligned Items:** Render a group with evenly spaced items.
       - [ ] **Cypress Tests for Group:**
         - [ ] Confirm that spacing and focus order are accessible.
   
   11. **Stack Component**
       - [ ] Create `src/components/Stack.jsx` using `@mantine/core`'s Stack.
       - [ ] Create `src/stories/Stack.stories.jsx` with these states:
         - [ ] **Vertical Stack:** Render several items stacked vertically with defined spacing.
       - [ ] **Cypress Tests for Stack:**
         - [ ] Check that the vertical order is preserved and navigable via keyboard.
   
   12. **Container Component**
       - [ ] Create `src/components/Container.jsx` using `@mantine/core`'s Container.
       - [ ] Create `src/stories/Container.stories.jsx` with these states:
         - [ ] **Fixed Width Container:** Render with a max-width and centered content.
       - [ ] **Cypress Tests for Container:**
         - [ ] Verify container responsiveness and focus management for contained elements.

   **Feedback Components:**
   13. **Alert Component**
       - [ ] Create `src/components/Alert.jsx` using `@mantine/core`'s Alert.
       - [ ] Create `src/stories/Alert.stories.jsx` with these states:
         - [ ] **Info Alert:** Render an alert with informational text.
         - [ ] **Warning Alert:** Render an alert with a warning message.
         - [ ] **Error Alert:** Render an alert with an error message.
         - [ ] **Success Alert:** Render an alert with success confirmation.
       - [ ] **Cypress Tests for Alert:**
         - [ ] Verify that alerts have appropriate ARIA roles (e.g., `role="alert"`) and contrast.
   
   14. **Notification Component**
       - [ ] Create `src/components/Notification.jsx` using `@mantine/core`'s Notification.
       - [ ] Create `src/stories/Notification.stories.jsx` with these states:
         - [ ] **Auto-dismiss Notification:** Render a notification that auto-dismisses after a timeout.
         - [ ] **Manual Dismiss Notification:** Render a notification with a close button.
       - [ ] **Cypress Tests for Notification:**
         - [ ] Check for proper ARIA announcements and dismiss behavior.
   
   15. **Progress Component**
       - [ ] Create `src/components/Progress.jsx` using `@mantine/core`'s Progress.
       - [ ] Create `src/stories/Progress.stories.jsx` with these states:
         - [ ] **0% Progress:** Render with no progress.
         - [ ] **50% Progress:** Render at 50%.
         - [ ] **100% Progress:** Render as complete.
       - [ ] **Cypress Tests for Progress:**
         - [ ] Verify progress indicators are accessible (e.g., using ARIA attributes like `aria-valuenow`).

   **Overlays & Modals:**
   16. **Modal Component**
       - [ ] Create `src/components/Modal.jsx` using `@mantine/core`'s Modal.
         - [ ] Ensure semantic HTML for the dialog.
         - [ ] Add ARIA attributes such as `aria-modal`, `aria-labelledby`, and `aria-describedby`.
         - [ ] Implement focus trapping when the modal is open.
       - [ ] Create `src/stories/Modal.stories.jsx` with these states:
         - [ ] **Closed State:** Render with the modal hidden.
         - [ ] **Open State:** Render with the modal visible, including a title ("Example Modal") and sample content.
         - [ ] **Accessibility Check State:** Use the Storybook Accessibility addon to display automated results.
       - [ ] **Cypress Tests for Modal:**
         - [ ] Mount the Modal component via Cypress.
         - [ ] Run an automated accessibility audit using `cypress-axe`.
         - [ ] Verify focus trapping within the modal and proper ARIA attributes.
   
   17. **Popover Component**
       - [ ] Create `src/components/Popover.jsx` using `@mantine/core`'s Popover.
       - [ ] Create `src/stories/Popover.stories.jsx` with these states:
         - [ ] **Hidden State:** Render with the popover hidden by default.
         - [ ] **Visible State:** Render when triggered by a button click.
       - [ ] **Cypress Tests for Popover:**
         - [ ] Test that the popover becomes accessible upon trigger and that focus is managed.
   
   18. **Tooltip Component**
       - [ ] Create `src/components/Tooltip.jsx` using `@mantine/core`'s Tooltip.
       - [ ] Create `src/stories/Tooltip.stories.jsx` with these states:
         - [ ] **Hidden State:** Render with the tooltip not visible.
         - [ ] **Hover/Focus State:** Render the tooltip visible when hovering or focusing on the target element.
       - [ ] **Cypress Tests for Tooltip:**
         - [ ] Verify tooltip visibility on hover/focus and check ARIA attributes.
   
   19. **Drawer Component**
       - [ ] Create `src/components/Drawer.jsx` using `@mantine/core`'s Drawer.
       - [ ] Create `src/stories/Drawer.stories.jsx` with these states:
         - [ ] **Closed State:** Render with the drawer hidden.
         - [ ] **Open State:** Render with the drawer visible.
         - [ ] **Swipeable (if applicable):** Demonstrate swipe-to-close behavior.
       - [ ] **Cypress Tests for Drawer:**
         - [ ] Verify that the drawer traps focus and is navigable via keyboard.

   **Data Display Components:**
   20. **Table Component**
       - [ ] Create `src/components/Table.jsx` using `@mantine/core`'s Table.
       - [ ] Create `src/stories/Table.stories.jsx` with these states:
         - [ ] **Basic Table:** Render with headers (e.g., "Name", "Age", "Occupation") and multiple rows of sample data.
         - [ ] **Paginated Table (if applicable):** Render with pagination controls.
       - [ ] **Cypress Tests for Table:**
         - [ ] Check that table headers, cells, and pagination controls are accessible.
   
   21. **Card Component**
       - [ ] Create `src/components/Card.jsx` using `@mantine/core`'s Card.
       - [ ] Create `src/stories/Card.stories.jsx` with these states:
         - [ ] **Image Card:** Render with an image at the top, a title, and text content.
         - [ ] **Text Card:** Render with a title and paragraph text only.
       - [ ] **Cypress Tests for Card:**
         - [ ] Verify that card content is announced properly by screen readers.
   
   22. **Paper Component**
       - [ ] Create `src/components/Paper.jsx` using `@mantine/core`'s Paper.
       - [ ] Create `src/stories/Paper.stories.jsx` with these states:
         - [ ] **Default Paper:** Render with standard elevation.
         - [ ] **Elevated Paper:** Render with increased shadow or elevation settings.
       - [ ] **Cypress Tests for Paper:**
         - [ ] Confirm that the Paper component maintains accessible contrast and layout.

7. **Implement AG Grid Integration**
   - [ ] **Create AGGrid Component:**
     - [ ] Create `src/components/AGGridComponent.jsx` integrating AG Grid.
       - [ ] Define columns: "Name", "Age", "Address".
       - [ ] Include 5–10 rows of realistic sample data.
   - [ ] **Create AG Grid Story:**
     - [ ] Create `src/stories/AGGrid.stories.jsx` with these states:
       - [ ] **Initial State:** Render the grid populated with sample data.
       - [ ] **Interactive State:** Demonstrate sorting and filtering (e.g., clicking on column headers).
   - [ ] **Cypress Tests for AG Grid:**
     - [ ] Verify that grid cells are accessible and that interactive features (sorting, filtering) work via keyboard.

8. **Develop Enhanced Skip Navigation Component**
   - [ ] **Create SkipNav Component:**
     - [ ] Create `src/components/SkipNav.jsx` inspired by PayPal’s SkipTo.
       - [ ] Ensure it is keyboard-accessible, appears on focus, and includes appropriate ARIA roles/attributes.
   - [ ] **Create SkipNav Story:**
     - [ ] Create `src/stories/SkipNav.stories.jsx` with these states:
       - [ ] **Default State:** Render with skip-nav hidden until focused.
       - [ ] **Focused State:** Render with skip-nav visible and focusable, allowing users to jump to the main content area.
   - [ ] **Cypress Tests for SkipNav:**
     - [ ] Test that the skip-nav becomes visible on focus and that it correctly shifts focus to the main content.

9. **Create Accessibility Settings Component**
   - [ ] **Create AccessibilitySettings Component:**
     - [ ] Create `src/components/AccessibilitySettings.jsx` that includes controls for:
       - Text size adjustment
       - Spacing adjustment
       - Font-family selection for headings and paragraphs
       - Line-height adjustment
       - Paragraph spacing adjustment
     - [ ] Implement global state management (e.g., using React Context) so that changes apply across the application.
   - [ ] **Create Accessibility Settings Story:**
     - [ ] Create `src/stories/AccessibilitySettings.stories.jsx` with these states:
       - [ ] **Default Settings:** Render the settings panel with default values.
       - [ ] **Adjusted Settings:** Provide interactive controls (sliders, dropdowns) and a sample text block that updates dynamically to reflect changes.
   - [ ] **Cypress Tests for Accessibility Settings:**
     - [ ] Test that changes in the settings update the UI globally.
     - [ ] Verify that controls are accessible and that live regions announce changes if applicable.

10. **Ensure Overall Accessibility Compliance Across All Components**
    - [ ] **Review Each Component and Story:**
      - [ ] Confirm the use of semantic HTML.
      - [ ] Verify proper ARIA attributes and roles are in place.
      - [ ] Ensure full keyboard navigability.
      - [ ] Use the Storybook Accessibility addon to check contrast ratios and other WCAG 2.2 criteria.
    - [ ] **Automated Cypress Accessibility Tests:**
      - [ ] Integrate `cypress-axe` into the Cypress test suite.
      - [ ] Write tests that run accessibility audits for each component/story.

11. **Finalize Package Configuration and Documentation**
    - [ ] **Create/Update `package.json`:**
      - [ ] Include dependencies such as:
        - React and ReactDOM
        - @mantine/core
        - Tailwind CSS, PostCSS
        - Style Dictionary
        - @storybook/react and relevant addons
        - AG Grid (ag-grid-react, ag-grid-community)
        - Cypress and cypress-axe (for accessibility testing)
        - Additional libraries for state management and accessibility if needed
    - [ ] **Document the Project in a README.md File:**
      - [ ] Provide instructions for installing dependencies (`npm install` or `yarn install`).
      - [ ] Explain how to run Storybook (`npm run storybook`).
      - [ ] Detail how to run Cypress tests.
      - [ ] Describe how to use the accessibility settings and switch between themes.
      - [ ] Include notes on accessibility best practices followed.

12. **Run Final Checks and Tests**
    - [ ] **Build and Launch the Project:**
      - [ ] Verify the project builds without errors.
      - [ ] Test each Storybook story for correct rendering and functionality.
    - [ ] **Run Cypress End-to-End and Component Tests:**
      - [ ] Ensure all Cypress tests pass.
      - [ ] Confirm that accessibility audits report no critical issues.