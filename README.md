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

    
