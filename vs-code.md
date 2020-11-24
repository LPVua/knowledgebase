## Get list of machine extensions
`--list-extensions | xargs -L 1 echo code --install-extension`

## Extensions
```
code --install-extension CoenraadS.bracket-pair-colorizer
code --install-extension eamodio.gitlens
code --install-extension eg2.tslint
code --install-extension emmanuelbeziat.vscode-great-icons
code --install-extension le0zh.vscode-regexp-preivew
code --install-extension minhthai.vscode-todo-parser
code --install-extension msjsdiag.debugger-for-chrome
code --install-extension pflannery.vscode-versionlens
code --install-extension sleistner.vscode-fileutils
code --install-extension speks.flowmaker
code --install-extension streetsidesoftware.code-spell-checker
code --install-extension thenikso.github-plus-theme
code --install-extension WakaTime.vscode-wakatime
code --install-extension whatwedo.twig
code --install-extension wix.vscode-import-cost
code --install-extension indent-rainbow
```

## Config
```json
{
    "editor.fontSize": 12,
    "editor.tabSize": 2,
    "editor.detectIndentation": false,
    "editor.renderWhitespace": "boundary",
    "editor.acceptSuggestionOnCommitCharacter": false,
    "editor.acceptSuggestionOnEnter": "off",
    "tslint.enable": true,
    "editor.lineHeight": 19,
    "editor.cursorWidth": 1,
    "editor.minimap.enabled": false,
    "editor.dragAndDrop": false,
    "workbench.editor.showTabs": false,
    "workbench.editor.enablePreview": false,
    "workbench.editor.enablePreviewFromQuickOpen": false,
    "explorer.openEditors.visible": 1,
    "explorer.autoReveal": false,
    "tslint.autoFixOnSave": true,
    "workbench.colorTheme": "GitHub Plus",
    "workbench.iconTheme": "vscode-great-icons",
    "workbench.panel.location": "bottom",
    "workbench.fontAliasing": "auto",
    "workbench.activityBar.visible": false,
    "window.nativeTabs": true,
    "gitlens.advanced.messages": {
      "suppressCommitHasNoPreviousCommitWarning": false,
      "suppressCommitNotFoundWarning": false,
      "suppressFileNotUnderSourceControlWarning": false,
      "suppressGitVersionWarning": false,
      "suppressLineUncommittedWarning": false,
      "suppressNoRepositoryWarning": false,
      "suppressResultsExplorerNotice": false,
      "suppressShowKeyBindingsNotice": true,
      "suppressUpdateNotice": true,
      "suppressWelcomeNotice": true
    },
    "explorer.confirmDragAndDrop": false,
    "TodoParser": {
      "include": ["ts, tsx"],
      "folderExclude": ["node_modules", ".vscode"],
      "showInProblems": false,
      "markers": ["TODO-FE:"],
      "autoDefaultMarkers": true
    },
    "files.autoSave": "afterDelay",
    "terminal.integrated.fontSize": 12,
    "terminal.integrated.lineHeight": 1.1875,
    "extensions.ignoreRecommendations": true,
    "window.zoomLevel": 0,
    "diffEditor.ignoreTrimWhitespace": true,
    "gitlens.keymap": "alternate",
    "gitlens.historyExplorer.enabled": true,
  }
```

## Key shortcuts
```json
[
    {
        "key": "cmd+d",
        "command": "workbench.files.action.showActiveFileInExplorer"
    },
    {
        "key": "cmd+,",
        "command": "workbench.action.navigateBack"
    },
    {
        "key": "ctrl+-",
        "command": "-workbench.action.navigateBack"
    },
    {
        "key": "cmd+.",
        "command": "workbench.action.navigateForward"
    },
    {
        "key": "ctrl+shift+-",
        "command": "-workbench.action.navigateForward"
    },
    {
      "key": "alt+t",
      "command": "workbench.action.terminal.toggleTerminal"
    },
    {
      "key": "ctrl+`",
      "command": "-workbench.action.terminal.toggleTerminal"
    },
    {
      "key": "ctrl+l",
      "command": "workbench.action.gotoLine"
    },
  ]
```
