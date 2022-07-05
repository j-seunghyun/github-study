# github-study

## github

   * github이란 ?
   
      - github은 VCS 종류의 프로그램들 중 하나
      - VCS는 version control system <버전 컨트롤 시스템>
      - 프로그램의 버전 관리 툴
      - 프로그램의 시간과 차원을 넘나드는 것
   
   * CLI vs GUI

      - CLI는 command line interface (명령줄을 입력해서 사용하는 것)
      - GUI는 graphic user interface (그래픽 요소를 활용한 인터페이스)
      - CLI와 GUI를 혼용해서 활용할 방법에 따라 사용하는 것이 좋다.

   * git init

      - git init명령어로 git관리 시작한다는 것
      - .git 폴더 생성 확인 가능하며 이 폴더 지우면 Git 관리내역이 삭제된다.
      - 소스트리 GUI 프로그램을 통해서는 create버튼을 누르면 폴더에 .git폴더가 생성되면서
      같은 역할을 함을 볼 수 있다.

   * git status

      - 현재 폴더에서 현재 폴더의 상황을 git의 관점으로 보여주는 것
      - 같은 방식으로 소스트리에서 폴더를 드래그함으로서 현재 저장소를 추가할 수 있다.
   
      - .git폴더 삭제하고 git status명령을 보면 git이 관리하고 있지 않으므로 
      not a git repository라고 알려준다.
   
   * git의 관리에서 특정 파일/폴더를 배제해야 할 경우

     - 포함 필요 x

         - 자동으로 생성 또는 다운로드 되는 파일들(빌드 -> java가 class파일로 빌드되는 것처럼 , 라이브러리)

         - 이러한 파일들은 굳이 git에서 버전관리를 하지 않아도 언제든 인터넷 등에서 다운로드 가능하기 때문에

     - 포함하지 말아야 할 때

         - 보안상 민감한 정보를 담은 파일(따로 관리하는게 좋음)

      
   - .gitignore파일을 사용해서 배제할 요소들 지정 가능하다.

         - .gitignore라는 파일을 자체적으로 생성하고 그 안에 무시할 파일을 추가해줌으로서 사용
         
         - 추가를 완료한 후 git status명령을 통해 확인했을때 더 이상 추가한 파일은 git에서 관리하지 않음을 확인할 수 있다. 

         - .gitignore형식 확인 https://git-scm.com/docs/gitignore
            # 이렇게 #를 사용해서 주석

            # 모든 file.c
            file.c

            # 최상위 폴더의 file.c
            /file.c

            # 모든 .c 확장자 파일
            *.c

            # .c 확장자지만 무시하지 않을 파일
            !not_ignore_this.c

            # logs란 이름의 파일 또는 폴더와 그 내용들
            logs

            # logs란 이름의 폴더와 그 내용들
            logs/

            # logs 폴더 바로 안의 debug.log와 .c 파일들
            logs/debug.log
            logs/*.c

            # logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
            logs/**/debug.log

   * 버전을 만들기

      - git status 명령
            - 변경사항 확인
            - untracked(추적하지 않은) -> 아직 git의 관리에 들어가지 않은 파일

      - git add 명령
            - 파일을 버전(타임캡슐)에 담기
            - git add [파일이름] 으로 사용할때도 있지만
            보통의 경우 git add .으로 다 같이 stage에 올림

      - git commit 명령
            - 버전에 담은 파일을 묻기(타임 캡슐이라고 생각)
            - default로 git commit명령을 실행하면 vim 에디터 실행됨.
            - git commit -m "message" -> commit메세지와 동시에 commit함
            - 파일들을 다 수정한 뒤 commit하면 한번에 가능 git은 그 당시의 상태를 기준으로 저장하기 때문에 commit하기 전 상태와 후 상태를 기준으로 함.
            (결국 commit의 상태 기준이라는 것)
            - source tree에서 History로 확인 가능하다.
      
      - git log 명령
            - commit한 상태에 대한 기록을 확인 가능

   * 파일 수정 후 상태 확인하기

      - git status를 통해 상태 확인
            ex) 파일 하나 삭제, 파일 하나 수정, 새로운 파일 생성을 했다고 한다면 그에 맞게 삭제되거나 수정된 것은 
            not commit으로 알려주고 , 새로 생성된 파일은 git의 관리를 안받고 있다는 의미로 untracked files라고 알려준다.

      - git diff를 통해 달라진점 확인
            -> git status와 다른점은 git의 관리를 아직 안 받고 있는 untracked files(추적되지 않는 파일)에 대해서는 확인하지 못하고 기존에 관리 받고 있던 파일들에 대해서 어떤점이 변경되고 수정되었는지 확인할 수 있다.

      - add와 commit을 동시에 하는 명령어
            - git commit -am "메세지"
            - source tree에서도 똑같이 stage에 올리는 일을 할 수 있고 같은 리포지토리를 참조하고 있기에 결과 반영은 똑같이 된다.
            - 새로 추가된(untracked) 파일이 없을 때 한정!
      
   * 과거로 돌아가는 법(과거의 commit 상태로)

      - Reset

            - 시간을 과거로 되돌리는 것
            - 되돌린 commit상태 이후의 것들은 history에서 지움
            - 즉 , 원하는 시점으로 돌아간 뒤 이후 내역들을 지움
            - reset을 할 때는 돌아가려는 시점의 해시값이 필요하다.
            - 아니면 tag를 통해 달아놓은 값을 사용한다.
            - 그냥 git reset 명령을 사용할 경우 commit을 실행하기 전 상태로 되돌아가므로 정말 reset을 시키려면 unstaged를 시켜줘야 한다.
            - git reset --hard [해시값] -> 중간과정 없이 아예 기록 삭제시키고 돌아가는 방법
            
            - 복원
                  - 백업해 둔 .git폴더를 사용
                  - git log와 git status로 상태를 확인하면 log의 경우 reset을 하기 전 리포지토리에 저장되어 있던 log가 그대로 있는 것을 볼 수 있고 
                  - git reset -- hard 명령으로 현 커밋 상태를 초기화 시킬 수 있다.
                  - git reset --hard의 경우 뒤에 커밋 해시가 없다면 마지막 커밋을 기본으로 가리킴.
                  - 고로 log들을 다 가져온 상태에서 마지막 커밋으로 돌아가는 것이기에 복원이 되는 것!!
                  - 문제가 발생하는 점은 commit의 log를 가져옴에 따라서 git은 log의 마지막 commit까지 한번에 일어난 것이라고 착각하게 된다는 것이다.

      
      - Revert 

            - 되돌릴 commit 상태 이후의 것들을 삭제하는 것이 아니다.
            - 이후의 변화를 거꾸로 수행하는 commit을 함으로써 되돌리는 상태로 만들어 주는 것.
            - 되돌리기 원하는 시점의 커밋을 거꾸로 실행.
            - 문제가 생기는 commit만을 콕 집어서 되돌리기 위할때 사용
            - 또한 협업을 할 때 한번 공유공간에 올라간 내역을 reset해버리면 그걸 기반으로 작업한 다른사람들의 코드와 심각한 충돌 발생
            - 공유를 하고 있는 작업의 경우 revert를 꼭 사용
      
      - repository는 .git으로 관리되기 때문에 백업 파일을 만들어 둘때는 .git만 복사해서 백업해두는 방식을 활용하면 된다.



      ## git의 내부구조 파악

      * git init명령을 통해 git관리를 시작하면 .git파일이 생성되면서 git관리가 시작됨을 볼 수 있다. 여기서 tree -a명령을 사용하면 git의 구조를 tree구조로 확인가능하다.

      * tree명령의 경우 기본으로 windows에는 사용불가능하므로 windows에도 사용할 수 있게 별도로 tree.exe를 설치해서 사용해야 한다.

            * SHA-1 해시

                  - git은 데이터를 저장하기 전에 항상 체크섬을 구하고 그 기준으로 데이터를 관리

                  - git은 SHA-1 해시를 사용(160bits 사용 - 16진수 문자열 형태로 표현해서 40자)

                  - 앞의 몇 글자만 사용해도 대부분 겹치지 않는다.

                  - SHA-1 해시값을 git에서는 key값으로 사용한다.

                  - 보통의 경우 7~8글자를 hash값으로 사용한다.

                  - .git/objects 디렉토리 아래 40글자 중 남은 2글자로 디렉토리를 만들고 남은 38자리로 파일명으로 해서 내용을 저장한다.

                  - .git/objects 디렉토리 아래에는 최대 256개의 디렉토리가 생성된다.

      * git은 내용을 주소로 활용!!

            * git은 내용을 주소로 활용하는 파일시스템

                  - 전체 내용을 hash값을 사용해서 주소로 활용하는 파일시스템

            * 내부는 사실 꽤 단순한 키-밸류 데이터베이스

                  - 어떤 데이터든 git에 담을 수 있고, git은 그 데이터의 sha1 hash값을 key값으로 해서 저장을 하고 나중에 key값을 기준으로 저장한 데이터를 찾을 수 있다.

            * Plumbing

                  - 저수준의 기본적인 일을 처리하는 plumbing 명령어

            * porcelain

                  - 고수준에서 사용자가 일반적으로 쓰는 porcelain 명령어
                  - 보통 우리가 쓰는 git의 명령어들은 porcelain 명령어이고 plumbing이 porcelain안에서 활용되어 명령어들을 처리하게 된다.
      
      * 일반적으로 File system 위에 git은 key-value storage로 단순화해서 사용하고 그것을 다루는 plumbing명령어군이 있고 plumbing명령어를 사용하는 porcelain 명령들이 있다. 그리고 우리가 사용하는 GUI나 IDE는 대부분 porcelain명령어를 사용하고 가끔은 plumbing명령을 사용하면서 우리가 원하는 일들을 처리해준다.

      * git이 저장하는 Objects

            * blob

                  - blob은 binary large object의 줄임말로 내부적으로 git add 명령으로 추가한 파일(프로젝트에 필요한 소스 파일, 이미지 파일 등)의 경우 기본적으로 blob파일로 저장하는데, 파일명 같은 메타데이터 없이 바이너리 데이터 자체만 저장한다.

                  - git hash-object라는 plumbing 명령어를 통해 생성가능 하고
                  git add README.md와 같은 porcelain명령어를 통해서도 생성가능하다.

                  - git은 내부적으로 저장하는 object파일들을 모두 zlib으로 압축해서 저장하므로 이를 확인하기 위해서는 zlib으로 압축을 풀어야 한다.

                  - ruby -rzlib -e 'p Zlib::Inflate.inflate(STDIN.read) < .git/objects/11/a1574a70b411c4b5646409608c8ab9500f48f8 이런식으로 압축을 풀어서 강제로 내용을 확인 할 수 있다.

                  - 확인해보면 blob의 경우 저장될 때 먼저 오브젝터 헤더가 저장되고 

            * tree

                  - 파일 이름과 기본 속성, 그리고 어느 디렉토리에 속하는 지의 정보 기록

                  - tree 오브젝트는 특정 시점의 디렉토리

                  - 디렉토리이기 때문에 tree 오브젝트 아래에는 여러 blob과 여러 tree가 들어갈 수 있다.

                  * tree 를 찾는 방법
                        
                        - ㅇㄴㄹㅇㄹㄴㄹ

                  * tree 저장 포맷

                        * tree_바이트수\0

                        - 타입_파일명\0오브젝트ID (트리에 포함된 아이템에 대해서)

                        * 타입 : 100644(일반 파일), 100755(실행할 수 있는 파일), 040000(디렉토리)

                        * 공백문자('_')
                        * 파일명 : NULL로 끝나는 문자열
                        * SHA1 해시값 : 20바이트 바이너리(오브젝트 ID이자 key값)
                  
            * 오브젝트 내용을 편하게 보는 방법

                  * git cat-file -t 해시값 -> 오브젝트의 type을 확인

                  * git cat-file -p 해시값 -> 오브젝트의 내용을 확인

            * commit

            * 오브젝트 헤더

                  - blob_바이트수\0

                   * 각 오브젝트 헤더는 , blob/tree/commit 등의 문자열로 시작
                   * 공백 문자(blob뒤에 '_'는 공백이라는 뜻)
                   * 헤더를 제외한 본문의 바이트 수를 문자열로 표기
                   * 마지막은 NULL문자로 헤더의 끝을 의미

             - git은 위와 같은 blob, tree, commit과 같은 object들을 sha-1 key값으로 보관을 한다.

            * master

            * Head

            * v1.0과 같은 tag들

             - git은 위와 같은 master, Head, v1.0과 같은 tag들을 reference라고 하는데 이름으로 지칭하는 값들이다.


