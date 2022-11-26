# Pokémon World <img src="https://vignette.wikia.nocookie.net/pkmnshuffle/images/3/3d/Mega_Blaziken.png/revision/latest?cb=20170409222119" alt="icon" height="50" />
[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://opensource.org/licenses/MIT)
[![Website shields.io](https://img.shields.io/badge/website-offline-lightgrey)](about:blank)

***Notice: The live hosting of this website has been shutdown as Heroku discontinued its free Dynos offering.***

Pokémon World is a dynamically served website that contains a lot of useful information related to game data and core mechanics. It is not a professional website like Serebii or Smogon, but it has a beautifully designed user interface powered by Materialize CSS. This application is built with Node.js and Express, and it has certain limitations due to the fact that HTML pages are entirely rendered on the server side. [Pokéapi-v2](https://github.com/PokeAPI/pokedex-promise-v2) is the backbone of the project as it provides all the data used internally inside the routing layer.

## Build <img src="https://raw.githubusercontent.com/Kairn/asset-bank/master/pok%C3%A9mon/mini-icons/798.png" alt="icon" height="40" />
### Prerequisites
* [Node.js](https://nodejs.org/en/)
* [Express.js](https://expressjs.com/)
* [node-sass](https://www.npmjs.com/package/node-sass?activeTab=versions)
* [Pokéapi-v2](https://github.com/PokeAPI/pokedex-promise-v2)
* [nodemon](https://nodemon.io/) (not required but highly recommended)

### Install and Run
1. Clone or download this repository.
2. Change into the project directory where the package.json is located.
3. Run `npm install` to acquire all dependencies.
4. Run `npm start` or `nodemon` (if you have installed nodemon) to start the server.
5. Open your browser and the application is served on port 3000 by default.

## Feature Tour <img src="https://raw.githubusercontent.com/Kairn/asset-bank/master/pok%C3%A9mon/mini-icons/001.png" alt="icon" height="40" />
As of now, the main features of the application are provided by three separate pages which can be accessed using the links on the navbar.

### Pokédex
* Use the search box on the Pokédex page to look up any pokémon that you are interested in.
* You can search a pokémon by its national pokédex number or name.
* If you do not wish to do manual searching, under the search box, there will be a long list of all pokémon of a particular generation, and you can view their data by simply clicking on the buttons.
* By default, the Pokédex page only shows pokémon in generation one. You can navigate to other generations by clicking on the floating button on the **BOTTOM RIGHT** corner and then click on the generation index number.
* After you selected a pokémon, a new page containing the information about this pokémon will open up.
* The newly opened page will have the pokémon's official artwork, animated 3D game sprites, basic characteristics data, base statistics, and a list of obtainable moves.
* On each individual pokémon page, you can use the **PREV.** and **NEXT** buttons to navigate to the pokémon that appear just before or after the selected pokémon on the national pokédex.

### Itemdex
* The Itemdex page simply lists out most of the items that exist in the official pokémon games with their icon images and brief descriptions.
* Trivial items such as key items are omitted. Items which are no longer available in the newest games are omitted. Items which might be different in different games such as technical machines are also not included.
* Items are separated into categories and sub-categories.
* You can use the floating button on the **BOTTOM RIGHT** corner for quick navigation.

### Calculator
* In the Type Effectiveness section, you can view each type's effectiveness data by clicking on its corresponding type icon.
* The Stats Calculator provides an interface for you to calculate in game statistics.
* In order to calculate a stat, you must provide the pokémon's level and nature, as well as the base value, individual value, and effort value of this stat. (If you are not a pro gamer and do not know what are base value, IV, and EV, then you can look them up on [Bulbapedia](https://bulbapedia.bulbagarden.net/wiki/Statistic) if you are interested.)
* All input boxes of the Stats Calculator have built-in validation, and they will have red underlines if you enter invalid values.
* Effort values which are not multiples of 4 will be rounded down to the nearest integer that is a multiple of 4 when you click on **Calculate**.
* The **Max IVs** and **Max EVs** buttons provide a quick way to fill all IV fields with 31 and EV fields with 252.
* Each stat is calculated independent of other stats, so although no individual stat can have an effort value greater than 252 (or 255), the total EV value can exceed 510.
* Finally, the Damage Calculator is designed for calculating the actual damage range of a generic pokémon with a given attack stat using a generic move of a certain type with a given power on another generic pokémon of given types with a given defense stat.
* Certain abilities, items, and various other battlefield conditions can also be input into the calculator in order to apply additional modifiers.
* Use the **Custom Modifier** field to add an extra modifier that cannot be represented by the given information such as move specific abilities (Sheer Force, Iron Fist, etc).
* Input fields marked with a red **\*** are required.
* Don't worry too much about the technicalities, just play with the calculator and have some fun.

## Issues <img src="https://raw.githubusercontent.com/Kairn/asset-bank/master/pok%C3%A9mon/mini-icons/282.png" alt="icon" height="40" />
* Because of server-side rendering, certain pages (the Itemdex page in particular) that contain lots of fetched data can take more than a few seconds to load before the view is returned. If you are running the application locally and you have suboptimal Internet, the connect could time out on these pages in which case you have to click on the link again to get the page to properly render. Fortunately, Node has internal caching, meaning that once data is received, it stays in memory until you shutdown the server, so even if the server times out while fetching data, the fetched data will no longer need to be retrieved again, and the next request can be processed way faster.
* The application relies on Pokéapi to function, but unfortunately, Pokéapi-v2 is not maintained by developers enthusiastically, and therefore the server cannot retrieve information about some of the newest pokémon (after #802 as of day of this writing). Most pokémon's move learnsets are also out of date. I have noticed in multiple occasions where I know there are moves legally obtainable by certain pokémon but they are not shown on the page. Mega Evolutions are currently not present in the application due to other complications.
* Even though I made my best effort to make the Damage Calculator as accurate as possible, the calculated values might vary slightly compare to the real game or the Pokémon Showdown calculator when creating a complex scenario with multiple conditions that interact with each other. This is due to the fact that too many modifiers can be applied to a single calculation, and they might be applied at different parts of the damage formula. The official Pokémon game has crazy rounding rules and the order for applying modifiers also matter, so it is incredibly hard to make a ***perfect*** calculator without the official documentation which Nintendo obviously never made publicly available.
* You can contact me directly if you have solid and realistic suggestions which I can use to improve the quality of this application.

## References <img src="https://raw.githubusercontent.com/Kairn/asset-bank/master/pok%C3%A9mon/mini-icons/373.png" alt="icon" height="40" />
* [Bulbapedia](https://bulbapedia.bulbagarden.net/wiki/Main_Page)
* [Serebii](https://www.serebii.net/index2.shtml)
* [Pokémon Showdown!](https://pokemonshowdown.com/)
