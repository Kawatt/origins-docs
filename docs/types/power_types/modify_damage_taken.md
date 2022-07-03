---
title: Modify Damage Taken (Power Type)
date: 2021-04-06
---

# Modify Damage Taken

[Power Type](../power_types.md)

Modifies how much damage the entity that has the power takes.

For the `bientity_action` and `bientity_condition`, the actor is the entity that attacks (left-clicks) the target entity (which has the power).

Type ID: `origins:modify_damage_taken`


### Fields

Field  | Type | Default | Description
-------|------|---------|-------------
`bientity_condition` | [Bi-entity Condition Type](../bientity_condition_types.md) | _optional_ | If specified, the specified modifier(s) and/or action(s) will only apply if either or both 'actor' (the attacker) and 'target' (the entity that has the power) fulfills this bi-entity condition type.
`damage_condition` | [Damage Condition Type](../damage_condition_types.md) | _optional_ | If specified, the specified modifiers(s) and/or action(s) will only apply if the taken damage fulfills this condition.
`modifier` | [Attribute Modifier](../data_types/attribute_modifier.md) | _optional_ | If specified, this modifier will apply to the damage amount.
`modifiers` | [Array](../data_types/array.md) of [Attribute Modifiers](../data_types/attribute_modifier.md) | _optional_ | If specified, these modifiers will apply to the damage amount.
`bientity_action` | [Bi-entity Action Type](../bientity_action_types.md) | _optional_ | If specified, this bi-entity action type will be executed on either or both 'actor' (the attacker) and 'target' (the entity that has the power).
`self_action` | [Entity Action Type](../entity_action_types.md) | _optional_ | If specified, this action will be executed on the entity that has the power whenever the modifier(s) is applied.
`attacker_action` | [Entity Action Type](../entity_action_types.md) | _optional_ | If specified, this action will be executed on the entity/entities that has been hit whenever the modifier(s) is applied.


### Examples
```json
{
    "type": "origins:modify_damage_taken",
    "damage_condition": {
        "type": "origins:attacker",
        "entity_condition": {
            "type": "origins:equipped_item",
            "equipment_slot": "mainhand",
            "item_condition": {
                "type": "origins:or",
                "conditions": [
                    {
                        "type": "origins:enchantment",
                        "enchantment": "minecraft:binding_curse",
                        "comparison": ">=",
                        "compare_to": 1
                    },
                    {
                        "type": "origins:enchantment",
                        "enchantment": "minecraft:vanishing_curse",
                        "comparison": ">=",
                        "compare_to": 1
                    }
                ]
            }
        }
    },
    "modifier": {
        "name": "Weak to cursed items",
        "operation": "addition",
        "value": 5.5
    }
}
```

This example will make the entity that has the power take 3 additional hearts of damage if the attacker is holding an item with either the Curse of Binding, or Curse of Vanishing enchantments.
<br>

```json
{
    "type": "origins:modify_damage_taken",
    "bientity_condition": {
        "type": "origins:actor_condition",
        "condition": {
            "type": "origins:equipped_item",
            "equipment_slot": "mainhand",
            "item_condition": {
                "type": "origins:or",
                "conditions": [
                    {
                        "type": "origins:enchantment",
                        "enchantment": "minecraft:binding_curse",
                        "comparison": ">=",
                        "compare_to": 1
                    },
                    {
                        "type": "origins:enchantment",
                        "enchantment": "minecraft:vanishing_curse",
                        "comparison": ">=",
                        "compare_to": 1
                    }
                ]
            }
        }
    },
    "modifier": {
        "name": "Weak to cursed items",
        "operation": "addition",
        "value": 5.5
    }
}
```

This example is an updated version of the first example.
