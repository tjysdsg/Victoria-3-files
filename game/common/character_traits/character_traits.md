	notorious = {
		type = condition														# Can be one of Personality, Skill, or Condition. Each category is limited by defines. Random traits can be applied based on a particular type.
		texture = "gfx/interface/icons/character_trait_icons/direct.dds"		# The trait's texture asset
	
		character_modifier = {													# Applies to the Character regardless of role
			character_popularity_add = 25
		}

		command_modifier = {													# Applies to any Combat Units under the Character's command, assuming the unit is fully Mobilized (or does not need to Mobilize)
			unit_kill_rate_mult = 0.1
		}
	
		country_modifier = {													# Applies to the Character's Country if they are the Ruler of it
			state_turmoil_mult = 0.1
		}
	
		interest_group_modifier = {												# Applies to the Character's Interest Group if they are the Leader of it
			interest_group_pol_str_mult = -0.05
			interest_group_pop_attraction_mult = 0.1
		}
		
		executive_modifier = {													# Applies to building levels owned by the company that the character is the executive for
			building_throughput_add = 0.05
		}
																			
		possible = {															# Used to determine if this trait is a valid random choice
			popularity < 0														# Does NOT impact the validity of the trait once it's acquired
		}
	
		weight = {																# Script value to determine how likely it is the character will randomly get this trait, compared to other traits in its category. Default 1
			value = popularity
			multiply = -1
		}
	
		replace = {																# When the character gains this trait, any traits they have in the following list are removed
			famous
			wicked
		}
	
		value = 2																# How much this trait is "worth" in experience levels traits or not. Default 1
																				# Used to determine whether the character is owed more traits, and which trait category is overrepresented
	}
