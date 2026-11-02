# Greyscale

An HCFR-style greyscale report for a rooted LG webOS TV, measured with a Spyder5 and shown on the TV. It **only measures**: no picture setting or calibration table is changed.

- 0–100% grey in **0.5% steps** (201 levels), against SDR **BT.709, gamma 2.4 (power), D65**.
- Per step: luminance and its target, gamma, RGB balance (100/100/100 = D65), colour temperature, ΔE2000 (with and without the luminance error).
- On the TV: average and worst ΔE, average gamma, white, black, white CCT; charts of gamma, RGB balance and ΔE; a scrolling table of every step.
- Saved on the TV as `/media/internal/com.muhib.bloob/calibration/latest-greyscale.html`, `.csv` and `.json` (and a dated copy in `reports/`).

## Install

From the folder you downloaded it to:

```
ares-install -d rootedTV com.muhib.greyscale_1.0.0_arm.ipk
```

## Use

1. Switch the TV to the picture mode you want to measure.
2. Hang the Spyder5 flat in the middle of the screen.
3. Open **Greyscale** (LG's app list), or from a computer:
   `ssh root@<TV> "luna-send -n 1 luna://com.webos.applicationManager/launch '{\"id\":\"com.muhib.greyscale\"}'"`
4. Choose **Measure greyscale** (about 45 minutes). The screen goes black with a small card in a corner: LG's test squares only draw over a playing video, so the app plays a black one.
5. The report opens by itself when it finishes. **Last greyscale report** opens it again. Up/Down scroll the table, Left/Right a page, Back returns.

## Needs

- A rooted TV with the Homebrew Channel (the measurement runs as root through it).
- The Spyder probe app's Argyll `spotread` on the TV, and optionally the meter correction file at `/media/internal/com.muhib.bloob/calibration/argyll/lg-55g2.ccss`.

Made from Bloob (`native/` in muhibegypt-del/Bloob): the same program under its own app id, with one screen and no service.
