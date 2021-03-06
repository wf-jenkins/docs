---
title: Interacting with Dashboards and Charts
keywords: dashboards
tags: [dashboards, charts, getting started, videos]
sidebar: doc_sidebar
permalink: dashboards_interacting.html
summary: Learn how to isolate sources and series, share URLs, alter time windows, apply global queries, and activate chart display modes.

---
Watch this video for an introduction:

[Interacting with Charts and Dashboards](https://vmwarelearningzone.vmware.com/oltpublish/site/openlearn.do?dispatch=previewLesson&id=5a810256-dc7a-11e7-a6ac-0cc47a352510&inner=true&player2=true)

## Common Interactions
A few interactions are common to dashboards and charts. You can isolate sources and share shortened URLs. These are available in the action buttons at the bottom right of a dashboard or chart:

![action buttons](images/action_buttons.png)

### Isolating Sources and Series

When looking at charts, you can investigate a particular source or series further. Charts and dashboards have a couple of ways to do this.

**To isolate one or more sources**

Start typing the name of the sources to isolate. The fly-out supports wildcards. For example, you can search for **app-1**, **app-1\***, or **\*-1\***. When you isolate a source, series with those sources display as saturated and all other series lose color saturation.

   ![highlight sources](images/highlight_sources.png)

1. Type the name of the sources to isolate.

   ![isolated line](images/isolated_line.png)

   An isolation bar appears at the bottom of the page.

   ![isolation bar](images/isolation_bar.png)


**To isolate sources and aggregated series** you can click a series in a chart:

1. Hover over the series you want to isolate. The series you hover over display as saturated and all other series lose color saturation.
1. Click the series.  An isolation bar appears at the bottom of the page. To isolate multiple series on all charts, hold down the **Windows** or **Command** key and repeat.
   - If a series is related to a single source, it appears in the **Sources:** list. When you isolate a source, every series in the dashboard containing that source is isolated.
   - If a series represents an aggregation of sources, it appears in the **Series:** list.  When you isolate a series, the query field name displays in the isolation bar and every series in the dashboard with that query field name is isolated.

     ![isolated series](images/isolated_series.png)

**To remove a single isolation**, click the **X** icon next to the series.

**To remove all isolated sources or series** click the **X** icon next to the list label.

### Sharing Dashboards and Charts

The URLs in the Wavefront address bar encode information about the dashboard or chart name and any settings you have applied. When you make a change to a dashboard or chart, for example, change the time window, the URL updates to reflect that change. With this functionality, you can quickly and easily share your current view with other users. Those users can see exactly what you see and can also interact with the dashboard or chart.

The actual URL can be a long string. When you click the link icon in the action buttons, a shortened URL is copied to your clipboard. The shortened URL allows you to share a fully interactive dashboard or chart, but the link is associated with a specific time frame instead of a live view.

**To share the dashboard or chart** in live view mode:

1. Navigate to the dashboard or chart.
2. In the time bar, click **Live Data**.
3. Select the desired time window (10m, 2h, 6h, 12h, 1d, 8d) from the time bar that you'd like to share. When a dashboard or chart is set to Live Data, a new link icon appears below the gear icon on the taskbar.
1. Right-click the link icon and select **Copy link address**.
2. Share the link with other users.

The time window associated with your live view URL link is based on your selection on the time bar. For example, if you select 10m, the result is a live view URL link with a 10 minute view.

## Dashboard Interactions

You can perform some tasks, such as working with sections, on the dashboard itself, while other tasks such as selecting the time window, apply to every chart in the dashboard.

<a name="time_window"></a>

### Selecting Dashboard Time Windows

By default dashboards display charts with a two-hour time window with real-time data flowing in. Charts are updated every 30s and the Live Data control displays the state of the update cycle:

![live data](images/live_data.png)

You can configure the default time window in [dashboard preferences](dashboards_managing.html#prefs).

To select a larger or smaller time window or to view past data instead of realtime data, use the time bar controls to select time windows:

![time window](images/time_bar.png)

- To see up-to-date data on the charts, click **Live Data**.
- To look at past data, click **Custom Date**. When you select Custom Date, fields for a start and end time display.
- A set of time window intervals (10m, 2h, 6h, 12h, 1d, 8d)  display to the right of Live Data and Custom Date.
  - When Live Data is selected, click an interval to quickly increase or decrease the amount of live data displayed within each chart.
  - When Custom Date is selected, clicking an interval adjusts the start time based on the end time. For example, if your end time is 3:00 PM and you choose 12h, the start time is adjusted to 3:00 AM.

The following video gives an overview:

[Interacting with Dashboards and Charts]([Interacting with Charts and Dashboards](https://vmwarelearningzone.vmware.com/oltpublish/site/openlearn.do?dispatch=previewLesson&id=5103bc38-dc7a-11e7-a6ac-0cc47a352510&inner=true&player2=true)

### Working with Sections

Dashboard [sections](dashboards_managing.html#configuring-dashboard-sections) allow you to group saved charts in a meaningful way. By default, every dashboard has at least one section. The section link bar is located directly below the time bar.

![section toc](images/section_links.png)

**To jump to any section** on a dashboard, click the section name in the section link bar.

**To toggle whether a section is expanded or collapsed**, click the section name. All sections are expanded when you first display a dashboard.

### Displaying Events on Charts

The **Show Events** dropdown (with **From Chart** <i class="fa fa-caret-down"/> selected) in the middle of the time bar allows you to overlay [events](charts_events_displaying.html) on the X-axis of charts.

![time window](images/time_bar.png)

See [Controlling Event Overlays](charts_events_displaying.html#controlling-events-overlays).

### Performing Temporary Global Queries

Suppose you would like to apply a temporary ts() expression to every chart to help identify when the time series in a set of charts cross a threshold. For example, you have a dashboard that tracks errors per second across several applications and drawing a temporary constant 5 across every chart helps you to see which applications have the highest number of errors. Instead of permanently applying a constant value of 5 to every chart, you can use the Global Query fly-out. Global queries allow you to temporarily apply any ts() expression to every chart on a dashboard. For example:

- A constant value such as 5
- A simple ts() expression such as `ts(~metrics.counter)`
- An advanced ts() expression such as `(ts(mem.total) - ts(mem.free)) * 100`

To apply a global query:

1. Hover over the Global Query fly-out (**+**) icon in the action buttons at the bottom right corner of a dashboard.
1. Specify a ts() expression, for example, 5:

   ![global query flyout](images/global_query_flyout.png)

1. Press **Enter** or **Return**. For the query 5, every chart displays a temporary constant time series 5:

   ![global query](images/global_query.png)

The Global Query fly-out stays out until you remove the query expression.

### Opening a Chart

To open a chart, click the chart name in the upper right corner.

![chart title](images/chart_title.png)

In the chart editor, you can modify and add chart queries and display properties.

## Selecting Chart Time Windows

You can select time windows for individual charts in a few different ways.

### Time Bar

The chart time bar ![chart time bar](images/chart_time_bar.png#inline) displays in the upper-right corner of a chart when you hover over the chart. The magnifying lenses allow you to quickly increase or decrease the time window. You can also adjust the time window by clicking 2h, 6h, 12h, 1d, or 8d.

### Displaying Live Data

If the chart is not displaying live data, a <span style="color:#8B0000">GO LIVE</span> <i class="fa fa-play-circle" style="color:#8B0000"/> link displays to the left of the time bar.

![chart_name_corner](images/chart_name_corner.png)

Click the link to display live data.

### Zooming In

Here's a shorcut for zooming into a time window:

1. Hover over a chart and place your cursor at the beginning of the desired time window. In the chart below, this would be 12:00 PM.
1. Left click and hold while dragging over the desired time window. A blue box appears over the desired time window.
1. At the desired end point, 12:05 PM in the chart below, release the mouse button. The highlighted time window expands to fill your chart.

To zoom into to all charts on a dashboard, hold down the **Shift** key while selecting the window.

![drag and zoom](images/drag_zoom.png)

### Shifting the Time Window

You can shift the time window of a single chart by shifting the X-axis.

1. Place your cursor over the X-axis until your cursor changes to a 4-way arrow <i class="fa fa-arrows"/>.
1. Click and hold while dragging your cursor to the left to shift the time window into the past, or to the right to shift the time window into the future. When you reach the present you cannot drag the X-axis further to the right.

To shift the time windows of all charts on a dashboard, hold down the **Shift** key while dragging.

### Propagating and Resetting Time Windows

Whenever you adjust the time window of a single chart, you can easily propagate that window to every other chart on the dashboard or reset the individual chart to match all of the other time windows.

To propagate a chart time window to all other charts on the dashboard, click the share icon <i class="fa fa-share-square-o" /> that appears directly under the chart name in the top right corner of the chart box.

To reset the individual chart window to match all other charts, click **RESET**: ![reset time window](images/reset_time_window.png#inline)


## Activating Chart Display Modes
Charts support a few modes for controlling how data displays. You can display data in full precision mode, hide the hover legend, and display a fish-eye view. These features are enabled using  Shift, Ctrl, and Alt or Option hot keys.

### Full-Precision Mode
To display data in full-precision mode in the hover legend, hold down the **Shift** key and hover over any chart:

![full precision](images/full_precision.png)

### Hide Hover Legend
To hide the hover legend when hovering over a chart, hold down the **Ctrl** key. For charts that include a hover legend by default, you can permanently disable the hover legend under the Legend tab in the individual chart view.

### Fish-Eye View
When data streams are populated very densely, it can be hard to tell the exact value of each series. The fish-eye view expands the chart in the neighborhood of the cursor. To enable fish-eye view, hold down the **Alt** or **Option** key while you hover over a chart.

![fish eye](images/fish_eye.png)

When using this feature, the vertical and horizontal lines are preserved.
