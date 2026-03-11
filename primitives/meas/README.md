# PRIMITIVE CATEGORY: meas 

This directory contains the reference documentations for XMODEL's measurement probe primitives, which make various measurements on simulated waveforms.

## Contents
- check_delay         : A primitive for checking the delay of an xbit-type signal.
- check_delay_bit     : A primitive for checking the delay of a bit-type signal.
- check_duty          : A primitive for checking the duty-cycle of an xbit- type clock input.
- check_freq          : A primitive for checking the frequency of an xbit- type clock input.
- check_period        : A primitive for checking the period of an xbit-type clock input.
- check_phase         : A primitive for checking the phase of an xbit-type clock input.
- check_value         : A primitive for checking the value of an xreal-type signal.
- check_value_real    : A primitive for checking the value of a real-type signal.
- meas_avg            : A primitive for measuring the average value of an xreal-typed signal within a time interval.
- meas_ber            : A primitive for measuring the bit-error rate of a data stream.
- meas_cross          : Measurement of the time instants of xreal-typed signal's crossing events.
- meas_delay          : A primitive for measuring the time difference between two triggering events.
- meas_deriv          : A primitive for measuring the n-th derivative value of an xreal-typed signal at triggering events.
- meas_edge           : Measurement of the time instants of an xbit-typed signal's transition events.
- meas_fall           : Measurement of the time instants of xreal-typed signal's falling events.
- meas_freq           : A primitive for measuring the frequency of a trigger.
- meas_integ          : A primitive for measuring the integrated value of an xreal-typed signal within a time interval.
- meas_max            : A primitive for measuring the maximum value of an xreal-typed signal within a time interval.
- meas_min            : A primitive for measuring the minimum value of an xreal-typed signal within a time interval.
- meas_negedge        : Measurement of the time instants of an xbit-typed signal's falling transition events.
- meas_period         : A primitive for measuring the time difference between two consecutive events of one trigger.
- meas_posedge        : Measurement of the time instants of an xbit-typed signal's rising transition events.
- meas_pp             : A primitive for measuring the peak-to-peak value of an xreal-typed signal within a time interval.
- meas_rise           : Measurement of the time instants of xreal-typed signal's rising events.
- meas_rms            : A primitive for measuring the root-mean-squared (RMS) value of an xreal-typed signal within a time interval.
- meas_slope          : A primitive for measuring the slope of an xreal- typed signal at triggering events.
- meas_time           : A primitive for measuring the time instants of triggering events.
- meas_value          : A primitive for measuring the values of an xreal- typed signal at triggering events.
- probe_ac            : An AC analysis probe for measuring frequency-domain, AC transfer function.
- probe_ber           : A probe for measuring the bit-error rate of a data stream.
- probe_bit           : A probe for a bit-typed signal.
- probe_dc            : A DC analysis probe for measuring DC transfer function.
- probe_delay         : A delay probe for a clock signal.
- probe_duty          : A duty-cycle probe for a clock signal.
- probe_freq          : A frequency probe for a clock signal.
- probe_meas          : A measurement probe (for internal use only).
- probe_period        : A period probe for a clock signal.
- probe_phase         : A phase probe for a clock signal.
- probe_real          : A probe for a real-typed signal.
- probe_stb           : A stability analysis probe for measuring the open-loop transfer function of a feedback loop.
- probe_value         : A probe for measuring the values of an xreal-typed signal at triggering events.
- probe_xbit          : A probe for an xbit-typed signal.
- probe_xreal         : A probe for an xreal-typed signal.
- trig_call           : A trigger generator for called events.
- trig_cross          : A trigger generator for an xreal-typed signal's crossing events.
- trig_edge           : A trigger generator for an xbit-typed signal's transition events.
- trig_fall           : A trigger generator for an xreal-typed signal's falling events.
- trig_negedge        : A trigger generator for an xbit-typed signal's falling transition events.
- trig_posedge        : A trigger generator for an xbit-typed signal's rising transition events.
- trig_rise           : A trigger generator for an xreal-typed signal's rising events.
- trig_time           : A trigger generator for timed events.

