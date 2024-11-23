	scripted_gui_key = {
		scope = < string >			# What scope type this SGUI is available to
		is_shown = { trigger }		# Determines whether the SGUI is shown / available to a player
		is_valid = { trigger }		# Determines whether the SGUI can be used by a player
		effect = { effect }			# Determines what will happen when the SGUI element is activated
		saved_scopes = { scopes }	# List of strings corresponding to scopes you want event targets for in triggers / effects
		notification_key = < key >	# Notification key when this SGUI is activated (default jomini_scripted_gui_confirm)
		confirm_title = {}			# Confirmation window title for this SGUI
		confirm_text = {}			# Confirmation window text for this SGUI
		ai_is_valid = { trigger }	# Whether this SGUI is available to the AI or not (default false)
		ai_chance = { }				# The chance that the AI will activate this SGUI (script value between 1 and 100)
		ai_frequency = {}			# Named value determining how frequently the AI will evaluate this SGUI (in months)
	}
