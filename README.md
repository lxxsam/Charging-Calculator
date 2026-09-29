# Charging-Calculator
Charging Time Calculator

A small web app that estimates how long an EV takes to charge from its current
percentage to a target percentage. It also shows the finish time, the energy
added and the estimated cost in SGD.

The defaults are set for the **Zeekr 7X Long Range** (100 kWh battery, about 94 kWh
usable, 22 kW max AC, 480 kW max DC). You can change them under **Car settings** in the app.

## Using it

1. Type your **current charge** (%).
2. Pick a **target** (80 / 90 / 100 %, or **Other** to type your own).
3. Pick a **charger speed** (11 / 22 / 80 / 480 kW, or **Other speed…**).
4. Check the **price per kWh** for that charger. Each charger speed remembers its own price.

The result updates as you type.

### How the estimate works

- **AC (22 kW or less):** the charger speed is capped at the car's AC limit (22 kW),
  and about 10% is added for charging losses.
- **DC (above 22 kW):** power is capped by both the charger and the car. The car
  also slows charging as the battery fills, as real cars do (Zeekr's 10→80% claim
  on a 480 kW charger is about 11 minutes).
- **Cost** = energy billed by the charger × your price per kWh.

## Putting it on your Android phone

This is a web app you add to your home screen. It gets its own icon, opens
full-screen and works offline. You don't need the Play Store.

### 1. Publish it free with GitHub Pages (one-time)

1. On GitHub, open this repository → **Settings** → **Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Pick the branch that contains the app (`main` once it is merged) and the `/ (root)`
   folder, then click **Save**.
4. After a minute or two the page shows your link, for example
   `https://lxxsam.github.io/Charging-Calculator/`.

> GitHub Pages is free for **public** repositories. A private repository needs a
> paid GitHub plan for Pages.

### 2. Install it on your phone

1. Open the link in **Chrome** on your phone.
2. Tap the **⋮** menu → **Add to Home screen** (or **Install app**).
3. Open **Charge Time** from your home screen whenever you need it.

When the code on GitHub changes, the app updates itself the next time you open
it with an internet connection.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: layout, styling and calculator logic |
| `manifest.webmanifest` | Lets Android install it with a name and icon |
| `sw.js` | Service worker that makes it work offline |
| `icons/` | App icons |
