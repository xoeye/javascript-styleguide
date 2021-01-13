# JavaScript Style Guide

> An opinionated and adequately reasonable guide to writing JavaScript

## Naming

### File/Directory naming standards

#### PascalCase

- Component file names
- If a folder that functions as a component (i.e. contains an index.js which exports a component)
- Stories files (`.stories.js`)
- Test files of components (`.test.js`, `.spec.js`)

#### kebab-case

- Directory names

#### camelCase

- Utility files

#### MACRO_CASE

- String constants
- Number constants

### Boolean naming standards

- Boolean variables should be prefixed with "is", "has", "should", or another similar modal auxiliary verb.

### Function naming standards

- **Event Functions** - functions called by an event should be prefaced with the word `on`. (i.e. If there is an `onChange` event on an element or component, the function passed as the `onChange` prop should be be something _like_ `onInputChange`)
- **Return Functions** - functions that return a value should generally be prefaced with `get`. (i.e. If a function returns an object of Knowledgebase Collections, the function would be called `getKbCollections` while the value returned could be stored as `kbCollections`, like `const kbCollections = getKbCollections()`)

### Component naming standards

#### Parent-child relationships

- Child components that are tightly coupled with their parent should include the parent component name as a prefix.

- If a component only makes sense in the context of a single parent component, that relationship should be evident in its name.

- This naming convention should continue down the chain of parent/child relationships between components. For example if I have a `AppDrawer` component, which has a component which contains a list of navigation links called `AppDrawerNav`, then its child link component would be named `AppDrawerNavLinks`.

#### Order of words

- Component names should start with the highest-level (often most general) words and end with descriptive modifying words. For example...

```
components/
  app/
    AppDrawer.js
    AppDrawerFooter.js
    AppDrawerHeader.js
    AppDrawerHeaderLogo.js
    AppDrawerNav.js
    AppDrawerNavLink.js
```

- Do not place the modifier words at the beginning of the component name. Although it may read more like plain english this way, it will cause your components to be unorganized in the code editor, as well as increase the possibility of naming conflicts.

<!-- These are bad examples from a previous styleguide, TODO: grab better examples from Vision codebase -->

```
👎 BAD
components/
  ClearSearchButton.js
  LaunchOnStartupCheckbox.js
  RunSearchButton.js
  SearchInput.js
  TermsCheckbox.js
```

```
👍 GOOD
components/
  SearchButtonClear.js
  SearchButtonRun.js
  SearchInputQuery.js
  SettingsCheckboxTerms.js
  SettingsCheckboxLaunchOnStartup.js
```

---

## Directory structure

### Each component folder or subfolder should have tests and stories folders

- Each folder containing component files should contain a `__tests__` folder and a `__stories__` folder.

---

## Exports

### Prefer named exports

Prefer using named over default exports whenever possible. Named exports have the benefit of making sure that variable names are searcheable throughout the codebase and removes the possibility of renaming on import. This concept is also known as passing the [Grep Test](http://jamie-wong.com/2013/07/12/grep-test/).

There are many instances in our existing codebase that commonly use default exports. Therefore, in any new code named exports should be used, and default exports should be converted to named when appropriate.

---
## Testing

### Component unit tests

- All components should have a coresponding test file.
- Component tests should not test implementation details, but rather test user interaction.
- Unique UI functionality should be the primary concern for tests.

### Stories and Storybook

- All components should be developed with a corresponding story.
- Each stories file should contain at least one "Default" story which should function as a playground for changing the states of the component.
- Additional stories should be written to visually test each of the possible states of the component.

### Storyshots

- Storyshots is a tool which creates snapshots of all of our rendered component stories.
- If any changes have been made to any returned JSX or the UI in general, new snapshots must be created before a PR can be merged.
- Storyshots are used to visualize changes in the Chromatic Visual Regression Testing Suite, and allow for easily viewing visual diffs in a branch.
