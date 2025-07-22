# Pandoc Cheatsheet

**Author:** Ice Liu

## Examples

### Commands

| Commands | Description |
|----------|-------------|
| `pandoc [input-file] -o [output-file] [options]` | Basic usage |
| `pandoc --list-input-formats` | List supported formats |
| `pandoc --list-output-formats` | List supported output formats |
| `pandoc input.md -o output.html` | Markdown to HTML |
| `pandoc input.md -o output.pdf` | Markdown to PDF |
| `pandoc input.md -o output.docx` | Markdown to DOCX(Word) |
| `pandoc input.html -o output.md` | HTML to Markdown |
| `pandoc input.tex -o output.pdf` | Latex to PDF |
| `pandoc -f markdown -t html input.md -o output.html` | Use -f (from) and -t (to) for the format. |
| `pandoc input.md -o output.pdf --metadata title="Document Title"` | Add title |
| `pandoc input.md -o output.pdf --toc` | Table of contents |
| `pandoc input.md -o output.pdf --metadata-file=metadata.yaml` | Include metadata file |
| `pandoc input.md -o output.html -V author="Author Name" -V date="2024-01-01"` | Set document variables |
| `pandoc input.md -o output.html --css=style.css` | Custom CSS for HTML |
| `pandoc input.md -o output.pdf --template=mytemplate.tex` | Custom template |
| `pandoc input.md -o output.pdf --highlight-style=monochrome` | Highlight syntax style |
| `pandoc chapter1.md chapter2.md -o book.pdf` | Merge multiple files |
| `pandoc https://example.com -o output.pdf` | Convert from URL |
| `pandoc input.docx -t markdown -o output.md --extract-media=./media` | Extract images from docx |
