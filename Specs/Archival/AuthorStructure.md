# Structuring Authors Directory

Each Author receives 1 folder in `Artistic_Setup` or `MIDI`. These folders will contain the files created or last held by the "author" who had or made the file.

How would each folder looks like as follows

- Links List, `link.txt`
  - Lists sauce URL where the file was downloaded from
  - Sometimes traces other URLs that lead to the target sauce URL
  - May have extra Links List, e.g. due to different disk & branch maintenance works, so you can see e.g.
    - `link.txt`
    - `link75498234759275893427589.txt`
    - `link383883883883.txt`
    - and so on, with differentiator filename just so no other list gets overwritten destructively.
- Notification File / Folder. A meta file to notify Kolmo maintainers about the author and special cases.
  - `.PAID`. Files acquired by buying it, subcribing to something, or exclusive invite. A legal notification
    - Always set to hidden with prepending `.` so that it not get indexed to sparsdat.
    - Unless if it's gone, the file will no longer set to hidden, i.e. remove `.` into `PAID-NOHIDE`.
  - `ISGONE`. One, more, or entire of the files belonged to this author, are **GONE!!!**
    - Maintainer must remove `hidden` & prepending `.`, & explicitly add `*-NOHIDE` to all legal notifications.
    - Firstly, make sure before doing this, it won't put any of us into an immediate litigation.
  - `NOTORIOUS`. The author is being notorious and toxic, granting that all files must be shared and/or specially taken care of.
    - There are subtypes of this, such as
      - `EMAIL`. Require subscription with email address just to get it, or put behind a shopping system (**which asks you full house address**). Used only if the file supposedly gratis to download
        - You could get spammed to explosion, especially if the sign-up form is deliberate.
        - Also known as
          - `SUBSCRIBEMAIL`
      - `JOIN`. Require joining forum just to access and download, especially Discord (max 100 on free tier).
        - Also known as
          - `MUSTGUILD`. Explicitly tells that you must join walled garden community like Discord
      - `BEER`s. The file is no longer gratis, such as
        - `BEERCANCELED`. Author made files free (old or new), but then paywalls it again afterward without even telling discount promo whatsoever. Not to be confused with Free for Limited Time (explicitly told discount).
        - `BEERPOISONED`. Author paywalls newer file, but kept the old file $0. Note, both BEERDRAINED & BEERPOISONED can be applied if both new file paywalled & also old files repaywalled
        - `BEERDRAINED`. Not to be confused with TRAITOR. Author repaywalls old files previously $0. May not mean paywalls newer files
      - `TRAITOR`. author resigns from Kolmorotzet, & asked all files removed from kolmorotzet. Kolmorians are granted to contribute force reupload, but Master Kolmo himself may not be able to do so, for safety reason.
        - Source code becomes proprietary, any mean not allowing reuploading source code even you may see it.
      - `ULTILOCK`. There are archive files or Sauce URL without key password provided.
      - `ANTIARCHIVE`. There are files sourced from Cloud Storage that are typically hard to automatically crawl into preservation without special intervention required.
      - `MEATPROXY`. Author is known for not drawing anything themselves, but outsource everything they do to somebody else.
        - Generate xyz using AI prompter.
        - Too few self-drawn files, Moar commission into somebody else instead.
        - No label if there's abundant amount self-drawn files without outsource nor AI.
        - But the label may stick permanently, if e.g.,
          - despite you code everything (AI-assist only or pure hand) yourself,
          - you used AI for the skin & upscaling, **So obvious!**
  - `JUSTSPREADPLS`. Explicit order from high order of Kolmorottzzet, to just sparsdat and spread everything inside this Author folder. **Rarely used**, sparsdat order are given only with clear reason. Unless, if the author is one of the high order themselves including Joel Sensei (`Joel Robert Justiawan`), which in that case, **you definitely should help preserve our own files too**.
  - `AMEMBER`. The author is a member of X0p1r4t3 Eenvrnsmnt! Horray!!!
    - They are already agreed to
      - Files to be reuploaded elsewhere, for the preservation sake.