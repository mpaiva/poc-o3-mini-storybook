# Comprehensive Storybook Codebase – Accessibility-First, Design Tokens, and Automated Testing

This repository is a complete, production-ready codebase that demonstrates our approach to building a UI component library with **accessibility-first principles**. It integrates a full gallery of Mantine UI components, an AG Grid example, an enhanced skip navigation component, and an accessibility settings panel. All styling and theming are driven solely by design tokens managed via Style Dictionary, ensuring a single source of truth for all design decisions.

## Project Overview

This project was generated using an extensive prompt provided to the o3-mini model. The prompt (found in `prompt.md`) specifies detailed requirements including:

- **Comprehensive Component Coverage:** Every Mantine UI component is showcased via Storybook.
- **Accessibility-First Design:** All components are built to meet WCAG 2.2 standards. They include semantic HTML, ARIA attributes, focus management, and keyboard navigability.
- **Design Tokens:** All design decisions—colors, typography, spacing, etc.—are defined in centralized token files processed by Style Dictionary. These tokens feed directly into Tailwind CSS and component styling.
- **Multiple Themes:** The project supports several themes (light, dark, solarized-light, solarized-dark, monokai, dracula, and tomorrow) that are automatically applied via CSS variables.
- **Automated Testing:** Component tests using Cypress (with `cypress-axe` for accessibility audits) are included to verify that each component adheres to our strict standards.

## How We Use the Prompt to Test the o3-mini Model

The requirements outlined in `prompt.md` are used as the specification for the o3-mini model. The testing process includes:

1. **Input Validation:**  
   We provide the prompt (with detailed checkboxes and steps) to the o3-mini model to generate a complete, self-contained project.  
   *Our goal is to ensure that the output meets every requirement listed in the prompt.*

2. **Automated Build and Verification:**  
   After the o3-mini model generates the codebase:
   - We run `npm install` (or `yarn install`) to install all dependencies.
   - We build the project to verify that it compiles without errors.
   - We launch Storybook using `npm run storybook` to visually inspect the component gallery and verify that all stories are present with the expected states.

3. **Accessibility Testing:**  
   We utilize the Storybook Accessibility addon to visually review each component's accessibility status.
   - Additionally, we run Cypress tests (with `cypress-axe`) to automatically audit each component for ARIA compliance, keyboard navigability, and color contrast.

4. **Design Tokens Verification:**  
   The integration of design tokens into both Tailwind CSS and the React components is verified by:
   - Inspecting the generated CSS (ensuring that tokens are correctly translated into CSS variables).
   - Confirming that components dynamically update based on token changes (e.g., switching themes).

5. **Continuous Integration:**  
   Our CI/CD pipeline runs automated builds and Cypress tests to ensure that any changes in the prompt or codebase do not break our accessibility-first standards.

## Getting Started

### Prerequisites

- **Node.js and npm/yarn:** Ensure you have Node.js installed.
- **Cypress:** For running component and end-to-end tests.

### Installation

1. Clone the repository:

   ```bash
   git clone https://your.repo.url/comprehensive-storybook.git
   cd comprehensive-storybook
   ```

2. Install dependencies:

   ```bash
   npm install
   # or
   yarn install
   ```

### Running Storybook

Launch Storybook to view the complete component gallery:

```bash
npm run storybook
```

Visit [http://localhost:6006](http://localhost:6006) in your browser to explore all components and their states.

### Running Cypress Tests

To open the Cypress test runner:

```bash
npm run cypress:open
```

Or run headless tests:

```bash
npm run cypress:run
```

These tests include:

- Automated accessibility audits (using `cypress-axe`).
- Functional tests for component states, focus management, and keyboard interactions.

## Project Structure

The project is organized as follows:

```text
/
├── .storybook/
│   ├── main.js
│   └── preview.js
├── src/
│   ├── components/          # All React components (Mantine UI, AG Grid, SkipNav, AccessibilitySettings)
│   ├── stories/             # Storybook stories for each component
│   └── theme/               # Design tokens and Style Dictionary configuration
│       ├── tokens.json      # Design tokens (or separate token files per theme)
│       └── style-dictionary.config.js
├── tailwind.config.js       # Tailwind CSS configuration integrated with design tokens
├── postcss.config.js        # PostCSS configuration
└── package.json             # Project configuration and dependencies
```

## How to Use These Requirements to Test the o3-mini Model

1. **Review the Prompt:**  
   Open `prompt.md` to see the full list of requirements and detailed task lists that the o3-mini model used to generate the codebase.

2. **Generate Codebase:**  
   Use the o3-mini model by providing the prompt. The generated output should include all the files and configurations specified.

3. **Verify Compliance:**  
   - Check that every component meets the defined requirements, especially in terms of accessibility (ARIA, keyboard navigation, etc.).
   - Confirm that design tokens are used consistently across Tailwind CSS, components, and themes.
   - Run the Cypress tests to verify functional and accessibility requirements.

4. **Feedback Loop:**  
   Use any discrepancies between the generated output and the prompt requirements as feedback to improve the prompt. This iterative process ensures that the o3-mini model delivers a codebase that fully meets our organizational priorities.

## Conclusion

This repository is both a demonstration of our UI component standards and a test harness for verifying that our design tokens drive every aspect of our application. By combining detailed prompt requirements, Storybook for visual validation, and Cypress for automated testing, we ensure that the generated codebase not only looks great but also meets the highest standards of accessibility and consistency.

Happy Coding.
