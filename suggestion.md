
# Förslag på 90gQopen Public API
Här är ett förslag på hur ni kan göra om erat public API för att innehålla lite mer information och lite mer möjligheter för användarna att gå anpassad information.

Allt är skrivet som en dokumentation, men det gör det förhoppningsvis enkelt att följa. Om ni väljer att acceptera förslaget får ni gärna, om ni vill, använda dokumentationen (som ett template) till en officiell version.

---

## Information om spelare
`https://90gqopen.se/api/user/?username={username}`

**Metod:** `GET`
| Parameter | Type | Beskrivning |
| -- | -- | -- |
| username (*required*)| String | Vilken användare du vill ha statistik för. Alternativt kan man använda `uuid` istället för `username`.|
| survival (*optional*) | Boolean | Om du vill ha med statistik från survival.
| creative (*optional*) | Boolean | Om du vill ha med statistik från creative.
| mb (*optional*) | Boolean | Om du vill ha med statistik från Musical Blocks.
| uhc (*optional*) | Boolean | Om du vill ha med statistik från UHC.
| event (*optional*) | Boolean | Om du vill ha med statistik från event.
| timezone (*optional*) | String | För att få `last_online` i en annan tidszon. Använd landskod, ex `sv`, `en`.

### Response: Uppbyggnad och förklaring
- `id` (*int*) Ett unikt id kopplat till spelaren.
- `uuid` (*string*) Spelarens UUID.
- `username` (*string*) Spelarens Minecraft namn.
- `rank` (*string*) Vilken rank spelaren har på servern.
- `gQmynt` (*int*) Hur mycket gQmynt spelaren har.
- `onlinetime` (*int*) Hur länge spelaren har varit inne på servern. (Millisekunder)
- `last_online` (*string*) Vilken tid spelaren senast var online.
- `last_server` (*string*) Vilken delserver spelaren senast var ansluten till.
- `friend_count` (*int*) Antalet vänner som spelaren har.
- `parkourservern_whitelist` (*boolean*) Om spelaren är vitlistad på parkourservern eller inte.
- `muted` (*boolean*) Om spelaren är mutad eller inte.
- `banned` (*boolean*) Om spelaren är bannlyst eller inte.
- `survival` (*object*) 
    - `money` (*int*) Hur mycket pengar spelaren har.
    - `experience` (*int*) Mängden XP som spelaren har.
    - `level` (*int*) Vilken level spelaren är på.
    - `plot_claims` (*int*) Antalet claimade plotter spelaren har.
    - `plot_claims_max` (*int*) Maxantalet claimade plotter spelaren kan ha.
    - `guild` (*string*) Vilken guild som spelaren är med i.
    - `warp_slots` (*int*) Hur många upplåsta warp-slotter spelaren har.
    - `quests_completed` (*int*) Antalet quests som spelaren har slutfört.
    - `quest_streak` (*int*) Spelarens nuvarande quest streak.
- `creative` (*object*) 
    - `rank` (*string*) Vilken creative rank spelaren har.
    - `plot_claims` (*int*) Hur många plotter spelaren har claimat.
    - `plot_claims_max` (*int*) Maxantalet plotter spelaren kan claima.
- `mb` (*object*) 
    - `games_played` (*int*) Antalet spelade spel i Musical Blocks.
    - `winstreak` (*int*) Spelarens nuvarande vinststreak i Musical Blocks.
    - `best_winstreak` (*int*) Spelarens bästa vinststreak i Musical Blocks.
    - `points` (*int*) Spelarens poäng i Musical Blocks.
    - `hat` (*string*) Vilken hatt spelaren har valt i Musical Blocks.
- `uhc` (*object*) 
    - `games_played` (*int*) Antalet spelade spel i Ultra Hardcore.
    - `points` (*int*) Spelarens poäng i Ultra Hardcore.
    - `wins` (*int*) Antalet vinster i Ultra Hardcore.
    - `kills` (*int*) Antalet dödade spelare i Ultra Hardcore.
    - `deaths` (*int*) Antalet gånger spelaren har dött i Ultra Hardcore.
- `event` (*object*) 
    - `event_wins` (*int*) Antalet vinster i event.
    - `gold` (*int*) Mängden guld eventuellt belönad.
    - `gold_earned` (*int*) Totalt förtjänad guld i event.
    - `mvps` (*int*) Antalet gånger spelaren har blivit MVP i event.
    - `participation` (*int*) Antalet gånger spelaren har deltagit i event.
    - `party_invites` (*int*) Antalet inbjudningar till eventparty.
    - `spectator_speed` (*int*) Spelarens hastighet som åskådare i event.
    - `spectator_visibility` (*int*) Spelarens synlighet som åskådare i event.
    - `anvil_games_played` (*int*) Antalet spelade spel i Anvil.
    - `anvil_wins` (*int*) Antalet vinster i Anvil.
    - `anvil_gold_earned` (*int*) Totalt förtjänad guld i Anvil.
    - `border_runners_games_played` (*int*) Antalet spelade spel i Border Runners.
    - `border_runners_wins` (*int*) Antalet vinster i Border Runners.
    - `border_runners_gold_earned` (*int*) Totalt förtjänad guld i Border Runners.
    - `border_runners_rounds_survived` (*int*) Antalet överlevda rundor i Border Runners.
    - `border_runners_powerups_used` (*int*) Antalet använda powerups i Border Runners.
    - `border_runners_most_rounds_survived` (*int*) Flest antal rundor överlevda i Border Runners.
    - `dragons_games_played` (*int*) Antalet spelade spel i Drakattack.
    - `dragons_wins` (*int*) Antalet vinster i Drakattack.
    - `dragons_gold_earned` (*int*) Totalt införtjänat guld i Drakattack.
    - `dragons_arrows_shot` (*int*) Antalet skjutna pilar i Drakattack.
    - `dragons_arrows_hit` (*int*) Antalet träffade pilar i Drakattack.
    - `dragons_leaps_used` (*int*) Antalet hopp använda i Drakattack.
    - `infection_games_played` (*int*) Antalet spelade spel i Infection.
    - `infection_wins` (*int*) Antalet vinster i Infection.
    - `infection_gold_earned` (*int*) Totalt förtjänad guld i Infection.
    - `infection_alpha_games` (*int*) Antalet spel som Alpha i Infection.
    - `infection_infected_kills` (*int*) Antalet dödade spelare som Infected i Infection.
    - `infection_survivor_kills` (*int*) Antalet dödade spelare som Survivor i Infection.
    - `infection_most_kills_infected` (*int*) Flest antal dödade som Infected i Infection.
    - `infection_most_kills_survivor` (*int*) Flest antal dödade som Survivor i Infection.
    - `maze_games_played` (*int*) Antalet spelade spel i Maze.
    - `maze_wins` (*int*) Antalet vinster i Maze.
    - `maze_gold_earned` (*int*) Totalt förtjänad guld i Maze.
    - `oitc_games_played` (*int*) Antalet spelade spel i OITC.
    - `oitc_wins` (*int*) Antalet vinster i OITC.
    - `oitc_gold_earned` (*int*) Totalt förtjänad guld i OITC.
    - `oitc_melee_kills` (*int*) Antalet dödade med närstridsvapen i OITC.
    - `oitc_ranged_kills` (*int*) Antalet dödade med avståndsvapen i OITC.
    - `oitc_deaths` (*int*) Antalet gånger spelaren har dött i OITC.
    - `oitc_arrows_shot` (*int*) Antalet skjutna pilar i OITC.
    - `oitc_highest_kill_streak` (*int*) Spelarens högsta dödstreak i OITC.
    - `oitc_longest_bow_kill` (*int*) Längsta bågdöd i OITC.
    - `parkour_games_played` (*int*) Antalet spelade spel i Parkour.
    - `parkour_wins` (*int*) Antalet vinster i Parkour.
    - `parkour_gold_earned` (*int*) Totalt förtjänad guld i Parkour.
    - `parkour_rounds_survived` (*int*) Antalet överlevda rundor i Parkour.
    - `parkour_most_rounds_survived` (*int*) Flest antal rundor överlevda i Parkour.
    - `red_rover_games_played` (*int*) Antalet spelade spel i Red Rover.
    - `red_rover_wins` (*int*) Antalet vinster i Red Rover.
    - `red_rover_gold_earned` (*int*) Totalt förtjänad guld i Red Rover.
    - `red_rover_killer_games` (*int*) Antalet spel som Killer i Red Rover.
    - `red_rover_rounds_survived` (*int*) Antalet överlevda rundor i Red Rover.
    - `red_rover_kills` (*int*) Antalet dödade spelare i Red Rover.
    - `red_rover_dashes` (*int*) Antalet dashes använda i Red Rover.
    - `red_rover_most_rounds_survived` (*int*) Flest antal rundor överlevda i Red Rover.
    - `snow_fight_games_played` (*int*) Antalet spelade spel i Snow Fight.
    - `snow_fight_wins` (*int*) Antalet vinster i Snow Fight.
    - `snow_fight_gold_earned` (*int*) Totalt förtjänad guld i Snow Fight.
    - `snow_fight_kills` (*int*) Antalet dödade spelare i Snow Fight.
    - `snow_fight_snowballs_thrown` (*int*) Antalet kastade snöbollar i Snow Fight.
    - `snow_fight_snowballs_hit` (*int*) Antalet träffade snöbollar i Snow Fight.
    - `spleef_games_played` (*int*) Antalet spelade spel i Spleef.
    - `spleef_wins` (*int*) Antalet vinster i Spleef.
    - `spleef_gold_earned` (*int*) Totalt förtjänad guld i Spleef.
    - `spleef_blocks_broken` (*int*) Antalet block som spelaren har krossat i Spleef.
    - `spleef_snowballs_thrown` (*int*) Antalet kastade snöbollar i Spleef.
    - `spleef_most_blocks_broken` (*int*) Flest antal block krossade i Spleef.
    - `sumo_games_played` (*int*) Antalet spelade spel i Sumo.
    - `sumo_wins` (*int*) Antalet vinster i Sumo.
    - `sumo_gold_earned` (*int*) Totalt förtjänad guld i Sumo.
    - `sumo_kills` (*int*) Antalet dödade spelare i Sumo.
    - `sumo_most_kills` (*int*) Flest antal dödade spelare i Sumo.
    - `sg_games_played` (*int*) Antalet spelade spel i Survival Games.
    - `sg_wins` (*int*) Antalet vinster i Survival Games.
    - `sg_gold_earned` (*int*) Totalt förtjänad guld i Survival Games.
    - `sg_kills` (*int*) Antalet dödade spelare i Survival Games.
    - `sg_deaths` (*int*) Antalet gånger spelaren har dött i Survival Games.
    - `sg_chests_looted` (*int*) Antalet kistor som spelaren har plundrat i Survival Games.
    - `sg_most_kills` (*int*) Flest antal dödade spelare i Survival Games.
    - `tnt_run_games_played` (*int*) Antalet spelade spel i TNT Run.
    - `tnt_run_wins` (*int*) Antalet vinster i TNT Run.
    - `tnt_run_gold_earned` (*int*) Totalt förtjänad guld i TNT Run.
    - `tnt_run_walked_over_blocks` (*int*) Antalet block som spelaren har gått över i TNT Run.
    - `tnt_run_leaps_used` (*int*) Antalet hopp använda i TNT Run.
    - `tnt_run_most_blocks_broken` (*int*) Flest antal block krossade i TNT Run.
 
### API Exempel:
##### Request:
```
https://90gqopen.se/api/user/?username=Fy17&survival=true&creative=true&mb=true&uhc=true&event=true
```

##### Response:
```json
{
	"id": 17518,
	"uuid": "d284d134-51e7-42da-90db-c28826aaf8a9",
	"username": "Fy17",
	"rank": "bashlang",
	"gQmynt": 180,
	"onlinetime": 3530858733,
	"last_online": "2024-04-09 20:32:12",
	"last_server": "parkour",
	"friend_count": 21,
	"parkourservern_whitelist": false,
	"muted": false,
	"banned": false,
	"survival": {
		"money": 10011,
		"experience": 4850,
		"level": 19,
		"plot_claims": 12
		"plot_claims_max": 19,
		"guild": "Avox",
		"warp_slots": 1,
		"quests_completed": 188,
		"quest_streak": 3
	},
	"creative": {
		"rank": "apprentice",
		"plot_claims": 22,
		"plot_claims_max": 24
	},
	"mb": {
		"games_played": 18,
		"winstreak": 0,
		"best_winstreak": 1,
		"points": 169,
		"hat": "unicorn"
	}
	 "uhc": {
		 "games_played": 5,
		 "points": 35,
		 "wins": 0,
		 "kills": 0,
		 "deaths": 5
	},
	"event": {
		"event_wins": 0,
		"gold": 189,
		"gold_earned": 189,
		"mvps": 0,
		"participation": 1,
		"party_invites": 1,
		"spectator_speed": 1,
		"spectator_visibility": 1,
		"anvil_games_played": 1,
		"anvil_wins": 0,
		"anvil_gold_earned": 2,
		"border_runners_games_played": 0,
		"border_runners_wins": 0,
		"border_runners_gold_earned": 0,
		"border_runners_rounds_survived": 0,
		"border_runners_powerups_used": 0,
		"border_runners_most_rounds_survived": 0,
		"dragons_games_played": 9,
		"dragons_wins": 0,
		"dragons_gold_earned": 16,
		"dragons_arrows_shot": 11,
		"dragons_arrows_hit": 2,
		"dragons_leaps_used": 17,
		"infection_games_played": 1,
		"infection_wins": 0,
		"infection_gold_earned": 1,
		"infection_alpha_games": 0,
		"infection_infected_kills": 1,
		"infection_survivor_kills": 3,
		"infection_most_kills_infected": 1,
		"infection_most_kills_survivor": 3,
		"maze_games_played": 0,
		"maze_wins": 0,
		"maze_gold_earned": 0,
		"oitc_games_played": 12,
		"oitc_wins": 0,
		"oitc_gold_earned": 29,
		"oitc_melee_kills": 9,
		"oitc_ranged_kills": 59,
		"oitc_deaths": 124,
		"oitc_arrows_shot": 169,
		"oitc_highest_kill_streak": 3,
		"oitc_longest_bow_kill": 15,
		"parkour_games_played": 13,
		"parkour_wins": 0,
		"parkour_gold_earned": 42,
		"parkour_rounds_survived": 48,
		"parkour_most_rounds_survived": 0,
		"red_rover_games_played": 9,
		"red_rover_wins": 0,
		"red_rover_gold_earned": 19,
		"red_rover_killer_games": 0,
		"red_rover_rounds_survived": 19,
		"red_rover_kills": 0,
		"red_rover_dashes": 0,
		"red_rover_most_rounds_survived": 0,
		"snow_fight_games_played": 0,
		"snow_fight_wins": 0,
		"snow_fight_gold_earned": 0,
		"snow_fight_kills": 0,
		"snow_fight_snowballs_thrown": 0,
		"snow_fight_snowballs_hit": 0,
		"spleef_games_played": 7,
		"spleef_wins": 0,
		"spleef_gold_earned": 17,
		"spleef_blocks_broken": 516,
		"spleef_snowballs_thrown": 58,
		"spleef_most_blocks_broken": 0,
		"sumo_games_played": 2,
		"sumo_wins": 0,
		"sumo_gold_earned": 7,
		"sumo_kills": 1,
		"sumo_most_kills": 0,
		"sg_games_played": 14,
		"sg_wins": 0,
		"sg_gold_earned": 38,
		"sg_kills": 6,
		"sg_deaths": 14,
		"sg_chests_looted": 24 ,
		"sg_most_kills": 2,
		"tnt_run_games_played": 6,
		"tnt_run_wins": 0,
		"tnt_run_gold_earned": 18,
		"tnt_run_walked_over_blocks": 1327,
		"tnt_run_leaps_used": 16,
		"tnt_run_most_blocks_broken": 0
	}
}
```

## Information om guilds
 `https://90gqopen.se/api/guild/?name={name}`

**Metod:** `GET`
| Parameter | Type | Beskrivning |
| -- | -- | -- |
| name (*required*)| String | Namnet på guilden du vill få information om.|
| memberlist (*optional*) | Boolean | Om du vill få med en lista av alla medlemmar i guilden.
### Response: Uppbyggnad och förklaring
- `id` (*int*) Ett unikt id kopplat till guilden.
- `name` (*string*) Namnet på guilden.
- `created` (*string*) Datumet då guilden skapades.
- `money` (*int*) Mängden pengar som guilden har.
- `members` (*int*) Antalet personer som är med i guilden.
- `experience` (*int*) Mängden XP som guilden har.
- `level` (*int*) Vilken level guilden är på.
- `plot_claims` (*int*) Antalet plotter som guilden har claimat.
- `plot_claims_max` (*int*) Maxantalet plotter som guilden kan claima.
- `memberlist` (*array*)
  - *En lista på medlemmarna i guilden, samt vilken rank de har.*
  - *Uppbyggnad: `["SPELARE", "owner|moderator|member"],`*

### API Exempel:
##### Request:
```
https://90gqopen.se/api/guild/?name=Avox&memberlist=true
```
##### Response:
```json
{
	"id": 8,
	"name": "Avox",
	"created": "2023-08-16",
	"money": 22247952,
	"members": 7,
	"experience": 6324,
	"level": 4
	"plot_claims": 22,
	"plot_claims_max": 55,
	"memberlist": [
		["Fy17", "owner"],
		["Kruxa", "moderator"],
		["Medlem3", "member"],
		["Medlem4", "member"],
		["Medlem5", "member"],
		["Medlem6", "member"],
		["Medlem7", "member"]
	]
}
```
## Topplistor
`https://90gqopen.se/api/leaderboard/?type={type}`

**Metod:** `GET`
| Parameter | Type | Beskrivning |
| -- | -- | -- |
| type (*required*)| String | Vilken sorts topplista du vill ha.|
| length (*optional*) | Int| Hur lång topplistan ska vara, om den inte anges så får man 10. Maxgräns: 50.

Alla sorter ("type") ger tillbaka en lista med listor, innersta listorna är uppbyggda som `["SPELARNAMN", "REKORD"]`.
#### Lista på alla olika sorters topplistor ("type" parameter):
```
onlinetime gqmynt survival_money guild_money guild_members guild_exp guild_level survival_exp level quests_completed quest_streak mb_games_played mb_winstreak mb_best_winstreak mb_points uhc_games_played uhc_points uhc_wins uhc_kills uhc_deaths event_wins gold gold_earned mvps anvil_games_played anvil_wins anvil_gold_earned border_runners_games_played border_runners_wins border_runners_gold_earned border_runners_rounds_survived border_runners_powerups_used border_runners_most_rounds_survived dragons_games_played dragons_wins dragons_gold_earned dragons_arrows_shot dragons_arrows_hit dragons_leaps_used infection_games_played infection_wins infection_gold_earned infection_alpha_games infection_infected_kills infection_survivor_kills infection_most_kills_infected infection_most_kills_survivor maze_games_played maze_wins maze_gold_earned oitc_games_played oitc_wins oitc_gold_earned oitc_melee_kills oitc_ranged_kills oitc_deaths oitc_arrows_shot oitc_highest_kill_streak oitc_longest_bow_kill parkour_games_played parkour_wins parkour_gold_earned parkour_rounds_survived parkour_most_rounds_survived red_rover_games_played red_rover_wins red_rover_gold_earned red_rover_killer_games red_rover_rounds_survived red_rover_kills red_rover_dashes red_rover_most_rounds_survived snow_fight_games_played snow_fight_wins snow_fight_gold_earned snow_fight_kills snow_fight_snowballs_thrown snow_fight_snowballs_hit spleef_games_played spleef_wins spleef_gold_earned spleef_blocks_broken spleef_snowballs_thrown spleef_most_blocks_broken sumo_games_played sumo_wins sumo_gold_earned sumo_kills sumo_most_kills sg_games_played sg_wins sg_gold_earned sg_kills sg_deaths sg_chests_looted sg_most_kills tnt_run_games_played tnt_run_wins tnt_run_gold_earned tnt_run_walked_over_blocks tnt_run_leaps_used tnt_run_most_blocks_broken
```

#### API Exempel:
##### Request:
`https://90gqopen.se/api/leaderboard/?type=playtime&length=5`
##### Response:
```json
[
	["sydsi", 20201635930],
	["pocke01", 19829137642],
	["pandacat81", 18874666012],
	["nilsson321", 18434676108],
	["snichard", 17297470201]
]
```
##### Request:
`https://90gqopen.se/api/leaderboard/?type=uhc_wins`
##### Response:
```json
[
	["gurros", 37],
	["erikbacke", 36],
	["vliime", 35],
	["ohtame", 16],
	["dagge_bagge", 15],
	["vetyyy", 14],
	["wqtchy", 8],
	["addezero", 7],
	["vattenhink", 6],
	["vharold", 6]
]
```
## Error Koder:
Här är några errorkoder samt orsaker som kan ha orsakat dem.
| Error Kod | Beskrivning |
| -- | -- |
| 404 | - Inga användare kunde hittas.
| 404 | - Ingen guild kunde hittas |
| 400 | - Inget Minecraft användarnamn eller UUID angavs.
| 400 | - Inget guild namn angavs.
| 429 | - För många förfrågningar. (Rate limit)
| 500 | - Internt serverfel, var vänlig och kontakta ledningen.
