# Front Speakers Optimization Guide

## System Analysis

**Hardware:**
- AVR: Denon AVC-X6800H (7.1.2ch)
- Front Speakers: KEF LS50 Meta
- Software: Dirac Live with ART (Active Room Treatment)

**KEF LS50 Meta Specifications:**
| Parameter | Value |
|-----------|-------|
| Frequency range (-6dB) | 47 Hz - 45 kHz |
| In-room bass response (-6dB) | 26 Hz |
| Frequency response (±3dB) | 79 Hz - 28 kHz |
| Crossover frequency | 2.1 kHz |
| Sensitivity | 85 dB |

---

## Current Issues Identified

Based on the measurement screenshots:

1. **Major Room Mode Peak (~50-70 Hz)**: +10-15dB boost caused by room resonance
2. **Deep Null (~100-120 Hz)**: -10 to -15dB cancellation from room reflections
3. **LS50 Meta Bass Limitation**: Natural roll-off below 47 Hz limits deep bass capability

---

## Optimized Settings Recommendations

### 1. Target Curve for Front Speakers (Group 1)

The KEF LS50 Meta is a compact bookshelf speaker. The target curve should respect its physical limitations:

**Recommended Target Curve Shape:**
```
Frequency    Target Level
20 Hz        -12 dB (natural roll-off)
30 Hz        -8 dB
40 Hz        -4 dB
50 Hz        -1 dB
60-80 Hz     +2 dB (slight bass shelf for warmth)
100-200 Hz   0 dB (flat reference)
200-2000 Hz  0 dB (flat)
2-10 kHz     -0.5 dB/octave (gentle high-frequency tilt)
10-20 kHz    -2 to -3 dB total
```

**Key Points:**
- Do NOT attempt to boost below 50 Hz - causes distortion and driver damage
- A gentle +2dB bass shelf at 60-80 Hz adds perceived warmth without stress
- High-frequency tilt improves listening fatigue on extended sessions

### 2. ART Support Settings for Group 1 (Front L/R)

Based on the Dirac ART Technical Guide, the LS50 Meta qualifies as a "smaller speaker" requiring special consideration:

**Current Settings (from your screenshots):**
| Support Group | Level | Range |
|---------------|-------|-------|
| Group 3 | -18 dB | 90-150 Hz |
| Group 4 | -24 dB | 120-150 Hz |
| Group 5 | -18 dB | 100-150 Hz |
| Group 6 | -24 dB | 20-100 Hz |

**Optimized Settings:**

#### If Group 6 Contains Subwoofer(s):
| Support Group | Level | Range | Rationale |
|---------------|-------|-------|-----------|
| Group 6 (Sub) | **-24 dB** | **30-100 Hz** | Raise low-end from 20 Hz to 30 Hz - subwoofer handles the deepest bass; increased support level helps fronts |
| Group 3 | **-18 dB** | **80-150 Hz** | Lower the low-end from 90 Hz to 80 Hz for better room mode coverage |
| Group 4 | **-18 dB** | **100-150 Hz** | Change from -24 dB to -18 dB nominal |
| Group 5 | **-18 dB** | **100-150 Hz** | Keep as-is |

#### If Surrounds Are Supporting Fronts:
Per the ART guide: *"Care needs to be taken not to drive small speakers with too much low-frequency power"*

| Support Group | Level | Range | Rationale |
|---------------|-------|-------|-----------|
| Surrounds | **-6 dB** | **80-150 Hz** | Reduce support level to -6 dB (less support); raise low-end to 80 Hz minimum |

### 3. Channel Grouping Recommendations

**Current Grouping:**
- Group 1: Front Left + Front Right
- Group 2: Center
- Group 3: Surround Right + Surround Left

**Recommended Grouping (no change needed):**
- Keep Front L/R paired - they are identical speakers in symmetric positions
- If experiencing asymmetric issues at listening position, consider separating FL and FR into individual groups

### 4. LFE Channel Support

**Critical Rule from Dirac:** *"Only let subwoofers and large full-range speakers support the LFE channel"*

**Action Required:**
- **Disable** support from Front L/R (LS50 Meta) to LFE channel
- **Disable** support from Surrounds to LFE channel
- Only subwoofer(s) should support LFE

To disable: Click the checkbox on the support range slider for the LFE channel group.

### 5. Fsiso (ART Crossover Frequency)

**Current:** 150 Hz

**Recommendation:** Keep at **150 Hz**

This is optimal because:
- ART operates in the 20-150 Hz range
- Room modes are most problematic below 150 Hz
- The LS50 Meta crossover is at 2.1 kHz, so 150 Hz Fsiso doesn't interfere

---

## Step-by-Step Implementation

1. **Open Dirac Live** and load your current project

2. **Adjust Target Curve:**
   - Click "Set target" button
   - Use the control points to create a gentle bass shelf (+2dB at 60-80 Hz)
   - Roll off below 50 Hz (don't try to extend bass beyond speaker capability)
   - Add slight high-frequency tilt (-0.5 dB/octave above 2 kHz)

3. **Modify ART Support Settings:**
   - Select Group 1 (Front L/R)
   - Click "..." to access advanced ART settings
   - Adjust each support group one at a time
   - Click "Calculate" after each change to see impact

4. **Disable Small Speaker LFE Support:**
   - Select the LFE channel group
   - Uncheck support from Front, Center, and Surround groups
   - Only subwoofer groups should remain checked

5. **Recalculate and Test:**
   - Press "Calculate" to regenerate filters
   - Upload to AVR
   - Test with familiar content

---

## Expected Results

After optimization:

| Aspect | Before | After |
|--------|--------|-------|
| Bass clarity | Boomy at 50-70 Hz | Tighter, controlled |
| Bass extension | Distorted below 40 Hz | Clean down to 45 Hz |
| Room mode at 50-70 Hz | +15 dB peak | Reduced to +3-5 dB |
| Null at 100-120 Hz | -15 dB | Improved to -5-8 dB |
| Driver stress | High (trying to produce 20 Hz) | Reduced (respecting limits) |
| Sweet spot | Narrow | Wider with ART |

---

## Additional Recommendations

### Physical Room Treatment
ART works best alongside minimal physical treatment:
- Bass trap in corners (handles frequencies ART can't fully correct)
- First reflection points absorption

### Measurement Tips
- Use at least 9 measurement positions for ART to work optimally
- Include positions slightly outside the primary listening area
- Validate all measurements before calibration

### Alternative Target Curves to Try

**Harman Curve Style:**
- +3 dB bass shelf at 60-100 Hz
- Flat 100-1000 Hz
- -1 dB/octave above 1 kHz

**BBC Dip Style:**
- Slight dip (-2 dB) at 2-4 kHz for reduced harshness
- Useful if recordings sound too bright

---

## Summary Table: Optimized ART Settings

| Parameter | Current | Optimized |
|-----------|---------|-----------|
| Target curve bass | Flat to 20 Hz | Roll-off below 50 Hz, +2dB shelf 60-80 Hz |
| Group 6 (Sub) range | 20-100 Hz | 30-100 Hz |
| Group 6 (Sub) level | -24 dB | -24 dB (keep) |
| Surround support level | -18 dB | -6 dB (less support) |
| Surround support range | 90-150 Hz | 80-150 Hz |
| LFE support from mains | Enabled | **Disabled** |
| Fsiso | 150 Hz | 150 Hz (keep) |

---

*Document generated based on Dirac Live ART Technical Guide and KEF LS50 Meta specifications.*
