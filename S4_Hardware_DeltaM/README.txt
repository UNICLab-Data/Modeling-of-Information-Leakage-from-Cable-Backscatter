S4_Hardware_DeltaM

Purpose
Full-band comparison of the original 10-kHz square-wave modulation response
with cable-disconnected controls. These are not the UART captures acquired
on 2026-10-28 and are not the UART transmitter-off controls in S3.

Data selection
all_heldout_results.csv retains only stage=independent_test and partition=test
from the supplied all_results_long.csv. Mdelta is Delta M: the magnitude of
the difference of the two state-conditioned complex IQ means divided by the
test-segment IQ RMS. Phase selection uses the separate training segment.
The 50 phase bins and 10-kHz nominal modulation are recorded in the export.
Source filesystem paths have been omitted from the upload copy.
Seven source rows have zero IQ RMS; their numerical source values are retained
but valid_metric=false, so they must not be interpreted as measured Delta M=0.
None belongs to the four sweeps used in the main comparison figure.

Figure configuration and provenance
The main figure uses the normal-operation source R_1M_C_331P_Version,
sweeps 50cm_1 and 50cm_2: a 50-cm cable and nominal 331-pF termination,
with 121 points per sweep at 10-MHz spacing over 300-1500 MHz.
This termination belongs to the 22/331/681-pF hardware experiment described
in the manuscript. The full-band repeat sweeps shown here have 10-MHz
spacing, as distinct from the 20-MHz branch-tracking grid.
Group A in the CSV summaries identifies this main-figure selection only.
The legend uses Normal operation, without a group or terminal label.

Additional normal-operation sets are retained in the CSV summaries:
group B is R_1M_C_30P_Version, sweeps 50cm_1 and 50cm_2 (121 points each);
group C is R_1M_C_221P_Version, sweeps 30cm_1 and 30cm_2 (61 points each).
All retained source conditions, including the 331-pF and 681-pF sweeps,
remain in all_heldout_results.csv. Source identifiers are preserved and
the 30P label has not been reinterpreted as 22 pF.

The two disconnected sources are R_1M_C_30P_Version/50cm_no_data and
R_1M_C_221P_Version/30cm_no_data, each with 61 points at 20-MHz spacing.
Their pointwise mean is the background shown in the single-panel figure;
their measured range is retained. With the cable disconnected, there is
no assigned terminal load. The source labels are archival identifiers,
not terminal assignments for the disconnected measurements.
The supplied control metadata identifies the effective length as 50 cm
in both archival source groups; for the 221-pF source label, this includes
20 cm of fixed wiring in addition to the 30-cm folder label.
The author identifies no_data as cable disconnected, with the RF transmitter
remaining on, and confirms unchanged gain settings, antenna positions and
processing. The exports do not independently record the MCU output state
during the disconnected captures.

normal_vs_disconnected_curves.csv contains the two normal measurements,
their pointwise mean and minimum/maximum, and the measured control where
available. Blank control entries at intermediate 10-MHz frequencies mean
unmeasured, not zero. Controls are not interpolated for numerical comparisons.
Shading shows ranges of two sweeps, not confidence intervals.
All ratios and counts compare each normal mean with the same disconnected
mean at the 61 directly shared frequencies, without baseline subtraction.
For the main 331-pF selection, normal operation exceeds background at 55/61
shared frequencies; the median pointwise ratio is 8.61272720026177.
The normal_terminal_capacitance_pF column applies only to normal operation.

independent_local_peaks.csv enumerates all strict internal local maxima of
the unsmoothed normal-operation mean curves and the disconnected mean,
together with their topographic prominences. No model-centered windows,
prominence cutoff or theoretical branch information is used. Endpoints
are excluded. The disconnected rows have no terminal capacitance assigned;
their method field identifies the disconnected response. The normal_mean
column contains the corresponding curve value for all rows, including the
disconnected mean in those explicitly identified rows.
These lists are not quantitative assignments to the theoretical branches.

Cross-check
The no_data independent-test values agree with the separately supplied
hardware_no_data_deltaM_heldout.csv to within 5e-14 in absolute Delta M.
No raw IQ, firmware or processing scripts are included in this section.
