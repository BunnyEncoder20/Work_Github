# Technologies to Learn

## Development

## Deployment (CICD)

### 1. [Tmux Terminal multiplexer](https://www.youtube.com/watch?v=nTqu6w2wc68)
- it is kind of terminal virtualization
- Tmux has 3 layers:
    1. Session (cmd: tmux)
    2. Window


#### Commands
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




## Pet Projects
1. [Spec Kit by Github](https://www.youtube.com/watch?v=em3vIT9aUsg): for Sprec Driven Development (SDD) of AI coding. The Tool focus only one one spec file and builds the application from there, using the specifications files as the single source of truth.

2. Making own Home/Office-Lab AI servers: Try following this networkChuck [video](https://www.youtube.com/watch?v=Wjrdr0NU4Sk)
