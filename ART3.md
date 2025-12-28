# ART

How-to: ART Channel Group and Support Settings

A PDF-version of this guide can be found here (click to download): ART Channel Group and Support Settings

Problem formulation

If you are not completely convinced by the sound performance with ART using its default settings, there are several customization settings beyond the target curve to explore, depending on the desired adjustments. These settings are:

Channel grouping

Group Support enable/disable

Group Support Range

Group Support Level

Considerations

Subwoofer rated capability

We recommend separating subwoofers with different capabilities into separate channel groups. The reason behind this recommendation is that they can thereby be assigned separate support settings that better fit their individual capabilities.

We also recommend that if a subwoofer is positioned with less support from near walls (i.e. standing near an opening to a neighbouring room), then it should be grouped separately from similar subwoofers that have more wall support (i.e. standing in a corner of the listening room). The reason behind this recommendation is that supporting walls significantly affect the performance of a subwoofer in a room.

So, to better customize the ART settings to each of the subwoofers’ capabilities, the separation into different groups is a necessary first step. The second step would be to manually adjust the Support Range and Support Level that each subwoofer support group contributes to LFE or other main channels.

The adjustments to take the subwoofer’s rated bandwidth into account would mainly be addressed by the Support Range. If the subwoofer is relatively small, it may have a bandwidth limitation in the low end, calling for a higher frequency value than 20 Hz at the low end of the Support Range. If the subwoofer on the other hand is specifically designed for very low frequencies, it may call for a frequency value lower than 150 Hz in the high end of the Support Range.

As a rough indication for Support Level adjustments (a nominal value for the Support Level parameter is -18dB):

When wanting a subwoofer support group to contribute more to the output, the Support Level can be set to -24dB.

When wanting a subwoofer support group to contribute less to the output, the Support Level can be set to -6dB.

Consider only changing these settings on one support group at a time before pressing the “Calculate” button, to see how the change impacts the overall speaker co-optimization.

LFE main channel

LFE (low-frequency effects) is a single discrete content channel in multichannel formats. It is usually defined to produce and deliver content below 120Hz (see <https://en.wikipedia.org/wiki/Low-frequency_effects>). As such, it fits perfectly into the ART support range below 150Hz.

Dirac Live requires that a device that is configured with an LFE channel, declares one of the speakers as the main speaker for the LFE channel. That main speaker will serve as reference for the ART impulse response correction at all the measured microphone positions. The channel group that contains this LFE main speaker will also have a target curve associated with it.

Due to the low frequencies present in the LFE channel, it should be taken as a main rule of thumb to only let subwoofers and large full-range speakers support the LFE channel. This means disabling support from smaller speakers to the LFE channel group, which is done by clicking their support range slider associated to the LFE channel group:

Figure 1

The support from any channel group to the LFE group can be toggled on/off by clicking the checkbox on the corresponding slider rail while the LFE channel group is selected.

In case of not applying this rule of thumb, the following should be considered:

Direction of arrival

There is a quite high consensus around the non-audibility of direction-of-arrival of sounds below 80 Hz. ART support speakers align well with the main speaker in terms of impulse response target, so this should normally not need to be a consideration to make when assigning support groups for the LFE channel. One case where it would make sense to take the audibility of directivity into account, is when the listening position is much closer to one of the support speakers than to the main speaker it is supporting.

It may then make sense to bring out the support speaker to its own group and reduce its high end of the support range in the group it is supporting.

Since these conditions are often symmetrical, it also makes sense to separate the main speaker group into two, so that for example Left Front has a lower support range from Right Surround than from Left Surround, and vice versa.

Figure 2

Example of symmetrical assignment of asymmetrical support. This could be used, for example, to mitigate situations when a listener is expected to be sitting very close to either of the surround speakers. Note that Left Front and Right Front channels have been separated, as have the Left Surround and Right Surround, into different groups in the right-side panel.

Load balancing:

When using multiple subwoofers, the LFE load assigned to each of them with ART may sometimes seem unbalanced. Please refer to section Subwoofer rated capability, above, for further guidance.

Distortion:

Care needs to be taken not to drive small speakers with too much low-frequency power, as they may be forced into non-linear behaviour that causes distortion, or even worse, over-excursion that may eventually break the speaker. Consult the speakers’ rated bandwidth and sensitivity for guidance and make the following adjustments to avoid such undesired conditions:

Reduce the Support Range of the smaller speakers to the LFE channel. Specifically, drag the low end of the support range upwards to avoid feeding low frequencies into the small speakers.

Reduce the Support Level of the smaller speakers to the LFE channel. A good rough number for less support is -6dB (the nominal value is -18dB).

The Support Level setting for the LFE channel is accessed by clicking the “…” symbol in the LFE channel group on the right side of the Dirac Live window.

Figure 3

Left: Where to access the advanced ART settings for the LFE channel group. Right: Where to adjust the Support Level from the Surround channel group to the LFE channel group.

If distortion remains unacceptable, then resort to the main rule of thumb of disabling support from the smaller distorting speakers.

Directional bass

Some systems let you configure subwoofers for bass management with directional bass. This means that participating subwoofers will be positioned near a main speaker for a discrete content channel and be fed bass content specifically from that channel. Dirac Live ART will have this behaviour as a natural consequence of the concept of main and support speakers, giving each main channel as ideal properties as possible, including extending their bass capabilities while not sacrificing their imaging properties. However, for those interested to delve deeper into further manual adjustments to possibly push this effect even further, the following tips indicate some exploratory paths to try:

Separate the subwoofers that should be assigned to support specific main channels from the LFE group into separate groups.

Separate the main speakers that should be associated with specific subwoofers for directional bass into separate groups. This is necessary to associate different supporting subwoofers to each of the main channels separately.

For example, drag the Front Right speaker out of the Front group to form one group for the Front Right and one for the Front Left channel.

For each of the main channels, enable the corresponding subwoofers and adjust their support ranges and support levels as to reach the desired effect. This is not a binary on/off setup, but can be adjusted to make more or less use of ART control:

Ensure that each directional subwoofer is supporting its corresponding main channel maximally:

Select the main channel to be configured.

Among its support speakers, ensure the directional subwoofer is enabled and has the maximal range.

Optionally, increase its Support Level. A good rough number for more support is -24dB (the nominal value is -18dB).

Optionally adjust other subwoofers’ support settings to contribute less than the directional subwoofer. Note that this may have the consequence that the subwoofer is not contributing maximally to optimize the main speaker’s impulse response, so you are encouraged to compare the manual adjustments to the default settings.

Reduce the Support Range to reduce their contribution above 80Hz.

Reduce the Support Level. Again, a good value for less support is -6dB.

Optionally adjust other speakers’ support settings to increase or reduce their contribution to directivity of each main channel. Again, this may have the consequence that the support speaker is not contributing maximally to optimize the main channel.

Support speakers don’t have specific target curves

Conceptually, in Dirac Live ART, target curves are assigned to main channels. When a subwoofer is separated into a different group than the main LFE channel, it will not have a dedicated target curve directly associated to it. It will instead contribute to attain the target of each main channel group it is set up to support.

Conclusion on recommended use

The sections above give more detail into the exact considerations for different situations, but as a rule of thumb:

ART support from channel groups with considerably smaller or incapable speakers, to the LFE main channel group, should be avoided and such support connections be switched off by unchecking the corresponding support checkbox.

If subwoofers are significantly different in rated or actual in-room performance, it usually pays off to separate them into different support groups and adjust the Support Range and Support Level accordingly.

When an ART design has created support filters with unexpectedly different magnitude responses (but not necessarily sounding bad in any way) it can be explored to assign different Support Levels to the different support channel groups. Rough numbers for different Support Levels:

Less support: -6dB

Nominal support: -18dB

More support: -24dB
