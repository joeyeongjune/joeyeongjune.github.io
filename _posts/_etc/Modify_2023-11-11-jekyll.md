

# Jekyll+GithubPage 를 이용한 블로그 구축

- OS : Windows 11

## Install Ruby

- [Ruby Download](https://www.ruby-lang.org/)
- 32bit로 다운로드 해서 설치 해준다
- 버전 확인
  - `CMD) ruby -v`
  `ruby 3.1.4p223 (2023-03-30 revision 957bb7cb81) [i386-mingw32]`

## Install jekyll, bundler, github-pages

- `CMD) gem install jekyll bundler github-pages`
- 버전 확인
  - `CMD) jekyll -v`
  `jekyll 4.3.2`

## jekyll 폴더 생성

- `CMD) jekyll new myblog`
  - myblog 폴더가 생성 되면서 jekyll 파일들이 생성된다
  - 만약, 별도의 폴더를 지정 하고 싶다면 해당 폴더로 이동후
  -  `jekyll new .` 커맨드를 실행 한다.
  -  주의할 점은 폴더 안에 파일이 있으면 에러가 생긴다
  -  그럴경우 폴더 내의 파일일 삭제후 다시 커맨드를 실행 하던지,
  -   `jekyll new . --force` 강제 옵션을 줘서 실행 하면 된다

## jekyll 서버 기동

- `CMD) cd myblog`
- `CMD/myblog) bundle exec jekyll serve`
  - 생략
    Server address: http://127.0.0.1:4000/

## 접속

- 브라우저를 열고 `http://127.0.0.1:4000/` 접속


## Jekyll theme Download

- minimal-mistakes-4.24.0


-----
D:\github\joeyeongjune.github.io>git add .
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of '404.html', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'Gemfile.lock', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of '_config.yml', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'about.markdown', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'index.markdown', LF will be replaced by CRLF the next time Git touches it

D:\github\joeyeongjune.github.io>git config --global core.autoCRLF false