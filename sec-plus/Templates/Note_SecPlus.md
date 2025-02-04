<%*
let title = await tp.system.prompt("Title")
await tp.file.rename(title)
let topic = await tp.system.prompt("Topic Tag")
let subTopic = await tp.system.prompt("Sub-Topic Tag")
tR += "---"
%>
tags:
topic: "<% topic %>"
subTopic: "<% subTopic %>"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_<% subTopic %>" 
cert: "Sec+"
---
# <% title %>
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

