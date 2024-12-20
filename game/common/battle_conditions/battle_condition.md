A battle condition is something that is added to one side of a battle when the battle begins. Each side gets its own
independent condition, which is randomly rolled but is based on external condition such as the traits of the commander
in charge, the terrain of the province tha battle is being fought in, and so on.

To that end, the weight calculation will have access to a battle_side scope.

A condition supports the following values:

- icon: a path to an icon which will be used to display this condition; the
  path is relative to the "game" directory
- instant_switch: a trigger determining if the current battle condition should
  be immediately switched to this other one (at the next check); weights are
  still considered if several instant_switch conditions apply; if empty,
  this will never be checked and the condition can only appear randomly with
  possible trigger and a positive weight
- possible: a trigger determining if the weight should be evaluated at all; if
  empty, this will never be checked and can only appear under instant_switch
- modifier: the modifier(s) that will impact this side of the battle
- weight: a scripted value that represents how likely this condition is to be
  picked among all the possible conditions. Has access to a battle_side scope
  that can be used to make certain conditions more or less likely depending
  on external factors such as commander traits, or even a commander not being
  present. If unset, this is 1.

Battle condition names are localized in their respective yml file. Similar to
other database objects, the key of the condition is used to look for the
localization of their name and description. Names are found by looking for
`battle_condition_<key>` keys, while description are found by looking for
`battle_condition_<key>_desc` keys. For example a battle condition called
`test_condition` would have its name localized by adding
`battle_condition_test_condition` to the localization file, while its
description would be found via `battle_condition_test_condition_desc`.

A battle_side scope has access to the following links:

- battle: scope to the overall battle itself
- commander: scope to the commander in charge of this side of the battle. Note
  that it's perfectly possible that a battle_side is not led by
  any commander at all
- province: scope to the province the battle is being fought in
- state: scope to the state that contains the province where the battle is
  being fought
- state_region: scope to the state region that contains the province where
  the battle is being fought
- country: scope to the country involved in this side of the battle

Example:

    example_condition = {
        icon = "/path/to/icon"

	    modifier = {
            battle_combat_effectiveness_mult = 0.1
	    }

	    weight = {
		    value = 0

		    if = {
			    limit = {
				    commander = { has_trait = some_trait }
			    }
			    add = 10
		    }
        }
    }