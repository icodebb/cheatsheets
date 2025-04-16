# Markdown Cheat Sheet  
  
Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!  
  
This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax/) and [extended syntax](https://www.markdownguide.org/extended-syntax/).  
  
## Basic Syntax  
  
These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.  
  
### Heading  
  
## H2  
  
### H3  
  
### Bold  
  
This is **bold text**.  
  
### Italic  
  
This is *italicized text*.  
  
### Blockquote  
  
> blockquote  
  
### Ordered List  
  
1. First item  
2. Second item  
3. Third item  
  
### Unordered List  
  
- First item  
- Second item  
- Third item  
  
### Checkboxes  
  
* [ ] Things need to be done  
  * [ ] Plan   
  * [ ] Estimate  
  * [ ] Deployment  
* [/] In progress  
* [x] Done
* [>] Waiting
* [ ] Things can wait  

NOTE: `*` is better than `-` in checkboxes content.  

**Emojis** GitHub-flavored Markdown (GFM):

- [ ] 🔄 In Progress: Implement user login
- [ ] ⏳ Waiting: Review from team
- [ ] 🧪 Testing: Unit tests for auth module
- [ ] 🚫 Blocked: Dependency issue on API
- [ ] 📝 Needs Review: Documentation update
- [x] ✅ Done
- [ ] 🔥 High: Fix security bug (due: 2025-04-20)
- [ ] ⚠️ Medium: Add pagination
- [ ] 💤 Low: Optimize images
- [ ] 📅 2025-04-17 
- [ ] 🛫 2025-04-16 
- [ ] ⏳ 2025-04-22 
- [ ] ⏫ Hi priority
- [ ] 🔼 M
- [ ] 🔽 L
- [ ] 🔺 Highest
- [ ] ⏬ Lowest
- [ ] 🔁 Recuring/repeat
- [ ] ⛔ Depend on
- [ ] 🏁 On completion 

### Code  
  
`code`  
  
### Horizontal Rule  
  
---  
  
### Link  
  
[Markdown Guide](https://www.markdownguide.org)  
  
### Image  
  
![alt text](https://www.markdownguide.org/assets/images/tux.png)  
  
## Extended Syntax  
  
These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.  
  
### Table  
  
| Syntax | Description |  
| ----------- | ----------- |  
| Header | Title |  
| Paragraph | Text |  
  
### Fenced Code Block  
  
```json  
{  
  "firstName": "John",  
  "lastName": "Smith",  
  "age": 25  
}  
```  
  
### Footnote  
  
Here's a sentence with a footnote. [^1]  
  
[^1]: This is the footnote.  
  
### Heading ID  
  
### My Great Heading {#custom-id}  
  
### Definition List  
  
term  
: definition  
  
### Strikethrough  
  
~~The world is flat.~~  
  
### Task List  
  
- [x] Write the press release  
- [ ] Update the website  
- [ ] Contact the media  
  
### Emoji  
  
That is so funny! :joy:  
  
(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))  
  
### Highlight  
  
I need to highlight these ==very important words==.  
  
### Subscript  
  
H~2~O    
H<sub>2</sub>O    
log<sub>2</sub>(x)    
### Superscript  
  
X^2^    
X<sup>2</sup>    
  
## Links  
  
- [lifeparticle/Markdown-Cheatsheet](https://github.com/lifeparticle/Markdown-Cheatsheet)  
- [Markdown cheat-sheet from MarkdownGuide.org](https://www.markdownguide.org/cheat-sheet/)  
- [interviewbit.com/markdown-cheat-sheet](https://www.interviewbit.com/markdown-cheat-sheet/)  
- [adam-pMarkdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)