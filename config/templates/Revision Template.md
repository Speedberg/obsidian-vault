<%*
const hasTitle = !tp.file.title.startsWith("Untitled");
let title;
if (!hasTitle) {
  title = await tp.system.prompt("Title"); // if there's not already a note title, prompt for one
  await tp.file.rename(title);
} else {
  title = tp.file.title; // if there's already a note title, use that
}
_%>
---
aliases: [<% title.toLowerCase() %>]
---

<% await tp.system.prompt("Enter tags:") %>
# Definition

# Flashcards

