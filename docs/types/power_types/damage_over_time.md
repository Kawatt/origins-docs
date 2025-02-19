---
title: Damage Over Time (Power Type)
date: 2021-04-08
---

# Damage Over Time

[Power Type](../power_types.md)

Inflicts damage on the entity that has the power from a specified damage source within the specified interval.

Type ID: `origins:damage_over_time`


### Fields

Field  | Type | Default | Description
-------|------|---------|-------------
`interval` | [Integer](../data_types/integer.md) | `20` | Duration of ticks to wait between the damage.
`onset_delay` | [Integer](../data_types/integer.md) | _optional_ | How many ticks the power has to be active in order to apply the first damage. If not set, this will be equal to `interval`.
`damage` | [Float](../data_types/float.md) | | How much damage will be dealt each interval.
`damage_easy` | [Float](../data_types/float.md) | _optional_ | How much damage will be dealt each interval on Easy difficulty. If not set, this will be equal to `damage`.
`damage_source` | [Damage Source](../data_types/damage_source.md) | **DEPRECATED** | Use `damage_type` instead. [More information here](https://gist.github.com/apace100/bfbf82a8f9d6bd2db13e4feaf653a6b0).
`damage_type` | [Identifier](../data_types/identifier.md) | `apoli:damage_over_time` | The damage type this power uses.
`protection_enchantment` | [Identifier](../data_types/identifier.md) | _optional_ | If set, the total amount of levels of this enchantment will be counted on the player's armor to increase the `onset_delay`.
`protection_effectiveness` | [Float](../data_types/float.md) | `1.0` | If `protection_enchantment` is set, this multiplier scales how effective it will be (1.0 = time the `onset_delay` is increased is the same as with Hydrophobia and Water Protection).


### Examples

```json
{
  	"type": "origins:damage_over_time",
  	"interval": 20,
  	"onset_delay": 1,
  	"damage": 2,
  	"damage_easy": 1,
  	"damage_type": "origins:hurt_by_water",
  	"protection_enchantment": "origins:water_protection",
  	"protection_effectiveness": 1.0,
  	"condition": {
    	"type": "origins:or",
    	"conditions": [
	      	{
	        	"type": "origins:fluid_height",
		        "fluid": "minecraft:water",
	        	"comparison": ">",
	        	"compare_to": 0.0
	      	},
	      	{
	        	"type": "origins:in_rain"
	      	}
    	]
  	}
}
```

This example will deal damage to the entity if the entity is in water.
