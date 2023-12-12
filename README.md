# Iterm2 셋팅



## zsh 셋팅

이미 시스템에 Oh My Zsh가 설치되어 있거나 이전 설치 시도로 인해 `$ZSH` 디렉토리(위치: `/Users/anseunghyeon/.oh-my-zsh`)가 생성되어 있어 설치가 완료되지 않았습니다. Oh My Zsh를 다시 설치하려면 기존 `$ZSH` 디렉토리를 먼저 제거해야 합니다. 다음 명령어를 터미널에 입력하여 이 디렉토리를 삭제할 수 있습니다:

```sh
rm -rf /Users/anseunghyeon/.oh-my-zsh
```

이 명령어는 `.oh-my-zsh` 폴더를 삭제합니다. 이 폴더를 삭제한 후에 다음 Oh My Zsh 설치 명령어를 다시 실행하세요:

```sh
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

이렇게 하면 설치 과정이 충돌 없이 완료될 것입니다. `.oh-my-zsh` 디렉토리를 삭제하기 전에 중요한 설정이나 커스텀 스크립트를 백업하는 것을 잊지 마세요.

