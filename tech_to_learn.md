# Technologies to Learn

## Development

## Deployment (CICD)

### 1. [Tmux Terminal multiplexer](https://www.youtube.com/watch?v=nTqu6w2wc68)
- [Tmux Wiki](https://github.com/tmux/tmux/wiki/Getting-Started)
- it is kind of terminal virtualization
- Tmux has 3 layers:
    1. Session (name on the bottom left)
    2. Window (the thing after the session name, also has the terminal we're using [default is bash])
    3. Panes (when we split the window)


#### Commands
##### Session Commands
- To create a session and attach to it
```bash
tmux
```
- To look at all sessions
```bash
tmux ls
```
- To attach to session:
```bash
tmux a  # attaches to most recetly used session
tmux a -t <session index>
tmux a -t <session name>
```
- To detach from a session:
```bash
>> ctrl - B
>> D
```
- To create a named session:
```bash
tmux new -s bob  # name is at the bottom left of the session window
```
- To kill a session:
```bash
tmux kill-session  # kills most recent session
tmux kill-session -t <session index/name>
```
- To kill all sessions at once
```bash
tmux kill-server
```

---

##### Window Commands
- To make a new window (current one marked with '*'):
```bash
>> ctrl + B
>> C
```
- To cycle through all the windows:
```bash
>> ctrl + B
>> N
```
- To Navigate between sessions and windows:
```bash
>> ctrl + B
>> W
```
- To Kill a window:
```bash
>> ctrl + B
>> W
# Be on the window you want to kill
>> ctrl + B
>> X
```

---

##### Pane Commands
- To Make a new pane (vertical split)
```bash
>> ctrl + B
>> shift + 5     # (%)
```
- To make a new pane (horizontal split)
```bash
>> ctrl + B
>> shift + '    # (")
```
- To Navigate between panes
```bash
>> ctrl + B
>> arrow keys to navigate
```
- To jump to a specific pane
```bash
>> ctrl + B
>> Q            # will show the index of panels
>> <index number>
```
- To size panes
```bash
>> ctrl + B
>> ctrl / alt (hold)    # which ever size of adjustment
>> <arrow keys>
```

---

Tmux Cheat Sheet / Quick Ref link [Link](https://tmuxcheatsheet.com/)

---

## Pet Projects
1. [Spec Kit by Github](https://www.youtube.com/watch?v=em3vIT9aUsg): for Sprec Driven Development (SDD) of AI coding. The Tool focus only one one spec file and builds the application from there, using the specifications files as the single source of truth.

2. Making own Home/Office-Lab AI servers: Try following this networkChuck [video](https://www.youtube.com/watch?v=Wjrdr0NU4Sk)
