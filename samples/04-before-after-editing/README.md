# Before & After: Editing for Clarity

**Document type:** Editing sample
**Why this sample:** Content review and plain-language editing are core to technical writing but hard to show in a finished document alone. This sample shows the editing judgment behind the final text.

---

## Example 1: Configuration Note

**Before (engineering draft):**

> In the event that the aforementioned configuration parameters are not correctly set in accordance with the specifications outlined in the preceding section, it is possible that the system may fail to initialize properly, and as such, users are advised to verify all settings prior to attempting a restart of the application.

**After (edited):**

> If the configuration parameters in the previous section are incorrect, the system may fail to initialize. Verify all settings before restarting the application.

**What changed and why:**
- Cut 55 words to 21 without losing any technical meaning
- Removed passive, hedging phrases ("it is possible that," "as such, users are advised") — these weaken instructions and slow the reader down
- Replaced "in the event that" with "if" — this is a controlled-language substitution common in ASD-STE100-style writing
- Kept it as two short, direct sentences instead of one long conditional clause

## Example 2: Installation Step

**Before (SME draft):**

> The technician should ensure that the bracket, which is typically secured using four M6 bolts, has been properly tightened, taking care not to over-torque, before moving on to the next stage of the installation process.

**After (edited):**

> Tighten the four M6 bracket bolts to the torque value in Table 3-1. Do not over-torque. Continue to the next step.

**What changed and why:**
- Converted from a description of what "should" happen to a direct instruction — procedural docs should tell the reader what to do, not describe the ideal outcome
- Replaced a vague caution ("taking care not to") with a direct warning and pointed to the specific spec (Table 3-1) instead of leaving torque value undefined
- Split into three short action sentences, matching the one-action-per-step convention used in maintenance manuals

## Editing Principles Applied

1. **One idea per sentence.** Long conditional or compound sentences hide the actual instruction.
2. **Active voice, imperative mood for procedures.** "Tighten the bolts," not "the bolts should be tightened."
3. **Cut hedge words.** "Typically," "generally," "it is possible that" — these add length without adding clarity, and in some cases introduce ambiguity about whether a step is mandatory.
4. **Point to specifics, don't restate them inline.** Reference a table or section instead of embedding values in prose where they're easy to miss or get out of sync.
