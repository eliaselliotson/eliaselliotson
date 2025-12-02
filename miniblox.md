# Miniblox hacking

Bookmarklet: `javascript:(function()%7Bfor%20(const%20blockName%20in%20window.Blocks)%20%7B%0A%20%20%20%20const%20block%20%3D%20window.Blocks%5BblockName%5D%3B%0A%20%20%20%20%0A%20%20%20%20block.onLanded%20%3D%20(a%2C%20b)%20%3D%3E%20%7B%0A%20%20%20%20%20%20%20%20if%20(b%3F.game%3F.player%20!%3D%3D%20undefined)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20window.player%20%3D%20b.game.player%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D%0A%0Afunction%20applyHacks()%20%7B%0A%20%20%20%20const%20p%20%3D%20window%3F.player%3B%0A%20%20%20%20const%20bigNumber%20%3D%20299792458%3B%20%2F%2F%20The%20speed%20of%20light%0A%0A%20%20%20%20if%20(p)%20%7B%0A%20%20%20%20%20%20%20%20%2F%2F%20Enable%20creative%20mode%20abilities%0A%20%20%20%20%20%20%20%20p.abilities.mayFly%20%3D%20true%3B%0A%20%20%20%20%20%20%20%20p.abilities.mayEdit%20%3D%20true%3B%0A%20%20%20%20%20%20%20%20p.abilities.creative%20%3D%20true%3B%0A%0A%20%20%20%20%20%20%20%20%2F%2F%20Cancel%20all%20damage%0A%20%20%20%20%20%20%20%20p.knockbackResistance%20%3D%20bigNumber%3B%0A%20%20%20%20%20%20%20%20p.setHealth(bigNumber)%3B%0A%0A%20%20%20%20%20%20%20%20%2F%2F%20Update%20player%20info%0A%20%20%20%20%20%20%20%20p.updateClient()%3B%0A%20%20%20%20%20%20%20%20p.sendAbilities()%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20requestAnimationFrame(applyHacks)%3B%0A%7D%0A%0ArequestAnimationFrame(applyHacks)%3B%0A%0A%2F%2F%20Laser%20(press%20L%20to%20activate)%0Awindow.addEventListener(%22keydown%22%2C%20(e)%20%3D%3E%20%7B%0A%20%20%20%20if%20(e.key.toLowerCase()%20%3D%3D%3D%20'l')%20%7B%0A%20%20%20%20%20%20%20%20let%20%7B%20x%2C%20y%2C%20z%20%7D%20%3D%20window.player.pos%3B%0A%20%20%20%20%20%20%20%20let%20%7B%20pitch%2C%20yaw%20%7D%20%3D%20window.player%3B%0A%20%20%20%20%20%20%20%20let%20offsetX%20%3D%20-Math.sin(yaw)%20*%20Math.cos(pitch)%3B%0A%20%20%20%20%20%20%20%20let%20offsetY%20%3D%20Math.sin(pitch)%3B%0A%20%20%20%20%20%20%20%20let%20offsetZ%20%3D%20-Math.cos(yaw)%20*%20Math.cos(pitch)%3B%0A%20%20%20%20%20%20%20%20let%20r%20%3D%205%3B%0A%0A%20%20%20%20%20%20%20%20for%20(let%20mz%20%3D%20-r%3B%20mz%20%3C%3D%20r%3B%20mz%2B%2B)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20(let%20my%20%3D%20-r%3B%20my%20%3C%3D%20r%3B%20my%2B%2B)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20for%20(let%20mx%20%3D%20-r%3B%20mx%20%3C%3D%20r%3B%20mx%2B%2B)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20for%20(let%20i%20%3D%200%3B%20i%20%3C%20100%3B%20i%2B%2B)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20window.player.world.setAirXYZ(x%20%2B%20mx%20%2B%20(offsetX%20*%20i)%2C%201%20%2B%20y%20%2B%20my%20%2B%20(offsetY%20*%20i)%2C%20z%20%2B%20mz%20%2B%20(offsetZ%20*%20i))%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D)%3B%7D)()%3B`

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

// Laser (press L to activate)
window.addEventListener("keydown", (e) => {
    if (e.key.toLowerCase() === 'l') {
        let { x, y, z } = window.player.pos;
        let { pitch, yaw } = window.player;
        let offsetX = -Math.sin(yaw) * Math.cos(pitch);
        let offsetY = Math.sin(pitch);
        let offsetZ = -Math.cos(yaw) * Math.cos(pitch);
        let r = 5;

        for (let mz = -r; mz <= r; mz++) {
            for (let my = -r; my <= r; my++) {
                for (let mx = -r; mx <= r; mx++) {
                    for (let i = 0; i < 100; i++) {
                        window.player.world.setAirXYZ(x + mx + (offsetX * i), 1 + y + my + (offsetY * i), z + mz + (offsetZ * i));
                    }
                }
            }
        }
    }
});
```
