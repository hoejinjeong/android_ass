# Git 명령어 

---

## 1. 설정과 초기화


+ #### 전역 사용자명/이메일 구성하기
 ``` 
 git config - -global user.name “Your name”
 git config - -global user.email “Your email address” 
 ```

+ #### 저장소별 사용자명/이메일 구성하기 
```
git config user.name “Your name”
git config user.email “Your email address”
```

+ #### 전역 설정 정보 조회
```
git config - -global - -list
```

+ #### 저장소별 설정 정보 조회
```
git config - -list
```

+ #### Git의 출력결과 색상 활성화하기
```
git config - -global color.ui “auto”
```

+ #### 새로운 저장소 초기화하기
```
mkdir /path/newDir
cd /path/newDir
git init
```

+ #### 저장소 복제하기
```
git clone <저장소 url>
```

+ #### 새로운 원격 저장소 추가하기
```
git remote add <원격 저장소> <저장소 url>
```

---

## 2. 기본적인 사용법


+ #### 새로운 파일을 추가하거나 존재하는 파일 스테이징하고 커밋하기
```
git add <파일>
git commit -m “<메시지>”
```

+ #### 파일의 일부를 스테이징하기
```
git add -p [<파일> [<파일> [기타 파일들…]]]
```

+ #### add 명령에서 Git 대화 모드를 사용하여 파일 추가하기
```
git add -i
```

+ #### 수정되고 추적되는 파일의 변경 사항 스테이징하기
```
git add -u [<경로> [<경로>]]
```

+ #### 수정되고 추적되는 모든 파일의 변경 사항 커밋하기
```
git commit -m “<메시지>” -a
```

+ #### 작업 트리의 변경 사항 돌려놓기
```
git checkout HEAD <파일> [<파일>]
```

+ #### 커밋되지 않고 스테이징된 변경 사항 재설정하기
```
git reset HEAD <파일> [<파일>]
```

+ #### 마지막 커밋 고치기
```
git commit -m “<메시지>” - -amend
```

+ #### 이전 커밋을 수정하고 커밋 메시지를 재사용하기
```
git commit -C HEAD - -amend
```

---

## 3. 브랜치


+ #### 지역 브랜치 목록 보기
```
git branch
```

+ #### 원격 브랜치 목록 보기
```
git branch -r
```

+ #### 지역과 원격을 포함한 모든 브랜치 목록 보기
```
git branch -a
```

+ #### 현재 브랜치에서 새로운 브랜치 생성하기
``` 
git branch <새로운 브랜치>
```

+ #### 다른 브랜치 체크아웃하기
```
git checkout <브랜치>
```

+ #### 현재 브랜치에서 새로운 브랜치 생성하고 체크아웃하기
``` 
git checkout -b <새로운 브랜치>
```

+ #### 다른 시작 지점에서 브랜치 생성하기
```
git branch <새로운 브랜치> <브랜치를 생성할 위치>
```

+ #### 기존의 브랜치를 새로운 브랜치로 덮어쓰기
```
git branch -f <기존 브랜치> [<브랜치를 생성할 위치>]
```

+ #### 브랜치를 옮기거나 브랜치명 변경하기
``` 
git checkout -m <기존 브랜치> <새로운 브랜치>
```

+ #### <새로운 브랜치>가 존재하지 않을 경우
```
git checkout -M <기존 브랜치> <새로운 브랜치>
```

+ #### 무조건 덮어쓰기
```
git merge <브랜치>
```

+ #### 커밋하지 않고 합치기
```
git merge - -no-commit <브랜치>
```

+ #### 선택하여 합치기
```
git cherry-pick <커밋명>
```

+ #### 커밋하지 않고 선택하여 합치기
```
git cherry-pick -n <커밋명>
```

+ #### 브랜치의 이력을 다른 브랜치에 합치기
```
git merge - -squash <브랜치>
```

+ #### 브랜치 삭제하기
```
git branch -d <삭제할 브랜치>
```

+ #### 삭제할 브랜치가 현재 브랜치에 합쳐졌을 경우에만
```
git branch -D <삭제할 브랜치>
```

## 4. Git 이력


모든 이력 보기
git log
변경 사항을 보여주는 패치와 함께 로그 표시하기
git log -p
1개의 항목만 보이도록 로그 개수 제한하기
git log -1
20개의 항목과 패치만 보이도록 로그 제한하기
git log -20 -p
6개월 동안의 커밋 로그 보기
git log - -since=”6 hours”
이틀 전까지의 커밋 로그 보기
git log - -before=”2 days”
HEAD보다 세 개 이전의 커밋 로그 보기
git log -1 HEAD-3
git log -1 HEAD^^^
git log -1 HEAD~1^^
두 지점 사이의 커밋 로그 보기
git log <시작 지점>…<끝 지점>
시작 지점이나 끝 지점은 커밋명, 브랜치명, 혹은 태그명이 될 수 있고 조합하여 사용 가능하다.
각 항목의 로그 이력 한 줄씩 보기
git log - -pretty=oneline
각 항목마다 영향 받은 줄의 통계 보기
git log - -stat
커밋할 시점의 파일 상태 보기
git log - -name-status
현재 작업 트리와 인덱스의 차이점 보기
git diff
인덱스와 저장소의 차이점 보기
git diff - -cached
작업 트리와 저장소의 차이점 보기
git diff HEAD
작업 트리와 특정 위치 간의 차이점 보기
git diff <시작 지점>
시작 지점은 커밋명 or 브랜치명 or 태그명이다.
저장소의 두 지점 사이의 차이점 보기
git diff <시작 지점> <끝 지점>
차이점의 통계 보기
git diff - -stat <시작 지점> [<끝 지점>]
파일의 커밋 정보 줄 단위로 보기
git blame <파일>
파일의 줄 단위의 복사, 붙여 넣기, 이동 정보 보기
git blame -M <파일>
파일의 줄 단위의 이동과 원본 파일 정보 보기
git blame -C -C <파일>
로그에서 복사와 붙여 넣은 정보 보기
git log -C -C -p -1 <특정 지점>

## 5. 원격 저장소


저장소 복제하기
git clone <저장소>
마지막 200개의 커밋만 포함하여 저장소 복제하기
git clone - -depth 200 <저장소>
새로운 원격 저장소 추가하기
git remote add <원격 저장소> <저장소 url>
모든 원격 브랜치 목록 보기
git branch -r
원격 브랜치에서 지역 브랜치 생성하기
git branch <새로운 브랜치> <원격 브랜치>
원격 태그에서 지역 브랜치 생성하기
git branch <새로운 브랜치> <원격 태그>
origin 저장소에서 합치지 않고 지역 브랜치로 변경 사항 가져오기
git fetch
원격 저장소에서 합치지 않고 지역 브랜치로 변경 사항 가져오기
git fetch <원격 저장소>
원격 저장소에서 변경 사항을 가져와 현재 브랜치에 합치기
git pull <원격 저장소>
origin 저장소에서 변경 사항을 가져와 현재 브랜치에 합치기
git pull
지역 브랜치를 원격 브랜치에 푸싱하기
git push <원격 저장소> <지역 브랜치>:<원격 브랜치>
지역 브랜치를 동일한 이름의 원격 브랜치에 푸싱하기
git push <원격 저장소> <지역 브랜치>
새로운 로컬 브랜치를 원격 저장소에 푸싱하기
git push <원격 저장소> <지역 브랜치>
원격 저장소에서 쓸모가 없어진 원격 브랜치 제거하기
git remote prune <원격 저장소>
원격 저장소를 제거하고 관련된 브랜치도 제거하기
git remote rm <원격 저장소>

출처 : https://medium.com/@joongwon/git-git-명령어-정리-c25b421ecdbd

헤더 (top)
H1 ~ H6까지 테그를 #으로 표현

# 헤더 스타일 (h1)
## 헤더 스타일 (h2)
### 헤더 스타일 (h3)
#### 헤더 스타일 (h4)
##### 헤더 스타일 (h5)
###### 헤더 스타일 (h6)
출력 결과
헤더 스타일 (h1)
헤더 스타일 (h2)
헤더 스타일 (h3)
헤더 스타일 (h4)
헤더 스타일 (h5)
헤더 스타일 (h6)
효과: 다음과 같은 코드와 동일한 결과가 됨
<h1>헤더 스타일 (h1)</h1>
<h2>헤더 스타일 (h2)</h2>
<h3>헤더 스타일 (h3)</h3>
<h4>헤더 스타일 (h4)</h4>
<h5>헤더 스타일 (h5)</h5>
<h6>헤더 스타일 (h6)</h6>
수평선 (top)
<hr />와 동일한 결과를 출력
’-‘, ‘*‘, ‘_‘을 세개 이상 나열하면 수평선을 만듦
단락 나누기 용도로 많이 사용.
***
___
___
출력 결과
텍스트 출력 (top)
별도의 테그 없이 입력된 내용은 <p> ~ <\p> 처리가 됨

markdown은 직관적이고 간단한 문법으로 컨텐츠 관리에 매우 효과적입니다.
효과: 다음과 같은 코드와 동일한 결과가 됨
<p>markdown은 직관적이고 간단한 문법으로 컨텐츠 관리에 매우 효과적입니다.</p>
텍스트 강조 (top)
*single asterisks* - 기울임체
_single underscores_ - 기울임체
**double asterisks** - 굵은글씨체
__double underscores__ - 기울임체/굵은글씨체
***triple underscores*** - 기울임체/굵은글씨체
~~cancelline~~ - 취소줄
결과 출력

 
single asterisks - 기울임체
single underscores - 기울임체
double asterisks - 굵은글씨체 
double underscores - 기울임체/굵은글씨체
triple underscores - 기울임체/굵은글씨체 
cancelline - 취소줄

인용 (top)
분문 중 인용된 글을 표시할 때 사용하며, “>” 기호를 모든 줄 앞에 붙임.
”>” 기호의 개수에 따라 들여쓰기 레벨 조정 가능
인용 블록 안에서 다른 마크다운 테그를 포함할 수 있음
인용 블록 안에서 중첩 인용 표기 가능
인용 예제 1: 기본 스타일
> 인용되는 글입니다. > 인용되는 글의 두 번째 줄. > 인용되는 글의 세 번째 줄.
출력 결과
인용되는 글입니다. 
인용되는 글의 두 번째 줄.
인용되는 글의 세 번째 줄. 

인용문의 레벨을 설정 할 수 있음
인용 예제 2: 중첩 인용 및 스타일 적용
> 인용되는 첫 번째 줄입니다.
>> 인용되는 내용 안에서 다시 인용되는 부분입니다.
> (인용 수준을 변경할 때 이렇게 빈 줄 하나 넣어주세요)
> 꺽쇠 한 번만 쓰면 다시 상위 수준으로 표시됩니다.
> ###### 인용문 내부 헤더
인용되는 첫 번째 줄입니다.

인용되는 내용 안에서 다시 인용되는 부분입니다.

(인용 수준을 변경할 때 이렇게 빈 줄 하나 넣어주세요)

꺽쇠 한 번만 쓰면 다시 상위 수준으로 표시됩니다.

인용문 내부 헤더
인용 예제 2: tab 을 적용한 인용
인용 기호 앞에 tab을 입력하면 인용문의 들여 쓰기를 작성 가능.
> 인용되는 글입니다. > 인용되는 글의 두 번째 줄. > 인용되는 글의 세 번째 줄.
출력 결과

인용되는 글입니다. 
인용되는 글의 두 번째 줄.
인용되는 글의 세 번째 줄. 
인용문의 레벨을 설정 할 수 있음

목록 (top)
MarkDown으로 숫자 리스트, 블릿 리스트를 표현할 수 있음.
순차가 없는 리스트를 표현할 때는 ‘*‘, ‘+’, ‘-” 기호 사용 가능.
순차가 있는 리스트를 표현할 때 ‘숫자’ 사용용
* 리스트1 + 리스트2 * 서브 리스트1 * 서브리스트 2 - 리스트3 1. 순차 리스트1 2. 순차 리스트2
출력 결과

리스트1

리스트2

서브 리스트1
서브리스트 2
리스트3

순차 리스트1
순차 리스트2
코드 (top)
코드 유형 1: 공백
4개의 공백 또는 하나의 탭으로 들여쓰기를 만나면 변환되기 시작하여 들여쓰지 않은 행을 만날때까지 변환이 계속됨.

공백 없이 바로 시작...

    스페이스 4개로 시작
    스페이스 4개로 시작

공백 없이 바로 시작...
출력 결과
공백 없이 바로 시작…

스페이스 4개로 시작
스페이스 4개로 시작
공백 없이 바로 시작…

코드 유형 2: 코드 블록
코드 첫라인 앞과 마지막 라인 다음에 “`” (fense) 설치
코드 유형 3: 인라인 코드
스칼라에서는 `val a:Int = 3`과 같은 형식으로 변수를 선언합니다.
출력 결과
스칼라에서는 val a:Int = 3과 같은 형식으로 변수를 선언합니다.

테이블 (top)
| 이름   | 설명  | 나이 |
| ----- | ---- | --- |
| 김태완  | 아빠  | 40 |
| 임선영  | 엄마  | 30 |
| 김민수  | 아들  | 2  |
이름	설명	나이
김태완	아빠	40
임선영	엄마	30
김민수	아들	2
테이블 정렬
테이블 정렬: 헤더와 row 구분 자에 적용
오른쪽 정렬
—-:
왼쪽 정렬
:—-
가운데 정렬
:—-:
| 이름   | 설명  | 나이 |
| :----- | ----: | :---: |
| 김태완  | 아빠  | 40 |
| 임선영  | 엄마  | 30 |
| 김민수  | 아들  | 2  |
이름	설명	나이
김태완	아빠	40
임선영	엄마	30
김민수	아들	2
링크 (top)
기본 링크
기본 문법: [링크걸 문구](http://주소)
[taewan.kim](http://taewan.kim)
HTML 변환 결과
<a href="http://taewan.kim">taewan.kim</a>
출력 결과
taewan.kim

타이틀을 포함하는 링크
기본 문법: [링크걸 문구](http://주소 “타이틀 문구”)
“타이틀 문구”는 툴팁으로 표현 됨
[taewan.kim](http://taewan.kim "김태완 블러그")
HTML 변환 결과
<a href="https://taewan.kim" title="김태완 블러그">taewan.kim</a>
출력 결과
taewan.kim

참조 링크
주소를 id로 참조
[id] 형식으로 지정
    [구글][1]
    [1]: http://www.google.com
출력 결과
구글

주소만으로 링크
주소를 “<“와 “>“기호로 감싸서 사용
<http://taewan.kim>
HTML 변환 결과
<a href="https://taewan.kim">http://taewan.kim</a>
출력 결과
http://taewan.kim

네임드 앵커
네임드 앵커는 특정 앵커로 점프하는 용도로 적합.

### 테이블 구성
  * [1장](#chapter-1)
  * [2장](#chapter-2)
  * [3장](#chapter-3)

###### 1장 <a id="chapter-1"></a>
1장의 내용은.....

###### 2장 <a id="chapter-2"></a>
2장의 내용은.....

###### 3장 <a id="chapter-3"></a>
3장의 내용은.....
출력 결과
테이블 구성
1장
2장
3장
1장
1장의 내용은…..

2장
2장의 내용은…..

3장
3장의 내용은…..
