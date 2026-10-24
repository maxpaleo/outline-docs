---
created: 2026-10-23T17:01:08.351Z
updated: 2026-10-23T17:01:08.351Z
---
Let's discuss the below. These are some changes I think we should make or discuss before publishing these new articles.



---

# /notes/elements

I see that we currently list all of the elements in a table, but I think that we can maybe expand this a little bit.

Maybe use an H1 For Core elements and More elemetns.&#32;

And then for each element title an h2.&#32;

And we can then have a description of each element under the element title, with potentially also a direct example of the element, which we can maybe show like in a screenshot or something.



<!-- outline:block id="img_8fe46248-4d8" type="image" version="1" assetId="Attachments/Screenshot 2026-10-23 at 7.05.51 PM.png" src="Attachments/Screenshot 2026-10-23 at 7.05.51 PM.png" alt="Screenshot 2026-10-23 at 7.05.51 PM.png" -->
![Screenshot 2026-10-23 at 7.05.51 PM.png](<Attachments/Screenshot 2026-10-23 at 7.05.51 PM.png>)
<!-- /outline:block -->



# /notes/tables

<!-- outline:block id="img_0e3f02f1-64b" type="image" version="1" assetId="Attachments/Screenshot 2026-10-23 at 7.02.15 PM.png" src="Attachments/Screenshot 2026-10-23 at 7.02.15 PM.png" alt="Screenshot 2026-10-23 at 7.02.15 PM.png" -->
![Screenshot 2026-10-23 at 7.02.15 PM.png](<Attachments/Screenshot 2026-10-23 at 7.02.15 PM.png>)

I think that a table to show the column input types is a bit unnecessary. I think we can just use a bullet list with the data type and then an example use or description.
like:
- Text - A text type value 
<!-- /outline:block -->

I also don't think it's necessary to mention what a link should be used for. I mean, it's pretty obvious. I think it's unnecessary to add this in the notes. Also, I think image URL. I don't really think it needs like an explanation in the content and we also can remove the text that is describing older tables. Any legacy stuff should be removed because



# /notes/create-a-note-from-a-template

This is good, but let's maybe add a placeholder screenshot for a screenshot that shows the modal to select templates.



&nbsp;

&nbsp;

# /notes/excalidraw-with-ai-agents

This page currently contains this section that says use outline AI Chad, which like describes how to use the ask or agent mode, but I think that this is not really supposed to be here. I think that this article should be specifically for using Exceli draw with AI agents and should be shorter.

The difference between ask and agent mode is already mentioned in: [Starting an ai chat — localhost](http://localhost:3011/docs/v0/ai/starting-an-ai-chat)

<!-- outline:block id="img_200f3f07-282" type="image" version="1" assetId="Attachments/Screenshot 2026-10-23 at 7.14.17 PM.png" src="Attachments/Screenshot 2026-10-23 at 7.14.17 PM.png" alt="Screenshot 2026-10-23 at 7.14.17 PM.png" -->
![Screenshot 2026-10-23 at 7.14.17 PM.png](<Attachments/Screenshot 2026-10-23 at 7.14.17 PM.png>)
<!-- /outline:block -->



&nbsp;

&nbsp;

# /ai/starting-an-ai-chat

This looks like it's the main article for in-app AI chats, right? So I think that we can maybe add one or 2 screenshot, placeholders here. The 1st one can maybe show like an active AI chat, and the 2nd one can maybe be like more specific.



# /spaces/choose-where-attachments-are-saved

This article is currently under spaces, but I think this should go in advance. I mean, regular users don't have to know this.

We can add a code blog here to show the configuration because choosing where the attachments are saved requires the user to. Update the space that Jason, right? Or I guess you can also do this from the settings. So, Okay, so maybe what we should do is divide this article into 2 sections. One is how to change the attachment folder from the settings, then here we can add a screenshot placeholder to show like the settings drop down where this takes place. And the 2nd section can explain how to change this from the space that JSON file. And here we can add a code block to show like what exactly to add in the space that JSON. But this article can go in the advanced section.



&nbsp;

# /spaces/hide-files-and-folders-from-the-sidebar

I think this article is currently too long because it makes us both hiding a file or a folder and then seeing hidden files and folders. And then. Adding or editing a pattern. I think that we should break this down into 2 separate articles. So the hide files and folders can be a simple article that just explains how to hide, hide, and hide, and how to see hidden files and paths, and then a separate article can specifically be For managing exact baths and patterns. And this article can go in the advanced section and can add a link to like this advanced article in this article.



We can add one of these gifs that show the hiding process:&#32;

/Users/max/Library/Mobile\\ Documents/com\\\~apple\\\~CloudDocs/Outline/App\\ Demo\\ Videos/hiding-files-folders



# /ai/working-with-ai

I think that we can slightly reword this instead of work with an external AI app for that 1st heading inside of the article, I think we can use work with an external AI. Or work with external agents or something.

Then maybe we can add like one screenshot placeholder to show an example of asking An agent in the ChatGPT app to update a outline note or something.



# /ai/manage-mcp-access-for-a-space

Don't you think that this should go in advanced?



# /ai/troubleshoot-outline-mcp

This would probably also go in advanced.



# /ai/ai-in-the-terminal

This article mentions how to add commands, but this is a separate concern. Like it's not really related to using AI in the terminal, is it? This is. Discovery items, right? I mean, commands on its own, it's not really like an entity. It's the user can create a command. But at the core, this is just a resource item. So I don't think we need to explain how to add commands here. I think that, you know, we can keep this shorter and mention, you can also add commands in the terminal or something by defining a commands. Discovery bath or something. Right? But keep it relatively short and then add a link to configuring discovery items.



# /ai/set-up-ai-chat

A small wording change, but instead of saying outlines, building AI chat uses codex, I would specifically say outlines building AI chat uses the codex. Harness. Because that's what it is, right?



# /ai/starting-an-ai-chat

This can probably contain one screenshot placeholder that just shows the Starting an in-app AI chat, or maybe even like an animated GIF or something.



# /ai/add-context-and-reusable-content

This is good, but I would probably add a screenshot placeholder to show what discovery items look like in the command menu of the AI Chad, but also I would slightly rewrite That 1st sentence to make it a bit more understandable. Because it currently says resource items make it easy to add notes, folders, et cetera. But I think that we can write something like resource items, make it easy to add reusable content. In your outline space. And then it can give examples like reasonable content, like skills, terminal commands, note templates, and more. And we can then briefly explain that these resource items can easily be referenced from the AI Chad, the terminal, and more.

Additionally, you've listed available resource groups, but this is not correct. These are the default resource groups which recreate when a new space is created, but the resource groups are completely customizable by the user. He can define his own groups. So things like context, templates, and so forth, these are not really available resource groups. We can just put these under default resource groups. And then mention that these are the default groups that we create for new spaces, but that it's completely after the user to configure these how he wants.

And I don't think we need to have this section about resource warnings. I mean, this doesn't really matter, right? Like if there's a warning, the user can see it, but I don't think it has to be mentioned in the article.



&nbsp;

&nbsp;

&nbsp;

---



# Additional



# Locking

I think we need one additional article in these spaces section for note locking. Because this is one of the core features. So it should briefly explain that a space can have a fault, that can be locked and unlocked, if the user has never set a password for the volty person needs to set a password. And notes can then be locked and unlocked.

We can add one of these gif’s: /Users/max/Library/Mobile\\ Documents/com\\\~apple\\\~CloudDocs/Outline/App\\ Demo\\ Videos/locking-notes&#32;



## Links

One additional thing I would add to the articles. So many articles currently like at the end show Or mention a similar or related article. This is good, but I think that for articles that mentions several like or even just one related articles, we could potentially add like a bullet list of links. At the end, to give the user a clear list of similar articles that he can look into to learn more about a certain concept.

Something liek this:

```
Content
---
Related articles
- Use Excalidraw with Ai agents

```



## Article titles

I think that some article titles are too long. Because of this, they don't fully show any left sidebar, but I think that in general they're too long.

For ex:&#32;

- “**Use Outline from the menu bar” can be: “Menu bar"**
- **Create a note from a template &gt; “Templates”** 
- **[Create Excalidraw drawings](http://localhost:3011/docs/v0/notes/create-excalidraw-drawings "http://localhost:3011/docs/v0/notes/create-excalidraw-drawings") &gt; “Excalidraw Drawings"**
- **[Use Excalidraw with AI agents](http://localhost:3011/docs/v0/notes/excalidraw-with-ai-agents "http://localhost:3011/docs/v0/notes/excalidraw-with-ai-agents") &gt;  Excalidraw &amp; AI Agents**
- [Create and manage Spaces &gt; Spaces](http://localhost:3011/docs/v0/spaces/create-and-manage-spaces)
- **[Choose where attachments are saved](http://localhost:3011/docs/v0/spaces/choose-where-attachments-are-saved "http://localhost:3011/docs/v0/spaces/choose-where-attachments-are-saved") &gt; Attachement locations**
- **[Hide files and folders from the sidebar](http://localhost:3011/docs/v0/spaces/hide-files-and-folders-from-the-sidebar "http://localhost:3011/docs/v0/spaces/hide-files-and-folders-from-the-sidebar") &gt; Hiding Files &amp; Folders**
- **[About the Outline MCP server](http://localhost:3011/docs/v0/ai/mcp-server "http://localhost:3011/docs/v0/ai/mcp-server") &gt; MCP Server**
- **[Connect Outline MCP to AI clients](http://localhost:3011/docs/v0/ai/mcp-with-ai-clients "http://localhost:3011/docs/v0/ai/mcp-with-ai-clients") &gt; Connect MCP TO AI Clients**
- **[Manage MCP access for a Space](http://localhost:3011/docs/v0/ai/manage-mcp-access-for-a-space "http://localhost:3011/docs/v0/ai/manage-mcp-access-for-a-space") &gt; MCP Access**
- [Troubleshoot Outline MCP &gt; Troushoot MCP](http://localhost:3011/docs/v0/ai/troubleshoot-outline-mcp)
- **[Use AI in the Terminal](http://localhost:3011/docs/v0/ai/ai-in-the-terminal "http://localhost:3011/docs/v0/ai/ai-in-the-terminal") &gt; AI in the Terminal** 
- **[Add context and reusable content](http://localhost:3011/docs/v0/ai/add-context-and-reusable-content "http://localhost:3011/docs/v0/ai/add-context-and-reusable-content") &gt; Context &amp; Reusable Content**
- **[Configure a Space with space.json](http://localhost:3011/docs/v0/advanced/configuration "http://localhost:3011/docs/v0/advanced/configuration") &gt; Space.json** 
- **[View and edit note frontmatter](http://localhost:3011/docs/v0/advanced/view-and-edit-note-frontmatter "http://localhost:3011/docs/v0/advanced/view-and-edit-note-frontmatter") &gt; Frontmatter**
- 



<!-- outline:block id="img_cde3e79b-709" type="image" version="1" assetId="Attachments/Screenshot 2026-10-23 at 7.27.44 PM.png" src="Attachments/Screenshot 2026-10-23 at 7.27.44 PM.png" alt="Screenshot 2026-10-23 at 7.27.44 PM.png" -->
![Screenshot 2026-10-23 at 7.27.44 PM.png](<Attachments/Screenshot 2026-10-23 at 7.27.44 PM.png>)
<!-- /outline:block -->

