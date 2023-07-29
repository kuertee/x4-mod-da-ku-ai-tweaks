# DeadAirAITweaks

## Updates for 6.x (8-May-2023 to 8-Jun-2023)
- Implemented options menu for DA tweaks.
- New feature: Added handling for capital ships attacking station but not having line of sight due to module wrecks. Ships will rotate 15 degrees around the station at their max range periodically until they have LOS on the module they are trying to attack. Only affects high attention and ships with front weapons.
- Stage 4:
 * Increased number of scripts covered by Player ship boost tweak. Updated attack interrupt changes to be covered by Smarter Flee Tweaks.
 * Updated targeting selection changes to be covered by Targeting Script Tweaks.
 * Improved capital attack script for ships without front weapons to use travel drive less when doing angled attack runs.
- Stage 3:
 * Added new improvement to flee distance on boost script so if using travel drive, they will flee further.
 * Added new improvement to flee docking IF vanilla fails to find a place to flee to, will likely change to not requiring vanilla to fail.
 * Cleaned up changes and added additional changes in move.gate and move.generic resulting in improved speed large ships will travel.
 * Fixed issue for Kuertee's script in order.fight.escort resulting in X4 6.0HF4.
 * Added improvement in excessive delay time for vanilla trade script order.trade.routine and trade.find.free.
 * Added check for missing variables in md script for DA options and made button text red if option is disabled.
 * Added improvement for job_helper script that makes factions choose closer shipyard more often but comes at the cost potentially of player shipyard/wharf sales (massive improvement to xenon).
- Stage 2:
 * Reimplemented improvements to move.attack.object.capital, improvements to blind tourist (explore) script order.move.recon, removed DA diffs from order.supply, improved xpath for factiongoal_invade_space change and restricted improvement until game is 2h+ old
 * Fixed bug that would occasionally cause ships with travel charge time to slowboat long distances.
- Stage 1:
 * Removed DA fight.attack.object.bigtarget/capital/fighter/medium/stations, interrupt.attacked, interrupt.npc.usecases, masstraffic.watchdog, move.attack.object.capital, move.flee.dock, order.collect.ship.lockbox, order.dock, order.fight.attack.object, order.fight.board, order.fight.escort, order.fight.lasertower, mining routine range changes, order.move.recon.police, order.plunder, trade.find.free, factiongoal_patrolcoordinationservice, factionsubgoal_buildstation, optional engineer.ai tweaks.

## Changes to X4 AI (finally updated on 2-Jul-2022)
- Allows drone travel drive usage logic (if you have a mod that adds it to engine)
- Rebalances ship/station repairs in optional file. Amount and quality of service personnel matters more.
- Lots of combat changes for capital ships. Not writing a 3000 word essay. Basically, reduced RNG for skill based checks, reduced some obviously poor decisions, reduced differences between player rules and AI rules.
- Turrets firing tolerance lowered.
- Ships will fire missiles more often (less fake skill delay)
- Ships will use countermeasures more often
- Trading and Mining ships will flee instead of returning attacks when on default response (AI + player)
- Resource probe bonus applies to entire sector instead of 40km.
- Targeting preference implemented as follows:
XL prefer L/XL/Stations twice as likely, half-interested in XS/S
L prefer M/L/XL twice as likely, half-interested in XS/S
M prefer S/M/L twice as likely, half-interested in XS/XL/Stations
S prefer XS/S/M twice as likely, Half-interested in L/XL/Stations
S/M with Torp prefer L/XL/Stations twice as likely, half-interested in XS/S
Targets not covered by notes above stay at vanilla preference  
- Capital ships are now capable of looking up and down in combat as long as you don't have a poorly written diff on engines loading after this mod
- Drones will use travel drive when collecting loot (if you have a mod that adds it to engine)
- Small ships will use travel drive when collecting loot if distance to next crate >= 5km
- Fleeing ships will now prefer to dock at a really close station (especially if it is hostile to attacker)
- If ship decides to flee via boost, it is more likely to flee away from attacker
- Fleet commanders of mimic fleets will no longer wait for subordinates that aren't following
- L/XL gate movement is generally much faster
- Ships are much more likely to use travel drives instead of slow boating
- Patrol ships will respond to a station/ship in distress if their relation is higher with victim than attacker
- Patrol/Police ships will respons to a station/ship in distress ALWAYS if they are same faction as victim (this applies to player ships as well)
- Police ships that find trouble will signal patrol ships to help subdue the threat
- Police scans will take much less time
- Ships are much more likely to use travel drive when further than 15km from boarding target
- Ships assigned to defend will defend withing their entire radar range instead of only targets within 20km
- AI owned laser towers die after 15 minutes of inactivity instead of 1 hour
- Advanced mining routine range increased for non station miners to a max of ([([@this.assignedcontrolled.commander.tradenpc.skill.management, @this.assignedcontrolled.commander.pilot.skill.management, @this.assignedcontrolled.pilot.skill.piloting].max)-5,4].max)
- Expert mining routine range increased for non station miners to a max of ([([@this.assignedcontrolled.commander.tradenpc.skill.management, @this.assignedcontrolled.commander.pilot.skill.management, @this.assignedcontrolled.pilot.skill.piloting].max),12].max - 1)
- Miners will now check which station has the highest need instead of largest buy order amount
- AI will be able to find objects at a greater distance using explore command
- AI will consider enemy stations to be a larger threat when determining invasion size
- Police will occasionally check and detect pirates using cover of the same faction
- Free traders will actually take the best offer they find instead of having RNG make them take worse trades (it's still not nearly as good as tater/deadtater)
- Increased level gain limits for most difficult activities to 15. Excel sheet floating around of % chance to level available on request.
- Ships/Stations launch more of their defense drones and at a faster rate
- Reduced penalty for 1,2,3,4 star pilots acceleration, turn rate, and speed.
- Will receive notification of trading/mining ships under attack even in fleets or assigned to station
- Factions will use ships further from the front lines for offense and defense
- Player ships can now drop deployables when fleeing
- Factions will attempt to place defense stations closer to gates

##### Save game compatible.

##### Requires DLC

##### Installation: extract to x4 foundations\extensions
