Supplementary Materials — TIOT-2026-0170.R1

Contents
1. S1_HFSS: HFSS project files and mesh-convergence results.
2. S2_Data/differential_impedance: differential input-impedance exports.
3. S2_Data/frequency_screening_analysis: frequency-screening tables and figures.
4. S2_Data/hfss_state_exports: state-dependent field and current exports.
5. S3_UART/run1 and run2: acquisition settings, acquisition logs, per-frequency
   recovery results, candidate-frame decoding results, and raw-file checksums
   for the two TX-enabled sweeps.
6. S3_UART/no_tx/run3 and run4: settings, logs, decoding results and signal-quality
   and checksum inventories for the two matched-grid TX-disabled sweeps.
   no_tx/control_summary.json summarizes the two controls together.

UART data guide
Each analyzed run covers 400–1600 MHz in 20 MHz steps (61 frequency records).
run1 corresponds to the source label full_sweep_30cm; run2 corresponds to
full_sweep_30cm_1. The directory/run columns retain these original labels.
The results are exported from the existing analysis without recomputation.
Each TX-enabled run has seven CRC-valid frames (14 combined).

TX-disabled controls also cover 400–1600 MHz in 20 MHz steps, with 61 recordings
per run and 2 seconds per recording (122 recordings and 244 seconds in total).
Run3 yields eight candidates, seven complete; run4 yields five candidates,
four complete. Neither run yields synchronization-, header-, or CRC-valid frames.
Original control run labels 3 and 4 are retained in the result tables.

run_config.json contains the recorded acquisition settings.
manifest.csv is the unmodified acquisition log. The run1 log also contains four
preliminary acquisition entries before the final 61-frequency sweep; these
preliminary entries are not additional records in frequency_summary.csv.
frequency_summary.csv contains one analysis record per sweep frequency.
decoded_frames.csv contains candidate-frame results; not every candidate is a
valid UART frame. Use sync_ok, header_ok and crc_ok to distinguish valid frames.
The saved decoding results use 9600 baud, a raw sampling rate of 500 kS/s,
and a processing sampling rate of 96 kS/s.
raw_iq_manifest_sha256.csv lists checksums only for the 61 analyzed files in
each run. The original binary IQ recordings are not included in this package.


7. S4_Hardware_DeltaM: full-band held-out square-wave modulation results,
   normal-operation repeat means and ranges, cable-disconnected controls,
   and independently extracted local maxima with their prominences.
   See S4_Hardware_DeltaM/README.txt for selection and source-label mapping.

Differential-port impedance models (S1_HFSS)
Z_10cm.aedt, Z_20cm.aedt, Z_30cm.aedt, and Z_40cm.aedt are the
physical interconnect models with a lumped port across the signal and return
conductors at the logic-side reference plane. The incident plane wave and
logic-side state-load branches are removed; the far-end termination is retained.
These projects document the differential-port configuration used for impedance
extraction. The existing reference_*.aedt and test_*_state*.aedt files retain
the plane-wave configurations for the field/current study.

Screening dB convention (S2_Data/frequency_screening_analysis)
The exported selected_E_loss_dB and
selected_E_loss_vs_strongest_local_E_dB columns store the signed level
20*log10(E_selected/E_reference), so a weaker selected field is negative.
The manuscript reports the positive selection loss
20*log10(E_reference/E_selected), the negative of the corresponding CSV
value. The main manuscript tables use the strongest principal internal
field peak as reference, rather than the sweep-wide maximum when that
maximum lies at a boundary. Exported numerical values are preserved.
