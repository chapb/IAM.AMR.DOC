

The CEDAR Database
==================





Data extraction rules
---------------------

Multiple measurements at single stage
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Where multiple measurements are available within a single stage, the measurement closest to human exposure *should* be extracted, except ...

... where there are missing or unavailable data at the measurement closest to human exposure.
   
   For example, where an observation is missing from one treatment group, or where multiple experiments end at different time points. The measurement that is closest to human exposure that is comparable across experiments or within an experiment *should* be extracted.

... where the data is inapplicable in the Canadian context.

   For example, where an observation is recorded after production would have ended in Canada. The measurement that is closest to human exposure that is within production timelines *should* be extracted.

.. tip::   
   Resistance was assayed at days 10, 20, and 30 of production. Measurement from day 30 is extracted.

   Resistance was assayed at days 10, 20, and 30 of production for the treatment group, and at days 10, and 20 for the referent group. Measurement from day 20 is extracted.

   Resistance was assayed at days 7, 14, 21, 28, 35, 42, and 49 of broiler production. Measurement from day 35 is extracted, as it is the latest within the Canadian production timeline of 36 days.


