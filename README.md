KUDA AI tweaks
Release version: https://www.nexusmods.com/x4foundations/mods/839
Development version: https://github.com/kuertee/x4-mod-da-ku-ai-tweaks
by deadair, kuertee

Attack AI Tweaks read-me is below. There is also a Google Sites that contains the main portions of this text for easy reading: https://sites.google.com/view/x4-mod-kuda-ai-tweaks/kuda-behaviours
DeadAir's AI Tweaks read-me is here: https://github.com/kuertee/x4-mod-da-ku-ai-tweaks/blob/master/deadairaitweaks-read-me.md
(Check the Extension Options, please.)

Updates
=======
v7.6.1.2, 16 Jun 2025:
- Bug-fix: Calculation in vector angles used in the avoidance behaviour. E.g. determining which vector to take to avoid an obstacle.

v7.6.1.1, 15 Jun 2025:
- Tweak: Chinese localisation by Mantxi.

v7.6.1, 14 Jun 2025:
- New feature: Turreted-focus capital ships now rotate to attack their module targets with their broadsides. Note that the base-game determines which capital ships do this. E.g. The Barbarossa is set to attack front-facing even when they have no guns by the base game, not by Kuda. Note that with this feature, no capital ships should be performing the base-game strafing runs across against stations. In previous versions, only front-focused capital ships were Kuda-controlled. In this version all capital ships are. (These strafing runs were the primary cause of losses against stations.)
- New feature: Capital ships now consider other stations very near their station target as a structure of their station target. What this means is that capitals now do not "avoid" those other stations. E.g. Khaak defense stations around Khaak bases.
- Bug-fixes: Several bugs to the Move To Engage (MTE) behaviour of capital ships to their module targets were fixed. E.g. Determining when the capital ship has arrived at their intended vector. E.g. Getting stuck in the MTE at the same position. etc.
- Tweak: Capital ships now re-engage their module targets vertically when they have trouble firing at their module targets on the horizontal plane. E.g. They don't have line-of-sight to the module target. Note that in previous versions, this vertical re-engagement was only used if their engage position is too near a nearby high-risk enemy. In this version, this vertical re-engagement is used at the two cases described above.
- Removed feature: Bug-fix to ships pursuing targets outside their protect range. Official Egosoft fix was added to the base game in 7.5 beta 9.

Attack AI Tweaks:
=================

Mod effects
===========
All ships acquire the "Avoid High-risk Enemies" and "Move To Engage Target" behaviours. Destroyers and larger ships acquire the "Step Forward" and "Withdraw (to regenerate shields)" behaviours.

Requirements
============
SirNukes Mod Support APIs mod (https://www.nexusmods.com/x4foundations/mods/503)
Kuertee's UI Extensions mod (https://www.nexusmods.com/x4foundations/mods/552)

Notes about this mod and my ideas behind it:
============================================
1. This read-me is for my portion (Attack AI Tweaks) of this combined mod. DeadAir's read me is linked at the top of this read-me.
2. Stations are for delaying attackers until reinforcements arrive. They're not ship destroyers - unless only a few ships or small ships attack them. No changes to station behaviours are in this mod.
3. Survivability is the reason behind the changes to the ship behaviours: avoid high-risk enemies, attack slowly, withdraw when necessary.
4. Re: Skill adjustments to behaviours: Low-ranked pilots are impulsive and overly-confident. High-ranked pilots are careful and patient.
5. There are no actions that are random in the mod (in all my mods, actually). The only actions that are random are the ship's avoidance direction (clockwise/counter-clockwise) and angle adjustments to their withdraw vectors.
6. Situations (e.g pilot skill, shield strength, direction of enemy, etc.) and events dictate the ships' actions. They are easily guessable (when you learn their behaviours, of course).
7. When they are not avoiding, withdrawing, moving to engage position, the ships attack with the base game AI. I.e. This mod doesn't actually change their actual attack behaviours (e.g. lauch drones, what their turrets do, etc.).
8. Read the "What this mod doesn't do" section below.

The custom behaviours: Avoid, Move to engage, Step forward, Withdraw
====================================================================
Note that all ships will always acquire the Attack behaviour when their AI commanders or the player orders them to attack. The Attack order will be listed in their Behaviour menu. This mod will never remove this order. Only their commanders or the player cancels this Attack order.

This mod only applies the custom behaviours at the events listed below. When the ships do not have any of these custom behaviours in their Behaviour menu, their base-game AI is controlling them.

Note that these behaviours can be controlled by the player several ways. They are listed in the section, Player controls, below.

1. At the start of attack runs:
	Vs stations:
		Ships will acquire the MOVE TO ENGAGE POSITION behaviour at a distance based on their combat range and adjusted by the pilot's rank.
			The engage position is 75% their combat range for low-rated pilots - putting them in danger sooner. And 100% for higher-rated pilots.
			The MOVE TO ENGAGE behaviour prevents them from ramming their targets.
		XSSM ships will AVOID (i.e. circle) their station targets until the number of attackers, adjusted by their pilot's rank, outnumber 75% of the station's turrets or if they have missiles and/or torpedoes.
			Low-rated pilots will over-estimate the number of attackers by up to 2 times - causing them to attack earlier.
		When the number of attackers outnumber the station's turrets (at that percentage), XSSM ships will attack as long as their shields are full.
			75% shields for low-rated pilots. They are impulsive and over-confident. And up to 90% shields for high-rated pilots. They are careful and patient.
	Vs ships:
		XSSM ships with full shields will attack their ship targets.
		XSS ships with less than full shields will AVOID their ship targets until the number of attackers, adjusted by their pilot's rank, outnumber 25% of the ship's turrets.
			Low-rated pilots will over-estimate the number of attackers by up to 2 times - causing them to attack earlier.
		M ships with less than full shields will AVOID their ship target until the number of attackers, adjusted by their pilot's rank, outnumber 50% of the ship's turrets.
			Low-rated pilots will over-estimate the number of attackers by up to 2 times - causing them to attack earlier.
		When the number of attackers outnumber the ship's turrets (at that percentage), XSSM ships will attack as long as their shields are above a certain percentage based on their pilot's rank.
			75% shields for low-rated pilots. They are impulsive and over-confident. And up to 90% shields for high-rated pilots. They are careful and patient.
2. During attack runs:
	Vs stations:
		L,XL class ships will STEP FORWARD several meters based on their pilot's rank once a minute until they are at an optimal range based on their main guns and turrets.
			2 km at every step for low-rated pilots - putting them in danger sooner. And 1 km at every step for high-rated pilots.
		By the base-game's default AI, carriers' operational distance during combat is 60% to 90% their max radar range - putting them out of combat.
			Enable "Carriers attack like destroyers" setting to allow them to fight like destroyers.
			Remember that carriers may not have long range main guns - putting them in danger as they attack with their close-range turrets.
3. While AVOIDING:
	XSSM will repair/resupply if necessary. Make sure their resupply settings in their "Individual Instructions" menu are enabled.
	Ships with the "Attack all enemies" setting enabled in the Behaviour menu will attack non-high-risk enemies.
4. When shield levels fall:
	Vs ships and stations:
		XSSM ships will WITHDRAW when their shields fall below a certain percentage based on their pilot's rank.
			Vs stations: 75% shields for low-rated pilots. And 90% shields for high-rated pilots.
		LXL ships will WITHDRAW when their shields fall below a certain percentage of their enemy's shields.
			Vs stations: 75% shields for low-rated pilots. And 90% shields for high-rated pilots.
			E.g. if a ship's enemy has 50% shield, the ship will withdraw when the ship's shields fall below 90% of their enemy's shield, which is 45%.
		The distance of this WITHDRAWAL is based on the level of their shields.
		Farther when shields are low. Nearer when shields are still high.
		Ships will try to draw their targets towards an ally when WITHDRAWING.
		Note that the WITHDRAW behaviour is not the Flee behaviour.
		The WITHDRAW behaviour is to remove the ship from their target's weapons range temporarily to regenerate their shields.
	Vs ships:
		LXL ships WITHDRAW later than when fighting against a station.
		They also return to combat if the enemy chases them.
		When their survivial chance is low, they will stop WITHDRAWING and fight on.
5. While WITHDRAWING:
	XSSM and LXL ships will cancel their WITHDRAWAL when their hull is damaged to below 50%. Their chance of survival is low.
		Vs stations: 40% shields for low-rated pilots. And 25% shields for high-rated pilots. High-rated pilots stay in the attack longer.
	They will also cancel their WITHDRAWAL when their ship target's shields fall below 25%.
	They will also cancel their WITHDRAWAL when they detect that their ship target has stopped chasing them.
6. When changing station module targets:
	LXL ships will attempt to get a better attack vector by moving around the station with the MOVE TO ENGAGE POSITION behaviour.
7. Avoiding high-risk obstackles:
	XSSM and LXL ships will always AVOID enemy stations and enemy LXL ships that are in the way of their destinations or targets. (https://youtu.be/mWBef0_mrmE)

High-risk enemies
=================
Potentially high-risk enemies are 1.5x physically larger than the ship.
For XSS ships, high-risk ships have 75% more turrets, adjusted by the pilot's rank, than the number of attackers.
For M ships, high-risk ships have 50% more turrets, adjusted by the pilot's rank, than the number of attackers.
For XSSM ships, high-risk stations have 75% more turrets, adjusted by the pilot's rank, than the number of attackers.
For LXL ships, high-risk enemies have 25% more damage-per-second (DPS), adjusted by the pilot's rank, than the ship's DPS.

NPC piloting skills and morale
==============================
The NPC pilot's piloting skills and morale affect these behaviours:
1. Counting attackers on enemy targets: Pilots of lower skills and morale overly count attackers - judging their targets to be of lower-risk than they should be.
2. Engage position: The engage position of pilots with lower skills and morale are closer to the target - specifically, 75% combat range instead of 100% combat range.
3. Step forward distance: Pilots of lower skills and morale step forward 2 km at a time instead of 1 km at a time.
4. Shield percentage for withdrawal against stations: Pilots of lower skills and morale will withdraw when their shields are at 75% instead of at 90%.
5. Shield percentage for withdrawal against ships: Pilots of lower skills and morale will withdraw when their shields are at 40% instead of at 25%. Against ships, pilots of lower ranks withdraw sooner than pilots of higher ranks.

Disable these skill-based features in the Extension Options so that all ships operate at perfect skill and high morale.

Player controls
===============
1. The AVOID, STEP FORWARD and WITHDRAW behaviours can be disabled several ways:
	Disabling the option in the ship's Behaviour menu will prevent the ship from acquiring the behaviour during an Attack session. I.e. Multiple successive Attack orders is one session.
	It will be re-enabled on new Attack sessions.
	Cancelling the order from the Behaviour menu will prevent the ship from acquiring the behaviour again until all the Attack orders in the queue are complete.
	Using the Interact menu will prevent the ship from acquiring the behaviour until it is re-enabled with the Interact menu.
	Disabling the behaviours in the Extension Options will prevent all ships from acquiring the behaviour.
2. The ATTACK ALL ENEMIES setting of the base-game Attack AI can be enabled/disabled with the Interact Menu.

Coordinated Attack Quality-Of-Life Changes
==========================================
1. "Weak targets first" option is disabled by default.
	Addresses this problem in this AI of the base game: The opposite default in the base game would make the attackers chase after fighters and ignore their capital ship primary target.)
1. Rally points are much further from the target.
	Addresses this problem: This minimises the occurence of the target attacking the ships while they wait for the others to arrive at the rally point.
2. The rally points are not set until the ships are in the same sector as the target.
	Addresses this problem: This prevents rally points from sometimes getting set on the other side of the target - causing your ships to fly across its turrets.
3. The attackers will not wait for wingmen that are busy or are two or more sectors away. This allows you to order other ships in the fleet to do other activities. In the base game, their orders will be overriden by orders from the Coordinated Attack AI.
	Addresses this problem: E.g. Subordinates don't need get removed from the fleet if you've ordered them to get repaired already.
4. Rally points are reset when the target moves.
	Addresses this problem: The target has moved elsewhere.
5. Target is engaged when either: it attacks or when it moves away and its travel drive is activated.
	Addresses this problem: The ships continue to wait at the rally point when they should just attack.
6. The Coordinated Attack order of the lead ship is replaced with the normal Attack order when the attack starts. The new behaviours work better when the Attack order is not "embedded" in the Coordinated Attack order.

What this mod doesn't do
========================
1. Order fleet subordinates to attack. Fleet subordinates only acquire this mod's attack behaviours WHEN they acquire an attack order from either their commander or the player. This mod will never start their attacks. How they behave at the start of their attack, defend and intercept stances are determined by their AI commander's orders.
2. For XSSM ships: set their starting targets. The only time this mod sets targets for XS (except for drones), S, and M ships are when they are circling a high-risk enemy AND their "Attack all enemies" option is enabled.
3. For LXL ships: set their targets.
4. Dictate when ships use their missiles and torpedoes.
5. Increase the efficiency of attacks in low attention. Damages received and dealt in attacks in low attention are determined by the base game. I.e. ships could be in good attack ranges (and out of reach of their target's weapons) but still not deal the optimal damage per second.

Install
=======
- Unzip to 'X4 Foundations/extensions/kuertee_attack_ai_tweaks/'.

Uninstall
=========
- Delete the mod folder.

Debugging
=========
1. Allow the game to log events to a text file by adding "-debug all -logfile debug.log" to its launch parameters.
2. If an Extension Options entry exists for the mod, enable the mod-specific Debug Log.
3. Play for long enough for the mod to log its events. Or force the error that you are experiencing.
4. Send the log found in My Documents\Egosoft\X4\(your player-specific number)\debug.log to my e-mail (kuertee@gmail.com) with the mod name in the subject line.

Uninstall
=========
- Delete the mod folder.

Credits
=======
Attack AI Tweaks by kuertee.
DeadAir's AI Tweaks by DeadAir.
Chinese localisation by Mantxi.
French localisation by Merlwynn (pre 7.5) and Calvitix (post 7.5).
German localisation by EagleFour. Previously by LeLeon.
Japanese localisation by Schwarzemona. Previously by Arkblade.
Russian localisation by leonkillerua.

History
=======
v7.6, 28 May 2025:
- Tweak: 7.6 compatibility.

v7.5.14.1, 24 May 2025:
- Bug-fix: Ships were sometimes getting stuck trying to avoid stations near gates.

v7.5.14, 24 May 2025:
- Bug-fix: L and XL ships: were not withdrawing against capital ship enemies when their shields are low.
- Bug-fix: DA's Increased Bounty Range were rewarding the player for kills performed by player-owned npcs. It's suppose to increase the range of finding factions to reward the player for kills of the faction enemies to the player's whole sector instead of just to the player's max radar range.

v7.5.12, 5 May 2025:
- Bug-fix: L and XL ships: were having problems moving towards their module target that is positioned at their stations' 0,0,0 origin. Examples of these types of stations are the Xenon asteroid base stations - and maybe the Khaak hives also. But I've not tested this against Khaak hives. In this version, the module target's orientation and size is taken into account in determing the attack vector for them.
- Bug-fix: L and XL ships: The Move To Engage position were adding the number of times the ship Withdrew to its distance that causes the Move To Engage position to be very far from the station. In this version, the number of times the ship Withdrew is reset when they use the Step Forward behaviour.
- Bug-fix: All ships: The Avoid behaviour was sometimes losing its destination data causing it to get stuck "avoiding" the obstacle instead of continuing towards its destination when the obstacle is no longer "in its way".

v7.5.11, 26 Apr 2025:
- Bug-fix: Compatibility with Scouts feature of the NPC Reactions mod. Kuda was making scouts ignore their Do Not Engage order settings.
- Tweak: XS (except drones), S and M ships: The ship's "Attack when more than this turret count" settings are now used to determine whether they should take a risk or not. Previously, the settings were used to determine high-risk enemies. (The difference between the two is subtle, but they are different in-code.) Note that ships with missiles and torpedoes are still exempt from this restriction.
- Bug-fix: L and XL ships: in some circumstances, were still using the Move To Engage behaviour against ship targets. They shouldn't.

v7.5.101, 18 Apr 2025:
- Bug-fix: L and XL ships: Ships not moving towards their targets: Module targets that have been disabled but not destroyed were preventing ships from performing the Move To Engage and Step Forward behaviours because those modules became wrecks and were no longer classed as station modules.
- Bug-fix: L and XL ships: The Move To Engage behaviour was not moving the ships away from stations when moving between targets when they had to.
- Bug-fix: L and XL ships: The Step Forward behaviour was moving the ships up (or down) the vertical plane at every "step". The vertical adjustment to their position is suppose to only determine their vertical position at the start of the their attack.
- Bug-fix: All ships: The Avoid behaviour was interrupted when avoiding a high-risk enemy on the way to the ship's actual target causing the ship to alternate between the Avoid behaviour and an attack behaviour which immediately was cancelled for the Avoid behaviour to continue.

v7.5.10, 16 Apr 2025:
- Bug-fix: L and XL ships: Turreted-only ships were staying away from their station targets. Kuda behaviours are suitable for capital ships with front mounted weapons. Turreted-only ships now perform base-game AI movements. (I'll find Kuda behaviours for them in the future. I don't like capital ships flying like corvettes and frigates.)
- Bug-fix: L and XL ships: were still not facing their target after performing their Kuda behaviour. They will now.
- Tweak:   L and XL ships: were still performing the Step Forward behaviour against ships. They now down.
- Bug-fix: L and XL ships: their Move To Engage behaviours around station targets were sometimes getting interrupted. They will now continue moving around to their allocated attack vector.
- Tweak:   L and XL ships: better Move To Engage attack vectors.
- Tweak:   L and XL ships: when their Move To Engage path will put them near a dangerous area of the station (e.g. convex-shaped stations), they will firstly move away from the station before moving to their attack vector.

v7.5.09, 07 Apr 2025:
- Bug-fix: Kills by the player were getting processed twice in regards to faction relationships and reactions when DA's Notifications - SubordinateBounties is enabled.
- Bug-fix: XS (except drones), S and M ships: Will now acquire the Avoid behaviour against ships ONLY when their shield levels are low or have no missiles or turrets. Previously, they were acquiring the Avoid behaviour even when their shield levels are high.
- Bug-fix: XS (except drones), S and M ships: When the Avoid behaviour is active, will re-evaluate their target's risk levels for cancellation of the Avoid behaviour. Previously, they were indefinitely circling their target.
- Bug-fix: XS (except drones), S and M ships: When assessing risk, they now count all their target's attackers. Previously, they were counting only their target's capital ship attackers.
- Bug-fix: XS (except drones), S and M ships: Will not acquire the Move To Engage behaviour anymore. Previously, they were using it when they should just attack their target. The Move To Engage behaviour is only for capital ships.
- Bug-fix: XS (except drones), S and M ships: Will not acquire the Withdraw behaviour anymore. Previously, they were using it when they should use the Avoid behaviour. The Withdraw behaviour is only for capital ships.
- Bug-fix: L and XL ships: Will not acquire the Move To Engage behaviour against ship targets anymore. Its use is too inefficient against ships. Will be used only against station targets.
- Bug-fix: L and XL ships: Will not acquire the Step Forward behaviour against ship targets anymore. Its use is too inefficient against ships. Will be used only against station targets.
- Bug-fix: L and XL ships: Will face the target at the end of the Move To Engage behaviour and the Step Forward behaviour.

v7.5.07, 29 Mar 2025:
- Bug-fix: The mod-specific debug logging was likely left on after the last update. This will disable it, if it wasn't already disabled manually in the mod's Extension Options.

v7.5.06, 20 Mar 2025:
- Bug-fix: The mod-specific Debug Log (found in the Extension Options menu) functionality was sticking to "on" in new games.

v7.5.03, 05 Mar 2025:
- Bug-fix: Coordinated Attacks were not adding the attack orders on ships.
- Bug-fix: Carriers were ignoring the "Carriers attack like Destroyers" option at the first instance of the attack.

v7.5.02, 03 Mar 2025:
- ALL the points below only apply to ships that are allowed to avoid and/or step forward and withdraw:
- Bug-fix: The Move To Engage Position is now only applied on capital ships vs stations. Previously, capital ships vs ships were acquiring the behaviour.
- Tweak: If a Move To Engage Position will put the ship near another high-risk enemy, a pitch component will be added to the vector to the target that ensures the capital ship will not get near the other high-risk enemy.
- Tweak: New high-risk enemies while in high-risk operations (vs. stations, for example) are now always reported to the fleet. Previously, only when a high-risk enemy has hit a ship in the fleet will that high-risk enemy be reported. In this version, a radar identification of that high-risk enemy would alert the ships in the fleet.
- Tweak: ALL base-game attack moves by capital ships are now disabled. There were two other movements that were getting triggered in the 7.5.01. To clarify, ships will now only use these custom behaviours during attacks: Move To Engage, Step Forward, Withdraw, Avoid.
- Tweak: Better obsolete data clean-up on every game-load.
- Tweak: Better detection of when the ship is destroyed for data clean-up.

v7.5.01, 21 Feb 2025:
- Bug-fixes: 7.5 compatibility updates.
- Tweak: re-enable step forward every 60 seconds.
- Tweak: Increase threshold of determining nearby high-risk enemies. Useful when two enemy stations are near each other.
- Bug-fix: Do not acquire stations as new big targets. Only allow capital ships as new big targets. Note: Attack All Enemies settings need to be enabled in the ship's attack orders for them to acquire new big targets.
- Bug-fix: Ships in Coordinated Attack wait orders were not acquiring new big targets.
- Bug-fix: Better Move To Engage vectors when targeting modules.
- Tweak: Prevent new module targets if the old module target is still operational.
- Bug-fix: Coordinated Attack wait orders were released too far from the target.
- Bug-fix: Move To Engage position behaviour now avoids high-risk enemies blocking their targets.
- Tweak: L and XL ships of a fleet will repair/resupply one at a time only instead of all together.
- Tweak: removed fixes to pursue targets because they are now in 7.5. beta 9 of the base game

v7.1.17, 10 Dec 2024:
- Bug-fix: Deteminating a ship's behaviour towards an enemy in the way towards the ship's attack target or flight destination could result in the ship avoiding a non-high risk enemy. Bug introduced in last version when I added the option "Attack all enemies" to this determination. In this version, the ship would ignore low-risk enemies that are in the way and decide to either attack or avoid high-risk enemies in the way. Previously, the ship would either only attack or avoid and not acquire the ignore behaviour.

v7.1.16, 03 Dec 2024:
- Bug-fix: The Alerts set in the Global Orders of the Player Information menu were getting minimised to near suppression.
- New feature: The Pursue Targets settings of the patrol and protect orders were getting ignored. This was a base-game bug.
- Tweak: The Wait For Signal for 1 hour on auxilliary ships are now removed when the orders of ships requesting to dock for repairs change. The WaitForSignal getting stuck could be caused by the base game.

v7.1.13, 02 Nov 2024:
- Tweak: High-risk determination takes into account the ship's primary purpose along with the ship's threat score.

v7.1.12, 19 Oct 2024:
- Bug-fix: While performing one of the custom behaviours of Avoid, Withdraw, Move To Engage, enemies in the ship's way were either only attacked or avoided. In this version, they can also be ignored. An example case is when a capital ship is targeting an enemy capital ship on the other side of a station. In previous versions, that capital ship would attack low-risk enemies on the way around the station. In this version, those low-risk enemies are ignored.
- Tweak: The calculation of whether an obstacle is in the way only used its yaw bearing and distance in relation to the ship. In this version, the obstacle's pitch bearing is also used.
- New feature: updated the Russian, German, and Chinese language text files. Included a Japanese language text file.

v7.1.11, 19 Oct 2024:
- New feature: High-risk enemies in the way of a ship's target can now be attacked, ignored or avoided. In previous versions, they were always avoided.
- Tweak: The size aspect of high-risk calculations are now based on the ship's internal threat score instead. In previous versions, it was based on the ship's physical in-world size. I wanted to trigger the behaviours based on "oh sht! that ship is huge." rather than an internal data that is magically known. (But not anymore.)
- New features and tweaks from DA: MANY!

v7.0.02, 29 Jun 2024:
- Tweak: 7.00 hf 1 compatibility.
- Beta: Tested only so that no errors are thrown. Actual AI performance is in beta.

v6.2.013, 25 Feb 2024:
- Localisation: Russian translation by Leonkillerua.
- Bug-fix: The attackers of victims are not getting counted properly which causes strike ships to continually avoid their high-risk targets.

v6.2.011, 18 Feb 2024:
- Bug-fix: The name of ships were getting cleared. My bug. Fixed by DA. Most ships should "fix" themselves on first use of this version. The rest will eventually get fixed as they use the AI files that were affected by the bug.
- Bug-fix: The player's Interact menu settings of Avoid and Withdraw/Step forward were getting reset in previous versions.
- DeadAir updates: Updated to match vanilla class selection that previously omitted class.ship_xs.
- DeadAir updates: Added missing check that may have prevented patrol ships from assisting same owner assets in sector owned by separate faction.
- DeadAir updates: Other minor updates.
- Tweak: Coordinated attack: ships avoid untargeted high-risk enemies like they do when with normal Attack AI.
- Tweak: Strike craft (with no missiles and no torpedoes) encircling their high-risk targets will use their skill-based avoid distance instead of the much shorter distances of previous versions, which were not far enough to avoid enemy turrets when the VRO mod is used.
- Tweak: Optimisation: Fleet commanders share their big enemies list with nearby subordinates. In previous versions, all subordinates ping their radar for big enemies. Note that this is specific to Kuda behaviours. The ships' base-game radar functionality is unaffected.
- Tweak: Optimisation: Strike craft finding smaller target (while circling their high-risk target) is now based on the nearest small target and the nearest big enemy. In previous versions, this process loops through each object in both lists to identify the most appropriate smaller target.
- Tweak: Optimisation: Withdraw behaviour: Reactions to hit frequency reduced from one every 0.25 seconds to one every 1 second. This can be changed in the Extension Options but only when Debug Log is enabled. Enable Debug Log in the mod's Extension Options menu. Exit the menu. Then re-open it. Remember to disble Debug Log again after changing this setting.
- Tweak: Optimisation: Avoid behaviour: Reactions to radar contact frequency reduced from one every 0.25 seconds to one every 1 second. This can be changed in the Extension Options but only when Debug Log is enabled. Enable Debug Log in the mod's Extension Options menu. Exit the menu. Then re-open it. Remember to disble Debug Log again after changing this setting.

v6.2.010, 28 Dec 2023:
- New feature: coordinated attack: avoids high-risk enemies on the way to target.
- Tweak: optimisation: limit avoid/withdraw determination on hits and radar scan. to every quarter second. My previous implementation of this wasn't working, allowing many events within one second.
- Bug-fix: move to engage: hits were interrupting the move around for a better solution avoid ai.
- Bug-fix: get in the way: distance calculation of destination.
- Bug-fix: S/M ships avoid high-risk but find smaller targets: on attacking smaller targets, the avoid behaviour was getting disabled.

v6.2.0095, 26 Dec 2023:
- Bug-fix: avoid: general move around target had a bug.
- Bug-fix: avoid: while in patrol or protect mode, avoid high-risk untargeted enemies but do not avoid attack targets.
- Bug-fix: ship names were getting removed. Unfortunately, players will need to fix the names of ships that have been cleared manually. Open the ship's Information menu, activate the name entry text box, ensure that it's empty, and press enter. This will set the name to its base name from the internal game library.

v6.2.0094, 25 Dec 2023:
- Bug-fix: avoid: unlink behaviour from stepforward settings;
- Bug-fix: avoid: allow on ships on way to attack.
- Bug-fix: move to engage: clear forced avoid destination var used in moving around to better target modules when done with move to engage behaviour.
- Bug-fix: allow custom behaviours to continue even if module target is not operational because order.fight.attack.object keeps setting it as a target even if it is non-operational.

v6.2.0093, 24 Dec 2023:
- Bug-fix/returned feature: encircle target instead of moving around it for attacks and attack small target in this avoid order instead of the general attack order;
- Bug-fix/returned feature: move to engage position: move around previous destroyed module to target new module target uses avoid ai
- Tweak: find smaller target doesn't require 'Attack all enemies' anymore because they would often attack nearby stations instead of circle their original station target after attacking smaller targets.
- Bug-fix: avoid and withdraw: better assessment of whether new attacker should be ignored, attacked or avoided.
- Bug-fix: determining if object is in the way: in some cases the larger arc is getting used rather than opposite smaller arc of within -45 and 45;
- Tweak: avoid or not: assess if target is in the way only if taking risk;
- Bug-fix: get is take risk: bug-fix test of low shields;
- Tweak: get avoid vector: limit pitch to between -15 and 15 of avoid target.
- Tweak: get in the way: test only if obstacle is within max radar range AND obstacle is nearer than destination.
- Tweak: avoid or not handler: always evaluate if ship will take risk;
- Tweak: avoid and withdraw: add station/ship size to distance to avoid/withdraw
- Bug-fix: encircle AI clockwise/anti-clockwise direction doesn't changes once set for that attack.
- Tweak: assess avoid or not at start of protect, escort, attack and move orders;
- Bug-fix: avoid, withdraw, stepforward orders: when interrupted by another attacker, capital ships do not get distracted by smaller ships.

v6.2.0091, 19 Dec 2023:
- Bug-fix: Determining if an object is in the way: difference of the two -180 to 180 yaw angles is greater than 180 results in the larger arc - which is considered not in the way. The opposite smaller arc is used in this version.
- Bug-fix: Ships that are withdrawing can determine if new attackers should be attacked, avoided or ignored.
- Bug-fix: Ships that are moving to engage position can determine if new attackers should be attacked, avoided or ignored.

v6.2.009, 17 Dec 2023:
- New feature: Debugging: When "Debug log" is enabled in kuertee: Attack AI Tweaks Extension Options, the ship's behaviour will be labeled with Kuda behaviours WHEN they are using Kuda behaviours. Note: Determining if a ship is using Kuda AI or base-game AI is easier. See one of the screenshots on Nexus Mods to see how this looks on the map.
- Tweak: Re-enabled Kuda behaviours during attacks. In the last version, only the avoid behaviour was enabled. I.e. Move to engage position, withdraw and step-forward were disabled.
- Bug-fix: An instance of the avoid behaviour was not getting used even when the ship should avoid.
- Tweak: Optimisation: use the $jumppath var from move.generic when determining next move position instead of recalculting it.
- Bug-fix: Avoid/withdraw determination: sort gravidar contacts in ascending distance order from the ship.
- Bug-fix: Avoid/withdraw determination: shield test and ship purpose vs stations.
- Bug-fix: Corrected the vectors for the avoid (while heading towards the ship's destination). In the previous version, the vectors were sometimes wrong - based on the orientation of the object to avoid and the ship's destination. I.e. some vectors were correct. This math (based on the autopilot AI of my Autocam and Autopilot mod) is corrected in this version.
- Bug-fix: Do not use Withdraw behaviour except during attacks. i.e. Withdraw behaviour moves exactly away (180 deg) from the object. Avoid behaviour moves around (about 90 deg, more or less) while heading towards the ship's next destination.
- Bug-fix: Taking risk determination: vs a target, other nearby big enemies.

v6.2.008, 09 Dec 2023:
- Bug-fix: Avoid behaviour: do not recalculate avoid vector when the ship's movement is interrupted by an attack.
- Tweak: Cleaner method of refreshing the order on new mod updates without relying on the base-game's versioning numbers. (Using the base game's versioning number method to refreshing the order may conflict with Egosoft's updates.)
- Tweak: Avoid determination: when avoidance due to low shields (instead of the enemy ship being simply high-risk) is determined to be the best behaviour, perform the withdraw behaviour instead.
- New feature: "Surround" toggle in the Coordinate Attack order. When enabled, engage position of all ships will encircle the target.

v6.1.004, 01 Aug 2023:
- Bug-fix: Withdraw custom behaviour: withdraw position was still getting reset to a new position at every hit.
- Tweak: When you have my mod UI Extensions installed, the custom behaviours will be listed in the Interact Menu's Custom Actions/Custom Orders sub-menu.

v6.1.002, 29 Jul 2023:
- New feature: DeadAir's major update.
- Bug-fix: Fleeing AI of Kuda-enabled ships returned. Previously, it was deferring to Kuda's avoid/withdraw AI - which wasn't ideal.
- Tweak: Fleeing conditions: Kuda-enabled ships only flee based on their avoid/withdraw AI. Note that this although the triggers for the flee AI has been reset to the base game's triggers, the conditions of when Kuda-enabled ships flee defers to their avoid/withdraw determination.
- Bug-fix: Avoid High-risk Enemies: Default to the ship's next original intended waypoint if it is closer (and is not blocked by the high-risk enemy) than the Avoid High-risk Enemies position. E.g. When the intended destination is a gate, and it is closer than the Avoid position, then the avoid position will be at the gate.
- Bug-fix: The Move To Engage Position behaviour was getting reset to a new position at every interruption of the move.
- Tweak: Move To Engage Position: minimise overcrowding. It still occurs if you have a lot of ships (e.g. more than 10).
- Tweak: Coordinated Attack positions: better ship movement to their rally point positions. i.e.: Ships do not move to the other side of the arc anymore.
- Bug-fix: The conditions to repair/resupply was broken that ships were still going to repair even when high-risk enemies are nearby.

v6.0.002, 13 Apr 2023:
- Tweak: Version number update for consistency with my other mods. No internal changes since v6.0.0007.

v6.0.0007, 4 Apr 2023:
- Tweak: Compatibility with 6.0 beta 7 of the base game.
- New feature: When the fleet commander is destroyed, the replacement commander acquires their default order. Note: In the base game, the replacement commander acquires the Hold Position order when their commander is destroyed.
- Tweak: Better implementation of the Interact Menu options for setting individual ship's usage of the custom behaviours.
- Tweak: Subordinates acquire the Attack AI sooner when their commander acquires the Attack AI.
- Bug-fix: The Wait For Signal AI on resupply ships are cancelled when the repair or resupply order on the ship that forced the resupply ships to Wait For Signal.
- Tweak: Determining vector for avoidance based on their final destination.
- Bug-fix: Some ships were not getting initialised as Kuda-enabled - even when they should be.
- Other tweaks and bug-fixes: Many other minor tweaks and minor bug-fixes.
- Note: This version should work with 6.x and 5.x of the base game.

v6.0.00041, 28 Feb 2023:
- Tweak/Bug-fix: Capital ships' avoid/withdraw determination against other capital ships: when shields are lower than their skills-based percentage of their target's shields. In previous versions, the ships withdraw/avoided when their shields are lower than those percentage levels. In this version, they avoid/withdraw when their shields are lower than the percentage levels OF THEIR TARGET. Result: ships will stay in fights against other ships much longer. This follows more closely the more realistic surrender reactions of NPC combatants portrayed in my Oblivion (NPCs Yield) and Skyrim (Fight or Fly) mods.
- Bug-fix: Ships not using all their missiles/torpedoes. I had to remove a couple of lines of DeadAir's tweaks in fight.attack.object.medium AI because it was preventing use of some missiles/torpedoes.
- Tweak: Ships with the order.fight.escort AI were avoiding their commander's attack targets.
- Bug-fix: Ships were still not acquiring their commander's attack orders soon enough.
- Tweak: Ships were moving to engage positions even when not really required.
- Note: This version should work with 6.x and 5.x of the base game.

v6.0.0004, 17 Feb 2023:
- Note: Renew any important big attack operations (e.g. Remove All Orders, Attack) that are active after a game is loaded. You only need to do this once. There's no need to renew non-importanat attack operations. Their data will renew soon after load.
- Tweak: The Avoid behaviour determination is delayed by 0.5 seconds. This prevents it from getting triggered immediately after a Remove All Orders. This allows new orders to be issued without the Avoid behaviour present in the Behaviour queue. Note that this is only useful when the game is paused. Half-a-second is simply not enough time for issuing new orders without the Avoid behaviour getting instantiated.
- Tweak: Vector determination for avoid and withdraw behaviours. E.g. All nearby high-risk enemies are considered when deciding which direction to avoid and withdraw from. Previously, only the nearest high-risk enemy factored into the avoid/withdraw vector. Watch these vidoes: https://youtu.be/UQ2xJnRdsoc (Capital ships move around the station to a better vector to target a module after destroying their previous module target.), https://youtu.be/UQ2xJnRdsoc (Capital ships moving away from a station before attacking a Xenon K.)
- New feature: Cancelling an Avoid order will disable the Avoid behaviour option in Attack orders in the Behaviour queue. This feature in previous versions prevented the use of the behaviour for only 10 seconds. Note that you can still disable the behaviour on a per-ship basis using the Interact Menu.
- New feature: Cancelling a Step forward or Withdraw order will disable the Step forward and Withdraw behaviour options in Attack orders in the Behaviour queue. This feature in previous versions prevented the use of the behaviour for only 10 seconds. Note that you can still disable the behaviour on a per-ship basis using the Interact Menu.
- Bug-fix: Ship preferences for using the Avoid and Step forward/Withdraw behaviours were getting reset at the end of combat.
- Note: This version should work with 6.x and 5.x of the base game.

v6.0.0003, 11 Feb 2023:
- NOTE: This version works with BOTH 5.1 and 6.0 beta 3.
- Tweak: Compatibility with 6.0 beta 3. About half a dozen of DeadAir's AI Tweaks had to be removed because of changes in the 6.0 beta of the base game. 90% of his tweaks are still valid.
- Bug-fix: XS, S, and M (XSSM) ships were moving away constantly while avoiding - causing them to move out of sector bounds.
- Bug-fix: XSSM ship behaviours were broken.
- Bug-fix: XSSM ships: Attacking smaller target when avoiding big target now works properly. E.g. finding targets on their side of the station, moving around the station to attack their target that's on the other side, etc.
- Bug-fix: L and XL (LXL) ships move to next module target was broken. I.e. after destroying one module target, LXL ships again move to a vector better suited to their next module target - moving away from the station first when required.
- Tweak: Carriers with ANY subordinates will now maintain distance. The Extension Option, "Carriers attack like destroyers" now works as expected. Previously, even when that option is disabled, carriers were STILL behaving like destroyers IF they had no subordinates that dock on them. In this version, they will only act lke destroyers IF (1) "Carriers attack like destoyers" is enabled; or IF (2) they have no subordinates, AND capital ship wingmen.
- Tweak: Avoid vectors now incoporate the ship's destination's vector. Previously, the vector they choose to avoid was random.
- Tweak: Withdraw vectors now incoporate ALL high-risk enemies nearby. Previously, they move away from the position of ALL nearby high-risk enemies - which somtimes is not ideal.
- Tweak: Move to engage position: Always move to engage position if target is more than 75% of max radar range.
- Bug-fix: Move to engage position: Prevent loop of move to engage position, attack, move to engage position, attack, etc.
- Tweak: Coordinated Attack: Allow sequential Coordinated Attacks. Previously, this order wouldn't chain properly because one of their attack orders would get inserted into their order list incorrectly.
- Bug-fix: Removed changes to order.move.recon.xml because one of the changes has a rare chance of causing the game to stall, making the game unresponsive while still running. May be re-enabled after the bug is tracked down in the future or when DeadAir returns to X4 modding.
- Bug-fix: Data is cleaned when docked and undocked (in case the ship receives damage while docked). Previously data is cleaned when the ship enters a new sector.
- Tweak: Optimised the hull/shield damaged event listener.
- Tweak: Optimised looking for smaller targets instead of avoiding routine.
- Tweak: Optimised avoid or take risk routine.
- Bug-fix: Many other bug-fixes.

v5.1.0314, 6 Dec 2022:
- Tweak: Better performance.
- Tweak: More reactive withdrawals by listening to "hits to shield and hull events". Previously, the mod only listened to "attacked events" - which occurred milliseconds to a second AFTER hits to shield and hull events - too late sometimes.
- Tweak: Withdraw vectors towards a nearest ally (to lure the enemy towards that ally) will never cause the withdrawing ship to move towards the enemy. Previously, the direction towards the nearest ally would cause the withdrawing ship to move towards the enemy.
- New feature: Fleet commanders now react to alerts of L and XL (LXL) targets in their sectors. They'll use the Coordinated Attack order against far away targets, and direct Attack order against nearby targets.
- New feature: LXL ships will avoid their targets when they only have 25% or less operational weapons. Previously, they cancelled their orders and reverted to their fall-back order. E.g. attack again if they are part of a fleet - which is not ideal.
- Returned features: LXL ships now perform the MOVE TO ENGAGE and STEP FORWARD behaviours against LXL targets. Base-game combat distance is sometimes too far against speedy LXL enemies.
- Tweak: Coordinated Attack: LXL subordinates attacking XS, S and M (XSSM) ships are not considered to be in the "busy" state and will join the attack.
- Bug-fix: Some ships were acquiring the behaviours when they shouldn't.
- Bug-fix: Withdraw positions were changing at every hit which was impacting the withdrawal effectiveness.
- Bug-fix: Move to engage positions and Avoid positions were changing before the ship arrived at those positions.
- Tweak: Refactored all aiscript vars into MD vars. Minimises mod footprint on the save without the mod installed.
- New feature: The WaitForSignal orders on Auxiliaries were sticking even after the Repair order has been cancelled.
- Bug-fix: Some of the "all factions" Extension Options were defaulting to true, when they shouldn't.

v5.1.0312, 22 Oct 2022:
- Bug-fix: Allow/disallow of custom behaviours on individual ships with the Interact Menu (right-click menu) was broken.
- Bug-fix: L and XL ships during the AVOID behaviour get stuck at the first avoid point.
- Tweaks: Refactored variables to the MD. The allow/disallow variables on individual ships were not working during order initialisation.

v5.1.0310, 14 Oct 2022:
- New feature: XS (except drones), S and M ships repair/resupply if required when they need to perform the AVOID behaviour.
- New feature: Carriers attack like destroyers setting. Default is off. The base-game AI prevents carriers from directly attacking their target by setting their operational distances to between 60% and 90% their max radar range. When enabled, Kuda changes this to their weapon ranges - like destroyers. Enable this in the Extension Options.
- New feature: Step forward/withdraw in the Interact Menu (i.e. the right-click menu).
- Tweak: L and XL against ships stay in the fight longer and withdraw at specific shield and hull levels. Previously they withdrew from ships like when against stations.
- New feature: WITHDRAWING ships that fail to escape notifies the fleet which stops other withdrawing ships so that they can attack the target.
- Bug-fix: The user settings that allow/disallow the use of the custom behaviours on the Interact Menu were getting ignored. From this version on, the settings in the Extension Options override all other settings. And the settings from the right-click menu persists for the ship.
- Bug-fix: Large enemies with no DPS was getting identified as high-risk.
- Tweak: Pitch angle towards target for the custom behaviours are now capped between -15 degrees and 15 degrees.

v5.1.0309, 30 Sep 2022:
- Bug-fix: XSSM ships with missles and torpedoes weren't attacking their targets even when their shields were full.
- Tweak: The "avoid" and "withdraw" behaviours were getting applied when either the "avoid" and "withdraw" Extension Options were enabled. The avoid behaviour is now applied when the avoid option is enabled. And the withdraw behaviour is applied when the withdraw option is enabhled.

v5.1.0308, 29 Sep 2022:
- Bug-fix: Remove possibility of a game freeze that sometimes occurs after having the mod for some time. Thanks to blosphere on Nexus for reporting it, providing logs and save files, and testing my fixes several times.
- Bug-fix: In general attacks (i.e. not Coordinated Attacks), the ships were not acquiring the move to engage positions behaviour - causing them to run towards their targets at speed. Bug introduced during my work on Coordinated Attack.
- Returned feature: Bombers (XS, S and M with missiles and/or torpedoes) now attack stations like they do ships. I removed this feature because I made XS, S and M ships attack their target when their shields are above the threshold for them withdrawing/avoiding EXCEPT for stations in the v5.1.0305, 15 Sep 2022 version. In this version, bombers attack stations until their shields are below their withdraw/avaoid threshold. Other XS, S and M ships avoid stations allways.
- Tweak: Improved (again) capital ships moving to their next module target - especially if its on the other side of the station.
- Tweak: Withdraw vectors to draw enemy towards allies: If there are no allies within 10 km of the enemy, ships will withdraw towards the nearest ally. If an ally is within 5 km from the target, the vector is directly away from the enemy. If an ally is within 10 km, the vector is perpendicular (90 deg) to that ally, giving the ally more chance to get closer to the enemy.
- Tweak: Only ships within 5 km or in front of their high-risk ship enemy withdraws. They withdraw against stations as in previous versions.
- Bug-fix: While avoiding targets (e.g. flying around stations), the ships were not obeying the Attack order option "Attack all enemies". They were attacking others even when the option was not enabled.
- Tweak: The "Attack all enemies" base-game feature now finds enemies in the vicinity of the fleet commander. Prevents ships away from the fleet (e.g. in another sector) acquiring targets far from the area of engagement.
- Tweak: The arc of attackers of Coordinated Attacks is half its length. Previously, each attacking ship was separated by 10 degrees. In this version, they are separated by 5 degrees.
- Bug-fix: Custom behaviours were getting cancelled automatically sometimes - causing them to flick between trying to perform the behaviour then not.
- Bug-fix: The ignore flag that gets set when to allow the ship to simply fight on when they have a low chance of surviving is removed when they regenerate their shields or when they switch to a new target.
- Tweak: Better performance tweaks.

v5.1.0306, 18 Sep 2022:
- New feature: When the custom behaviours, avoid, step forward, and withdraw, are cancelled, they will not be applied again until after 10 seconds. This gives you some control of their use. Note that this doesn't persist after 10 seconds - unlike the "Avoid high-risk enemies" Interact Menu command, which persists until re-enabled.
- Tweak: Consolidated the avoid and withdraw handlers for better performance.
- New feature: Ships will never try to restock/repair if their commander has attack orders - unless their hull is at 25% or less.
- New feature: The base flee behaviour now points to what the ship is fleeing from.
- Bug-fix: Withdraw vectors were not being applied. Instead ships were withdrawing at their facing orientation.
- Bug-fix: Recall subordinates only when the destination is more than 2 gates away wasn't working.
- Bug-fix: Coordinated Attack: Rally points weren't updating when the target moves.
- Bug-fix: The normal flee was interrupting Kuda's custom behaviours. E.g. Fleeing when withdrawing - causing large ships to break off from their attack rather than withdraw then return to attack.
- Tweak: Rewrote the avoid and withdraw conditions for better performance and clarity (ease of debugging).
- New feature: German localisation.

v5.1.0305, 15 Sep 2022:
- Note: I added notes about my ideas behind this mod. Read them as a starter for this mod - if you wish. But I always suggest to "just" use the mod after skimming through the read-me. If you have question about the mod AFTER experiencing it, THEN read the read-me.
- Bug-fix: Ships were moving WAY out of sector. This occured only once during my tests/modding. But there was definitely a bug-fix required in my avoidance code. This bug shouldn't happen again.
- Bug-fix: Escorting non-fighters (e.g. supply ships and carriers) were still drifting towards high-risk enemies. They now stay a certain distance behind their commander during attacks.
- New feature: Small-sized and medium-sized ships harass their high-risk ship targets. With full shields, they attack. With shields at their skill-based withdrawal percentage or more, they avoid their target at half their avoidance distance. With less shields, they avoid them at their full avoidance distance - as they did in previous versions.
- New feature: The recall subordinates feature of the generic move order defaults to false unless the destination is more than 2 gates away. Note that this is the Recall Subordinates order that is initiated automatically from the general move order. Ships will still recall subordinates at other times.
- New feature: Fleets can now disengage from their small attack targets to prioritise new high-risk targets. This occurs when one in the fleet first engages a new high-risk target. Addresses the problem with large ships continuing to engage with smaller ships when there's higher-risk enemy.
- Tweak: A lot of the tests for avoidance and withdraw are now in event conditions. This allows for smoother operation of the AIs.
- Tweak: Added tests to engine's capabilities to capital ship's withdraw tests. If less than 25%, they stop to withdraw and just fight.
- Tweak: Avoid AI now knows whether to either (1) move around a high-risk enemy while keeping it as a target (i.e. combat-appropriate avoid distance) or (2) actually avoid a high-risk enemy during general flights (i.e. longer avoid distances).
- Tweak: Made small craft with missiles/torpedoes to follow fighter avoidance rules. Now that fighters harass their targets, limiting these ships' attack runs will increase their surviviability, especially against station targets. Previous versions made these ships ignore the rules until their missiles/torpedoes are expended.
- Many Coordinated Attack fixes. I think this order was meant to be: (1) used from a short distance to the target and (2) managed manually. My changes (from the last update and this update) is to allow it to be used like other orders - fire and forget.
	The Coordinated Attack changes from this update are:
	1. Bug-fix of original order: subordinate orders getting initialised twice.
	2. New feature: Allow the leader to receive my custom avoid behaviour. E.g. if there's a big enemy station between it and Coordinated Attack target.
	3. New feature: Subordinates respond properly to attacks on them while they wait at their rally point. I.e. small harassing enemies will not release them but high-risk enemies will.
	4. New feature: Coordinated Attacks start to attack once their target attacks or is attacked by another ship of the same faction as the attackers. Note that Coordinated Attacks are only applied by the player to their ships. But if ever it is applied by another faction, this will work.
	5. New feature: Rally points are now in an organised arc. Ships with the Attack order are the front. Ships with the Protect Ship order are at the back.
	6. Bug-fix of Kuda's addition: Rally point of subordinates were at the original distances - instead of my intended longer distance, which the lead ship had. I.e. the lead ship's rally point was well behind its subordinate's rally points.
	7. Bug-fix of Kuda's addition: Lead ship wasn't showing its rally point.
	8. Bug-fix of Kuda's addition: Ships engage properly if the target attacks them or moves closer to the rally points.
	9. Bug-fix of Kuda's addition: Rally point now gets reset properly if the target moves elsewhere.
	Read all the changes to this order in the Coordinated Attack section below.
- Bug-fix of Protect Ship AI: Add event listeners so that ships in low-attention function like in visible attention.
- Tweaks (many): Cleaned up more of the code. Moved testing of avoidance and withdrawl determination into event conditions. Added vars to clearly define intent of code - e.g. instead of repeating test conditions. Removed unnecessary blocks of code, unnecessary debug outputs, variables. Etc.

v5.1.0304, 3 Sep 2022:
- Bug-fix: Withdrawal getting stuck between withdraw and attack behaviours.
- Tweak: Carriers now behave similar to Auxiliaries: they'll stay away from their attack target.

v5.1.0303, 1 Sep 2022:
- New feature: Refactored about 90% of my portion of the mod. DeadAir's portions are unchanged. The codebase is cleaner and easier to edit. DeadAir will be happier. :D
- New feature: Escort, Follow, and Protect orders (and any other AIs that use these, e.g. Supply) acquire the Withdraw custom behaviour. The implementation in previous versions of the withdrawal behaviour on these AIs didn't working.
- New feature: Ships that are not fighters (e.g. Auxiliaries) will always stay away (e.g. Avoid custom behaviour) from their target. E.g. Monitors will never find themselves caught within an enemy station's weapon range.
- New feature: Coordinated Attack Quality-Of-Life Changes
	1. "Weak targets first" option is disabled by default.
		Addresses this problem in this AI of the base game: The opposite default in the base game would make the attackers chase after fighters and ignore their capital ship primary target.)
	1. Rally points are much further from the target.
		Addresses this problem: This minimises the occurence of the target attacking the ships while they wait for the others to arrive at the rally point.
	2. The rally points are not set until the ships are in the same sector as the target.
		Addresses this problem: This prevents rally points from sometimes getting set on the other side of the target - causing your ships to fly across its turrets.
	3. The attackers will not wait for wingmen that are busy or are two or more sectors away. This allows you to order other ships in the fleet to do other activities. In the base game, their orders will be overriden by orders from the Coordinated Attack AI.
		Addresses this problem: E.g. Subordinates don't need get removed from the fleet if you've ordered them to get repaired already.
	4. Rally points are reset when the target moves.
		Addresses this problem: The target has moved elsewhere.
	5. Target is engaged when either: it attacks or when it moves away and its travel drive is activated.
		Addresses this problem: The ships continue to wait at the rally point when they should just attack.
	6. The Coordinated Attack order of the lead ship is replaced with the normal Attack order when the attack starts. The attack routines work better with the mod when they are not embedded in another order.
- New feature: NPC Piloting Skills and Morale
	The NPC pilot's piloting skills and morale affect these behaviours:
	1. Counting attackers on enemy targets: Pilots of lower skills and morale overly count attackers - juding their targets to be of lower-risk than they should be.
	2. Engage position: The engage position of pilots with lower skills and morale are closer to the target - specifically, 75% combat range instead of 100% combat range.
	3. Step forward distance: Pilots of lower skills and morale step forward 3 km at a time instead of 1 km at a time.
	4. Shield percentage for withdrawal: Pilots of lower skills and morale will withdraw when their shields are at 50% instead of at 90%.
	5. Withdrwal and avoidance distance: Pilots of lower skills and morale withdraw to 25% their max radar range (approximately, 10 km) instead of to 50% their max radar range (approximately 20 km).
	As an overall guide for these settings, I assumed lower-skilled pilots with low morale to be more impulsive and overly-confidennt.
	And higher-skilled pilots with high morale are more careful and patient.
	Disable all these skills-based features so that all ships operate at perfect skills and high morale in the Extension Options.
- Bug-fix: The order options, Enable/disable Avoid High-Risk Enemies, etc., for the custom behaviours weren't working.
- New feature: Board and Protect orders now have the attack "Avoid high-risk" and "Step forward/withdraw" order options.
- Tweak: New withdrawal cancellation: Ships that have a low chance of survival or ships with enemies that have a low chance of survival never withdraw or cancel their withdrwals.
- Tweak: New withdrawal cancellation: Withdrawing ships cancel their withdrawal when their enemy ship stop chasing them (and when they are at least 10km away, to allow for some shields to recharge).

v5.1.0301, 3 July 2022:
- kuertee: New feature: On new module targets: L and XL ships uses withdraw behaviour but with horizontal and vertical offsets - promotes ships to move around their station targets.
- kuertee: New feature: L and XL ships stop their withdraw behaviour against ships if their hull is less than 50%. Allows the ship to stand their ground instead of to flee a losing battle.
- kuertee: Tweak/bug-fix: When attacking a target in a different sector, the move to engage behaviour will not activate until appropriate. This prevents the bug where the engage position is at the other side of the target.
- kuertee: Bug-fix: Move to engage position behaviour against ships now update as the ships move, preventing ramming behaviour against ships. Previous versions had this disabled.
- kuertee: Bug-fix: Escorts were ignoring the new behaviours because they weren't evaluating their "$primarytarget" var properly.
- kuertee: Bug-fix: User toggle for avoid high risk wasn't sticking.
- kuertee: Bug-fix: "Move around instead of attack" behaviour applied only on XS, S, M or non-fighter ships.
- Dead Air: move.attack.object.capital: Adjusted ideal ranges for ships against stations, capitalships, and smaller ships. They will attempt to keep more distance against stations. Player ships no longer get artificial skill boost. Missile ships will no longer act as if they have a front weapon unless they actually have one. Ships will attempt to get above/below ships much less often (due to front weapon and capital aiming restrictions by egosoft). Ships will consider their minoperationalrange and maxoperationalrange when finding a position near the enemy with less RNG. Capital ships will use travel drive and boost much less often when the target is within range. Capital ships will no longer try to get into the weakquadrant of ships since it mostly led to them getting too close or trying to move too often.
- Dead Air: Engineer: Default script - removed all changes other than hull damage limit. Optional Script - Increased station repair amount 5X and scaled frequency to 5X. Reduced station max repair per cycle to 1% hull instead of 5%.
- Dead Air: lib.target.selection: Reduced stickiness of primary target by 20%. Reduced relation impact to vanilla and removed impact from subordinates relation value. XL ships will be more likely to target L/XL ship hulls or station modules themselves instead of turrets now.  L will be more likely to target M/L/XL ship hulls and XL turrets/engines/shields. Torp S/M will be more likely to target L/XL ship hulls, station modules, or L/XL/Station turrets/engines/shields. Reduced chance of non torpedo S/M of attacking station over preferred targets.
- Dead Air: move.flee: Reduced chance of AI ships dropping their cargo every time they flee.
- Dead Air: drops.xml: Reverted seminar drop rate changes.
- Dead Air: faction logic changes: Hold Space: Set default range search for defense ships to 3 jumps (preliminary steps taken to allow user to enable/disable change), balanced the desired fleet sizes so moodlevel is less likely to have fleets never engage, improved defense station placement to vicinity of gates further (preliminary steps taken to allow user to enable/disable change). Invade Space: Set default range search to include all owned sectors for the faction. No more fleets sitting around idle doing nothing in backwater systems. Balanced desired fleet sizes so moodlevel is less likely to have fleets never engage, enabled factions to order more ships from shipyard/wharf to meet their desired fleet strength. Patrol coordination: balanced acceptable force differential so patrols are more likely to engage enemies for certain moodlevels.
- Dead Air: Carrier attack fix: Added logic for current bug where docked subordinates on a carrier never receive new orders. This fix checks all docked ships and re-adds then to $escortgroup. Behavior for attacking carriers slightly changed where they will send all of their subordinates that are currently available at their primary target or it's turrets/engines/shields. If attacking and a station is a primary target but not the only target, the carrier will send a subordinate L/XL if available, else it will focus down smaller targets first. Carriers will now auto repair docked subordinate ships if they have a shiptrader.
- Dead Air: Old bugfixes: Mining ships will now drop all of the unsellable cargo if they are stuck at or above 50% cargo after mining and unable to sell. Recon - updated threat scaling of stations to account for possible weapons.operational bug

v5.1.00081, 27 May 2022:
- Bug-fix: Avoid high-risk Extension Options was getting ignored by the aiscript.

v5.1.0008, 22 May 2022:
- Bug-fix: Weapon counts on stations were 0 even if they had turrets.
- Tweak: Force L and XL ships to always move to engage position on stations even if their low DPS is not considered high-risk. I.e. they might still have high-damage plasma turrets.
- New feature/Extension Options: Separated weapon/turret count threshold on when to attack for ship and station targets. By default, S ships attack when attackers count more than 25% the weapon/turret count of ship targets and when more than 75% the weapon/turret count of station targets. M ships attack at the previous defaults of 50% for ship targets and 75% for station targets.
- New feature/Extension Options: Separated the options for L and XL ship's avoidance behaviour against ship and station targets. By default L and XL ships avoid high-risk ships and high-risk stations.

v5.1.0007, 14 May 2022:
- Bug-fix: Turret counts on high-risk enemies for the new behaviours from Attack AI Tweaks for S-sized and M-sized ships.
- Optional tweak: DeadAir's alternative to DeadAirAITweaks repair calculations. To use: copy the file from the "optional" folder into the "aiscripts" folder. From DeadAir's notes: "Changed the calculation for repair amount more based on number of crew, skill of crew, and number of repair drones. Repairs happen less often, they are lower than vanilla with small amount of service crew who are low skilled. Repair drones are now a multiplier effect on the ability of service crew. New repair rate is a minimum of 0.1% and a max of 5% hull and occurs around every 60%. Stations have a lower repair rate due to massive amount of HP and reasoning that they have less "combat" personnel onboard."

v5.1.0006, 6 May 2022:
- Tweak: The "Step forward" and "Move out of range" behaviours are separated between attacking ships and attacking stations. By default, they are set to true for both. Set them in the Extension Options.
- Bug-fix: S and M ships with missiles and torpedoes were acquiring avoid high-risk targets even if they had ammo left over.
- Bug-fix: The mod supressed global chatter but didn't reactivate it.
- Tweaks/bug-fix: Various deadairaitweaks including the bug-fix that allowed miners to mine too far away from their station commanders.

v5.1.0005, 18 Apr 2022:
- Tweak: The v5.1.0003 fix didn't actually fix the bug. v5.1.0005 fixes it properly: Travel mode is enabled for the "Avoid high-risk enemy" and "Move to engage position" behaviours if the ship's distance to its target is more than the ship's max radar range.

v5.1.0004, 16 Apr 2022:
- DeadAirAITweaks updates.

v5.1.0003, 14 Apr 2022:
- Tweak: Travel mode is enabled for the "Avoid high-risk enemy" and "Move to engage position" behaviours if the ship's distance to its target is more than the ship's max radar range. (Whether they actually use their travel engines is up to the game. :D)

v5.1.00021, 11 Apr 2022:
- Uploaded the CORRECT folder this time. :D. Sorry, everyone.

v5.1.0002, 11 Apr 2022:
- New feature: Merged file with DeadAirAITweaks. Its read-me is here: https://github.com/kuertee/x4-mod-da-ku-ai-tweaks/blob/master/deadairaitweaks-read-me.md.
- New feature: The "Step forward/Withdraw" behaviour can now be disabled in the ship's Behaviour Menu or from the right-click Interact Menu.
- New feature: The AI movements, "Avoid high-risk enemies" and "Move to engage position" (prevents accidental kamikaze), are now shown as such in the ship's Behaviour Menu. It'll show those order names instead of the generic move to order name. It's easier to know what they're doing with these new orders.
- Bug-fix: The "Step forward" and "Withdraw" do not stop the ship's subordinates from attacking. The downside is that they do not appear in the ship's Behaviour Menu because the moves are embedded within their attack orders.
- New feature (WIP): The Escort Ship, Follow Ship, and Supply Fleet behaviours acquire the Withdraw behaviour. I'm hoping that the interrupt handlers I attached to these behaviours trigger the Withdraw behaviour properly. If they don't, then these behaviours will perform as per the base-game's AI (so no loss there, relatively speaking): i.e. ignore incoming hits at certain times the behaviours are active.
- Localisation files: Chinese from Tiomer. And Japanese from Arkblade. Thank you to you both!

v5.0.00151, 3 Apr 2022:
- Bug-fix: Avoid behaviour for fighter craft v fighter craft were getting skipped on low-attention ships. Thanks DeadAir!

v5.0.0015, 3 Apr 2022:
- New behaviour: XS (except for drones), S, and M ships attack high-risk ship targets when they outnumber 50% of their weapons and turrets. It's still 75% against high-risk stations. These two values can be set in the Extension Options.
- New behaviour: L, and XL ships do not withdraw against high-risk ship targets unless there's another L or XL ship attacker.
- New feature: Enable/Disable 'Avoid high-risk enemies' on the ship's order panel or from the right-click Interact Menu. Disabling this will allow the ships to ignore their determination of high-risk enemies and forcing them to attack.

v5.0.0014, 31 Mar 2022:
- New behaviour: The attack runs of XS (except for drones), S, and M class ships will start when they outnumber 50% of their ship's turrets.
- New behaviour: L, and XL ships will not withdraw against other high-risk enemy ships unless there are other L, and XL attackers.
- Bug-fix: In low-attention fighter to fighter attacks, attackers were not stoping their attack runs on small targets that get near high-risk enemies.

v5.0.0013, 30 Mar 2022:
- Bug-fix: L and XL ships was acquiring the "stop kamikaze" behaviour (stop short of the target) against ship targets.
- Bug-fix: The "stop kamikaze" behaviour was getting applied on L and XL ships that are already in attack range.
- Bug-fix: One of the flee AI types was acquiring the avoid behaviour instead of just fleeing.

v5.0.0012, 25 Mar 2022:
- Note: This version will invalidate the mod's attack behaviours from the previous version, causing the ships to act unexpectedly UNTIL their next AI cycle. Or you can simply cancel then reissue any attack orders.
- New feature: L, and XL ships will now start their attack at their max combat range. Prevously, they started their attack at their optimal combat range - which made it look like they ignored their long-range weapons. As in previous versions, they'll inch towards their optimal combat range.
- New feature: L, and XL ships will approach their target at a vertical angle. Previously, they approached their target at their target's vertical position.
- New feature: XS (except for drones), S, and M ships will circle high-risk targets at a vertical angle.
- Bug-fix: L, and XL ships were still trying to get to the other side of their targets - exposing themselves to their target's weapons as they passed them. This happened when the ship acquired an attack order against the same target and the target is outside combat range. I.e. the ship only acquired the "stop kamikaze" behaviour once per target in previous version. In this version, this doesn't happen. (I had to rewrite how the mod's internal data for an attack order was stored for this fix.)
- New feature: L, and XL ships will move away a short distance after destroying a station module for a better attack vector against their next module target. They'll use the mod's behaviour for avoiding high-risk enemies so that they don't get within range of the station's turrets.
- New feature: High-risk enemies are no longer determined on object class. Potentially high-risk enemies are 1.5x larger physically than the ship. For XS (except for drones), S, and M ships, high-risk enemies have turrets that outnumber the attackers. For L, and XL ships, high-risk enemies have more DPS than the ship.

v5.0.0011, 19 Mar 2022:
- Bug-fix: Capital ships were still trying to find better attack vectors at the other side of their target stations.
- Tweak: Better optimal range values.
- Bug-fix: Some of the new behaviours were getting applied to ALL ships even if that option is disabled in the Extension Options.
- Tweak: Cleaned-up some unnecessary get_safe_pos calls.

v5.0.001, 17 Mar 2022:
- New feature: "Enable/Disable: 'Attack all enemies'" Interact Menu (i.e. right-click context sensitive menu) to enable or disable the "Attack all enemies" options of any attack orders of the selected ships.
- New feature: XS (except for drones), S, and M ships with missiles and torpedoes are do not use their avoidance AI until their missiles and torpedoes are exhausted.
- New feature: L and XL ships will never use boost against stations - except when their base-game AI makes them use their boost to flee.
- New feature: Disables the base-game AI that allows L and XL ships to look for better attack vectors on the other side of their target stations (ignoring the danger of passing by the main body of the station).
- New feature: L and XL module targets are shown on the map.
- Tweak: More careful "inch forward" and better withdraw AI.
- Tweak: Better "move around" vectors.

v4.2.0810, 12 Mar 2022:
- Initial release.
