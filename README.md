# Vue Search Filter

A reusable Vue 2 search/filter component built around a tag-based filtering pattern. The component supports configurable dropdown content, scoped slots, localization, event-driven state updates, and integration with Element UI.

This is an older Vue 2 project, so I treat it as historical work rather than a current framework recommendation. What I still like about it is the component-design problem it solves: creating a reusable interface that can support different filter controls without being tied to one screen or workflow.

## What this project demonstrates

- Reusable Vue component design
- Props, events, scoped slots, and `v-model` integration
- Parent/child state synchronization
- Configurable submit/reset/click-away behavior
- English/German localization support
- Storybook-driven component examples
- Library packaging with Vue CLI
- Release workflow using Semantic Release and Commitizen
- Linting and CI tooling

## Stack

Vue 2 · Element UI · Storybook · Vue CLI · ESLint · Semantic Release · Commitizen · CircleCI

## Install

```bash
npm install --save @tillhub/vue-search-filter
```

## Usage

Please see `src/stories` for a complete example. The component styles need to be imported separately, and this version assumes Element UI is available in the consuming application.

To run the examples locally:

```bash
npm run storybook
```

```html
<template>
  <th-search-filter
    @submit="handleSubmit"
    @reset="handleReset"
    :width="500"
    locale="de"
    resetButtonText="Reset now"
    input-placeholder="Search in customer names"
  >
    <template slot="dropdown-content" slot-scope="{input, addTag}">
      <branch-filter :input="input" :add-tag="addTag"/>
      <status-filter :input="input" :add-tag="addTag"/>
      <active-switch :input="input" :add-tag="addTag"/>
      <date-picker :input="input" :add-tag="addTag"/>
    </template>
  </th-search-filter>
</template>

<script>
import ThSearchFilter from '../src/index.vue'
import BranchFilter from './BranchFilter.vue'
import StatusFilter from './StatusFilter.vue'
import ActiveSwitch from './ActiveSwitch.vue'
import DatePicker from './DatePicker.vue'

export default {
  components: {
    ThSearchFilter,
    BranchFilter,
    StatusFilter,
    ActiveSwitch,
    DatePicker
  },
  methods: {
    handleSubmit (result) {
      console.log('submit', result)
    },
    handleReset () {
      console.log('reset')
    }
  }
}
</script>
```

## Attributes

| Attribute | Type | Required | Example | Default | Description |
|---|---|---|---|---|---|
| width | number | no | 500 | 460 | Sets fixed width of component in pixels; minimum is 350 |
| locale | string | no | `de` | `en` | Supported locales are German and English |
| inputPlaceholder | string | no | `Search in products` | `Search` | Sets the input placeholder |
| searchButtonText | string | no | `Submit` | `Search` | Sets custom submit-button text |
| resetButtonText | string | no | `Reset` | `Cancel` | Sets custom reset-button text |

## Events

| Event | Description | Params |
|---|---|---|
| submit | Triggered when the user submits the search | filters |
| reset | Triggered when the filter is reset | -- |
| close-dropdown | Triggered when the dropdown closes | -- |

## Scoped slot

The component exposes a `dropdown-content` scoped slot so consuming code can supply its own filter controls. The slot receives the current input state and an `addTag` function, allowing child filters to communicate changes back to the parent component without hard-coding specific filter types into the library.

| Name | Type | Description |
|---|---|---|
| input | object | Current filter/tag state exposed to slot content |
| addTag | function | Adds or replaces a filter tag in the parent component |
