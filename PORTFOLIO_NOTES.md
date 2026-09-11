# Portfolio Notes

This repository contains a reusable Vue 2 search/filter component built around a tag-based filtering pattern. It supports a configurable dropdown, custom filter content through scoped slots, localization, event-driven parent/child communication, and integration with Element UI.

## What this project demonstrates

- Building a reusable Vue component rather than a page-specific feature
- Designing component APIs through props, events, scoped slots, and `v-model`
- Managing derived UI state and synchronized parent/child state
- Supporting configurable behavior such as submit-on-enter, submit-on-item, reset behavior, and click-away handling
- Adding localization support with English/German fallbacks
- Packaging a Vue component for distribution
- Using Storybook for component examples and documentation
- Release/tooling work with Semantic Release, Commitizen, ESLint, and CircleCI

## Stack

Vue 2 · Element UI · Storybook · Vue CLI · ESLint · Semantic Release · Commitizen · CircleCI

## Context

This is an older Vue 2 component library, so I treat it as historical work rather than a current framework recommendation. What still matters to me in the project is the component-design thinking: defining a clean interface, keeping the component reusable, and giving consuming code enough flexibility without tying the implementation to one screen or workflow.
