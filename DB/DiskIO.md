
#IO

    __ DiskIO란 __
    
      * 데이터를 작성하고 변경할시 디스크에 저장되는 것
      
* 오라클 스토리지의 구조 7단계  
![OracleStorage](../image/OracleStorage.PNG)

* Block & Extent & Segment  
![databasewithoracle1](../image/databasewithoracle1.PNG)

* Oracle Database Architecture  
![databasewithoracle2](../image/databasewithoracle2.jpg)

       * __ Block __  
       DB Block(Oracle Block)은 OS Block을 한개이상 합쳐서 생성하며 DB_BLOCK_SIZE로 지정 가능하다.
       DB Block의 크기가 4KB이고 OS Block이 2KB 이면 OS Block 2개가 합쳐져야 1개의 DB Block이 생성된다.  
       SGA(ORACLE SERVER의 메모리 영역 - ORACLE의 인스턴스에 대한 데이터와 제어정보를 가지는 공유 메모리 영역의 집합)의 DB 블록 버퍼에서 I/O의 기본 단위 이다.
       Block의 단위는 init.ora 파일에서 DB_BLOCK_SIZE로 지정한다.
        
       * __ EXTENT __  
       연속적인 Block을 여러개 묶어 놓은 단위를 뜻하며 I/O를 진행할 때 속도를 높이기 위해 도입 된 개념이다.
       
       * __ SEGMENT __
       TableSpace 내에 특정 구조에 대한 모든 데이터를 갖고 있는 하나 혹은 하나 이상의 EXTENT 집합을 말한다.  
       (Data Segment / Index Segment / Rollback Segment / Temporary Segment)


##참조

* 디스크IO  
https://boxtalk.tistory.com/14
* Block & Extent & Segment 이미지 참조  
https://okun.tistory.com/entry/Block-Extent-Segment
* Oracle Database Architecture 이미지 참조  
https://link.springer.com/chapter/10.1007/978-1-4842-4517-0_10
