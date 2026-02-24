### Hi there 👋
Working on things.  [mrbuilder](https://mr-builder.github.io) and stuff.  

#### Here are a few folks who think I'm cool:
- [Zaid A](https://github.com/beatzball)

<!--
**jspears/jspears** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

My git aliases look like

```
[alias]
        undo = checkout origin/main
        last = log -1 HEAD
        ignore = "!f() { for f in \"$@\"; do echo \"$f\" >> .git/info/exclude; done; }; f"
        unignore = "!f() { for f in \"$@\"; do sed -i \"\" \"\\\\|^${f}$|d\" .git/info/exclude; done; }; f"
        ls = branch  --sort=committerdate
        alias = config --global alias.
        main = switch main
        wip = commit -nam 'wip'
        back = "!f() { ~/bin/git-back.sh $@ | xargs git switch; }; f"
        unwip = "!f() { ~/bin/git-unwip.sh \"$@\"; }; f"


```
