# 변경 요약
풀 리퀘스트로 인해 변경되는 내용을 요약하고, 관련된 이슈가 있을 경우 연결합니다.

# 체크리스트
- [ ] Endpoint가 변경되었는가?
- [ ] request 형식이나 내용이 변경되었는가?
- [ ] response 형식이나 내용이 변경되었는가?
- [ ] 데이터베이스 스키마가 변경되었는가?

# 변경 상세
상단의 체크리스트에 체크된 항목이 있다면 적습니다. 아래는 예시입니다.
## Endpoint
**추가**
- [POST] /signin  

**수정**
- [GET] /app/main -> [GET] /app/mainpage  

**삭제**
- [PATCH] /board/modify

## Request
- [POST] /signup : phone->mobile로 프로퍼티명 수정
- [POST] /signup : email 프로퍼티 필수 입력 항목으로 수정
- [POST] /signup : middleName 프로퍼티 삭제

## Response
- [GET] /{board_idx}/article : 배열 전체를 list 프로퍼티에 담아 응답함
```
/* [GET] /{board_idx}/article */
{
    "code": "0000",
    "message": "success",
    "data": {
        ...
    }
}
```

- [POST] /signin : token 프로퍼티 삭제
## Database
```
/* 컬럼 수정 */
ALTER TABLE `member` MODIFY COLUMN `phone` `mobile` varchar(16) COMMENT `회원 전화번호`;
```
