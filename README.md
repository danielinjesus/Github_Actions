# 이것은 Actions를 시작하는 데 도움이 되는 기본 워크플로우임

name: CI

# 워크플로우가 실행될 시점을 제어함
on:
  # "main" 브랜치에 대한 push 또는 pull request 이벤트가 발생했을 때 워크플로우를 트리거함
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

  # Actions 탭에서 이 워크플로우를 수동으로 실행할 수 있습니다
  workflow_dispatch:

# 워크플로우 실행은 하나 이상의 작업으로 구성되며, 이러한 작업은 순차적으로 또는 병렬로 실행될 수 있습니다
jobs:
  # 이 워크플로우는 "build"라고 불리는 단일 작업을 포함함
  build:
    # 작업이 실행될 러너의 유형
    runs-on: ubuntu-latest

    # 단계는 작업의 일부로 실행될 일련의 작업을 나타냅니다
    steps:
      # $GITHUB_WORKSPACE 아래에서 리포지토리를 체크아웃하여 작업이 이에 접근할 수 있도록 함
      - uses: actions/checkout@v4
      # https://github.com/actions/checkout 을 사용함.
      

      # 러너의 셸을 사용하여 단일 명령을 실행함
      - name: Run a one-line script
        run: echo Hello, world!

      # 러너의 셸을 사용하여 일련의 명령을 실행함
      - name: Run a multi-line script
        run: |
          echo Add other actions to build,
          echo test, and deploy your project.
