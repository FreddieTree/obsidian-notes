```dataview
table 
    length(regexmatch("Key Point", file.content)) as "🟡 Key Points",
    length(regexmatch("Question or Critique", file.content)) as "🔴 Questions",
    length(regexmatch("Definition / API", file.content)) as "🔵 Definitions",
    length(regexmatch("How-To / Code", file.content)) as "🟢 How-To",
    length(regexmatch("Idea / Application", file.content)) as "🟣 Ideas",
    file.mtime as "🕒 Last Modified"
from "Zotero Notes"
where contains(tags, "zotero")
sort file.mtime desc

```


