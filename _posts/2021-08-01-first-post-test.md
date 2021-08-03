---
title: "Mac) github.io 만들기_01: 환경설정"
excerpt: "Mac에 guthub.io(깃허브 블로그)를 만들기 위한 환경을 세팅 해보자. "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
date: 2020-05-25
last_modified_at: 2020-05-25
# author_profile: true
# sidebar:
#   nav: "main"
---

# Mac) github.io 만들기, 깃헙 블로그, jekyll

bundle exec jekyll serve

1. 환경 설정
   1. homebrew install: terminal 에 입력하여 homebrew 를 설치한다.
      (사이트 참조: [https://brew.sh/index_ko](https://brew.sh/index_ko))
      **/bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"**
   2. **brew install rbenv**: mac 은 기본적으로 ruby 가 설치되어 있다. 이에 따라 알맞은 버전의 ruby 를 설치하고 경우에 따라 원하는 버전의 ruby 를 사용해야할 일이 있을 수 있는데 rbenv 를 이용해 ruby 설치 및 버전관리를 진행한다. 터미널에 brew install rbenv 입력하여 다운.
   3. 알맞은 ruby 설치: [https://www.ruby-lang.org/en/downloads/](https://www.ruby-lang.org/en/downloads/) 를 참고하여 알맞은 version을 설치하자. 나는 2.6.8이 설치 가능한 버전이며 EOL 이어서 설치했다. rbenv install 2.6.8
      1. 설치전 체크할 것!
      2. rbenv versions:
      - system (set by /Users/"내컴퓨터이름"/.rbenv/version) 이렇게 나오면서 현재 ruby는 기존 설치되어 있던 ruby를 쓰고 있음을 알 수 있다.
      3. rbenv install -l: 설치 가능한 ruby의 버전을 확인 할 수 있다.
   4. 설치한 ruby 로 변경
      1. rbenv versions: 다시 한번 확인하면 다음과 같이 나온다.
      - system (set by /Users/"내컴퓨터이름"/.rbenv/version)
        2.6.8
      2. rbenv global 2.6.8: ruby 사용 버전을 설치한 2.6.8 로 바꿔준다.
         rbenv versions 를 입력하면 다음과 같이 바뀐 것을 알 수 있다.
         system
      - 2.6.8 (set by /Users/"내컴퓨터이름"/.rbenv/version)
      3. 터미널을 종료하고 재실행 한 뒤 ruby -v 를 입력하면 버전이 올바르게 반영 된 것을 볼 수 있다.
   5. ~~gem install --user-install bundler jekyll: jekyll, bundler 설치 하는 명령어
      만약 다음과 같은 오류가 뜬다면
      WARNING:  You don't have /Users/"내컴퓨터이름"/.gem/ruby/2.6.0/bin in your PATH, gem executables will not run.
      2.6.8 을 2.6.0 으로 인지해야 하기 때문이다. 즉 path 설정을 해주면 되는데
      echo 'export PATH="$HOME/.gem/ruby/2.6.0/bin:$PATH"' >> ~/.zshrc~~
   6. gem install bundler jekyll: 이거 일때는 괜찮?
      export PATH="$HOME/.rbenv/bin:$PATH"
      eval "$(rbenv init -)"
      를 ~/.zshrc 에 추가해준다.
   7. jekyll -v: jekyll 4.2.0, bundler -v: Bundler version 2.2.24임을 확인할 수 있다.
   8. gem 으로 install 한 것들을 다 날리고 싶다면 gem uninstall -aIx 또는 gem uninstall —aIl
2. github repository 생성 및 클론
   1. Repository name 은 username.github.io 로 한다. 예) minsu.github.io
3. jekyll theme 고르기

   1. [http://jekyllthemes.org/](http://jekyllthemes.org/), [http://themes.jekyllrc.org/](http://themes.jekyllrc.org/), [https://jekyllthemes.io/](https://jekyllthemes.io/) 와 같은 사이트에서 원하는 테마를 고른다. 나는 [https://github.com/mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) 이 테마 사용한다. 얘네는 가이드도 있다 [https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
   2. 골랐으면 해당 깃을 클론한다. git clone [https://github.com/mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)
   3. .git 파일을 지워준다.
   4. [https://mmistakes.github.io/minimal-mistakes/docs/installation/#install-dependencies](https://mmistakes.github.io/minimal-mistakes/docs/installation/#install-dependencies) 을 참조하여 Gemfile 을 수정한다. 아래 코드와 같다.

      ```ruby
      source "https://rubygems.org"

      # Hello! This is where you manage which Jekyll version is used to run.
      # When you want to use a different version, change it below, save the
      # file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
      #
      #     bundle exec jekyll serve
      #
      # This will help ensure the proper Jekyll version is running.
      # Happy Jekylling!

      # gem "github-pages", group: :jekyll_plugins

      # To upgrade, run `bundle update`.

      gem "jekyll"
      gem "minimal-mistakes-jekyll"

      # The following plugins are automatically loaded by the theme-gem:
      #   gem "jekyll-paginate"
      #   gem "jekyll-sitemap"
      #   gem "jekyll-gist"
      #   gem "jekyll-feed"
      #   gem "jekyll-include-cache"
      #
      # If you have any other plugins, put them here!
      group :jekyll_plugins do
      end
      ```

   5. [https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remove-the-unnecessary](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remove-the-unnecessary) 을 참고하여 추가적으로 불필요한 파일을 삭제한다. 아래와 같다.
      - `.editorconfig`
      - `.gitattributes`
      - `.github`
      - `/docs`
      - `/test`
      - `CHANGELOG.md`
      - `minimal-mistakes-jekyll.gemspec`
      - `README.md`
      - `screenshot-layouts.png`
      - `screenshot.png`
