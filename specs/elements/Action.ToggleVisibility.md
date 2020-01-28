<!-- AUTO-GENERATED: This section is auto-generated from schemas/adaptive-card.json. Do NOT add anything above this or edit anything inside, it MUST be the first thing in the document and will be overwritten. -->

# Action.ToggleVisibility

#### Introduced in version 1.2

| Property | Type | Required | Description | Version |
| -------- | ---- | -------- | ----------- | ------- |
| **type** | `"Action.ToggleVisibility"` | Yes | Must be `"Action.ToggleVisibility"`. | 1.2 |
| **targetElements** | `TargetElement[]` | No | The array of TargetElements | 1.2 |

**Inherited properties**

| Property | Type | Required | Description | Version |
| -------- | ---- | -------- | ----------- | ------- |
| **title** | `string` | No | Label for button or link that represents this action. | 1.2 |
| **iconUrl** | `uri` | No | Optional icon to be shown on the action in conjunction with the title. Supports data URI in version 1.2+ | 1.1 |
| **style** | `ActionStyle` | No | Controls the style of an Action, which influences how the action is displayed, spoken, etc. | 1.2 |
| **fallback** | `Action`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can't be met. | 1.2 |
| **associatedInputIds** | `string[]`, `ActionInputs` | No, default: `"None"` | None, All, or an array of ids for inputs (or containers of inputs) that should be validated before allowing this action. | 1.3 |
| **requires** | `Dictionary<string>` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |


## targetElements

The array of TargetElements

* **Type**: `TargetElement[]`
* **Required**: No
* **Allowed values**:
  * `TargetElement`
  * `string`


## style

Controls the style of an Action, which influences how the action is displayed, spoken, etc.

* **Type**: `ActionStyle`
* **Required**: No
* **Allowed values**:
  * `"default"`: Action is displayed as normal
  * `"positive"`: Action is displayed with a positive style (typically the button becomes accent color)
  * `"destructive"`: Action is displayed with a destructive style (typically the button becomes red)


## fallback

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

* **Type**: `Action`, `FallbackOption`
* **Required**: No
* **Allowed values**:
  * `Action.OpenUrl`
  * `Action.ShowCard`
  * `Action.Submit`
  * `Action.ToggleVisibility`
  * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.


## associatedInputIds

None, All, or an array of ids for inputs (or containers of inputs) that should be validated before allowing this action.

* **Type**: `string[]`, `ActionInputs`
* **Version** : 1.3
* **Required**: No, default: `"None"`
* **Allowed values**:
  * `string`
  * `"All"`: All inputs will be validated and submitted for this Action.
  * `"None"`: None of the inputs will be validated or submitted for this Action.
<!-- END AUTO-GENERATED -->

## Rendering

See `ActionSet`.

When the user invokes this action, for each object in `targetElements`...

1. If the object is a string, up-convert it to a new `TargetElement` object, setting `TargetElement.elementId` = string.
1. Now the object should be a `TargetElement` object...
1. Look up the element using the `elementId`
	1. If not found, issue warning and continue to next in loop
1. If the `isVisible` property is NOT supplied, toggle the element's visibility
1. Else, if the `isVisible` property is supplied, set the element's visibility to the value of `isVisible`.

The action button should be greyed out if any of the inputs referenced in `inputs` do not meet the requirements specified by the card author.