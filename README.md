# vhdl-style-guide’s documentation!

https://vhdl-style-guide.readthedocs.io/

vsg -f [source file name] --fix --configuration config_jeong.json

## 설치 방법

```pip install vsg --use-pep517```

## VS code에 적용 방법

### 단축키 설정

Ctrl + Shift + P를 눌러 `Preferences: Open Keyboard Shortcuts (JSON)`을 선택하고 직접 수정.

아래 항목 추가

``` json
{
  "key": "shift+alt+f",
  "command": "workbench.action.tasks.runTask",
  "args": "vsg-fix",
  "when": "editorTextFocus && editorLangId == vhdl"
}
```

### task 정의

Ctrl + Shift + P → `Tasks: Configure Default Build Task` 선택.

아래 내용 추가.

이때 command 에 vsg 위치는 자신의 환경에 맞도록 설정

```
"command": "C:\\Users\\jeong\\anaconda3\\envs\\venv\\Scripts\\vsg -f ${relativeFile} --fix --configuration d:/Work/VSG_configuration/config_jeong.json",
```

``` json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
      {
        "label": "vsg-check",
        "type": "shell",
        "command": "vsg -f ${relativeFile}",
        "problemMatcher": {
          "owner": "vsg",
          "fileLocation": [
            "autoDetect",
            "${workspaceFolder}"
          ],
          "pattern": [
            {
              "regexp": "^File:  ([^\\s]*)\\s*$",
              "file": 1
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^  ([^\\s]*_\\d*)\\s*. ([^\\s]*)\\s*.\\s*([^\\s]*) . (.*)$",
              "code": 1,
              "severity": 2,
              "location": 3,
              "message": 4,
              "loop": true
            }
          ]
        }
      },
      {
        "label": "vsg-fix",
        "type": "shell",
        "command": "C:\\Users\\jeong\\anaconda3\\envs\\venv\\Scripts\\vsg -f ${relativeFile} --fix --configuration d:/Work/VSG_configuration/config_jeong.json",
        "problemMatcher": {
          "owner": "vsg",
          "fileLocation": [
            "autodetect",
            "${workspaceFolder}"
          ],
          "pattern": [
            {
              "regexp": "^File:  ([^\\s]*)\\s*$",
              "file": 1
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^.*$"
            },
            {
              "regexp": "^  ([^\\s]*_\\d*)\\s*. ([^\\s]*)\\s*.\\s*([^\\s]*) . (.*)$",
              "code": 1,
              "severity": 2,
              "location": 3,
              "message": 4,
              "loop": true
            }
          ]
        },
        "group": {
          "kind": "build",
          "isDefault": true
        }
      }
    ]
  }
```  