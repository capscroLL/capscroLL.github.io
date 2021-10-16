---
title: Windows Input Method
i18n:
  - zh
---

# Windows Input Method

微软拼音输入法, 切换全拼和双拼模式

```shell
@echo off

set MainKey=HKEY_CURRENT_USER\SOFTWARE\Microsoft\InputMethod\Settings\CHS

reg query %MainKey% /v "Enable Double Pinyin" /s

for /f "skip=1" %%i in ('reg query %MainKey% /v "Enable Double Pinyin" /s ^| findstr /i "0x1"') do (
    set isDouble=1
)

if not defined isDouble (
    reg add %MainKey% /v "Enable Double Pinyin" /t REG_DWORD /d 0x1 /f
    echo 设定微软拼音模式为: 双拼
) else (
    reg add %MainKey% /v "Enable Double Pinyin" /t REG_DWORD /d 0x0 /f
    echo 设定微软拼音模式为: 全拼
)

pause
```