<a href="../README.md">
<button>⬅Back</button>
</a>

# Enhance your git log with conventional commits

Git is a very powerful tool installed on most of our machines. As developer, we use it every day. But, unfortunately, at first glance, this tool is not very developer friendly. That’s why a lot of people bypass the command line interface (CLI) with a graphical user interface (GUI).
It’s like using a framework without knowing the language itself. It can be OK at the beginning but, sooner or later you, you will have problems.

Let’s take an example:

```bash
$ git log --oneline ./src/components/button/

daccff1f test should pass
3fff19f6 test should pass
5b998d9a add disabled property for button
06faab4d fix lint
186cce90 refactor button
4b99d91a fix spinner component
5b998d9a fix css
263288a5 test should pass
c3fb85af Create Button component
```

There’s might be nothing wrong for you with this log. Let me show you the issues I’ve found with this log:

- It’s hard to understand the Component’s history. We might repeat errors already fixed.
- There are unnecessary commits which pollute logs and make history hard to read. Also, functionalities like git blame become irrelevant.
- It seems that a feature was added by a few commits. Which commit should I include if I want to revert this operation?
- `4b99d9a` say something about a different component. Is it an unwanted change? Again, what if we need to revert?
- …