<%*
const hasTitle = !tp.file.title.startsWith("Untitled");
let title;
if (!hasTitle) {
  title = await tp.system.prompt("Title");
  await tp.file.rename(title);
} else {
  title = tp.file.title;
}
_%>

---
tags: <%*
let tag = "";

tR += "["

while(tag != null)
{
	tag = await tp.system.suggester(item => item, Object.keys(app.metadataCache.getTags()).map(x => x.replace("#", "")))

	if (tag == null)
		break;
	
	tR += tag + ","
}

tR += "]\n"
_%>
aliases: <%*
let alias = "";

//Add lowercase note name to aliases
tR += "[" + title.toLowerCase() + ","

while(alias != null)
{
	alias = await tp.system.prompt("Enter an alias:")

	if (alias == null)
		break;
	
	tR += alias + ","
}

tR += "]\n"
_%>
---
# <% title %>