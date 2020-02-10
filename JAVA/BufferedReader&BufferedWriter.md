
# JAVA 입출력 함수 - BufferedReader / BufferWriter

  BufferedReader / BufferedWriter은 이름처럼 버퍼를 이용해서 읽고 쓰는 함수이다.
  버퍼를 이용하는 이 함수를 통해 입출력을 실행하면 효율이 비교할수 없을만큼 좋아 진다.
  
  ![Buffer](../image/bufferuse.PNG)  
  
  하드디스크는 매우 속도가 느린 장치로 문자의 정보를 목적지로 바로 이동시키는 것보다 중간에 메모리 버퍼를 둬서 데이터를 한데 묶어서 이동시키는 것이 보다 효율적이고 바르다.
  
  예를 들자면, 흙을 파서 저 옮기는데, 한 번 삽질할때마다 가서 옮기는것 보단, 수레에 가득 채워서 한번에 나르는 것이 효율적인 것과 같은 이치이다. 즉, 모아뒀다가 한 번에 전송 하는것이 훨씬 더 효율적이다.
  
  - 버퍼 (Buffer)
    데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 임시 메모리 영역
    입출력 속도 향상을 위해 버퍼를 사용한다.
    
  - 버퍼 플러시 (Buffer Flush) - flush()
    버퍼에 남아 있는 데이터를 출력시킴 (버퍼를 비우는 동작)
    
  - 버퍼를 이용한 입력
    BufferedReader
    
  - 버퍼를 이용한 출력
    BufferedWriter
    
## BufferedReader

  Scanner를 통해 입력받는 경우 스페이스(띄어쓰기)와 엔터(개행문자)를 경계로 입력 값을 인식하기 때문에 따로 가공할 필요가 없어서 사용하기 매우 편리하다. 반면에 __ BufferedReader는 엔터만 경계로 인식하고 받은 데이터가 String로 고정 __ 되기 때문에 데이터를 다로 가공해야 하는 경우가 많다.
    
  