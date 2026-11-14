---
last_updated: 2026-11-13
product_versions:
  android: "0.2.0"
  windows: "0.1.0"
---

# Plain JSON User Manual

Plain JSON is a read-only viewer for JSON, JSON Lines, and JSON with Comments on
Windows and Android. Files are read locally and are never edited by the viewer.
JSON is free and JSON Lines needs full access. JSON with Comments is free on
Android and needs full access on Windows. See [Licensing](#licensing).

## Install and launch

### Windows

No public download of Plain JSON for Windows is available yet, so this manual
gives no installation steps for it. The Windows instructions in the rest of this
manual describe version 0.1.0.

### Android

Install Plain JSON from
[Google Play](https://play.google.com/store/apps/details?id=com.plaintxtoffice.plainjson).
It requires Android 7.0 or later.

Launch **Plain JSON** from your device's app launcher, or choose **Plain JSON**
when opening a `.json`, `.jsonl`, `.ndjson`, or `.jsonc` file from your device's
Files app.

## Inspect a document

1. On Windows, choose **File → Open** or press **Ctrl+O** and select a supported
   file. On Android, tap **Open** in the top bar and pick a supported file.
1. Expand objects and arrays in the tree. The columns show key or index, JSON
   type, and a short value preview.
1. Select an entry to see its bracket path above the text panel. The
   **Selected value** tab shows its JSON representation. On narrow Android
   screens, switch between **Tree** and **Source & Value** tabs or tap **View**
   next to the path bar.
1. Use **Original source** to inspect the file's text, including comments.
1. Choose **Edit → Copy path** or **Edit → Copy value** on Windows, or tap
   **Copy path** or **Copy value** on Android, to copy the selected entry to the
   system clipboard.
1. On Windows, use **Edit → Find** or **Ctrl+F** to focus the text search, then
   press **Enter**, **F3**, or **Find next**. On Android, tap **Find** or choose
   **Menu → Find…**, enter your search text, and tap **Find next**. Search
   covers the active text tab and wraps at its end.
1. Use **File → Reload** or **Ctrl+R** on Windows, or tap **Reload** on Android,
   to reread the current file after editing it in another application.

Trees load 200 children at a time. On Windows, double-click **Load next 200** or
select it and press **Enter**; on Android, tap **Load next 200** to reveal more
children. Array and JSONL record indices start at zero. JSONL error messages use
one-based physical line numbers.

The selected path starts with `$`, meaning the root of the document. For
JSONL, `$` represents all records, `$[0]` is the first record, and
`$[0]["answers"]` is that record's `answers` field. Paths are navigation labels
provided by the viewer, not text added to your file.

Use **View → Collapse all** on Windows or **Menu → Collapse all** on Android to
fold the tree. **Help → Using Plain JSON** (**F1** on Windows, or
**Menu → Using Plain JSON…** on Android) opens an offline guide to navigation,
formats, shortcuts, and limits. **About Plain JSON** describes the app. On
Windows, **File → Exit** (**Ctrl+Q**) closes the viewer, waiting for any active
read to finish.

## Work with JSON Lines records on Android

When a `.jsonl` or `.ndjson` file is open, the Android menu has three commands
for its records:

- **Go to record…** shows the record with the number you enter and selects it.
  Records are numbered from 0, so enter 0 for the first record and 9 for the
  tenth. Tap **Load previous 200** or **Load next 200** to see the records
  around it.
- **Filter records…** keeps only the records that contain your text. It
  searches every record in the file as written, ignoring upper and lower case,
  and the message above the tree shows how many match. Records keep their
  original numbers. Choose **Menu → Clear filter** to show all records again.
- **Record fields…** lists each top-level field, how many records have it, and
  the JSON types it holds, most common first.

Without full access these commands cover the 50 records in the preview. With
full access they cover the whole file.

## Send feedback

On Android, choose **Menu → Send feedback…**, then **Report a bug** or
**Request a feature**. Your email app opens a message to
`support@plaintxtoffice.com` with the app version, Android version, and device
model filled in. Nothing is sent until you send it, and you can edit or remove
anything first. If no email app is installed, the address is copied to the
clipboard instead. If you attach a file, remove anything private from it first.

The same dialog has **Open contact form**, which opens
<https://plaintxtoffice.com/contact/> in your browser so you can write to us
without an email app. If no browser is installed, the link is copied to the
clipboard instead.

The Windows app has no feedback command. On Windows, use the contact form at
<https://plaintxtoffice.com/contact/>.

## Privacy on Android

Choose **Menu → Privacy…** to read what the app reads, stores, and sends: your
files, the full access purchase, feedback, and removing data. **Contact Plain
Text Office** at the end opens the contact form in your browser.

## Licensing

Full access is a one-time purchase with no subscription, and it does not
expire. On Windows it is a **$19.99** license key. On Android it is a **$9.99**
in-app purchase through Google Play, which may show the price in your currency.

| | Free | Full access |
| --- | --- | --- |
| `.json` | Full file, up to 20 MiB | Full file, no size limit |
| `.jsonl`, `.ndjson` | First 50 records | Full file, no size limit |
| `.jsonc` on Android | Full file, up to 20 MiB | Full file, no size limit |
| `.jsonc` on Windows | First 50 lines, top-level keys only | Full file, no size limit |

In a JSON with Comments preview on Windows, nested objects and arrays appear as
locked rows that show their size but not their contents. A message above the
tree appears whenever a preview leaves part of a file out.

On Windows, choose **Help → Enter license key**, paste your key, and choose
**OK**. Plain JSON checks the key on your computer without going online, and
your key holds no personal details.

On Android, choose **Menu → Unlock full access…** and complete the purchase in
Google Play. The purchase stays with your Google account, so it returns when
you reinstall the app or change phones, and it keeps working offline.

Either way, the open file reloads in full.

A build of Plain JSON that leaves out the paid formats opens `.json` files
only, so it shows no previews and has no **Enter license key** or
**Unlock full access** command.

## Supported formats

| Extension | Behavior |
| --- | --- |
| `.json` | Strict JSON; objects, arrays, and scalar roots are supported. |
| `.jsonl`, `.ndjson` | One JSON value per physical line, displayed as a record array. |
| `.jsonc` | JSON with `//` line comments, `/* block comments */`, and optional trailing commas. |

Numbers retain their original spelling and precision, including large
integers and decimal exponents. Duplicate object keys, `NaN`, and `Infinity`
are rejected rather than silently changing the displayed meaning. JSONC does
not accept other JSON5 features such as single-quoted strings or unquoted keys.

JSONL requires a value on every line; blank records are errors. A final line
ending is accepted. Files must be UTF-8; a leading UTF-8 byte-order mark is
accepted for convenience with Windows-generated files.

These choices follow [JSON Lines](https://jsonlines.org/) for record
boundaries. Trailing commas are an explicit viewer extension to the
[JSONC specification](https://jsonc.org/trailingcommas.html).

## Limits and errors

- Without full access, files may be up to **20 MiB**. JSON Lines previews are
  the exception: they read only the start of the file, so any size can be
  previewed.
- With full access on Android, JSON Lines files of any size open. Plain JSON
  checks every record once while opening, then keeps only the records on screen
  in memory, so a very large file takes longer to open but does not run out of
  memory. A file from a source that cannot be read at any position, such as
  some cloud storage, is loaded whole instead.
- For other files with full access, and for all files on Windows, the size
  limit is your device's memory. Plain JSON loads the whole document into
  memory, so a log-style file can need about **12 times its size** in memory:
  about 1.3 GiB for a 100 MiB file. A file that does not fit shows an error.
- Source and selected-value text panels show at most **200,000 characters**.
  Truncated previews are labeled. **Find** covers displayed text only; on
  Android, **Filter records…** searches a whole JSON Lines file.
- On Android, if a JSON Lines file changes while it is open, records read
  afterwards may show a message asking you to reload. Tap **Reload**.
- **Copy value** refuses a truncated selection; select a smaller entry first.
  A copied object or array uses compact JSON without JSONC comments. Copying
  the JSONL root produces a JSON array of records.
- Excessively deep nesting is rejected with a readable error.
- **File → Cancel load** on Windows or **Cancel load** on Android discards the
  result after the current read and parse finish.
- Parsing and file errors appear above the tree. If another document was
  already open, it remains visible. Fix the indicated file and open it again,
  or use **Reload** for the current document.
