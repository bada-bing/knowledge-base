There are some conflicts between WT and Tmux
https://github.com/microsoft/terminal/issues/4763


Keys

Bind-Key - <C-b>
BK - x - delete pane
BK - c - create pane
BK - w - list windows (of a session)
BK - s - list sessions

BK - - - split horiznotally (remapped)
BK - | - split vertically (remapped)

`tmux new -s ses_1`
`tmux attach-session -t ses_1` (-t stands for target)
