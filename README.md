# Fuel Burn Estimator

Work out how much fuel a car burns per lap from what you put in and what you pump out, and turn jug scale weights into liters. Built for fuelers and engineers, remembers your jugs and your work, works offline, and looks and feels like the Tire Set Tracker.

**Open it:** https://themohawk13.github.io/Fuel-Burn-Estimator

Created by Ryne Hoover Transportation.

## Put it on your phone

1. Open the link above (Safari on iPhone, Chrome on Android).
2. Let the page finish loading while you have a connection. This saves it for offline use.
3. iPhone: tap **Share**, then **Add to Home Screen**. Android: open the browser menu, then **Install app** or **Add to Home Screen**.

After that it opens like an app and works without a signal.

## Burn per lap

1. **Pick the track.** Choose one from the list, or **Custom Track...** and type its length in miles.
2. **Pick how you measured the fuel.** **L** or **gal** if you read it off a pump, **kg** or **lbs** if you weighed it. The weight options also show the fuel blend and fuel temperature, because the same weight is a different volume when the fuel is warm.
3. **Enter the numbers.** Fuel put in, fuel pumped out, laps completed, and optionally the tank size.
4. **Read the result.** Fuel used per lap (in liters, kg and lbs), net burned, liters per km, and the most laps a full tank would last.
5. **Log session** adds it to the list below so you can compare runs. **Remove** takes an entry off.

## Jugs & fill

**My jugs.** Weigh each empty jug once and save its number (or name) and tare. Name them to match the numbers on your jugs. After you save one, the next number fills in for you, so a full set goes in quickly. To fix a tare, change it in the list. Saved tares stay on your phone, so you only do this once.

**Pump-out jugs.** Pick the jug, weigh it full, and type the gross weight. The app uses that jug's saved tare and shows the liters in it. Tap **Add jug to total** and the next saved jug is picked for you. For a jug you haven't saved, choose **Other** and type its tare. **Send total out to Burn** puts the combined liters into the fuel pumped out box.

**Fill a jug to a target.** Pick the jug and type how many liters you want. The app shows the **gross scale target** to stop filling at, plus the net fuel weight.

**Send SG to Burn** copies the fuel SG and temperature over so both screens use the same density.

## Where your data lives

Everything you enter is saved on **your own device only**: your setup, the session log, the jugs you have weighed so far in a pump-out, and your saved jug tares. It is still there after the phone locks, you switch apps, or you close the app. Other people who open the link start with a blank copy and can't see your data, and you can't see theirs. Clearing your browser's website data erases it, and a different phone or browser will not have it. **Clear all** on the session log or the pump-out list empties that list.

## Calculation reference

1. **Temperature-adjusted specific gravity**

   $$\text{SG}_{\text{adj}} = \text{SG}_{60^\circ\text{F}} - \left[\beta \times (T_{^\circ\text{F}} - 60)\right]$$

   $\beta$ is 0.00060 per °F for VP E100 and 0.00050 per °F for the other presets.

2. **Weight to volume**

   $$\text{Liters} = \frac{\text{Weight (kg)}}{\text{SG}_{\text{adj}}}$$

3. **Fuel used per lap**

   $$\text{Liters/Lap} = \frac{\text{Fuel Put In (L)} - \text{Fuel Pumped Out (L)}}{\text{Laps Completed}}$$

## Updating the site (for the site owner)

Upload the changed files to the repository, then raise the version number in `sw.js` (for example from `fuel-burn-v3` to `fuel-burn-v4`) so phones pick up the new version. iPhones save the home screen icon when it is added, so delete the old shortcut and add it again to see a new icon.
