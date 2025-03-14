Implementation Plan: Heroes of the Rift (Offline Base Game)
Objective
Build a fully offline, single-file version of Heroes of the Rift with hero recruitment, tactical combat, and a basic Campaign mode, optimized for vertical mobile play using the provided tech stack.
Prerequisites
Tool: Visual Studio Code.

Output: A single heroes-of-the-rift.html file.

Testing: Modern mobile browser (e.g., Chrome, Safari) on a phone.

Phase 1: Setup and Core Structure
Step 1: Create Single HTML File
Instruction: In VS Code, create heroes-of-the-rift.html. Add basic HTML5 structure: <!DOCTYPE html>, <html>, <head> with a <title> ("Heroes of the Rift"), and <body>.

Test: Open the file in a mobile browser. Confirm a blank page loads with "Heroes of the Rift" in the title bar.

Step 2: Embed CSS for Vertical Layout
Instruction: In <head>, add a <style> tag. Use CSS to set the body to 100vh height, lock vertical orientation with flex-direction: column, and create three stacked divs (IDs: enemy-area, battlefield, player-area) each with height: 33vh and distinct background colors (e.g., red, gray, blue).

Test: Add placeholder text ("Enemy", "Battle", "Player") to each div in <body>. Open in a browser. Confirm three vertical sections stack correctly, filling the screen, with no horizontal scroll.

Step 3: Add Canvas to Battlefield
Instruction: Replace "Battle" text in #battlefield div with a <canvas> tag (ID: game-canvas). In <style>, set canvas width to 300px and height to 100% of its parent div, centered with margin: auto.

Test: Open the file. Confirm a blank canvas appears in the middle section, vertically centered, with a visible outline (add a border in CSS to check).

Phase 2: Hero Data and Recruitment
Step 4: Embed Script and Define Hero Data
Instruction: In <body>, add a <script> tag at the bottom. Inside, create a heroes array with three objects: {name: "Lara", rarity: 4, health: 100, attack: 20, speed: 10}, {name: "Korr", rarity: 2, health: 120, attack: 15, speed: 5}, {name: "Mira", rarity: 3, health: 80, attack: 25, speed: 8}.

Test: Add console.log(heroes) in the script. Open the file, check the browser console, and confirm three hero objects appear with correct properties.

Step 5: Display Hero List in Player Area
Instruction: In <script>, create a playerHeroes array (empty initially). Replace "Player" text in #player-area with a <div> (ID: hero-list). Write a function updateHeroList() to loop through playerHeroes and set hero-list innerHTML to show each hero’s name and rarity (e.g., "Lara - Rarity 4"). Call it on page load.

Test: Temporarily add one hero to playerHeroes in the script. Open the file. Confirm #player-area shows "Lara - Rarity 4" (or similar) instead of "Player".

Step 6: Add Recruitment Button
Instruction: In #player-area, below #hero-list, add a <button> (ID: recruit-btn, text: "Recruit"). In <style>, make it 100x50px with a clear background and border. In <script>, add an onclick event logging "Recruit clicked".

Test: Open the file. Confirm the button appears below the hero list, is tappable, and logs "Recruit clicked" to the console when pressed.

Step 7: Implement Recruitment Logic
Instruction: In <script>, modify the onclick event for recruit-btn. Randomly pick a hero from heroes (e.g., heroes[Math.floor(Math.random() * heroes.length)]), add it to playerHeroes, call updateHeroList(), and show an alert (e.g., "Recruited: Lara").

Test: Click the button. Confirm an alert shows a random hero’s name, and #hero-list updates with that hero (e.g., "Lara - Rarity 4").

Phase 3: Tactical Combat Setup
Step 8: Draw Battlefield Grid on Canvas
Instruction: In <script>, get the canvas context (canvas.getContext('2d')). Write a drawGrid() function to draw a 3x5 grid (3 rows, 5 columns) using lines (each cell 60x60px, total 300x180px). Call it on page load.

Test: Open the file. Confirm a 3x5 grid appears on the canvas in #battlefield, with visible lines separating 15 cells.

Step 9: Place Player Heroes on Grid
Instruction: In drawGrid(), for each hero in playerHeroes (up to 3), draw their name in cells (row 1, cols 1-3) using fillText() at coordinates (e.g., col 1: 10,10; col 2: 70,10). Clear and redraw the canvas each call.

Test: Recruit two heroes, refresh. Confirm their names appear in row 1, cols 1-2 (e.g., "Lara" at 10,10; "Korr" at 70,10).

Step 10: Add Enemy Units
Instruction: In <script>, create an enemies array with two objects: {name: "Goblin", health: 50, attack: 10}, {name: "Orc", health: 70, attack: 15}. In drawGrid(), draw their names in row 3, cols 1-2 (e.g., "Goblin" at 10,130; "Orc" at 70,130).

Test: Refresh the file. Confirm "Goblin" and "Orc" appear in row 3, cols 1-2 on the canvas.

Step 11: Display Enemy Health
Instruction: In #enemy-area, replace "Enemy" with a <div> (ID: enemy-list). Write updateEnemyList() to set its innerHTML to show enemy names and health (e.g., "Goblin - HP: 50"). Call it on page load.

Test: Refresh. Confirm #enemy-area shows "Goblin - HP: 50" and "Orc - HP: 70".

Phase 4: Basic Combat Mechanics
Step 12: Add Attack Buttons
Instruction: In updateHeroList(), for each hero in #hero-list, append a <button> (text: "Attack", unique ID like attack-hero1). In <script>, add onclick events logging the hero’s name.

Test: Recruit two heroes. Confirm each has an "Attack" button next to their name in #hero-list, and tapping logs their name (e.g., "Lara").

Step 13: Implement Player Attack
Instruction: In each attack button’s onclick, reduce the first enemy’s health by the hero’s attack value, update enemies, redraw the grid, and call updateEnemyList().

Test: Recruit Lara (attack 20), click her Attack button. Confirm Goblin’s health drops from 50 to 30 in #enemy-list.

Step 14: Add Enemy Counterattack
Instruction: After a player attack, reduce the first hero’s health by the first enemy’s attack value (if both alive). Redraw the grid to show updated health next to hero names (e.g., "Lara 80").

Test: Attack with Lara (health 100). Confirm her health drops to 90 after Goblin’s counterattack (attack 10), shown on the canvas.

Step 15: Check for Defeat
Instruction: After each attack, if an enemy’s health ≤ 0, remove it from enemies. If enemies is empty, show an alert ("Victory!"). Redraw grid and update enemy list.

Test: Attack Goblin three times with Lara (20x3 = 60). Confirm Goblin disappears, and after Orc is defeated, "Victory!" alerts.

Phase 5: Campaign Mode Foundation
Step 16: Define Campaign Stage
Instruction: In <script>, create a campaign array with one stage: {name: "Plains Skirmish", enemies: [{name: "Goblin", health: 50, attack: 10}, {name: "Orc", health: 70, attack: 15}]}. Add a <button> (ID: start-stage, text: "Start Stage") in #player-area.

Test: Refresh. Confirm the button appears and logs "Stage started" when clicked.

Step 17: Load Stage into Battlefield
Instruction: On start-stage click, set enemies to the stage’s enemies array, redraw the grid, and call updateEnemyList().

Test: Click "Start Stage". Confirm Goblin and Orc appear on the canvas and in #enemy-list.

Step 18: Add Victory Reward
Instruction: On victory, add 100 to a gold variable (start at 0), show an alert ("Reward: 100 Gold"), and save gold and playerHeroes to localStorage.

Test: Defeat enemies. Confirm the alert shows, and localStorage.getItem("gold") logs 100 in the console.

Step 19: Display Gold
Instruction: In #player-area, add a <div> (ID: gold-display). Write updateGold() to set its text to "Gold: [gold]" and call it on load/victory. Load gold from localStorage on start.

Test: Win the stage, refresh. Confirm "Gold: 100" appears in #player-area.

Phase 6: Offline Polish
Step 20: Ensure Offline Functionality
Instruction: Load initial playerHeroes and gold from localStorage on page start (default to empty/0 if unset). Save them after every recruitment/victory.

Test: Recruit a hero, win the stage, close the browser, reopen offline. Confirm the hero and 100 gold persist.

Step 21: Finalize Single-File
Instruction: Ensure all code (HTML, CSS, JS) is in heroes-of-the-rift.html. Remove console logs, test on a phone offline.

Test: Download the file, open on a phone with no internet. Confirm the full game (recruitment, combat, campaign) works.

Completion Criteria
Single HTML file runs offline with:
Hero recruitment via button.

3x5 grid combat on Canvas.

One Campaign stage with gold reward.

Data persists via LocalStorage.

