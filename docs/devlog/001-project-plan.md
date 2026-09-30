# 001 — Project plan

## Goal

Define an incremental route from an unmodified Korg monotron DUO to a safe,
calibrated Cardputer-ADV controller with optional BLE and USB MIDI input.

## Design choices

- Use the MCP4725 for pitch CV because it provides a persistent 12-bit voltage
  through the Cardputer's I2C-capable Grove connection.
- Keep gate generation behind a protected interface whose polarity and voltage
  will be selected only after measuring the actual Monotron board.
- Reuse one monophonic note-event path for the local keyboard, sequencer, BLE,
  and USB transports.
- Put hardware characterization before firmware implementation.

## Limits

- No hardware measurements have been made yet.
- The Monotron `Vrib` input is not assumed to follow 1 V/octave.
- USB MIDI host power and connector behavior remain to be validated.

## Verification

Documentation-only slice. Verify that the README links to the plan and that
every stage contains observable acceptance criteria.

## Hardware observations

None. Stage 0 begins with board identification and non-invasive measurement.

