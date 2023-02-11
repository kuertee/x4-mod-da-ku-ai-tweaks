# DeadAirAITweaks

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
