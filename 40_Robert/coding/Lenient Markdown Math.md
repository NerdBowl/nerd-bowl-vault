Obsidian is very lenient when parsing unusual block formulas. 

For example:
```markdown
- This is a block formula, placed inline $$\text{A Formula}$$
```

Renders as:
- This is a block formula, placed inline $$\text{A Formula}$$
Other markdown renderers (such as those used by Quartz) would fail, or place the formula inline, but obsidian still renders it as a proper block formula. 

In order to prevent ambiguity, you would have to write it something like this:
```markdown
- This is a block formula, placed inline 
    $$
    \text{A Formula}
    $$
```
- As described in the Quartz documentation: https://quartz.jzhao.xyz/features/Latex

Generally, it is not possible to change the markdown rendering engine. An alternative solution may therefore be to rewrite unusual block formulas to a more usual format that renders same, but may be unambiguously parsed across rendering engines.

This is the goal of this file.

A rewrite should ensure the following:
- **Block Isolation**: Every `$$` delimiter must be placed on their own line.
- **Indentation** of the math block is determined by the line where the **opening** `$$` occurs.
	- **List Item Context:** If the line starts with a bullet (`-`, `*`, `+`) or ordered list marker (`1.`), the math block is indented by **4 spaces** relative to the start of the line.
	- **Standard Context:** If the line is not a list item, the math block preserves the **same indentation** as the start of the line.
- **Continuation Text:** Any text immediately following a closing `$$` on the same line is moved to a new line, using the same indentation calculated for the math block.
- **Whitespace Handling:**
    - Leading/trailing whitespace within the math content is trimmed.
    - Redundant blank lines around the `$$` markers are trimmed.

Here are some example rewrites.

Input 1: Simple bullet with inline math
```markdown
- Bullet $$\\text{Some Text}$$  
- Bullet 2
```

Output 1:  
```markdown
- Bullet
    $$
    \\text{Some Text}  
    $$
- Bullet 2
```

Input 2: Nested indentation
```markdown
- Outer bullet 1
    - Inner bullet 1 $$\\text{Some Text}$$
    - Inner bullet 2
- Outer bullet 2
```

Output 2:
```markdown
- Outer bullet 1
    - Inner bullet 1
        $$
        \\text{Some Text}
        $$
    - Inner bullet 2
- Outer bullet 2
```

Input 3: Multiple math blocks in one line
```markdown
- Bullet 1 $$\\text{Some Text}$$some more text$$\\text{Some more text}$$
- Bullet 2
```

Output 3:
```markdown
- Bullet 1
    $$
    \\text{Some Text}
    $$
    some more text
    $$
    \\text{Some more text}
    $$
- Bullet 2
```

Input 4: Malformed bullet (no space after dash)
```markdown
-Not really a bullet $$\\text{Some Text}$$ some more text
- Really a bullet
```

Output 4:
```markdown
-Not really a bullet
$$
\\text{Some Text}
$$
some more text
- Really a bullet
```

Input 5: Extra spaces after dash
```markdown
-  More than one space $$\\text{Some text}$$
- Only one space
```

Output 5:  
```markdown
-  More than one space
    $$
    \\text{Some text}
    $$
- Only one space
```

Input 6: Newline immediately within bullet
```markdown
-
A newline $$\\text{Some text}$$
- Just a space
```

Output 6:
```markdown
-
A newline
$$
\\text{Some text}
$$
- Just a space
```

Input 7: Already correctly formatted (Idempotency)
```markdown
- Already correct
    $$
    \\text{Some Text}
    $$
- No Formula here
```

Output 7:
```markdown
- Already correct
    $$
    \\text{Some Text}
    $$
- No Formula here
```

Input 8: Partial/Malformed block formatting
```markdown
- Almost correct
    $$
    \\text{Some Text}$$
- Also almost correct $$
    \\text{Some Text}
    $$
- Also also almost correct
    $$\\text{Some Text}
    $$
```

Output 8:
```markdown
- Almost correct
    $$
    \\text{Some Text}
    $$
- Also almost correct
    $$
    \\text{Some Text}
    $$
- Also also almost correct
    $$
    \\text{Some Text}
    $$
```

Input 9: Ordered Lists
```markdown
1. First item $$\text{A}$$
2. Second item
    1. Nested item $$\text{B}$$
```

Output 9
```markdown
1. First item
    $$
    \text{A}
    $$
2. Second item
    1. Nested item
        $$
        \text{B}
        $$
```

Input 10: Deep Nesting
```markdown
- Level 1
    - Level 2
        - Level 3 $$\text{Deep Math}$$
```

Output 10
```markdown
- Level 1
    - Level 2
        - Level 3
            $$
            \text{Deep Math}
            $$
```

Input 11: Indented Text (Non-List Context)
```markdown
Unindented text
    This is just indented text, not a list. $$\text{Math}$$
    
    Another indented line.
```

Output 11
```markdown
Unindented text
    This is just indented text, not a list.
    $$
    \text{Math}
    $$
    
    Another indented line.
```

Input 12: Math immediately following List Marker
```markdown
- $$f(x) = x^2$$
- text after
```

Output 12
```markdown
- 
    $$
    f(x) = x^2
    $$
- text after
```

Input 13: Mixed markers and Trailing text
```markdown
* Star marker $$\text{Math 1}$$ continuation text
+ Plus marker $$\text{Math 2}$$
```

Output 13
```markdown
* Star marker
    $$
    \text{Math 1}
    $$
    continuation text
+ Plus marker
    $$
    \text{Math 2}
    $$
```

Input 14: Empty or Whitespace-only Math
```markdown
- Empty math block $$ $$
- Whitespace block $$ $$
```

Output 14
```markdown
- Empty math block
    $$
    $$
- Whitespace block
    $$
    $$
```

Input 15: Existing Multi-line (Messy)
```markdown
- Messy start $$
\text{Line 1}
  \text{Line 2} $$ continuation
- Some stuff
```

Output 15
```markdown
- Messy start
    $$
    \text{Line 1}
  \text{Line 2}
    $$
    continuation
- Some stuff
```

Input 16: Escaped Dollar signs
```markdown
- This is not math: \$$\text{literal}\$$
- Mixed: \$$not math, but this is\$$$$ \text{math} $$
```

Output 16
```markdown
- This is not math: \$$\text{literal}\$$
- Mixed: \$$not math, but this is\$$
    $$
    \text{math}
    $$
```

Input 17: Code blocks
````markdown
```latex
$$\text{ignore me}$$
```
````

Output 17
````markdown
```latex
$$\text{ignore me}$$
```
````

Input 18: Task lists
```markdown
- [ ] Unchecked task $$\text{math}$$ 
- [x] Checked task $$\text{math}$$
```

Output 18
```markdown
- [ ] Unchecked task 
    $$ 
    \text{math} 
    $$ 
- [x] Checked task 
    $$ 
    \text{math} 
    $$
```

Input 19: Quoted math
```markdown
> This is a quote $$\text{quoted math}$$
> Continuation
```

Output 19
```markdown
> This is a quote 
> $$
> \text{quoted math}
> $$
> Continuation
```

Input 20: Mixed delimiters
```markdown
- Let $x$ be a variable and $$x^2$$ be the square.
```

Output 20
```markdown
- Let $x$ be a variable and
    $$
    x^2
    $$
    be the square.
```

Input 21: Tables
```markdown
| Column 1 | Column 2 |
| :--- | :--- |
| Text | $$\text{Math in table}$$ |
```

Output 21 (not entirely correct but sufficient)
```markdown
| Column 1 | Column 2 |
| :--- | :--- |
| Text | $\text{Math in table}$ |
```

Input 22: Links 
```markdown
- Click here: [$$\text{Link}$$](http://example.com)
```

Output 22 (not entirely correct but sufficient)
```markdown
- Click here: [$\text{Link}$](http://example.com)
```



To show how obsidian renders the sloppy and proper cases:

---
- Bullet $$\\text{Some Text}$$  
- Bullet 2
---
- Bullet
    $$
    \\text{Some Text}  
    $$
- Bullet 2
---
- Outer bullet 1
    - Inner bullet 1 $$\\text{Some Text}$$
    - Inner bullet 2
- Outer bullet 2
---
- Outer bullet 1
    - Inner bullet 1
        $$
        \\text{Some Text}
        $$
    - Inner bullet 2
- Outer bullet 2
---
- Bullet 1 $$\\text{Some Text}$$some more text$$\\text{Some more text}$$
- Bullet 2
---
- Bullet 1
    $$
    \\text{Some Text}
    $$
    some more text
    $$
    \\text{Some more text}
    $$
- Bullet 2
---
-Not really a bullet $$\\text{Some Text}$$ some more text
- Really a bullet
---
-Not really a bullet
$$
\\text{Some Text}
$$
some more text
- Really a bullet
---
-  More than one space $$\\text{Some text}$$
- Only one space
---
-  More than one space
    $$
    \\text{Some text}
    $$
- Only one space
---
-
A newline $$\\text{Some text}$$
- Just a space
---
-
A newline
$$
\\text{Some text}
$$
- Just a space
---
- Already correct
    $$
    \\text{Some Text}
    $$
- No Formula here
---
- Already correct
    $$
    \\text{Some Text}
    $$
- No Formula here
---
- Almost correct
    $$
    \\text{Some Text}$$
- Also almost correct $$
    \\text{Some Text}
    $$
- Also also almost correct
    $$\\text{Some Text}
    $$
---
- Almost correct
    $$
    \\text{Some Text}
    $$
- Also almost correct
    $$
    \\text{Some Text}
    $$
- Also also almost correct
    $$
    \\text{Some Text}
    $$
---
1. First item $$\text{A}$$
2. Second item
    1. Nested item $$\text{B}$$
---
1. First item
    $$
    \text{A}
    $$
2. Second item
    1. Nested item
        $$
        \text{B}
        $$
---
- Level 1
    - Level 2
        - Level 3 $$\text{Deep Math}$$
---
- Level 1
    - Level 2
        - Level 3
            $$
            \text{Deep Math}
            $$
---
Unindented text
    This is just indented text, not a list. $$\text{Math}$$
    
    Another indented line.
---
Unindented text
    This is just indented text, not a list.
    $$
    \text{Math}
    $$
    
    Another indented line.
---
- $$f(x) = x^2$$
- text after
---
- 
    $$
    f(x) = x^2
    $$
- text after
---
* Star marker $$\text{Math 1}$$ continuation text
+ Plus marker $$\text{Math 2}$$
---
* Star marker
    $$
    \text{Math 1}
    $$
    continuation text
+ Plus marker
    $$
    \text{Math 2}
    $$
---
- Empty math block $$ $$
- Whitespace block $$ $$
---
- Empty math block
    $$
    $$
- Whitespace block
    $$
    $$
---
- Messy start $$
\text{Line 1}
  \text{Line 2} $$ continuation
- Some stuff
---
- Messy start
    $$
    \text{Line 1}
  \text{Line 2}
    $$
    continuation
- Some stuff
---
- This is not math: \$$\text{literal}\$$
- Mixed: \$$not math, but this is\$$$$ \text{math} $$
---
- This is not math: \$$\text{literal}\$$
- Mixed: \$$not math, but this is\$$
    $$
    \text{math}
    $$
---
```latex
$$\text{ignore me}$$
```
---
```latex
$$\text{ignore me}$$
```
---
- [ ] Unchecked task $$\text{math}$$ 
- [x] Checked task $$\text{math}$$
---
- [ ] Unchecked task 
    $$ 
    \text{math} 
    $$ 
- [x] Checked task 
    $$ 
    \text{math} 
    $$



---
> This is a quote $$\text{quoted math}$$
> Continuation

---
> This is a quote 
> $$
> \text{quoted math}
> $$
> Continuation
---
- Let $x$ be a variable and $$x^2$$ be the square.
---
- Let $x$ be a variable and
    $$
    x^2
    $$
    be the square.
---