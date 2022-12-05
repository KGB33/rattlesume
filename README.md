# Rattlesume

A tool for building resumes by combining markdown snippets into a single
document using `yaml` definitions, then transformed into a PDF `pandoc`. Allows
developers to store their resumes in git, and present them in a common format.
Different yaml definitions can be used to craft bespoke resumes from a collection
of markdown snippets.

# Usage

## Snippets

To start, create a `content` directory with a subdirectory
to organize a class of snippets. **The name of the
subdirectory will be the same as the header in the final resume.**

```
 example/content/
├──  experience/
│  └──  FooBar.md
└──  projects/
   └──  Rattlusume.md
```

Each of these markdown files are called 'snippets'. They are
typically a short summary & include relevant information such as
dates, job titles, etc.

```markdown
---
filename: FooBar.md
---
# FooBar Inc.
## Sr. Foobar Enigneer, March 5th, 2015 - Present

Responsible for announcing the zero-modulate of the counting numbers greater than
zero with respect to three and five. Saved FooBar Inc. $15 annually by implementing
an `O(n)` solution.
```

> Snippets can contain an optional slug at the very top, denoted by `---`.
> This slug must be valid yaml. Currently, it is parsed, but not used.


## Definitions

Each unique resume has a corresponding definition file.
There are currently two required top-level values. `header`,
and `resume`.

### `header`

The format of this value is still in flux.

### `resume`

The `resume` section has arbitrary sub-key corresponding to the
names of the subdirectories the snippets are located in.

Each of these sub-keys take a list of values, which are ether file names
or special values.

For example, the aforementioned 'FooBar.md' could be defined as follows:

```yaml
header:
  ...

resume:
  experience:
    - "---"
    - "FooBar.md"
```

There is currently only one special value,
`"---"`, which denotes a horizontal rule.
