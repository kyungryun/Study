### head

- 문서 내용의 앞부분 출력

```bash
$ cat /etc/passwd | head -n 15 # 앞에서 15 줄 출력
$ cat /etc/passwd | head -n -5 # 마지막 5줄을 제외한 앞부분 출력
```

### tail

- 문서 내용의 뒷부분 출력
- -f : 추가되는 내용 대기 후 append하여 출력
- -F : 파일이 삭제 후 재 생성되어도 추적해여 출력해줌 (logrotate 에서 유용)

```bash
$ cat /etc/passwd | tail -n 15 # 뒤에서 15 줄 출력
$ cat /etc/passwd | tail -n +5 # 5 줄 부터 출력 (head의 제외와 다름)
```

### wc

- word count 명령어

```bash
$ wc -l /etc/passwd # 라인수 + 디렉토리 출력
$ wc -l /etc/passwd | awk '{ print $1 }' # 라인만 출력
```

### nl

- 파일 내용을 라인 넘버와 함께 출력
- -ba : 모든 라인에 대해 넘버링 (공백 포함)

### sort

- 파일 정렬 출력

### uniq

- 유니크 파일 출력

### cut

- 컬럼 잘라내기
- -f :필드(컬럼) 선택
- -d : tab 대신 사용할 구분자 지정

```bash
$ wc /etc/passwd -l | cut -d ' ' -f 1 # 공백을 기준으로 첫번째 컬럼만 출력
$ wc /etc/passwd -l | cut -d ' ' -f 1 --output-delimiter=">" # 구분자 변경 
```

### tr

- 어떤 내용을 변환 함
- 사용법 : tr [OPTION]... SET1 [SET2]

```bash
$ head /etc/passwd | tr [:lower:] [:upper:] # 소문자를 대문자로 변경
```

### sed

- stream editor
- {RANGE} p                  : range 내의 라인 출력
- {RANGE} d                  : range 내의 라인 삭제
- /SEARCHPATTERN/p : 패턴과 매치되는 라인 출력
- /SEARCHPATTERN/d : 패턴과 매치되는 라인 삭제
- s/REGEX/REPLACE/    : REGEX에 매치되는 부분을 REPLACE로 교체

```bash
# 2~5라인만 출력하는것이 아닌 stream editor 뜻 그대로 전체 내용을 출력하고 조건에 부합하는 내용만
# 한번씩 더 출력
$ head /etc/passwd | sed '2,5p' 

# 기본출력을 없애는 옵션 -n
$ head /etc/passwd | sed -n '2,5p'

# d 옵션일땐 -n을 안써도 됨
```

### awk

- 텍스트처리 스크립트
- syntax : awk options ‘selection _criteria {action }’ input-file
- 자주 사용되는 옵션
    - -F : 필드 구분자 지정
- 주요 내장 변수
    - $1, $2, $3 :필드 수

```bash
$ wc /etc/passwd | awk '{ print $1 }' # 1번째 컬럼 출력
```
