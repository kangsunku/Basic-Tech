# tmux

### Tmux

---

> `tmux`는 "terminal multiplexer"의 약자로, 여러개의 터미널 세션을 하나의 터미널 창에서 관리할 수 있게 해주는 유용한 도구입니다. `tmux`를 사용하면 여러개의 작업을 동시에 수행하거나, 세션을 저장하고 나중에 다시 연결하거나, 원격에서 작업하면서 연결이 끊어져도 작업을 중단하지 않고 계속 진행할 수 있습니다.
> 

### Session 확인

```bash
tmux ls
```

### 세션 생성

```bash
tmux
tmux new -s session_name
```

### 세션 종료

```bash
exit
#or
tmux kill-session -t session_name
```

### Terminal List 보기

```bash
tmux ls
```

**tmux 시작 및 세션 관리**

- `tmux` : 새로운 세션을 시작합니다.
- `tmux new-session -s <세션 이름>` 또는 `tmux new -s <세션 이름>` : 이름을 지정하여 새로운 세션을 시작합니다.
- `tmux attach-session -t <세션 이름>` 또는 `tmux a -t <세션 이름>` : 지정한 이름의 세션에 연결합니다.
- `tmux list-sessions` 또는 `tmux ls` : 현재 실행 중인 세션들의 목록을 보여줍니다.
- `tmux kill-session -t <세션 이름>` : 지정한 이름의 세션을 종료합니다.

### Terminal 들어가기

```bash
tmux attach -t 0
tmux attach -t 1
tmux attach -t 2
```

### 나오기

```bash
ctl+b,d
```

### 명령 전달

tmux send-keys -t session_name:0.0 ‘whomai’ Enter

### Window

- 윈도우 생성 ctl+b , c
- 윈도우 이름 변경 ctl+b , ,(진짜 컴마)
- 다음 윈도우 ctl+b , n
- 이전 윈도우 ctl+b , p
- 모든 윈도우 리스트 보기 ctl+b , w

### Pane

- 세로로 윈도우 분할 ctl+b , %
- 가로로 윈도우 분할 ctl+b, "
- 팬 이동 ctl+b, q + 숫자 ctl+b, q + 방향키
- 줌 : 특정 팬을 전체화면으로 전환, 한번 더 누르면 원상태 복구 ctl+b, z
- 기타 C+b,alt+화살표 : 해당 방향으로 pane 크기변경 C+b,q : 해당 숫자 pane으로 이동 C+b,o : 순서대로 이동 C+b,z : 현재 pane 최대화 토글 C+b,space : pane배치 변경 C+b,x : eXit pane (Pane 강제 종료) #### 기타
- C+b,? : list-keys
- Scroll Mode 진입 : C+b,[
    - 아래화살표·위화살표,PageUp,PageDown키로 화면 이동
    - esc키로 화Scroll Mode 끝내기

### alias example

```bash
alias t='tmux '
alias ta='tmux attach -t '
alias tl='tmux ls'
alias tn='tmux new -s '
```

**윈도우 관리**

- `Ctrl-b c` : 새로운 윈도우를 생성합니다.
- `Ctrl-b n` : 다음 윈도우로 이동합니다.
- `Ctrl-b p` : 이전 윈도우로 이동합니다.
- `Ctrl-b ,` : 윈도우 이름을 변경합니다.
- `Ctrl-b &` : 현재 윈도우를 종료합니다.

**패널 관리**

- `Ctrl-b %` : 현재 윈도우를 수평으로 분할합니다.
- `Ctrl-b "` : 현재 윈도우를 수직으로 분할합니다.
- `Ctrl-b o` : 다른 패널로 이동합니다.
- `Ctrl-b x` : 현재 패널을 종료합니다.
- `Ctrl-b + 방향키` : 패널 사이의 경계를 조정합니다.

**기타**

- `Ctrl-b ?` : `tmux` 단축키 목록을 보여줍니다.
- `Ctrl-b d` : 현재 세션에서 분리하되 세션을 종료하지 않습니다.
- `Ctrl-b [Space]` : 다양한 패널 레이아웃 중에서 변경합니다.

이외에도 `tmux`에는 많은 기능과 설정이 있습니다. `man tmux` 명령을 통해 더 많은 정보를 얻을 수 있습니다.
