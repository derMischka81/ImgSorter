<!-- README für GitHub (github.com/derMischka81/ImgSorter): Kopf mit Download-Links, Rest wie dist/README.en.md.
     Die Demo-GIFs liegen auf GitHub unter docs/ (hier: dist/ImgSorter-Demo_*.gif). -->
# ImgSorter
Sort photos and videos by drag &amp; drop into year/event folders. Reads dates from EXIF, video or filename, writes missing EXIF dates, fixes wrong camera clocks, detects duplicates, supports SMB and undo. Windows, Linux x64/ARM64.

![ImgSorter: drag photos onto a tile, check them in the conflict dialog, apply](docs/ImgSorter-Demo_en.gif)

*Demo in German: [docs/ImgSorter-Demo_de.gif](docs/ImgSorter-Demo_de.gif)*

## Download
Download the file for your system from the **[latest release](https://github.com/derMischka81/ImgSorter/releases/latest)** (or click a file name below):

| File | |
|---|---|
| [`imgsorter_x64-linux_GTK2`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_x64-linux_GTK2) | Linux 64 bit, GTK2 |
| [`imgsorter_x64-linux_Qt5`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_x64-linux_Qt5) | Linux 64 bit, Qt5 |
| [`imgsorter_x64-linux_Qt6`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_x64-linux_Qt6) | Linux 64 bit, Qt6 |
| [`imgsorter_x64-win64.exe`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_x64-win64.exe) | Windows 64 bit |
| [`imgsorter_arm64-linux_GTK2`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_arm64-linux_GTK2) | Linux ARM 64 bit (Raspberry Pi), GTK2 |
| [`imgsorter_arm64-linux_Qt5`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_arm64-linux_Qt5) | Linux ARM 64 bit (Raspberry Pi), Qt5 |
| [`imgsorter_arm64-linux_Qt6`](https://github.com/derMischka81/ImgSorter/releases/latest/download/imgsorter_arm64-linux_Qt6) | Linux ARM 64 bit (Raspberry Pi), Qt6 |

**ImgSorter** sorts photos and videos into folders by drag and drop: drop pictures onto a coloured tile – done. Optionally with year folders (from the capture date), event subfolders, network shares (SMB) and “Undo”.

### Which file?
Download just **one** file – it contains everything (translations, icon):
- **`imgsorter_x64-linux_GTK2`** – Linux, works on most systems
- **`imgsorter_x64-linux_Qt5`** – Linux, looks a bit nicer on KDE, needs Qt 5.15
- **`imgsorter_x64-linux_Qt6`** – Linux with Qt 6.8 or newer (e.g. Debian 13, KDE Plasma 6)
- **`imgsorter_x64-win64.exe`** – Windows
- **`imgsorter_arm64-linux_GTK2`**, **`_Qt5`** or **`_Qt6`** – Raspberry Pi 3/4/5 and other ARM computers with 64-bit Linux (e.g. Raspberry Pi OS 64-bit)

Runs on Linux on 64-bit PCs (x86_64) and 64-bit ARM (aarch64), and on Windows (64 bit). Not on a 32-bit Raspberry Pi OS – `uname -m` shows which one you have (`aarch64` works, `armv7l` does not).

### Requirements
- Linux, GTK2 version: GTK2, e.g. Debian/Ubuntu: `sudo apt install libgtk2.0-0`
- Linux, Qt5 version: Qt 5.15 – the Pascal bindings (`libqt5pas1`) are built in, also in the ARM version
- Linux, Qt6 version: Qt 6.8 or newer (e.g. Raspberry Pi OS “Trixie”) – the Pascal bindings (`libqt6pas6`) are built in, also in the ARM version
- Linux, optional: `smbclient` (network shares without mounting), `imagemagick` (previews for HEIC/WebP), `curl` or `wget` (check for updates), `exiftool` (write capture dates into JPEGs with EXIF), `ffmpeg` (read video capture dates, convert videos without a date such as MTS/AVI/MKV losslessly to MP4/MOV)
- Windows: nothing else – `curl` for “Check for updates” comes with Windows 10/11

### Start
**Linux:**
```
chmod +x imgsorter_x64-linux_GTK2
./imgsorter_x64-linux_GTK2
```
or make it executable in your file manager and double-click it.

**Windows:** double-click `imgsorter_x64-win64.exe`. If “Windows protected your PC” appears, click **More info** → **Run anyway** (the program is not signed).

### First steps
1. Click **☰** at the top right → **Options**.
2. Under **Drop areas** create tiles: name, destination folder (local or `smb://server/share/path`, on Windows also `\\server\share\path`), **Move** or **Copy**, optionally year and event subfolders.
3. Drag photos, videos or whole folders onto a tile (on Windows e.g. from Explorer).
4. If there is something to decide (file already at the destination, capture date missing or not fitting) or the tile creates event folders, a dialog shows all files at a glance: enter the event name, choose per file (**overwrite**, **Delete source**, **save under new name**, **do not transfer**) and click **Apply** – details in the user manual below.
5. Afterwards the tile shows **Undo** for about 30 seconds.

### Good to know
- **Language:** click the flag below ☰.
- **Launcher in the application menu (Linux):** Options → **Add launcher to menu**.
- **Updates:** Options → **Check for updates** – downloads the new version and restarts.
- **Passwords** for network shares are never saved, only kept in memory until the program exits. Settings: Linux `~/.config/imgsorter/imgsorter.ini`, Windows `%LOCALAPPDATA%\imgsorter\imgsorter.ini`.
- **Windows, share with a different user:** Windows allows only one user per server at a time. If the server is already connected with another user (e.g. as a network drive), Windows reports error 1219 – enter the same user there or disconnect the other connection.

### Problems?
Linux: if nothing happens on double-click, a library is usually missing. Start it in a terminal – it will tell you what is missing (e.g. `libQt5Widgets.so.5` → install Qt5: `sudo apt install libqt5widgets5t64` or `libqt5widgets5`, or use the GTK2 version).

### Support
Do you like ImgSorter? Then buy me a döner 🥙 – click the picture in the options or go directly to [paypal.me/dermischka](https://paypal.me/dermischka)

### Licenses
ImgSorter is built with [Free Pascal](https://gitlab.com/freepascal.org/fpc/source) and [Lazarus](https://gitlab.com/freepascal.org/lazarus/lazarus). Built in are the Free Pascal runtime library, the Lazarus components (LCL) and, in the Qt versions, the Pascal bindings for Qt (libQt5Pas/libQt6Pas, sources in the Lazarus tree under `lcl/interfaces/qt5` and `qt6/cbindings`). They are licensed under the LGPL with an exception that explicitly allows linking them into programs. Qt ([LGPL v3](https://www.qt.io/licensing/open-source-lgpl-obligations)) and GTK2 (LGPL) are not included: the program loads them from the system, where they can be replaced.

## User manual

### Usage

| Action | Effect |
|---|---|
| Drag files/folders onto a tile | Pictures are transferred (folders are searched recursively) |
| Right-click | Menu: Open target, Options, Always on top, Quit |
| ☰ at the top right | opens the options right away (narrow bar on the right – the window only gets wider, not taller) |
| Flag below ☰ | choose the language: Deutsch, English, Español, Français, Italiano, Polski (default English); also in the options |
| Double-click a tile | open the destination folder |

During a transfer the tile shows the progress (`Transferring 12/40`, `120.5 / 401.1 MB` and a bar,
also within large files). Further drops are queued.

#### Source on a share without write access

If the source is on an SMB mount (CIFS or gvfs) where the current user may not delete files, ImgSorter
asks for user, domain and password for this share the first time it is needed and deletes the source
via smbclient. Pre-filled is the user and domain last used successfully for this share – remembered in
the INI after a successful login (only user and domain, never the password) –, otherwise the one of the
drop area; if its password is already known, it is tried first without asking. If the password is wrong
or permission is missing, ImgSorter asks again. The password is only kept in memory until the program
exits. “Undo” and “delete empty source folder” use this login too. (Linux only.)

#### Empty source folder

If a source folder is empty after moving (no files left, not even hidden ones – helper files such as
Thumbs.db, ehthumbs.db, desktop.ini, .picasa.ini, .DS_Store, .directory do not count), ImgSorter asks
whether it should be deleted. For dropped folders this also applies to subfolders that became empty.
Only empty folders and the helper files in them are deleted, never other files; “Undo” recreates the folder.

#### Open target

If a tile has **year subfolders** or a **custom subfolder (event)** switched on, after an operation it
shows **↗ Open target** next to or above “Undo” for about 30 seconds. The link opens the folder the
files were just put into (with several year folders, the destination of the tile). Until the next
operation the tile's context menu also contains **Open target: <folder>**. For SMB destinations with a
“different user” the mount path is opened, otherwise `smb://…`.

#### Undo

After an operation the tile shows **↶ Undo** for about 30 seconds; until the next operation the command
is also in the right-click menu. After a confirmation

- moved files are moved back to their original location (with their original file date),
- source files deleted with “Delete source” are restored from the destination,
- copies at the destination are deleted – only if the original still exists unchanged,
- newly created year/event folders are removed if they are empty afterwards.

If another file now exists at the original location, nothing is overwritten. Overwritten destination
files cannot be restored (the confirmation points this out).

### Options per drop area

- **Name, colour**
- **Destination**: local or mounted path, `\\server\share\path`, `//server/share/path` or
  `smb://server/share/path`
- **Action**: Move or Copy
- **Year subfolders**: every picture/video ends up in `destination/YYYY/`. The capture date is taken from
  1. EXIF (JPEG, TIFF/RAW),
  2. the video header for MP4/MOV/3GP/M4V, for other video formats (MKV, WMV, AVI …) via `ffprobe`
     if ffmpeg is installed,
  3. the file name (`20240106_172854.mp4`, `IMG_20240106_…`, `PXL_…`, `2024-01-06 17.28.54.jpg`, also
     in day-month-year order such as `Nordbad 11_05_2009.mpg`, `06.10.2012`, `24-07-2015`),
  4. otherwise the file date.
- **Custom subfolder (event)**: when dropping, the conflict dialog always appears (see below), at the top
  with the event date (from the pictures) and the field **Event name**; the year follows from the date.
  Optionally with the date in front: `base folder/2026/2026-10-30 Event`. For pictures from several days a
  period is entered: `2024-07-16..26` (same month), `2024-07-30..08-02` (change of month),
  `2024-12-30..2025-01-02` (change of year). A whole year is possible too: `2019 in the garden` (then
  with an event name).
  **Default folder if no event fits** (per tile, e.g. `%YYYY in the garden`): if there is no event yet for
  the day or period of the pictures (pure year folders such as `2026 in the garden` do not count), the
  dialog is pre-filled with it (event date `2026`, name `in the garden`; without “Put the date before the
  event name” the whole `2026 in the garden` is the name) – Apply then puts the files into
  `2026/2026 in the garden`; you can still change it. Placeholders: `%YYYY` year with 4 digits, `%YY` with
  2 digits, `%MM` month with 2 digits, `%M` 1–2 digits, `%DD` day with 2 digits, `%D` 1–2 digits.
  If the dragged folder is already named “date + name” (e.g. `2012-06-10 on the balcony`, also a
  subfolder of it), **its date** is suggested – important for folders with videos only that have no
  embedded date (otherwise ImgSorter would take the copy date). With pure year folders such files go into
  the year from the folder name. Otherwise: if pictures have an EXIF date, plain file dates (e.g. the copy
  date) that are more than a month off do not count for the period.
  If a **folder** whose name is already “date + name” is dragged (e.g. `…/2009-01-02 Baby massage`, also a
  subfolder of it), the event name is pre-filled (`Baby massage`). For single files or several folders of
  different events the field stays empty.
  Existing folders whose date/period overlaps with that of the pictures are listed in the event name
  drop-down (e.g. pictures from 20 July → `2024-07-16..26 Vacation …`); choosing one takes over date and
  name. Changing the event immediately checks again whether files already exist there.
  If the pictures/videos contain a location (GPS from EXIF or video, e.g. Samsung, Apple), the **Map**
  button opens the place of the earliest picture in Google Maps in the browser.
- **SMB login with a different user**: user and domain (the password is not stored, see below)

General: layout of the tiles – **wide** (as many side by side as fit on the screen, as low as possible;
default), **square** or **fixed number of columns** –, tile size, always on top, allowed file types
(empty = all; default: common picture, RAW and video formats).

#### Check before dropping (conflict dialog)

Before moving/copying via a tile, ImgSorter checks all files. If there is something to decide – or the
drop area creates event folders (then the event name is chosen here as well) –, **one** dialog with all
files appears (otherwise the files are put away without asking):

- at the top **Source** (link: opens the folder in the file manager), **Destination** and the **event
  date** `YYYY-MM-DD .. YYYY-MM-DD` – editable; the suggestions follow it (empty = no event). For drop
  areas with event folders, next to it **Event name** (list: existing folders in this period) and **Map**;
  the destination shows the new path right away (with ⏳), it is checked 1.5 seconds after the last
  change – until then “⏳ Checking input shortly …” is shown and Apply is disabled (choosing from the list
  checks immediately); without a valid name or date Apply stays disabled,
- the **table**, one row per file, every column with a checkbox (clicking the checkbox in the column
  header toggles all, the space bar toggles the current cell):
  - **File** – unchecked, it is not transferred,
  - **Detected date** – the date ImgSorter found for the file, with its source: `EXIF`, `Video`
    (metadata in the video), `File name` or `File date`,
  - **Capture date** – is written (JPEG, MP4/MOV), for other files set as the *file date* or for videos
    *when converting*; double-click to change (`YYYY-MM-DD hh:mm:ss`, day only: the time stays),
  - **New file name** – combines renaming by date (`2014-02-04_00015.mp4`), the extension after converting
    and a free name if the name is already taken at the destination; double-click to change,
  - **Convert video** – MTS, AVI, MKV … losslessly to MP4 (or MOV),
  - **Target exists** – only if the file already exists at the destination: a drop-down list (click the
    cell) with **overwrite**, **Delete source** (not transferred, the source is deleted – e.g. if the
    picture is already at the destination; “Undo” brings it back), **save under new name** (suggestion
    `name (1).jpg`) and **do not transfer**; red until you choose. Clicking the column header: “All: …”
    for all such rows. In front of it, `=` stands for identical files (content compared, large files by
    samples) and `≠` for different ones; “Delete source” for different files is marked orange.
- on the right the **preview** of the selected row (picture or a frame from the video) with size,
  resolution, capture date and source of the date, camera, file date, note and destination; if the file
  already exists at the destination, source and target side by side (with size, resolution and date of
  the target file).

Colours: **red** = error or still to decide (name taken at the destination and not overwritten, two files
with the same target name, invalid input) – as long as there is red, **Apply** is disabled; **yellow** =
will be changed; **orange** = note without change (e.g. date does not fit, checkbox off). **Shift time …**
corrects a wrongly set camera clock for the selected rows (if only one is selected: all files of the same
camera). **To another event …** assigns the selected rows (otherwise the current one) to a different
event: the same dialog opens with event name and event date (pre-filled with the period of these files,
list of existing folders); after “Apply” they are transferred there – moved with “Test date/EXIF”, as set
in the tile when dropping –, and in the first dialog they are shown greyed out with “→ other event”.
There you then continue as usual. **Cancel** puts nothing away.

While the dialog is being prepared (with many files or videos and when comparing with existing target
files this can take a while), the tile shows the progress with a bar: “Reading capture dates”, “Checking
files”, “Comparing with target: x of y (z %)” – also with “Test date/EXIF” before the dialog of each
folder. When dropping, the files are read only once for this.

Whether a file already exists at the destination is checked in advance if the destination is readable
(local or mounted, also with “Use a different user”). SMB destinations without a mount show “cannot be
checked”; there, as before, the “file already exists” dialog asks during the transfer. Videos in a
different format at the destination are also still asked about during the transfer.

#### Pictures without capture date (EXIF)

If the dropped files include JPEGs without an EXIF capture date (e.g. scans, pictures saved from
messengers), the conflict dialog suggests a date: the date ImgSorter determines anyway (date in the file
name, otherwise the file date); if that does not fit the event, the event day with the time of the
picture (so the order stays right). DateTimeOriginal, CreateDate and DateTime are written – only in the
files at the destination, the sources stay unchanged. JPEGs without EXIF get an EXIF block; for JPEGs
with EXIF but without a date, ImgSorter adds the missing fields itself (without external programs), all
other data is kept. If the EXIF block is damaged or too full, the picture stays unchanged. Other formats
(PNG …) are not changed. “Undo” also works for files completed this way.

**Only add the date:** drag a folder onto a drop area whose destination is exactly this folder (with
events: choose the existing event folder). Files that are already at the destination are never compared
with themselves, moved or deleted – with the query above, the JPEGs without a date get their capture date
written directly into the file (locally and on SMB shares; the file date is set to the capture date).
Beforehand ImgSorter makes a backup in the temp folder; “Undo” puts back the original byte for byte.

#### Capture date does not fit the event (wrongly set camera clock)

When dropping into an event folder – or into a subfolder of it, even without event mode (e.g. destination
`…/2006-06-02 Birthday party/Conny`; what counts is the nearest “date + name” folder in the destination
path) – ImgSorter also checks JPEGs that already have an EXIF capture date: if it lies outside the event
period (from midnight of the first day until 6 a.m. after the last day – so parties past midnight still
fit; for `2019 in the garden` the whole year), the camera clock was probably set wrong. The conflict
dialog then suggests the first event day (the time of each picture stays). **Shift time …** opens the
familiar dialog for the camera (EXIF make/model) or the selected rows:

- **Set the event date, keep each picture's time** (pre-filled with the first event day), or
- **shift all by the same amount**: choose a picture (with thumbnail and path as a link to the file
  manager) and enter its correct time (`YYYY-MM-DD hh:mm`) – all pictures are shifted by the same amount,
  the intervals between the pictures stay. The result is shown immediately.

It is written as above (DateTimeOriginal and CreateDate, the modification date stays), only at the
destination or, with destination = source, directly in the file with a backup and “Undo”. A date
`0000:00:00 00:00:00` (camera clock never set) counts as a missing date and ends up in the query for
pictures without capture date.

#### File date does not fit the capture date

Important above all for the timeline in Immich: it uses the embedded capture date (EXIF or video
metadata) and only if there is none, the file date. That is why ImgSorter checks the file date
(modification date) only for files without an embedded capture date – PNG/GIF/BMP, JPEG without EXIF
(if none is written), videos without a date – and compares it with the date in the file name. If an EXIF
date is written or corrected, the file automatically gets the same file date (locally, via
`smbclient utimes` and with destination = source; “Undo” restores the old one). Typical case: all files
carry the date on which they were once copied (e.g. 14 January 2020). Differences of up to 2 minutes
(videos: up to 3 hours later, the file date is the end of the recording) count as fitting. Files without
a capture date only count with events if their file date lies outside the event period; they get the
event day, the time stays.

If files differ, the suggestion is shown in the conflict dialog (column Capture date, “File date”). The
file date is set only at the destination – locally directly, on SMB shares via `smbclient utimes` (there
also the creation date), on Windows the creation date as well. With destination = source only the date of
the file itself is changed; “Undo” sets the old date again.

#### Videos: read, write and convert the capture date

For Immich & co. the capture date embedded in the video counts. ImgSorter therefore treats videos by what
they are, not by their extension:

- **Reading:** ImgSorter reads MP4/MOV/M4V/3GP itself, all other formats (MKV, WMV/ASF, AVI with IDIT …)
  via `ffprobe` (`creation_time`) if ffmpeg is installed. This way the event period and year folders are
  right as well.
- **MP4/MOV/M4V/3GP without or with a wrong date** are treated like JPEGs: they appear in the “Capture
  date missing” query or in the “capture date does not fit the event” dialog (group “Videos”, e.g. for
  videos carrying the date of a later conversion). The date is written directly into the file – with
  `exiftool` into all date fields, without exiftool into the time fields of the file header (the size
  stays the same).
- **Videos without a date that ImgSorter cannot write to** (MTS/M2TS, AVI, MKV, MPG, MOD/TOD, VOB,
  FLV, DV …): in the conflict dialog “Convert video” and “New file name” – `00015.MTS` becomes
  `2014-02-04_00015.mp4` or (conversion unchecked) `2014-02-04_00015.mts`. Picture and sound are only
  repackaged (`ffmpeg -c copy`), subtitle tracks are dropped. Formats that do not fit well into MP4
  (PCM/ADPCM sound, MJPEG, DV – typical for AVI from old digital cameras) become lossless **MOV**; only if
  that does not work either is the sound converted to AAC. The new file gets the date as `creation_time`
  and as file date; before replacing, ImgSorter checks the duration (ffprobe, at most 1 s difference).
  Without ffmpeg only renaming is offered.
- **Such videos with a wrong date** (e.g. MKV) are also corrected via the “does not fit the event”
  dialog – by repackaging into MP4/MOV with the new date.
- If the name starts with a date in ImgSorter's scheme (`2020-01-14_00005.mp4`), this date in the name is
  adjusted as well when correcting (`2012-06-10_00005.mp4`).

Date for the name: the corrected file date, otherwise a date in the file name, otherwise the file date. If
the date is already at the start of the name, the name stays (only the extension changes).
When moving and with destination = source the original is replaced; beforehand ImgSorter makes a backup in
the temp folder (progress in the tile) and converts from this local copy – so the source, e.g. on the
NAS, is read only once. “Undo” brings back the original byte for byte and deletes the new file. When
copying, the source stays. On SMB destinations the new file is created locally and uploaded; with
destination = source on the share, the original is deleted (or renamed via `rename`) only after a
verified upload.

Uploaded files keep their file date on SMB shares (`smbclient put` alone would set the upload time –
Immich would use it for files without an embedded date); “Undo” also puts files back into the source with
their original file date.

#### Test date/EXIF (context menu of the tile)

For drop areas with “date before event name”, the right-click menu of the tile contains **Test
date/EXIF …**. ImgSorter then counts the files in the background and goes recursively through the
destination (in the tile: “x of y”, percent, bar and estimated remaining time; cancel via the link
“✕ Cancel” in the tile or the context menu) and checks all event folders with a day or period in the name
(`2006-06-02 Party`, `2024-07-16..26 Vacation`; subfolders such as `…/Party/Conny` belong to the event
above, pure year folders are skipped). If the drop area creates year folders, only the year folders
(`2019`, `2020` …) are searched in the destination – folders such as `_incoming` next to them are left
out. Checked are:

- JPEGs without an EXIF capture date and MP4/MOV without a date (“no date”),
- capture date (EXIF or in the video) outside the event period, with camera or “Videos”,
- videos without a date that can be converted or renamed (“Video”),
- file date for files without an embedded capture date (rule as above).

The report lists the folders with differences (“Copy report” puts it tab-separated on the clipboard). For
the selected folders, the conflict dialog appears for each folder (a double-click on a row corrects exactly
this folder). If not the capture date but the folder name is wrong (e.g. pictures from the evening
before), change the event date there: then **Rename folder** is offered (pre-selected, can be unchecked;
disabled if the name already exists). Next to it is the **Event name** (pre-filled with the previous one,
editable – e.g. `2012-08-09 to 11 Visit to the Kozas` becomes `2012-08-09..11 Visit to the Kozas`); you can
also change only the name this way. The folder is renamed after the changes to the files – locally or via
`smbclient rename` –, with “Undo” and an entry `RENAME` (info `folder`) in the log. In the report that
appears again there are **↗ Open last folder** (the last corrected one, under its new name if renamed) and
**↶ Undo**: takes back the last correction (renaming and files together), after which the folder is in the
list again.

**Save report …** saves the report as a file (`Datumstest <tile> <date>.imgcheck`, all checked folders
including files, plus tile, destination, year/event folders, “date before event name” and file types). Via
the tile menu **Load date/EXIF test …** you can continue later without a new check – but only if tile and
settings are still the same; otherwise a message names the differences. Folders and files that no longer
exist are dropped when loading. While loading, the tile shows the progress (“Loading report: x of y”); the
content of each folder is read only once. Corrections are made directly in the files (destination =
source), with “Undo”. Afterwards the report appears again – without the processed folders –, so you can
work through the folders one by one until “Quit”. Local and mounted destinations are checked (with “Use a
different user”, writing is done via SMB, with a password prompt).

**Immich:** if a capture date is written or corrected, the file also gets the same date as its file date.
This changes the file date, and the next scan of the external library reads the metadata again.

#### Log

Every action on a file is written as one line to `imgsorter.log` next to the configuration
(Linux: `~/.config/imgsorter/imgsorter.log`). The file is only appended to and **never deleted
automatically**; in the options (group “Log” below the drop areas) there are **Open log** and **Delete log**
(with confirmation). Fields are separated by tabs (paths with spaces stay unambiguous):

```
2026-11-21 11:30:12	/srcfolder/filenamea.jpg	COPY	/dst/folder/2004-11-01_filname.jpg
2026-11-21 11:31:40	/srcfolder/movie.mts	CONVERT	/dst/folder/2001-11-01_movie.mp4	MOVE
```

Actions: `COPY`, `MOVE` (info `überschrieben` if a target file was replaced), `CONVERT` (video
repackaged; info `MOVE`/`COPY` or `Original ersetzt`), `RENAME`, `DATE` (capture date written, info =
date), `FILEDATE` (file date set), `DELETE` (source deleted, e.g. “Delete source” in the conflict dialog),
`UNDO-MOVE`/`UNDO-COPY`/`UNDO-DELETE`/`UNDO-DATE`/`UNDO-FILEDATE`/`UNDO-CONVERT`/`UNDO-RENAME`
(undo: from → to) and `ERROR` (message in the info field). Destinations on SMB shares appear with the
mount path if there is one, otherwise as `//server/share/path`.

#### File already exists at the destination

If the destination is readable in advance, this is decided in the conflict dialog (overwrite, new name or
uncheck the file). Otherwise – SMB destination without a mount, or the file appeared only after the check –
a query with size/date of source and target appears during the transfer. If the files differ and they are
pictures (JPEG, PNG, GIF, BMP, WebP, HEIC/AVIF, TIFF/RAW), the resolution is shown as well (e.g.
“4032 × 3024 px”), and the note mentions a lower/higher resolution of the target. For SMB destinations
without a mount, the target file is briefly downloaded to the temp folder for this (up to 64 MB).
For pictures the dialog also shows small thumbnails of source and target (EXIF rotation is taken into
account). ImgSorter reads JPEG, PNG, BMP, GIF and TIFF itself, for RAW files (CR2, CR3, NEF, ARW, DNG, ORF,
RW2, RAF, PEF …) the embedded preview. HEIC/WebP/AVIF use ImageMagick on Linux if it is installed; on
Windows they come – like videos – from the Explorer preview (HEIC with the “HEIF Image Extensions”, RAW
also with the “Raw Image Extension”).

- **Overwrite destination**
- **Delete source** – not transferred, the source file is deleted (e.g. if the picture is already at the destination)
- **Do nothing** – source and target stay unchanged (default with Enter)
- **Cancel** – the rest of the operation is cancelled
- **Save under new name** – the source is saved under a free name (suggestion “name (1).jpg”, editable in
  the field “New name”; if that is taken too, ImgSorter asks again)

**Videos in a different format:** if a video with the same name but a different extension already exists
at the destination (e.g. `clip.mkv` for `clip.mp4` – probably transcoded, source e.g. from a backup),
ImgSorter asks as well: **Add anyway** (keep both), **Delete source** (cannot be undone, as only the
transcoded version is at the destination), **Do nothing**, **Cancel**. “For all” then only applies to
further videos in a different format.

With “Use for all further …” the choice applies to the rest of the drop – but only for conflicts of the
same or a safer kind. The files are still compared:

- ticked for **identical** files (“Use for all further identical files …”): applies only to further
  identical files; for a different file ImgSorter asks again,
- ticked for **same size** (SMB without content comparison): applies to identical and same-size files,
  not to different ones,
- ticked for **different** files: applies to all further conflicts.

#### Examples

- *Electricity meter*: destination `/data/house/electricity_meter`, Move, no subfolders
- *Trips*: destination `smb://nas/photos`, year folders + event + date in front →
  `smb://nas/photos/2026/2026-10-30 Trip to the Harz`

### SMB destinations

**Linux**: access runs via `smbclient` (`sudo apt install smbclient`).
- The login data is passed to smbclient via a temporary file (permissions 0600, deleted afterwards) –
  the password does not show up in the process list.
- Without “different user”, ImgSorter first connects without a password (guest/Kerberos). If the share
  requires a password, it is asked for the current user.
- Mounted shares (fstab, `/run/user/1000/gvfs/...`) can simply be entered as a local path.
- After uploading, every file is checked via `ls` for existence and size; only then is the source
  deleted when moving.

**Windows**: the destination is used as a UNC path (`smb://server/share/path` and `//server/share/path`
become `\\server\share\path`); copying, checking and deleting work through the file system as with local
destinations. With a different user, a temporary connection is set up first. Note: Windows allows only
one user per server at a time (error 1219).

#### Passwords

Passwords are **never stored**. On the first access to a server the password is asked for and kept in
memory until the program exits (per server + user). If the password is wrong, ImgSorter asks again and
repeats the operation.

### Configuration

`~/.config/imgsorter/imgsorter.ini` (Windows: `%LOCALAPPDATA%\imgsorter\imgsorter.ini`) – contains no
passwords.
