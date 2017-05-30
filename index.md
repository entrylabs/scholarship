<br>

## 자료 활용 방법

**데이터는 mongodb를 dump한 것이기 때문에
mongorestore를 통하여 복원 후 데이터 분석 하시는 것을 권장드립니다**

<hr/>

현재 엔트리에서 제공하는 데이터는 연구 및 분석에 쓰실 수 있도록 [2016년 코딩파티](https://playentry.org/codingparty/2016#!) 사용자들이 미션을 해결하는 일련의 과정을 로그 형태로 저장한 데이터입니다. 로그 데이터이기 때문에 용량이 커서 충분한 디스크 공간 확보가 필요합니다.<br><br>
데이터는 해당 페이지에 들어와 페이지를 떠나지 않고 연속적으로 미션을 해결한 부분에 대해서 기록되어 있습니다. 따라서 schema의 stages의 데이터 길이는 데이터 마다 상이합니다.<br><br>
데이터에는 사용자의 정보와 해당 사용자가 미션을 해결하는 과정에서 수행한 액션/커맨드(블록의 조립, 수정, 삭제, 실행, 정지 등)와 결과값(성공, 실패 등)들이 포함되어 있습니다. <br> 


<hr/>

### 데이터 스키마
* target
  * 데이터 수집 페이지(행사) 
* key
  * 사용자 식별자
* year
  * 출생년도
* gender
  * 1 == 남자
  * 2 == 여자
* swLearned 
  - 1 == learned
  - 2 == not learned
* difficulty
  * mode 
    * stage key
  * level
    * 1~5 high number means more difficulty
  * evalTime
    * evaluation time
 
* stages 
     * stageId 
      * 테이지 식별자 
     * startTime
      * 스테이지 시작 시간
     * finishTime
      * 스테이지 클리어 시간
     * actions    
        * name
          * user action name
        * data
          * key
            * property name
          * value
            * property value
          * timestamp
            * action이 발생한 시간 
* created
  * activity log 최초 생성 시간
* updated
  * activity log 마지막 갱신 시간

<hr/>

### code 구조
* code 
  * thread
    * block
      * params
      * statements

각 model의 명세는
[entryjs](https://github.com/entrylabs/entryjs)에 정의된 [code.js](https://github.com/entrylabs/entryjs/blob/master/src/workspace/code.js), [thread.js](https://github.com/entrylabs/entryjs/blob/master/src/workspace/thread.js), [block.js](https://github.com/entrylabs/entryjs/blob/master/src/workspace/block.js) 참고
<hr />

### 커맨드 타입
유저의 각 액션에 해당하는 commandType은
[entryjs](https://github.com/entrylabs/entryjs)에 정의된 [static 파일](https://github.com/entrylabs/entryjs/blob/master/src/util/static.js) 참고

<hr/>

### 유닛 액션 타입

**//unit action type**<br/>
STAND = 1;<br/>
WALK = 2;<br/>
JUMP = 3;<br/>
TURN_RIGHT = 4;<br/>
TURN_LEFT = 5;<br/>
SIMOOROOK = 6;<br/>
WALL_CRASH = 7;<br/>
BEE_ATTACK = 8;<br/>
ELECTRIC_SHOCK = 9;<br/>
SLIP = 10;<br/>
COMPLETE = 11;<br/>
STOP = 12;<br/>
SEQUENCE_SIMOOROOK = 13;<br/>
GET_ITEM = 14;<br/>
WITHOUT_ITEM_SUCCESS =15;<br/>
HALF_ROTATION = 16;<br/>
GO_SLOW = 17;<br/>
GO_SLOW_CRASH = 18;<br/>

**//space ship action type**<br/>
COLLISION = 13;<br/>
LOST = 14;<br/>

**//additional fail type**<br/>
ESSENTIAL_REQUIRED = 19;<br/>
OVER_LIMITED_BLOCK = 20;<br/>

**//animate type**<br/>
ROTATE = 1;<br/>
ROTATE_TO = 2;<br/>
ROTATE_INFINITE = 3;<br/>
FADE_OUT = 4;<br/>
POP_OUT = 5;<br/>
VIBRATE = 6;<br/>
    
<hr/>

### 데이터 다운로드 
[2016 코딩파티 데이터 다운로드](http://download.play-entry.org/data/entry_activity_201610.tar.gz)


<hr/>

contact info: vivid@entrylabs.org
    
<br><br>

