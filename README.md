# Orrery Flight

A solar-system fleet game in one HTML file (three.js): patched-conic orbital flight flown flat out, formations
and fleets, ship design, combat with fog of war (drive signatures, silent running, jamming), an economy of
propellant and metals, towed infrastructure, and an enemy faction that expands from Jupiter or Saturn. **New
game** offers a standard opponent or a cunning one that lays ambushes, feints, raids lone ships and designs its
warships against yours.

**Play:** https://ryangeng2.github.io/orrery-flight/

## Two-player co-op

Press **Co-op** in the controls bar. One player hosts (starting at Earth) and gets a code; the other joins with
it (or opens the `#join=CODE` link) and starts at Mars. The host's browser runs the game and sends its state to
the other player twice a second through Firebase Realtime Database; the other player's orders go back to the
host. The enemy is stronger for two, and time runs at the slower of the two players' chosen warps.

### Firebase setup (once)

Co-op uses the Realtime Database of the Firebase project `neu-microwave-map` (its Firestore is not touched).

1. Firebase console → Build → Realtime Database → Create database, location **United States (us-central1)**
   (the game expects `https://neu-microwave-map-default-rtdb.firebaseio.com`), start in locked mode.
2. Rules tab: paste `database.rules.json` and Publish. Games live under `orrery/<code>` and are removed when
   the host leaves.
