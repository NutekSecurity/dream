# Alacritty checklist

1. Spawn one session of Alacritty.
2. Check if the terminal is displayed correctly.
3. Check if the terminal is responsive.
4. Check if the terminal can be resized.
5. Run tmux in Alacritty.
    1. Start new named tmux session with `tmux new -s session_name`.
    2. Detach from the session with `Ctrl+b d`.\
    3. Reattach to the session with `tmux attach -t session_name`.
    4. Kill the session with `tmux kill-session -t session_name`.
    5. Split the window with `Ctrl+b %`.
    6. Split the window with `Ctrl+b "`.
