# Miniblox hacking

Bookmarklet: `javascript:(function()%7Bfor(const%20blockName%20in%20window.Blocks)%7Bconst%20block%3Dwindow.Blocks%5BblockName%5D%3Bblock.onLanded%3D(a%2Cb)%3D%3E%7Bif(b%3F.game%3F.player!%3D%3Dundefined)%7Bwindow.player%3Db.game.player%7D%7D%7D%0Afunction%20applyHacks()%7Bconst%20p%3Dwindow%3F.player%3Bconst%20bigNumber%3D299792458%3Bif(p)%7Bp.abilities.mayFly%3D!0%3Bp.abilities.mayEdit%3D!0%3Bp.abilities.creative%3D!0%3Bp.knockbackResistance%3DbigNumber%3Bp.setHealth(bigNumber)%3Bp.updateClient()%3Bp.sendAbilities()%7D%0ArequestAnimationFrame(applyHacks)%7D%0ArequestAnimationFrame(applyHacks)%7D)()%3B`

Javascript code:
```javascript
for (const blockName in window.Blocks) {
    const block = window.Blocks[blockName];
    
    block.onLanded = (a, b) => {
        if (b?.game?.player !== undefined) {
            window.player = b.game.player;
        }
    }
}

function applyHacks() {
    const p = window?.player;
    const bigNumber = 299792458; // The speed of light

    if (p) {
        // Enable creative mode abilities
        p.abilities.mayFly = true;
        p.abilities.mayEdit = true;
        p.abilities.creative = true;

        // Cancel all damage
        p.knockbackResistance = bigNumber;
        p.setHealth(bigNumber);

        // Update player info
        p.updateClient();
        p.sendAbilities();
    }

    requestAnimationFrame(applyHacks);
}

requestAnimationFrame(applyHacks);
```
