---
title: Area of Effect (Entity Action Type)
date: 2021-12-03
---

# Area of Effect

[Entity Action Type](../entity_action_types.md)

Executes a [bi-entity action](../bientity_action_types.md) within a specified radius.

Type ID: `origins:area_of_effect`


### Fields

Field | Type | Default | Description
------|------|---------|------------
`radius` | [Float](../data_types/float.md) | `16.0` | Determines the radius of the area.
`bientity_action` | [Bi-entity Action Type](../bientity_action_types.md) | | The bi-entity action to execute on either or both the `actor` (the entity that has the power) and `target` (the entities within the specified radius).
`bientity_condition` | [Bi-entity Condition Type](../bientity_condition_types.md) | _optional_ | If specified, only execute the specified bi-entity action if this bi-entity condition type is fulfilled by either or both the 'actor' (the entity that has the power) or 'target' (the entities within the specified radius).
`include_target` | [Boolean](../data_types/boolean.md) | `false` | Determines whether the 'actor' (the entity that invoked the action) should be included as the 'target'.


### Examples

```json
"entity_action": {
    "type": "origins:area_of_effect",
    "radius": 32,
    "bientity_action": {
        "type": "origins:target_action",
        "action": {
            "type": "origins:set_on_fire",
            "duration": 5
        }
    },
    "bientity_condition": {
        "type": "origins:can_see"
    }
}
```

This example will set entities within a 32 block radius on fire for 5 seconds if the entities that are within the radius can be "seen" by the entity that invoked the action.
