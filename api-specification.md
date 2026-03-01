# API Specification — react-ubiquitous UI Config

**Library version: `1.2.0`** · npm package: [`react-ubiquitous`](https://www.npmjs.com/package/react-ubiquitous)

> **The frontend is just a human-readable version of the API response.**

This document is generated automatically from the TypeScript type definitions in
`src/lib/types/` by running:

```bash
python generate_api_spec.py
```

It is the **definitive, framework-neutral reference** for the JSON contract that any
backend — regardless of language or runtime — must produce so that a
`react-ubiquitous` frontend can render a complete, interactive application.

## Table of Contents

- [Overview](#overview)
- [UIStageConfig](#uistageconfig)
- [UIPageConfig](#uipageconfig)
- [UISectionConfig](#uisectionconfig)
  - [BaseSectionConfig (shared fields)](#basesectionconfig-shared-fields)
  - [`layout: "flex"` — FlexSectionConfig](#layout:-"flex"-—-flexsectionconfig)
  - [`layout: "grid"` — GridSectionConfig](#layout:-"grid"-—-gridsectionconfig)
  - [`layout: "hero"` — HeroSectionConfig](#layout:-"hero"-—-herosectionconfig)
  - [`layout: "list-detail"` — ListDetailSectionConfig](#layout:-"list-detail"-—-listdetailsectionconfig)
  - [`layout: "tree-view"` — TreeViewSectionConfig](#layout:-"tree-view"-—-treeviewsectionconfig)
  - [`layout: "chat"` — ChatSectionConfig](#layout:-"chat"-—-chatsectionconfig)
  - [`layout: "media"` — MediaSectionConfig](#layout:-"media"-—-mediasectionconfig)
  - [`layout: "navbar"` — NavbarSectionConfig](#layout:-"navbar"-—-navbarsectionconfig)
  - [`layout: "sidebar"` — SidebarSectionConfig](#layout:-"sidebar"-—-sidebarsectionconfig)
  - [`layout: "breadcrumbs"` — BreadcrumbsSectionConfig](#layout:-"breadcrumbs"-—-breadcrumbssectionconfig)
  - [`layout: "pagination"` — PaginationSectionConfig](#layout:-"pagination"-—-paginationsectionconfig)
  - [`layout: "stepper"` — StepperSectionConfig](#layout:-"stepper"-—-steppersectionconfig)
  - [`layout: "tabs"` — TabsSectionConfig](#layout:-"tabs"-—-tabssectionconfig)
  - [`layout: "alert"` — AlertSectionConfig](#layout:-"alert"-—-alertsectionconfig)
  - [`layout: "progress"` — ProgressSectionConfig](#layout:-"progress"-—-progresssectionconfig)
  - [`layout: "skeleton"` — SkeletonSectionConfig](#layout:-"skeleton"-—-skeletonsectionconfig)
  - [`layout: "toast"` — ToastSectionConfig](#layout:-"toast"-—-toastsectionconfig)
  - [`layout: "modal"` — ModalSectionConfig](#layout:-"modal"-—-modalsectionconfig)
  - [`layout: "drawer"` — DrawerSectionConfig](#layout:-"drawer"-—-drawersectionconfig)
  - [`layout: "tooltip"` — TooltipSectionConfig](#layout:-"tooltip"-—-tooltipsectionconfig)
  - [`layout: "popover"` — PopoverSectionConfig](#layout:-"popover"-—-popoversectionconfig)
  - [`layout: "accordion"` — AccordionSectionConfig](#layout:-"accordion"-—-accordionsectionconfig)
  - [`layout: "collapse"` — CollapseSectionConfig](#layout:-"collapse"-—-collapsesectionconfig)
  - [`layout: "divider"` — DividerSectionConfig](#layout:-"divider"-—-dividersectionconfig)
  - [`layout: "card"` — CardSectionConfig](#layout:-"card"-—-cardsectionconfig)
  - [`layout: "table"` — TableSectionConfig](#layout:-"table"-—-tablesectionconfig)
  - [`layout: "badge"` — BadgeSectionConfig](#layout:-"badge"-—-badgesectionconfig)
  - [`layout: "avatar"` — AvatarSectionConfig](#layout:-"avatar"-—-avatarsectionconfig)
  - [`layout: "timeline"` — TimelineSectionConfig](#layout:-"timeline"-—-timelinesectionconfig)
  - [`layout: "stat"` — StatSectionConfig](#layout:-"stat"-—-statsectionconfig)
  - [`layout: "empty-state"` — EmptyStateSectionConfig](#layout:-"empty-state"-—-emptystatesectionconfig)
  - [`layout: "code-block"` — CodeBlockSectionConfig](#layout:-"code-block"-—-codeblocksectionconfig)
  - [`layout: "chart"` — ChartSectionConfig](#layout:-"chart"-—-chartsectionconfig)
  - [`layout: "iframe"` — IframeSectionConfig](#layout:-"iframe"-—-iframesectionconfig)
- [UIElementConfig](#uielementconfig)
  - [BaseElementConfig (shared fields)](#baseelementconfig-shared-fields)
  - [`type: "input"` — InputElementConfig](#type:-"input"-—-inputelementconfig)
  - [`type: "checkbox"` — CheckboxElementConfig](#type:-"checkbox"-—-checkboxelementconfig)
  - [`type: "radio"` — RadioElementConfig](#type:-"radio"-—-radioelementconfig)
  - [`type: "textarea"` — TextareaElementConfig](#type:-"textarea"-—-textareaelementconfig)
  - [`type: "select"` — SelectElementConfig](#type:-"select"-—-selectelementconfig)
  - [`type: "button"` — ButtonElementConfig](#type:-"button"-—-buttonelementconfig)
  - [`type: "label"` — LabelElementConfig](#type:-"label"-—-labelelementconfig)
  - [`type: "fieldset"` — FieldsetElementConfig](#type:-"fieldset"-—-fieldsetelementconfig)
  - [`type: "datalist"` — DatalistElementConfig](#type:-"datalist"-—-datalistelementconfig)
  - [`type: "output"` — OutputElementConfig](#type:-"output"-—-outputelementconfig)
  - [`type: "datepicker"` — DatePickerElementConfig](#type:-"datepicker"-—-datepickerelementconfig)
  - [`type: "multiselect"` — MultiSelectElementConfig](#type:-"multiselect"-—-multiselectelementconfig)
  - [`type: "autocomplete"` — AutocompleteElementConfig](#type:-"autocomplete"-—-autocompleteelementconfig)
  - [`type: "fileupload"` — FileUploadElementConfig](#type:-"fileupload"-—-fileuploadelementconfig)
  - [`type: "colorpicker"` — ColorPickerElementConfig](#type:-"colorpicker"-—-colorpickerelementconfig)
  - [`type: "rangeslider"` — RangeSliderElementConfig](#type:-"rangeslider"-—-rangesliderelementconfig)
  - [`type: "rating"` — RatingElementConfig](#type:-"rating"-—-ratingelementconfig)
  - [`type: "otpinput"` — OtpInputElementConfig](#type:-"otpinput"-—-otpinputelementconfig)
  - [`type: "phoneinput"` — PhoneInputElementConfig](#type:-"phoneinput"-—-phoneinputelementconfig)
  - [`type: "custom"` — CustomElementConfig](#type:-"custom"-—-customelementconfig)
- [Validation Rules](#validation-rules)
  - [`ValidationGroup`](#validationgroup)
- [Supporting Types](#supporting-types)
  - [`RadioOption`](#radiooption)
  - [`SelectOption`](#selectoption)
  - [`SelectOptGroup`](#selectoptgroup)
  - [`PhoneCountryOption`](#phonecountryoption)
  - [`NavLink`](#navlink)
  - [`SidebarItem`](#sidebaritem)
  - [`BreadcrumbItem`](#breadcrumbitem)
  - [`StepperStep`](#stepperstep)
  - [`TabItem`](#tabitem)
  - [`AccordionPanel`](#accordionpanel)
  - [`ListDetailItem`](#listdetailitem)
  - [`ListEndpointConfig`](#listendpointconfig)
  - [`FilterEndpointConfig`](#filterendpointconfig)
  - [`DetailEndpointConfig`](#detailendpointconfig)
  - [`DetailPage`](#detailpage)
  - [`TreeViewNode`](#treeviewnode)
  - [`MediaItem`](#mediaitem)
  - [`TableColumn`](#tablecolumn)
  - [`BadgeItem`](#badgeitem)
  - [`AvatarItem`](#avataritem)
  - [`TimelineEvent`](#timelineevent)
  - [`StatItem`](#statitem)
  - [`ChatMessage`](#chatmessage)
  - [`ChatConversation`](#chatconversation)
  - [`ChartDataPoint`](#chartdatapoint)
  - [`ChartSeries`](#chartseries)
- [Enum / Literal Type Reference](#enum--literal-type-reference)
  - [`InputType`](#inputtype)
  - [`ResizeBehaviour`](#resizebehaviour)
  - [`ButtonVariant`](#buttonvariant)
  - [`ButtonSize`](#buttonsize)
  - [`UITheme`](#uitheme)
  - [`UIPageTransition`](#uipagetransition)
- [I18n Message Overrides (`I18nMessages`)](#i18n-message-overrides-i18nmessages)


## Overview

### JSON Object Hierarchy

```
UIStageConfig              ← top-level container
 └─ UIPageConfig[]         ← tabs / pages inside the stage
     └─ UISectionConfig[]  ← layout containers (flex | grid | hero | …)
         └─ UIElementConfig[]  ← individual form controls / display elements
```

Every layer is a plain JSON object.  The backend is responsible for returning
the full `UIStageConfig` tree; the frontend renders it without any code changes.


## UIStageConfig

A stage is the top-level container — analogous to a worksheet in Excel. It holds an ordered set of pages (tabs).

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique stage identifier. |
| `title` | `string` |  |  | Optional heading displayed above the tab bar. |
| `description` | `string` |  |  | Optional description / subtitle for the stage. |
| `defaultPageId` | `string` |  |  | id of the page to display on first render. Falls back to the first page (by `order`) when omitted. |
| `pages` | `UIPageConfig[]` | ✔ |  | Ordered list of pages (tabs) in this stage. |
| `theme` | `UITheme` — one of: `"html"`, `"custom"`, `"light"`, `"dark"` |  | `Tailwind light-mode classes are applied` | Rendering theme for the stage. - `light`  — default Tailwind light-mode classes are applied. - `dark`   — default Tailwind dark-mode classes are applied. - `html`   — renders plain HTML with no extra CSS. - `custom` — CSS classes are supplied by the API via `className`. When omitted the stage renders with the host application's ambient styles. |
| `className` | `string` |  |  | Additional CSS class names applied to the stage wrapper. Typically used when `theme` is `"custom"` so the API can supply the exact classes required. |
| `pageTransition` | `UIPageTransition` — one of: `"none"`, `"fade"`, `"slide-left"`, `"slide-right"` |  |  | Animation played when the active page (tab) changes. Defaults to `'none'` (instant switch). |


**`UITheme` values**

| Value |
|-------|
| `"html"` |
| `"custom"` |
| `"light"` |
| `"dark"` |


**`UIPageTransition` values**

| Value |
|-------|
| `"none"` |
| `"fade"` |
| `"slide-left"` |
| `"slide-right"` |


## UIPageConfig

A page is a named, ordered collection of sections. In the stage view, each page corresponds to one tab.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique page identifier within the stage. |
| `title` | `string` | ✔ |  | Tab label / page heading shown to the user. |
| `description` | `string` |  |  | Optional longer description shown as a subtitle or tooltip on the tab. |
| `icon` | `string` |  |  | Icon identifier for the tab (e.g. a Lucide icon name like `"user"`, `"settings"`). Renderer resolves the icon by name. |
| `order` | `number` | ✔ |  | Sort order within the parent stage (ascending). |
| `sections` | `UISectionConfig[]` | ✔ |  | Ordered list of sections that make up this page. |
| `className` | `string` |  |  | Additional CSS class names applied to the page wrapper. |
| `visible` | `boolean` |  | `true` | Whether this page is visible. Hidden pages are still part of the config but not rendered as tabs. Defaults to `true`. |


## UISectionConfig

Discriminate on the `layout` field.  Every section config also includes
the **BaseSectionConfig** base fields listed first.


### BaseSectionConfig (shared fields)

All section configs inherit these fields:

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique section identifier within the page. |
| `title` | `string` |  |  | Optional visible title rendered above the section. |
| `description` | `string` |  |  | Optional description / subtitle rendered below the title. |
| `order` | `number` |  |  | Render order within the parent page (ascending). |
| `className` | `string` |  |  | Additional CSS class names on the section wrapper. |
| `style` | `StyleObject` |  |  | Inline styles on the section wrapper. |
| `elements` | `UIElementConfig[]` | ✔ |  | Ordered list of UI element configs that live in this section. |


### `layout: "flex"` — FlexSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'flex'` | ✔ |  |  |
| `flexDirection` | `FlexDirection` |  |  | Maps to CSS `flex-direction`. Default: `"row"`. |
| `flexWrap` | `FlexWrap` |  |  | Maps to CSS `flex-wrap`. Default: `"wrap"`. |
| `justifyContent` | `JustifyContent` |  |  | Maps to CSS `justify-content`. Default: `"flex-start"`. |
| `alignItems` | `AlignItems` |  |  | Maps to CSS `align-items`. Default: `"stretch"`. |
| `alignContent` | `AlignContent` |  |  | Maps to CSS `align-content` (multi-line flex containers). |
| `gap` | `string | number` |  |  | Shorthand gap (row and column). e.g. `"1rem"`, `"8px"`. |
| `rowGap` | `string | number` |  |  | Row gap only. Overrides `gap` for rows when provided. |
| `columnGap` | `string | number` |  |  | Column gap only. Overrides `gap` for columns when provided. |


### `layout: "grid"` — GridSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'grid'` | ✔ |  |  |
| `gridTemplateColumns` | `string` |  |  | Maps to CSS `grid-template-columns`. e.g. `"repeat(3, 1fr)"`, `"1fr 2fr 1fr"`, `"200px auto"`. |
| `gridTemplateRows` | `string` |  |  | Maps to CSS `grid-template-rows`. e.g. `"auto"`, `"100px 1fr"`. |
| `gap` | `string | number` |  |  | Shorthand gap (row and column). |
| `rowGap` | `string | number` |  |  | Row gap only. |
| `columnGap` | `string | number` |  |  | Column gap only. |
| `alignItems` | `AlignItems` |  |  | Maps to CSS `align-items` for all grid cells. |
| `justifyItems` | `JustifyItems` |  |  | Maps to CSS `justify-items` for all grid cells. |


### `layout: "hero"` — HeroSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'hero'` | ✔ |  |  |
| `subtitle` | `string` |  |  | Subtitle shown below the main title. |
| `backgroundType` | `'color' | 'gradient' | 'image'` |  |  | Which background mode is active. - `'color'`    — solid `backgroundColor` - `'gradient'` — CSS linear-gradient built from `gradientFrom`/`gradientTo`/`gradientDirection` - `'image'`    — `backgroundImage` URL Default: `'gradient'` |
| `backgroundColor` | `string` |  |  | Solid background colour (CSS value). Used when `backgroundType === 'color'`. |
| `gradientFrom` | `string` |  |  | Gradient start colour. Default: `'#6366f1'`. |
| `gradientTo` | `string` |  |  | Gradient end colour. Default: `'#1e293b'`. |
| `gradientDirection` | `string` |  |  | CSS gradient direction. Default: `'to bottom right'`. |
| `backgroundImage` | `string` |  |  | Background image URL. Used when `backgroundType === 'image'`. |
| `overlay` | `boolean` |  |  | Dark overlay rendered on top of the background. |
| `overlayOpacity` | `number` |  | `40` | Overlay opacity 0–100. Default: `40`. |
| `minHeight` | `string` |  |  | Minimum height of the hero section. Default: `'320px'`. |
| `textAlign` | `'left' | 'center' | 'right'` |  |  | Horizontal content alignment. Default: `'center'`. |
| `verticalAlign` | `'top' | 'center' | 'bottom'` |  |  | Vertical content position. Default: `'center'`. |
| `linkUrl` | `string` |  |  | URL for the CTA link. |
| `linkText` | `string` |  |  | Display text for the CTA link. Default: `'Read more'`. |
| `linkRelative` | `boolean` |  | `false` | When true the URL is treated as a relative path (same tab, no rel). Default: `false` (external). |


### `layout: "list-detail"` — ListDetailSectionConfig

A self-contained List & Detail view section. The left pane shows a searchable, paginated list of `listItems`. The right pane renders the section's `elements` as the detail panel.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'list-detail'` | ✔ |  |  |
| `listTitle` | `string` |  |  | Heading shown above the list pane. |
| `listWidth` | `string` |  |  | CSS width of the list pane. Default: `'260px'`. |
| `pageSize` | `number` |  | `100` | Number of items shown per page. Default: `100`. |
| `listItems` | `ListDetailItem[]` |  |  | Items in the left-hand list. |
| `listEndpoint` | `ListEndpointConfig` |  |  | Endpoint for fetching the paginated list with from / to / sort query params. |
| `filterEndpoint` | `FilterEndpointConfig` |  |  | Endpoint for searching / filtering the list by free text. |
| `detailEndpoint` | `DetailEndpointConfig` |  |  | Endpoint for loading detail data for the selected list item. |
| `detailPages` | `DetailPage[]` |  |  | Pages shown in the right-hand detail panel. Each page can contain multiple sections (grid / flex) with fields. When multiple pages are present a tab bar is shown above the detail area. Falls back to rendering flat `elements` when this array is empty / absent. |
| `virtualScrolling` | `boolean` |  | `false` | When `true`, the list pane uses `react-window` (FixedSizeList) to render only the visible rows, enabling efficient display of thousands of items without DOM overhead. Pagination is disabled when this flag is set. Default: `false`. |
| `virtualListHeight` | `number` |  | `400` | Height of the virtualized list container in pixels. Only applies when `virtualScrolling` is `true`. Default: `400`. |


### `layout: "tree-view"` — TreeViewSectionConfig

A self-contained Tree & Detail view section. The left pane shows an expandable/collapsible tree of `treeNodes`. The right pane renders the detail panel for the selected node. Two display modes are supported: - `'compact'` — reduced row height and icon size; best for deep / wide trees. - `'easy'`    — larger row height and icons; best for shallow trees. Detail loading mirrors `list-detail`: use `detailPages` with multi-section layouts or flat `elements` for simple cases.  When `detailEndpoint` is provided the component fires a GET request for the selected node's details.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'tree-view'` | ✔ |  |  |
| `treeTitle` | `string` |  |  | Heading shown above the tree pane. |
| `treeWidth` | `string` |  |  | CSS width of the tree pane. Default: `'260px'`. |
| `treeMode` | `'compact' | 'easy'` |  |  | Visual density of the tree pane. - `'compact'` — tighter spacing; recommended for long/deep trees. - `'easy'`    — more breathing room; recommended for small trees. Default: `'easy'`. |
| `treeNodes` | `TreeViewNode[]` |  |  | Root-level tree nodes (each may have nested `children`). |
| `detailEndpoint` | `DetailEndpointConfig` |  |  | Endpoint for loading detail data for the selected tree node. |
| `detailPages` | `DetailPage[]` |  |  | Pages shown in the right-hand detail panel. Each page can contain multiple sections (grid / flex) with fields. When multiple pages are present a tab bar is shown above the detail area. Falls back to rendering flat `elements` when this array is empty / absent. |


### `layout: "chat"` — ChatSectionConfig

A chat window section. The **left pane** shows a searchable list of conversations/groups (reusing the same list rendering as `list-detail`). The **right pane** shows the active conversation messages and a text area with a send button at the bottom.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'chat'` | ✔ |  |  |
| `listTitle` | `string` |  |  | Heading shown above the conversations list. Default: `'Messages'`. |
| `listWidth` | `string` |  |  | CSS width of the conversations pane. Default: `'280px'`. |
| `conversations` | `ChatConversation[]` |  |  | Conversations shown in the left pane. |
| `inputPlaceholder` | `string` |  |  | Placeholder text for the message input. Default: `'Type a message…'`. |
| `sendButtonText` | `string` |  |  | Label for the send button. Default: `'Send'`. |
| `currentUserName` | `string` |  |  | Display name used for messages sent by the current user. Default: `'You'`. |
| `messagesEndpoint` | `ChatMessagesEndpointConfig` |  |  | Endpoint for loading message history for the selected conversation. |
| `sendEndpoint` | `ChatSendEndpointConfig` |  |  | Endpoint for sending a new message to the selected conversation. |


### `layout: "media"` — MediaSectionConfig

A responsive, accessible carousel that shows a list of images, videos, or a mix of both.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'media'` | ✔ |  |  |
| `items` | `MediaItem[]` |  |  | Ordered list of media items. |
| `aspectRatio` | `string` |  |  | CSS `aspect-ratio` value for the carousel frame. Examples: `'16/9'`, `'4/3'`, `'1/1'`. Default: `'16/9'`. |
| `showArrows` | `boolean` |  | `true` | Show previous/next arrow buttons. Default: `true`. |
| `showDots` | `boolean` |  | `true` | Show dot navigation. Default: `true`. |


### `layout: "navbar"` — NavbarSectionConfig

A top app bar with a logo, navigation links, and a mobile hamburger toggle.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'navbar'` | ✔ |  |  |
| `logoText` | `string` |  |  | Text logo shown on the left side of the bar. |
| `logoUrl` | `string` |  |  | Image URL for a logo shown on the left side of the bar. |
| `links` | `NavLink[]` |  |  | Navigation links rendered in the bar. |
| `position` | `'static' | 'sticky' | 'fixed'` |  |  | CSS positioning mode for the bar. - `'static'`  — normal document flow (default) - `'sticky'`  — sticks to the top on scroll - `'fixed'`   — always visible at the top of the viewport |
| `theme` | `'light' | 'dark'` |  |  | Colour scheme. Default: `'light'`. |


### `layout: "sidebar"` — SidebarSectionConfig

A collapsible side navigation panel with nested item support.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'sidebar'` | ✔ |  |  |
| `items` | `SidebarItem[]` |  |  | Navigation items in the sidebar. |
| `defaultCollapsed` | `boolean` |  | `false` | Whether the sidebar starts collapsed. Default: `false`. |
| `collapsible` | `boolean` |  | `true` | Whether the user can toggle the collapsed state. Default: `true`. |
| `width` | `string` |  |  | CSS width of the expanded sidebar. Default: `'260px'`. |


### `layout: "breadcrumbs"` — BreadcrumbsSectionConfig

A hierarchical location trail (breadcrumb navigation).

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'breadcrumbs'` | ✔ |  |  |
| `items` | `BreadcrumbItem[]` |  |  | Ordered list of breadcrumb items (first = root, last = current page). |
| `separator` | `string` |  |  | Character or string rendered between crumbs. Default: `'/'`. |


### `layout: "pagination"` — PaginationSectionConfig

Page-number controls for navigating long lists.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'pagination'` | ✔ |  |  |
| `totalItems` | `number` | ✔ |  | Total number of items across all pages. |
| `pageSize` | `number` |  | `10` | Number of items per page. Default: `10`. |
| `currentPage` | `number` |  | `1` | Initially active page (1-based). Default: `1`. |
| `showFirstLast` | `boolean` |  | `false` | Show First / Last jump buttons. Default: `false`. |
| `showPrevNext` | `boolean` |  | `true` | Show Previous / Next buttons. Default: `true`. |
| `maxPageButtons` | `number` |  | `7` | Maximum number of page-number buttons to display before truncating. Default: `7`. |


### `layout: "stepper"` — StepperSectionConfig

A multi-step wizard progress indicator.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'stepper'` | ✔ |  |  |
| `steps` | `StepperStep[]` |  |  | Ordered list of steps. |
| `currentStep` | `number` |  | `0` | Zero-based index of the currently active step. Used as the initial value; the component manages state internally. Default: `0`. |
| `orientation` | `'horizontal' | 'vertical'` |  |  | Layout direction of the step indicators. Default: `'horizontal'`. |


### `layout: "tabs"` — TabsSectionConfig

A general-purpose tabbed content container. Unlike UIStage (which uses pages as tabs), this section renders tabs anywhere inside a page — including nested inside another section.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'tabs'` | ✔ |  |  |
| `tabs` | `TabItem[]` |  |  | The tab buttons and their associated content. |
| `defaultTabId` | `string` |  |  | `id` of the tab to show on first render. Falls back to the first tab. |


### `layout: "alert"` — AlertSectionConfig

Inline contextual message — error, warning, info, or success.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'alert'` | ✔ |  |  |
| `severity` | `'info' | 'success' | 'warning' | 'error'` |  |  | Visual severity of the alert. Default: `'info'`. |
| `dismissible` | `boolean` |  | `false` | Show a dismiss (×) button. Default: `false`. |
| `icon` | `boolean` |  | `true` | Show the severity icon. Default: `true`. |


### `layout: "progress"` — ProgressSectionConfig

Linear or circular loading / progress indicator.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'progress'` | ✔ |  |  |
| `variant` | `'linear' | 'circular'` |  |  | Variant of the progress indicator. Default: `'linear'`. |
| `value` | `number` |  | `0` | Current progress value (0–100). Default: `0`. |
| `showLabel` | `boolean` |  | `false` | Show the percentage label. Default: `false`. |
| `size` | `'sm' | 'md' | 'lg'` |  |  | Visual size preset. Default: `'md'`. |
| `color` | `string` |  |  | CSS color for the filled track. Default: `'#6366f1'`. |
| `indeterminate` | `boolean` |  | `false` | Indeterminate / animated mode (ignores `value`). Default: `false`. |


### `layout: "skeleton"` — SkeletonSectionConfig

Animated loading placeholder shown while content is fetching.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'skeleton'` | ✔ |  |  |
| `shape` | `'text' | 'rect' | 'circle'` |  |  | Shape of the skeleton block. Default: `'text'`. |
| `lines` | `number` |  | `3` | Number of text-line skeletons to render. Default: `3`. |
| `avatar` | `boolean` |  | `false` | Show a circular avatar skeleton before the lines. Default: `false`. |
| `width` | `string` |  |  | Explicit CSS width of the skeleton block. |
| `height` | `string` |  |  | Explicit CSS height of the skeleton block (used with `shape: 'rect'`). |


### `layout: "toast"` — ToastSectionConfig

Ephemeral notification that auto-dismisses after a configurable delay.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'toast'` | ✔ |  |  |
| `message` | `string` |  |  | Notification message text. |
| `severity` | `'info' | 'success' | 'warning' | 'error'` |  |  | Visual severity. Default: `'info'`. |
| `duration` | `number` |  | `4000` | Auto-dismiss delay in milliseconds. Set to `0` to disable auto-dismiss. Default: `4000`. |
| `position` | `'top-left' | 'top-center' | 'top-right' | 'bottom-left' | 'bottom-center' | 'bottom-right'` |  |  | Corner / edge of the viewport where the toast appears. Default: `'bottom-right'`. |
| `visible` | `boolean` |  | `true` | Whether the toast is visible on first render. Default: `true`. |


### `layout: "modal"` — ModalSectionConfig

Blocking overlay dialog with optional action content.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'modal'` | ✔ |  |  |
| `open` | `boolean` |  | `false` | Whether the modal is open on first render. Default: `false`. |
| `size` | `'sm' | 'md' | 'lg' | 'xl' | 'full'` |  |  | Size preset controlling the dialog max-width. Default: `'md'`. |
| `closeOnBackdrop` | `boolean` |  | `true` | Close the modal when the backdrop is clicked. Default: `true`. |
| `showCloseButton` | `boolean` |  | `true` | Show the × close button in the header. Default: `true`. |
| `confirmLabel` | `string` |  |  | Label for the primary action button. Omit to hide. |
| `cancelLabel` | `string` |  |  | Label for the cancel / secondary button. Omit to hide. |


### `layout: "drawer"` — DrawerSectionConfig

A panel that slides in from any edge of the viewport.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'drawer'` | ✔ |  |  |
| `open` | `boolean` |  | `false` | Whether the drawer is open on first render. Default: `false`. |
| `placement` | `'left' | 'right' | 'top' | 'bottom'` |  |  | Which edge the drawer slides in from. Default: `'right'`. |
| `size` | `string` |  |  | CSS width (left / right drawers) or height (top / bottom drawers). Default: `'320px'`. |
| `closeOnBackdrop` | `boolean` |  | `true` | Close the drawer when the backdrop is clicked. Default: `true`. |
| `showCloseButton` | `boolean` |  | `true` | Show the × close button in the drawer header. Default: `true`. |


### `layout: "tooltip"` — TooltipSectionConfig

Hover-triggered floating label attached to a trigger element.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'tooltip'` | ✔ |  |  |
| `content` | `string` |  |  | Text shown inside the tooltip bubble. |
| `placement` | `'top' | 'bottom' | 'left' | 'right'` |  |  | Preferred placement of the tooltip relative to its trigger. Default: `'top'`. |
| `triggerLabel` | `string` |  |  | Label rendered on the trigger button when no elements are provided. Default: `'Hover me'`. |


### `layout: "popover"` — PopoverSectionConfig

Click-triggered floating panel with richer content than a tooltip.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'popover'` | ✔ |  |  |
| `placement` | `'top' | 'bottom' | 'left' | 'right'` |  |  | Preferred placement of the popover relative to its trigger. Default: `'bottom'`. |
| `triggerLabel` | `string` |  |  | Label rendered on the trigger button. Default: `'Open'`. |
| `content` | `string` |  |  | Short body text shown inside the popover (alternative to placing elements). |


### `layout: "accordion"` — AccordionSectionConfig

An expand/collapse accordion with one or more panels.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'accordion'` | ✔ |  |  |
| `panels` | `AccordionPanel[]` |  |  | The accordion panels. |
| `allowMultiple` | `boolean` |  | `false` | Allow more than one panel to be open at the same time. Default: `false` (only one panel open at a time). |


### `layout: "collapse"` — CollapseSectionConfig

A single expand/collapse toggle that shows or hides its content.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'collapse'` | ✔ |  |  |
| `label` | `string` |  |  | Label rendered on the toggle trigger. Falls back to `title`. |
| `defaultOpen` | `boolean` |  | `false` | Whether the content is visible on first render. Default: `false`. |
| `icon` | `boolean` |  | `true` | Show the expand/collapse chevron icon. Default: `true`. |


### `layout: "divider"` — DividerSectionConfig

A visual separator line with an optional centred label.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'divider'` | ✔ |  |  |
| `label` | `string` |  |  | Optional text label centred in the divider line. |
| `orientation` | `'horizontal' | 'vertical'` |  |  | Line orientation. Default: `'horizontal'`. |
| `variant` | `'solid' | 'dashed' | 'dotted'` |  |  | Line style. Default: `'solid'`. |


### `layout: "card"` — CardSectionConfig

A generic content container with optional header and footer slots. `title` and `description` (from BaseSectionConfig) populate the header. `elements` (from BaseSectionConfig) populate the body.

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'card'` | ✔ |  |  |
| `footerElements` | `UIElementConfig[]` |  |  | Elements rendered in the card footer. |
| `padded` | `boolean` |  | `true` | Add padding to the card body. Default: `true`. |
| `bordered` | `boolean` |  | `true` | Render a border around the card. Default: `true`. |
| `shadow` | `false | 'sm' | 'md' | 'lg'` |  |  | Box-shadow size preset. - `false` — no shadow - `'sm'`  — small shadow (default) - `'md'`  — medium shadow - `'lg'`  — large shadow |


### `layout: "table"` — TableSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'table'` | ✔ |  |  |
| `columns` | `TableColumn[]` | ✔ |  | Column definitions. |
| `rows` | `TableRow[]` | ✔ |  | Row data. |
| `searchable` | `boolean` |  | `true` | Enable the search / filter input above the table. Default: `true`. |
| `pageSize` | `number` |  | `10` | Number of rows per page. `0` or omitted disables pagination. Default: `10`. |
| `emptyMessage` | `string` |  |  | Optional message displayed when no rows match the current filter. |


### `layout: "badge"` — BadgeSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'badge'` | ✔ |  |  |
| `badges` | `BadgeItem[]` | ✔ |  | Badge items to render. |
| `appearance` | `'subtle' | 'solid' | 'outline'` |  |  | Visual style. Default: `'subtle'`. |
| `size` | `'sm' | 'md' | 'lg'` |  |  | Size preset. Default: `'md'`. |


### `layout: "avatar"` — AvatarSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'avatar'` | ✔ |  |  |
| `avatars` | `AvatarItem[]` | ✔ |  | Avatar items to render. |
| `size` | `'sm' | 'md' | 'lg' | 'xl'` |  |  | Size preset. Default: `'md'`. |
| `stacked` | `boolean` |  | `false` | Whether to stack avatars (overlap them). Default: `false`. |


### `layout: "timeline"` — TimelineSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'timeline'` | ✔ |  |  |
| `events` | `TimelineEvent[]` | ✔ |  | Ordered list of events (rendered top-to-bottom). |


### `layout: "stat"` — StatSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'stat'` | ✔ |  |  |
| `stats` | `StatItem[]` | ✔ |  | Stat items to display. |
| `columns` | `number` |  | `auto (min 2)` | Number of columns in the grid. Default: auto (min 2). |


### `layout: "empty-state"` — EmptyStateSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'empty-state'` | ✔ |  |  |
| `heading` | `string` |  |  | Primary heading. Default: `"No data found"`. |
| `message` | `string` |  |  | Supporting description. |
| `icon` | `string` |  |  | Emoji or icon character. Default: `"🗂"`. |
| `actionLabel` | `string` |  |  | Optional call-to-action label. |
| `actionHref` | `string` |  |  | URL for the optional call-to-action button. |


### `layout: "code-block"` — CodeBlockSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'code-block'` | ✔ |  |  |
| `code` | `string` | ✔ |  | The source code string to display. |
| `language` | `string` |  |  | Language hint displayed in the header (e.g. `"typescript"`, `"bash"`). |
| `lineNumbers` | `boolean` |  | `false` | Show line numbers. Default: `false`. |
| `copyable` | `boolean` |  | `true` | Show a copy-to-clipboard button. Default: `true`. |


### `layout: "chart"` — ChartSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'chart'` | ✔ |  |  |
| `chartType` | `'line' | 'area' | 'bar' | 'pie' | 'donut' | 'radar' | 'scatter'` | ✔ |  | Chart variant. - `'line'`    — Line chart - `'area'`    — Area chart (filled line) - `'bar'`     — Vertical bar chart - `'pie'`     — Pie chart - `'donut'`   — Donut (ring) chart - `'radar'`   — Radar / spider chart - `'scatter'` — Scatter plot (requires `x` & `y` numeric keys) |
| `data` | `ChartDataPoint[]` | ✔ |  | Array of data points. |
| `series` | `ChartSeries[]` |  |  | Named series configuration. When omitted a single series named `'value'` is assumed. Each series key must correspond to a numeric property on the data points. |
| `showGrid` | `boolean` |  | `true` | Show horizontal grid lines. Default: `true` for line / area / bar / scatter. |
| `showLegend` | `boolean` |  | `true` | Show a legend. Default: `true` when there are ≥ 2 series. |
| `showLabels` | `boolean` |  | `false` | Show value labels on bars / pie slices. Default: `false`. |
| `height` | `number` |  | `300` | Chart height in pixels. Default: `300`. |


### `layout: "iframe"` — IframeSectionConfig

**Own fields** (in addition to BaseSectionConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `layout` | `'iframe'` | ✔ |  |  |
| `src` | `string` | ✔ |  | Base URL to load inside the iframe. e.g. `'https://example.com/report'` |
| `queryParams` | `Record<string, string | number | boolean>` |  |  | Query parameters appended to `src`. The rendered URL is recomputed whenever this object changes, which causes the iframe to navigate to the new URL. e.g. `{ tab: 'sales', year: 2025 }`  →  `?tab=sales&year=2025` |
| `frameWidth` | `string` |  |  | iframe width. Default: `'100%'`. |
| `frameHeight` | `string` |  |  | iframe height. Default: `'480px'`. |
| `sandbox` | `string` |  |  | HTML `sandbox` attribute value. e.g. `'allow-scripts allow-same-origin'`. Omit to apply no sandbox restrictions. |
| `frameTitle` | `string` |  |  | Accessible title for the iframe (required for screen readers). |
| `allowFullscreen` | `boolean` |  | `true` | Whether to allow the iframe to go fullscreen. Default: `true`. |
| `showLoader` | `boolean` |  | `true` | Whether to show a loading spinner while the iframe is loading. Default: `true`. |


## UIElementConfig

Discriminate on the `type` field.  Every element config also includes
the **BaseElementConfig** base fields listed first.


### BaseElementConfig (shared fields)

All element configs inherit these fields:

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique element identifier within the page. |
| `name` | `string` | ✔ |  | HTML name attribute / form field name. |
| `order` | `number` |  |  | Render order within the parent section (ascending). |
| `width` | `ElementWidth` — one of: `"1"`, `"2"`, `"3"`, `"4"`, `"5"`, `"6"`, `"7"`, `"8"`, `"9"`, `"10"`, `"11"`, `"12"` |  |  | Width — CSS value string or column span 1-12. |
| `label` | `string` |  |  | Label text shown alongside the element. |
| `labelPosition` | `'top' | 'left' | 'right' | 'hidden'` |  |  | Where the label is positioned relative to the control. |
| `tooltip` | `string` |  |  | Tooltip / help text (shown on hover or via info icon). |
| `units` | `string` |  |  | Unit label (e.g. "kg", "$", "°C"). |
| `unitsPosition` | `'prefix' | 'suffix'` |  |  | Whether the unit appears before or after the value. |
| `disabled` | `boolean` |  |  | Disable the element so it cannot be interacted with. |
| `readonly` | `boolean` |  |  | Make the element read-only (value visible but not editable). |
| `required` | `boolean` |  |  | Whether the field is mandatory. |
| `hidden` | `boolean` |  |  | Hide the element from the rendered output entirely. |
| `hiddenExpr` | `string` |  |  | Boolean expression evaluated at render time to dynamically hide this element. References other fields by name inside `{` `}` braces. Takes precedence over the static `hidden` flag when provided. @example `"{age} < 18"` — hides the element when the `age` field is less than 18. |
| `disabledExpr` | `string` |  |  | Boolean expression evaluated at render time to dynamically disable this element. References other fields by name inside `{` `}` braces. Takes precedence over the static `disabled` flag when provided. @example `"{role} !== \"admin\""` — disables the element unless the user is an admin. |
| `className` | `string` |  |  | Additional CSS class names to apply to the wrapper. |
| `style` | `StyleObject` |  |  | Inline styles to apply to the wrapper — delivered via JSON alongside element config. |
| `validations` | `ValidationRule[]` |  | `(all must pass)` | Array of validation rules delivered via JSON (evaluated by ubiquitous). Rules are evaluated as AND by default (all must pass). Use a `ValidationGroup` with `operator: 'or'` to express OR logic. |


### `type: "input"` — InputElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'input'` | ✔ |  |  |
| `inputType` | `InputType` — one of: `"text"`, `"password"`, `"number"`, `"email"`, `"date"`, `"datetime-local"`, `"time"`, `"month"`, `"week"`, `"tel"`, `"url"`, `"search"`, `"color"`, `"range"`, `"file"`, `"hidden"` | ✔ |  | HTML input type attribute. |
| `placeholder` | `string` |  |  |  |
| `defaultValue` | `string | number` |  |  |  |
| `value` | `string | number` |  |  | Controlled value (consumer manages state). |
| `min` | `number | string` |  |  | Minimum value (number / date inputs). |
| `max` | `number | string` |  |  | Maximum value (number / date inputs). |
| `step` | `number` |  |  | Step increment (number / range inputs). |
| `multiple` | `boolean` |  |  | Allow multiple files (type="file"). |
| `accept` | `string` |  |  | Accepted MIME types (type="file"), e.g. "image/*,.pdf". |
| `autocomplete` | `string` |  |  | HTML autocomplete attribute. |
| `datalistId` | `string` |  |  | id of an associated <datalist> element. |
| `validateUrl` | `string` |  |  | Async validation endpoint called on blur. `GET {validateUrl}?value={encodedValue}` → `{ valid: boolean, message?: string }` @example `"/api/users/available"` — checks username uniqueness. |


### `type: "checkbox"` — CheckboxElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'checkbox'` | ✔ |  |  |
| `defaultChecked` | `boolean` |  |  |  |
| `checked` | `boolean` |  |  | Controlled checked state (consumer manages state). |
| `value` | `string` |  |  | The value submitted with the form when checked. |
| `validateUrl` | `string` |  |  | Async validation endpoint called when the checkbox state changes. `GET {validateUrl}?value={true|false}` → `{ valid: boolean, message?: string }` |


### `type: "radio"` — RadioElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'radio'` | ✔ |  |  |
| `options` | `RadioOption[]` | ✔ |  | All available options in the radio group. |
| `defaultValue` | `string` |  |  |  |
| `value` | `string` |  |  | Controlled selected value. |
| `orientation` | `'horizontal' | 'vertical'` |  |  | Layout direction of the radio options. |
| `optionsUrl` | `string` |  |  | Remote endpoint for loading radio options dynamically on mount. `GET {optionsUrl}` → `Array<{ label: string, value: string, disabled?: boolean }>` Merges with (and overrides) any static `options`. |
| `validateUrl` | `string` |  |  | Async validation endpoint called when selection changes. `GET {validateUrl}?value={encodedValue}` → `{ valid: boolean, message?: string }` |


### `type: "textarea"` — TextareaElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'textarea'` | ✔ |  |  |
| `placeholder` | `string` |  |  |  |
| `defaultValue` | `string` |  |  |  |
| `value` | `string` |  |  | Controlled value. |
| `rows` | `number` |  |  | Visible number of text rows. |
| `cols` | `number` |  |  | Visible number of character columns. |
| `resize` | `ResizeBehaviour` — one of: `"none"`, `"both"`, `"horizontal"`, `"vertical"` |  |  | CSS resize behaviour. |
| `maxLength` | `number` |  |  |  |
| `validateUrl` | `string` |  |  | Async validation endpoint called on blur. `GET {validateUrl}?value={encodedValue}` → `{ valid: boolean, message?: string }` |


### `type: "select"` — SelectElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'select'` | ✔ |  |  |
| `options` | `Array<SelectOption | SelectOptGroup>` | ✔ |  | Flat options or grouped option sets. |
| `multiple` | `boolean` |  |  | Allow selecting multiple values. |
| `size` | `number` |  |  | Number of visible rows when multiple=true. |
| `defaultValue` | `string | string[]` |  |  |  |
| `value` | `string | string[]` |  |  | Controlled selected value(s). |
| `placeholder` | `string` |  |  | Placeholder / empty first option text. |
| `optionsUrl` | `string` |  |  | Remote endpoint for loading options dynamically on mount. `GET {optionsUrl}` → `Array<{ label: string, value: string, disabled?: boolean }>` Replaces static `options` when provided and loaded successfully. |


### `type: "button"` — ButtonElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'button'` | ✔ |  |  |
| `buttonType` | `'button' | 'submit' | 'reset'` |  |  | HTML button type. |
| `text` | `string` | ✔ |  | Visible button label. |
| `variant` | `ButtonVariant` — one of: `"default"`, `"outline"`, `"ghost"`, `"destructive"`, `"secondary"`, `"link"` |  |  | Visual variant (maps to shadcn/ui button variants). |
| `size` | `ButtonSize` — one of: `"sm"`, `"md"`, `"lg"` |  |  | Size preset. |
| `icon` | `string` |  |  | Optional icon name (e.g. Lucide icon identifier). |
| `iconPosition` | `'left' | 'right'` |  |  | Whether the icon appears before or after the text. |
| `submitUrl` | `string` |  |  | POST destination for config-driven form submission. When set and `buttonType === 'submit'`, clicking the button POSTs the current `formValues` to this URL instead of triggering a native browser form submit. `POST {submitUrl}` body: `Record<string, unknown>` → any |
| `submitMethod` | `'POST' | 'PUT'` |  |  | HTTP method used when `submitUrl` is provided. Defaults to `'POST'`. |


### `type: "label"` — LabelElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'label'` | ✔ |  |  |
| `text` | `string` | ✔ |  | Visible label text. |
| `htmlFor` | `string` |  |  | Associates the label with a control by id. |


### `type: "fieldset"` — FieldsetElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'fieldset'` | ✔ |  |  |
| `legend` | `string` |  |  | <legend> caption text. |
| `children` | `UIElementConfig[]` | ✔ |  | Child elements rendered inside the fieldset. |
| `submitUrl` | `string` |  |  | POST destination for config-driven form submission of the entire fieldset. When set, a `submit` button inside the fieldset will POST all child field values to this URL. `POST {submitUrl}` body: `Record<string, unknown>` → any |
| `submitMethod` | `'POST' | 'PUT'` |  |  | HTTP method used when `submitUrl` is provided. Defaults to `'POST'`. |


### `type: "datalist"` — DatalistElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'datalist'` | ✔ |  |  |
| `options` | `DatalistOption[]` | ✔ |  | Autocomplete suggestions — plain strings or label/value pairs. |
| `optionsUrl` | `string` |  |  | Remote endpoint for loading suggestions dynamically on mount. `GET {optionsUrl}` → `Array<{ label: string, value: string }>` or `string[]` Merges with static `options` when provided. |


### `type: "output"` — OutputElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'output'` | ✔ |  |  |
| `htmlFor` | `string[]` |  |  | ids of input elements this output depends on. |
| `defaultValue` | `string` |  |  |  |
| `value` | `string` |  |  | Controlled display value. |
| `format` | `'text' | 'currency' | 'percentage' | 'number' | string` |  |  | Display format hint for the renderer (e.g. "currency", "percentage"). |
| `valueUrl` | `string` |  |  | Remote endpoint for fetching a server-computed value on mount. `GET {valueUrl}` → `{ value: string }` or a raw string. Takes precedence over static `value` / `defaultValue` but is overridden by a `formula` when both are present. |
| `formula` | `string` |  |  | Formula expression for computing this field's value from sibling fields. Field values are referenced by their `name` inside `{` `}` braces. Basic arithmetic operators `+`, `-`, `*`, `/` and parentheses are supported. @example ```json { "formula": "{price} * {quantity}" } { "formula": "({subtotal} + {shipping}) * (1 + {taxRate} / 100)" } ``` When a formula is supplied, `value` is computed automatically and any static `value` / `defaultValue` fields are ignored. |


### `type: "datepicker"` — DatePickerElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'datepicker'` | ✔ |  |  |
| `value` | `string` |  |  | Controlled ISO date string value (YYYY-MM-DD). |
| `defaultValue` | `string` |  |  |  |
| `placeholder` | `string` |  |  |  |
| `min` | `string` |  |  | Minimum selectable date (YYYY-MM-DD). |
| `max` | `string` |  |  | Maximum selectable date (YYYY-MM-DD). |
| `includeTime` | `boolean` |  |  | Whether to include time selection. |
| `validateUrl` | `string` |  |  | Async validation endpoint called when a date is selected. `GET {validateUrl}?value={YYYY-MM-DD}` → `{ valid: boolean, message?: string }` @example `"/api/appointments/available"` — checks whether the chosen date is bookable. |


### `type: "multiselect"` — MultiSelectElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'multiselect'` | ✔ |  |  |
| `options` | `SelectOption[]` | ✔ |  | All available options. |
| `value` | `string[]` |  |  | Controlled array of selected values. |
| `defaultValue` | `string[]` |  |  |  |
| `placeholder` | `string` |  |  |  |
| `maxItems` | `number` |  |  | Maximum number of selectable items. |
| `optionsUrl` | `string` |  |  | Remote endpoint for loading options dynamically on mount. `GET {optionsUrl}` → `Array<{ label: string, value: string, disabled?: boolean }>` Replaces static `options` when provided and loaded successfully. |


### `type: "autocomplete"` — AutocompleteElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'autocomplete'` | ✔ |  |  |
| `options` | `SelectOption[]` | ✔ |  | Static suggestion list. |
| `value` | `string` |  |  | Controlled value. |
| `defaultValue` | `string` |  |  |  |
| `placeholder` | `string` |  |  |  |
| `suggestionsUrl` | `string` |  |  | Server-side type-ahead suggestions endpoint. `GET {suggestionsUrl}?q={encodedQuery}` → `Array<{ label: string, value: string }>` When provided, replaces local option filtering with server results. Requests are debounced (300 ms) and cancelled on unmount. |


### `type: "fileupload"` — FileUploadElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'fileupload'` | ✔ |  |  |
| `accept` | `string` |  |  | Accepted MIME types / extensions (e.g. "image/*,.pdf"). |
| `multiple` | `boolean` |  |  | Allow multiple files. |
| `maxSize` | `number` |  |  | Maximum individual file size in bytes. |
| `placeholder` | `string` |  |  | Placeholder text shown inside the drop zone. |
| `uploadUrl` | `string` |  |  | POST endpoint for uploading selected file(s) as `multipart/form-data`. |


### `type: "colorpicker"` — ColorPickerElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'colorpicker'` | ✔ |  |  |
| `value` | `string` |  |  | Controlled hex color string (e.g. "#ff0000"). |
| `defaultValue` | `string` |  |  |  |
| `format` | `'hex' | 'rgb'` |  |  | Display format shown in the text input. |
| `validateUrl` | `string` |  |  | Async validation endpoint called when the color changes. `GET {validateUrl}?value={encodedHex}` → `{ valid: boolean, message?: string }` |


### `type: "rangeslider"` — RangeSliderElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'rangeslider'` | ✔ |  |  |
| `min` | `number` |  |  | Minimum bound of the slider track. |
| `max` | `number` |  |  | Maximum bound of the slider track. |
| `step` | `number` |  |  | Step increment. |
| `value` | `[number, number]` |  |  | Controlled [minValue, maxValue] tuple. |
| `defaultValue` | `[number, number]` |  |  |  |
| `validateUrl` | `string` |  |  | Async validation endpoint called when the range changes (on pointer-up / keyboard). `GET {validateUrl}?min={minValue}&max={maxValue}` → `{ valid: boolean, message?: string }` |


### `type: "rating"` — RatingElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'rating'` | ✔ |  |  |
| `max` | `number` |  | `5)` | Maximum star count (defaults to 5). |
| `value` | `number` |  |  | Controlled rating value. |
| `defaultValue` | `number` |  |  |  |
| `allowHalf` | `boolean` |  |  | Allow half-star increments. |
| `submitUrl` | `string` |  |  | POST endpoint called immediately when a star rating is selected. `POST {submitUrl}` body: `{ name: string, value: number }` → any Useful for instant rating submission (e.g. product/content ratings). |


### `type: "otpinput"` — OtpInputElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'otpinput'` | ✔ |  |  |
| `length` | `number` |  | `6)` | Number of digits / segments (defaults to 6). |
| `value` | `string` |  |  | Controlled value string (digits only). |
| `defaultValue` | `string` |  |  |  |
| `mask` | `boolean` |  |  | Mask input characters (e.g. for PIN). |
| `verifyUrl` | `string` |  |  | Server-side OTP verification endpoint called automatically when all digits are entered. `POST {verifyUrl}` body: `{ otp: string }` → `{ valid: boolean, message?: string }` |


### `type: "phoneinput"` — PhoneInputElementConfig

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'phoneinput'` | ✔ |  |  |
| `countries` | `PhoneCountryOption[]` |  | `a built-in set when omitted` | List of country options. Defaults to a built-in set when omitted. |
| `defaultCountry` | `string` |  |  | Pre-selected country code (ISO alpha-2). |
| `value` | `string` |  |  | Controlled full phone value (dialCode + number). |
| `defaultValue` | `string` |  |  |  |
| `placeholder` | `string` |  |  |  |
| `validateUrl` | `string` |  |  | Async validation endpoint called on blur. `GET {validateUrl}?value={encodedPhoneNumber}` → `{ valid: boolean, message?: string }` @example `"/api/phone/validate"` — checks carrier lookup or format validity. |


### `type: "custom"` — CustomElementConfig

CustomElementConfig Renders a consumer-supplied React component registered via the `customComponents` prop on `UIStage` (or via `componentRegistry`). The `component` key must match a key in the `customComponents` map passed to `UIStage`. The renderer forwards `config`, `onChange`, and `formValues` to the custom component as props. @example Config: ```json { "type": "custom", "component": "my-special-widget", "id": "w1", "name": "w1" } ``` @example Registration: ```tsx <UIStage config={stageConfig} customComponents={{ 'my-special-widget': MyReactComponent }} /> ```

**Own fields** (in addition to BaseElementConfig):

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `type` | `'custom'` | ✔ |  |  |
| `component` | `string` | ✔ |  | Key used to look up the custom component in the `customComponents` map. |
| `props` | `Record<string, unknown>` |  |  | Arbitrary extra data forwarded to the custom component as `config.props`. |


## Validation Rules

Attach validation to any element via the `validations` array on
`BaseElementConfig`.  Each entry in the array is a `ValidationRule`
object discriminated on the `rule` field.

The `rule` field determines which additional fields are expected:

| `rule` value | Extra fields | Description |
|---|---|---|
| `"required"` | `message?` | Field must have a non-empty value |
| `"min"` | `value` (number\|string), `message?` | Numeric/date ≥ value |
| `"max"` | `value` (number\|string), `message?` | Numeric/date ≤ value |
| `"minLength"` | `value` (number), `message?` | String length ≥ value |
| `"maxLength"` | `value` (number), `message?` | String length ≤ value |
| `"pattern"` | `value` (string — regex, no delimiters), `message?` | Value must match pattern |
| `"email"` | `message?` | Must be valid e-mail address |
| `"url"` | `message?` | Must be valid URL |
| `"phone"` | `message?` | Must be valid phone number |
| `"step"` | `value` (number), `message?` | Numeric value must be a multiple of value |
| `"custom"` | `validator` (string), `config?` (object), `message?` | Custom registered validator |
| `"group"` | `operator` (`"and"`\|`"or"`), `rules` (ValidationRule[]), `message?` | Logical AND/OR group |


### `ValidationGroup`

Logical group that chains a set of {@link ValidationRule}s together. - `operator: 'and'` — **all** rules in the group must pass (short-circuits on first failure, like a flat array). The group message is used when none of the failing rules carries its own message. - `operator: 'or'`  — **at least one** rule must pass. If none pass the group message (or a default) is returned. Groups can be nested to any depth, enabling complex boolean logic: @example ```json [ { "rule": "required" }, { "rule": "group", "operator": "or", "rules": [ { "rule": "email" }, { "rule": "url" } ], "message": "Must be a valid email or URL." } ] ```

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `rule` | `'group'` | ✔ |  |  |
| `operator` | `'and' | 'or'` | ✔ |  | Logical operator applied to the nested rules. |
| `rules` | `ValidationRule[]` | ✔ |  | The nested rules evaluated by this group. |
| `message` | `string` |  |  | Error message returned when the group as a whole fails. |


## Supporting Types

These types are referenced by the section and element configs above.


### `RadioOption`

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `label` | `string` | ✔ |  |  |
| `value` | `string` | ✔ |  |  |
| `disabled` | `boolean` |  |  |  |


### `SelectOption`

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `label` | `string` | ✔ |  |  |
| `value` | `string` | ✔ |  |  |
| `disabled` | `boolean` |  |  |  |


### `SelectOptGroup`

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `group` | `true` | ✔ |  | Marks this entry as an option group (not a standalone option). |
| `label` | `string` | ✔ |  |  |
| `options` | `SelectOption[]` | ✔ |  |  |


### `PhoneCountryOption`

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `label` | `string` | ✔ |  | Country name. |
| `code` | `string` | ✔ |  | ISO 3166-1 alpha-2 country code. |
| `dialCode` | `string` | ✔ |  | Dial prefix (e.g. "+1"). |


### `NavLink`

A single link in a Navbar or Sidebar.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Display label. |
| `href` | `string` |  |  | Navigation target URL. |
| `active` | `boolean` |  |  | Whether this link is the currently active route. |


### `SidebarItem`

A single item in a Sidebar / Drawer, supporting nested children.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Display label. |
| `href` | `string` |  |  | Navigation target URL. |
| `icon` | `string` |  |  | Optional icon name (for future icon rendering). |
| `active` | `boolean` |  |  | Whether this item is the currently active route. |
| `children` | `SidebarItem[]` |  |  | Nested child items. |


### `BreadcrumbItem`

A single crumb in a Breadcrumbs trail.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Display label. |
| `href` | `string` |  |  | Navigation target URL (omit for the current / last crumb). |


### `StepperStep`

A single step in a Stepper indicator.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Short step label. |
| `description` | `string` |  |  | Optional longer description shown below the label. |
| `status` | `'complete' | 'current' | 'upcoming'` |  |  | Explicit status override. Derived from `currentStep` when omitted. |


### `TabItem`

A single tab in a Tabs section.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Tab button label. |
| `sections` | `UISectionConfig[]` |  |  | Sections rendered inside this tab's content panel. |
| `elements` | `UIElementConfig[]` |  |  | Flat elements rendered inside this tab when no sections are provided. |


### `AccordionPanel`

A single panel inside an AccordionSectionConfig.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique panel identifier. |
| `label` | `string` | ✔ |  | Panel header label. |
| `description` | `string` |  |  | Optional description shown below the label in the header. |
| `defaultOpen` | `boolean` |  | `false` | Whether this panel starts open. Default: `false`. |
| `sections` | `UISectionConfig[]` |  |  | Sections rendered inside the panel body. |
| `elements` | `UIElementConfig[]` |  |  | Flat elements rendered inside the panel body when no sections are provided. |


### `ListDetailItem`

An item in the left-hand list pane of a ListDetailSectionConfig.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Primary label shown in the list row. |
| `sublabel` | `string` |  |  | Secondary label shown below the main label. |
| `avatar` | `string` |  |  | Avatar URL (full URL) or initials string (≤ 2 chars). |
| `badge` | `string` |  |  | Short badge text, e.g. a status indicator. |


### `ListEndpointConfig`

Configuration for the paginated list endpoint.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `url` | `string` | ✔ |  | Base URL without query parameters. |
| `fromParam` | `string` |  |  | Query param name for the start offset. Default: `'from'`. |
| `fromValue` | `number` |  | `start offset value` | Default start offset value. Default: `1`. |
| `toParam` | `string` |  |  | Query param name for the end offset. Default: `'to'`. |
| `toValue` | `number` |  | `end offset value` | Default end offset value. Default: `100`. |
| `sortParam` | `string` |  |  | Query param name for sort order. Default: `'sort'`. |
| `sortValue` | `'asc' | 'desc'` |  |  | Sort order value appended to the sort param. Default: `'asc'`. |


### `FilterEndpointConfig`

Configuration for the search / filter endpoint.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `url` | `string` | ✔ |  | Base URL without query parameters. |
| `queryParam` | `string` |  |  | Query param name for the search text. Default: `'query'`. |


### `DetailEndpointConfig`

Configuration for the detail view endpoint (loads data for the selected item).

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `url` | `string` | ✔ |  | Base URL without query parameters. |
| `selectedParam` | `string` |  |  | Query param name for the selected item ID. Default: `'selected'`. |


### `DetailPage`

A lightweight page used inside the detail panel of a ListDetailSectionConfig. Defined here (rather than re-using UIPageConfig) to avoid a circular import between section.types.ts and page.types.ts.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  |  |
| `title` | `string` | ✔ |  |  |
| `description` | `string` |  |  |  |
| `order` | `number` |  |  |  |
| `sections` | `UISectionConfig[]` | ✔ |  |  |
| `className` | `string` |  |  |  |


### `TreeViewNode`

A single node in a tree-view. Nodes may contain nested `children` to form any depth of hierarchy.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Display label. |
| `sublabel` | `string` |  |  | Optional secondary description shown below the label. |
| `badge` | `string` |  |  | Short badge text, e.g. a status indicator. |
| `children` | `TreeViewNode[]` |  |  | Nested child nodes. |


### `MediaItem`

A single image or video item in a MediaSectionConfig carousel.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `type` | `'image' | 'video'` | ✔ |  | `'image'` or `'video'`. |
| `url` | `string` | ✔ |  | Publicly accessible URL. |
| `alt` | `string` |  |  | Alt text for images (accessibility). |
| `caption` | `string` |  |  | Optional caption shown as an overlay at the bottom of the slide. |


### `TableColumn`

A single column definition for a Table section.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `key` | `string` | ✔ |  | Unique column key matching a key in the row data. |
| `label` | `string` | ✔ |  | Visible column header label. |
| `sortable` | `boolean` |  | `false` | Whether this column is sortable. Default: `false`. |
| `width` | `string` |  |  | Column width (CSS value, e.g. `"120px"`, `"20%"`). |


### `BadgeItem`

A single badge / tag / chip item.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Display label. |
| `variant` | `'default' | 'primary' | 'success' | 'warning' | 'danger' | 'info'` |  |  | Color variant. - `'default'` — neutral grey (default) - `'primary'` — indigo - `'success'` — green - `'warning'` — yellow - `'danger'`  — red - `'info'`    — blue |


### `AvatarItem`

A single avatar item.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `initials` | `string` |  |  | Fallback initials (e.g. `"JD"`). Shown when `src` is absent or fails to load. |
| `src` | `string` |  |  | Image URL. |
| `alt` | `string` |  |  | Alt text for the image. |
| `name` | `string` |  |  | Optional display name shown below the avatar. |


### `TimelineEvent`

A single event in a Timeline.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `title` | `string` | ✔ |  | Event title / heading. |
| `description` | `string` |  |  | Optional longer description. |
| `timestamp` | `string` |  |  | Date / time label (any string, e.g. `"Jan 2025"` or ISO timestamp). |
| `variant` | `'default' | 'primary' | 'success' | 'warning' | 'danger'` |  |  | Dot color variant. - `'default'` — slate (default) - `'primary'` — indigo - `'success'` — green - `'warning'` — yellow - `'danger'`  — red |
| `icon` | `string` |  |  | Optional icon character / emoji rendered inside the dot. |


### `StatItem`

A single stat / metric item.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `value` | `string` | ✔ |  | Big primary number or value (e.g. `"1,234"`, `"98%"`). |
| `label` | `string` | ✔ |  | Descriptive label below the value. |
| `subLabel` | `string` |  |  | Optional supporting sub-label or context. |
| `trend` | `string` |  |  | Optional trend indicator string (e.g. `"+12%"` or `"↑ 5"`). |
| `trendDirection` | `'up' | 'down' | 'neutral'` |  |  | Trend direction — controls colour. - `'up'`     — green - `'down'`   — red - `'neutral'`— slate (default) |
| `icon` | `string` |  |  | Optional icon character / emoji. |


### `ChatMessage`

A single message in a chat conversation.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `text` | `string` | ✔ |  | The text content of the message. |
| `sender` | `string` | ✔ |  | Display name of the sender. |
| `role` | `'me' | 'other'` | ✔ |  | Message alignment / ownership. - `'me'`    — right-aligned (current user) - `'other'` — left-aligned (remote participant) |
| `timestamp` | `string` |  |  | ISO 8601 timestamp string, e.g. `'2024-01-15T10:30:00Z'`. |
| `avatar` | `string` |  |  | Avatar URL or ≤ 2-char initials string for the sender. |


### `ChatConversation`

A single conversation / group in the left-hand list pane.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `id` | `string` | ✔ |  | Unique identifier. |
| `label` | `string` | ✔ |  | Display name of the conversation or group. |
| `sublabel` | `string` |  |  | Last message preview shown below the label. |
| `avatar` | `string` |  |  | Avatar URL or ≤ 2-char initials for the conversation. |
| `badge` | `string` |  |  | Optional badge text, e.g. unread count. |
| `messages` | `ChatMessage[]` |  |  | Pre-seeded messages shown when this conversation is selected. |


### `ChartDataPoint`

A single data point for a chart. The `label` key is used for the x-axis / category label. Additional numeric keys map to series values.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `label` | `string` | ✔ |  | Category label (x-axis). |
| `value` | `number` |  |  | Primary value (used when no explicit series keys are defined). |


### `ChartSeries`

A single named series in a multi-series chart.

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `key` | `string` | ✔ |  | Key that matches a property in each `ChartDataPoint`. |
| `label` | `string` |  |  | Human-readable series label shown in the legend. |
| `color` | `string` |  | `the rotating` | Override color for this series. Accepts any CSS color string (hex, hsl, oklch, etc.). Defaults to the rotating `--chart-1..5` CSS variables. |


## Enum / Literal Type Reference

All string-literal union types used across the schema are collected here
for quick reference.


### `InputType`

| Value |
|-------|
| `"text"` |
| `"password"` |
| `"number"` |
| `"email"` |
| `"date"` |
| `"datetime-local"` |
| `"time"` |
| `"month"` |
| `"week"` |
| `"tel"` |
| `"url"` |
| `"search"` |
| `"color"` |
| `"range"` |
| `"file"` |
| `"hidden"` |


### `ResizeBehaviour`

| Value |
|-------|
| `"none"` |
| `"both"` |
| `"horizontal"` |
| `"vertical"` |


### `ButtonVariant`

| Value |
|-------|
| `"default"` |
| `"outline"` |
| `"ghost"` |
| `"destructive"` |
| `"secondary"` |
| `"link"` |


### `ButtonSize`

| Value |
|-------|
| `"sm"` |
| `"md"` |
| `"lg"` |


### `UITheme`

Controls how the stage is rendered: - `light`  — applies default Tailwind light-mode CSS classes. - `dark`   — applies default Tailwind dark-mode CSS classes. - `html`   — renders plain HTML without any additional CSS customisation. - `custom` — the API supplies CSS classes via the `className` field.

| Value |
|-------|
| `"html"` |
| `"custom"` |
| `"light"` |
| `"dark"` |


### `UIPageTransition`

Controls the animation that plays when the active page (tab) changes. - `none`        — instant switch, no animation (default). - `fade`        — the incoming page fades in. - `slide-left`  — new page slides in from the right (forward navigation feel). - `slide-right` — new page slides in from the left (backward navigation feel).

| Value |
|-------|
| `"none"` |
| `"fade"` |
| `"slide-left"` |
| `"slide-right"` |


## I18n Message Overrides (`I18nMessages`)

I18nMessages Pass an `i18n` prop to `UIStage` to override the default English validation messages. Any key that is omitted falls back to the built-in message. Dynamic messages (e.g. `minLength`) accept either a static string or a function that receives the rule value and returns a string. @example ```tsx <UIStage config={stageConfig} i18n={{ required: 'Ce champ est obligatoire.', email:    'Adresse e-mail invalide.', minLength: (n) => `Minimum ${n} caractères.`, }} /> ```

| Field | Type | Required | Default | Description |
|-------|------|:--------:|---------|-------------|
| `required` | `string` |  |  | Override for the "required" rule message. |
| `email` | `string` |  |  | Override for the "email" rule message. |
| `url` | `string` |  |  | Override for the "url" rule message. |
| `phone` | `string` |  |  | Override for the "phone" rule message. |
| `pattern` | `string` |  |  | Override for the "pattern" rule message. |
| `min` | `string | ((value: number | string) => string)` |  |  | Override for the "min" rule message. Static or function of the limit value. |
| `max` | `string | ((value: number | string) => string)` |  |  | Override for the "max" rule message. Static or function of the limit value. |
| `minLength` | `string | ((value: number) => string)` |  |  | Override for the "minLength" rule message. Static or function of the limit value. |
| `maxLength` | `string | ((value: number) => string)` |  |  | Override for the "maxLength" rule message. Static or function of the limit value. |
| `step` | `string | ((value: number) => string)` |  |  | Override for the "step" rule message. Static or function of the step value. |
| `orGroupFallback` | `string` |  |  | Override for the OR-group fallback message. |
