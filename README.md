# askai
Super comfortable ChatGPT client. Ask to ChatGPT with your text editor.

![gif](https://github.com/user-attachments/assets/a3c8cb2e-a1c1-4fb9-8fbf-e06a245810d3)

## Requirement
- Python 3.12.0+
- Windows
    - Because use batch files.
    - If Linux or Mac User, create wrapper script yourself properly.

## Tutorial

### Prepare
- API Key:
    - Prepare your OPENAI_API_KEY.
- Prompt files and launcher batches:
    - Create `i.bat` from `i.bat.sample`. For example: `1.bat`, `2.bat`, `3.bat`, ...
    - Create `i.md`. For example: `1.md`, `2.md`, `3.md`, ...
- Log files:
    - Create `askailog.md`
- (If need) Startup Script:
    - Create `aiprepare.bat` from `aiprepare.bat.sample`

### Usage
- 1: Execute `aiprepare.bat`
- repeative
    - 2: Write a prompt to `i.md`
    - 3: Execute `i.bat`

## Q&A

### Q: What is log file?
Ans: A file where all previous prompts and their response results are saved.

### Q: customize possible?
Ans: possible!

Edit `askai.py` directly.

### Q: SSL Error...
Ans: use `--use-ssl (your-cert-file).crt`.

### Q: What is your editor?
Ans: [秀丸エディタ(Hidemaru Editor)](https://hide.maruo.co.jp/software/hidemaru.html), A japanese high-quality text editor!

### Q: What is recommended editor or IDE?
Ans: An editor or IDE which has Multi-tab, Markdown oriented and Auto reloading.

I think VSCode is better choice.

### Q: What is recommended count of slots?
Ans: Depends on the person.

In my case, 3 slots were suitable.

### Q: Example of on VSCode?
Ans: Use .vscode/tasks.json on your folder.

```json
{
    "version": "2.0.0",
    "tasks": [
      {
        "label": "Run askai",
        "type": "shell",
        "command": "/usr/local/bin/python3",
        "args": [
            "askai.py",
            "--input",
            "${fileBasenameNoExtension}.md"
        ],
        "group": {
          "kind": "build",
          "isDefault": true
        }
      }
    ]
  }
```

### Q: Example of prepare script on Mac?
Ans: like this.

.bash_profile_askai:

```sh
alias python="/usr/local/bin/python3"
alias pip="/Library/Frameworks/Python.framework/Versions/3.11/bin/pip3"

export OPENAI_API_KEY=XXXX

function a1(){
  python askai.py --input 1.md &
}
function a2(){
  python askai.py --input 2.md &
}
function a3(){
  python askai.py --input 3.md &
}
export -f a1
export -f a2
export -f a3
alias 1="a1"
alias 2="a2"
alias 3="a3"
```

execute:

```terminal
$ source ~/.bash_profile_askai

$ 1
```

## License
[MIT](LICENSE)

## Author
[stakiran](https://github.com/stakiran)
