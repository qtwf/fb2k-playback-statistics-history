# Play Statistics History Viewer

View playback history of your tracks directly within the audio player [foobar2000](https://www.foobar2000.org/) with charts powered by [Chart.js](https://github.com/chartjs/)

<img width="1020" height="896" alt="p-s-h" src="https://github.com/user-attachments/assets/91f107d6-1f79-43df-b21e-0cf79a659ab8" />

The data is referenced from records by the components [foo_enhanced_playcount](https://github.com/kbuffington/foo_enhanced_playcount) (w/ foo_playcount), [foo_statistics](https://github.com/stuerp/foo_statistics), and [foo_skipcount](https://github.com/Fjara-h/foo_skipcount/).


### Environment
- Windows 10/11 (w/ Microsoft Edge)
- foobar2000 64-bit


## Setup

At least one from each category below is required to make use of this feature.

- **Aggregation**
  - foo_playcount and foo_enhanced_playcount
  - foo_statistics by stuerp (not to be confused with [foo_statistics](https://www.foobar2000.org/components/view/foo_statistics) by grimes)
  - foo_skipcount

- **Rendering**
  - foo_webview2

- **Access**
  - (access WebView directly from context menu)
  - foo_ui_columns
  - foo_flowin <!--(optionally with foo_spider_monkey_panel)-->


Follow the steps below to install this feature in foobar2000.

⚠ Caution: Before applying any modifications to foobar2000, **CREATE A BACKUP** of the `profile` folder in case of potential data corruption during modification.

---

### 1. Install Required Components

Download and install the following components via menu `[File] > [Preferences] > [Components] > [Install...]`:

#### Aggregation
Install at least one of the following play statistics providers:

- [foo_playcount](https://www.foobar2000.org/components/view/foo_playcount) + [foo_enhanced_playcount](https://www.foobar2000.org/components/view/foo_enhanced_playcount)
- [foo_statistics](https://www.foobar2000.org/components/view/foo_ui_columns)
- [foo_skipcount](https://www.foobar2000.org/components/view/foo_skipcount)

#### Rendering
Install the WebView component used to render charts.

- [foo_webview2](https://www.foobar2000.org/components/view/foo_webview2)

#### Access (choose an option)

To open the viewer conveniently inside foobar2000, install one of the following UI integrations.

- **Option A — Popup window via context menu**
  - Access the WebView panel directly via the context menu `[View] > [WebView2]`.
  - For users who have no other WebView templates/components utilized.

- **Option B — As a Columns UI Panel**
  - Access and display directly in the main window 
  - [foo_ui_columns](https://www.foobar2000.org/components/view/foo_ui_columns)

- **Option C — Popup window via context menu toggle**
  - For users who have other existing WebView templates/components
  - Access via the context menu `[View] > [Flowin] > [<WebView instance>] > [Show]`
  - [foo_flowin](https://github.com/ttsping/foo_flowin/releases)
<!--
- **Option D — Popup window via in-window toggle**
  - Option C that includes quick toggle within the main window
  - [foo_flowin](https://github.com/ttsping/foo_flowin/releases)
  - [foo_ui_columns](https://www.foobar2000.org/components/view/foo_ui_columns)
  - [foo_spider_monkey_panel](https://github.com/marc2k3/spider-monkey-panel-x64/releases)
-->
After installing components, restart foobar2000.

---

### 2. Install the Viewer Files

1. Download or clone this repository.
2. Place the HTML/JS files in a location accessible to foobar2000, for example:

```
└─[foobar2000]
  │ 
  ├─ (...)
  ├─ foobar2000.exe
  └─[profile]
      │ 
      ├─ (...)
      └─[foo_uie_webview]
          │ 
          ├─[EBWebView]
          ├─ play-statistics-history-externals.js
          ├─ play-statistics-history.html
          └─ (...)
```
---

### 3. Configure WebView

#### Option A
1. Navigate to menu `[File] > [Preferences] > [Display] > [WebView]` panel.
2. (proceed to [Set WebView template](#set-webview-template) below)

#### Option B
1. Enable Columns UI panel editing via menu `[View] > [Layout] > [Live Editing]`
2. Create a panel as WebView2 by right-clicking beside the panel you want to place the viewer.
3. Select the option `[Add <before|after>] > [Panels] > [WebView2]`
4. (proceed to [Access WebView config menu](#access-webview-config-menu) below)

#### Option C
1. Create a popup instance config via menu `[View] > [Flowin] > [New Flowin]`
2. Right-click within the new popup window and select `[Add new UI element...]`
3. Find and click `WebView2`, then click [OK]
4. Within the same popup window, follow the next step below

#### Access WebView config menu
- Right-click within that new panel/window and select `[WebView2] > [Preferences]`

#### Set WebView template
- Find "Template file path" input box and click the `[...]` button beside it.
- Set the source to the local `.html` file. For example:

```
C:\foobar2000\profile\foo_uie_webview\play-statistics-history.html
```

Apply and close Preferences.

---

### 4. Open the Viewer

Select or play a track in your library or playlist, then open the viewer using your configured method:

- **Option A**: Navigate to menu `[View] > [WebView2]`
- **Option B**: (should be displayed in front of you already)
- **Option C**: Navigate to menu `[View] > [Flowin] > [<WebView instance>] > [Show]`
<!--
- *Option D*: Click on the created panel script button
-->
The viewer will automatically read available statistics and generate the charts.

---

## Notes

- Charts are generated using [Chart.js](https://www.chartjs.org/)
- The amount of historical data available depends on the installed statistics component
- If no data is shown, verify that playcount tracking is enabled and that tracks have existing play history


## Troubleshooting

**WebView panel errors**
- Make sure Microsoft Edge (WebView2) is installed 
- Verify the WebView panel config path points to the correct `play-statistics-history.html`

**Other stuff**
- Make a repository issue
