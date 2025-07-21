## Theory:
- Tmux has 3 layers: `session` -> `window` -> `panel`

## Commands:
- Create a new `session`
	- Tạo 1 session mới với tên chỉ định (thêm `new -s <new-session-name>`)
```bash
tmux
tmux new -s <new-session-name>
```
- Back to a `session`
	- Mặc định sẽ quay lại session gần nhất (bỏ option `-t`)
```bash
tmux a -t <session-name>
```
- List all `session`
```bash
tmux ls
```
- Clear all `session`
```bash
tmux kill-server
```

## Hotkeys:
- Session
	- Make current `session` run in detach mode :  `Ctrl + b + d`
	
- Window
	- Create new window : `Ctrl + b + c`
	- Jump to window : `Ctrl + b + n`
		- Or `Ctrl + b + w`
	- Rename window : `Ctrl + b + ,`
	
- Panel
	- Create a new `pane` : 
		- Vertically: `Ctrl + b + %`
		- Horizontally: `Ctrl + b + "`
	- Jump to window in right side: `Ctrl + b + ->`
		- Or `Ctrl + b + q + <window-number>`
	- Make pane scale to the right : `(Hold)(Ctrl + b) + ->`
	- Kill pane: `Ctrl + b + x`

- Turn on copy mode
	1. `Ctrl + b + [`
	2. Move to the text with arrow keys
	3. `Space`
	4. Cover the text with arrow keys
	5. `Enter`
	6. `Ctrl + b + ]`

- Switch to other panels layout: `Ctrl + b + Space`
	

