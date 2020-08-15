# 대댓글 API
대댓글에 대한 API 안내입니다.

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Board/GetReCommentList** | 대댓글 목록 조회 |
| `POST` | **/api/Board/AddReComment** | 대댓글 작성 |
| `POST` | **/api/Board/RemoveReComment** | 대댓글 삭제 |

## 1. 대댓글 목록 조회 /api/Board/GetReCommentList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetReCommentList
```

### Parameters
```json
{
	"n4BoardSN": 402653189, // 게시판 번호
	"n4ArticleSN": 1, // 부모 게시글 고유 번호
	"n4CommentPageNo": 1, // 조회 페이지 번호
	"n1CommentPageSize": 10, // 한 페이지에 보여줄 대댓글 개수
	"n1PageSeparate": 10 // 한 페이지에 보여줄 페이지 번호 개수
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 부모 게시글 고유 번호 |
| n4CommentPageNo | int | Y | 조회 페이지 번호 |
| n1CommentPageSize | int | Y | 한 페이지에 보여줄 대댓글 개수 |
| n1PageSeparate | int | Y | 한 페이지에 보여줄 대댓글 페이지 번호 개수 |

### Responses
* **`ResultCode`**: 대댓글 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
* **`ResultData`**: 대댓글 목록 Object List

```json
{
	"ResultValue": 0,
	"ResultMessage": "success",
	"ResultData": {
		"List": [
			{
				"n4BoardSN": 402653189, // 게시판 고유 번호
				"n4ArticleSN": 2, // 부모 게시글 고유 번호
				"n4CommentSN": 3, // 대댓글 고유 번호
				"n4ParentCommentSN": 3, // 상위 댓글 존재 시 부모 댓글 고유 번호
				"maskGameCode": 94224, // 게임 고유 코드
				"n8MemberSN": 167962959, // 작성자 NEXON SN
				"strWriterID": "a9359", // 작성자 NEXON ID
				"strWriterName": "운영자", // 작성자 캐릭터 등 ID
				"strWriterInfo": "", // 작성자 기타 정보
				"strCommentContent": "세번째", // 대댓글 내용
				"dtWriteDate": "2020-07-23T17:06:16.73", // 대댓글 작성일
				"dtModifyDate": "0001-01-01T00:00:00", // 대댓글 수정일(사용안함)
				"strIP": null, // (사용안함)
				"strParentWriterName": "", // (사용안함)
				"isParent": true, // 부모 댓글 존재 여부
				"isDeleted": false, // 삭제 대댓글 여부
				"isReplyOfRecomment": false, // 대댓글의 대댓글 여부
				"n4LikeNo": 0, // 추천수
				"isLike": false // 추천 여부
			},
			{
				"n4BoardSN": 402653189,
				"n4ArticleSN": 2,
				"n4CommentSN": 2,
				"n4ParentCommentSN": 2,
				"maskGameCode": 94224,
				"n8MemberSN": 167962959,
				"strWriterID": "a9359",
				"strWriterName": "운영자",
				"strWriterInfo": "",
				"strCommentContent": "두두번째 두ㅐㅅ들",
				"dtWriteDate": "2020-07-23T17:06:07.713",
				"dtModifyDate": "0001-01-01T00:00:00",
				"strIP": null,
				"strParentWriterName": "",
				"isParent": true,
				"isDeleted": false,
				"isReplyOfRecomment": false,
				"n4LikeNo": 0,
				"isLike": false
			},
			{
				"n4BoardSN": 402653189,
				"n4ArticleSN": 2,
				"n4CommentSN": 1,
				"n4ParentCommentSN": 1,
				"maskGameCode": 94224,
				"n8MemberSN": 167962959,
				"strWriterID": "a9359",
				"strWriterName": "운영자",
				"strWriterInfo": "",
				"strCommentContent": "댓글임",
				"dtWriteDate": "2020-07-23T17:05:46.793",
				"dtModifyDate": "0001-01-01T00:00:00",
				"strIP": null,
				"strParentWriterName": "",
				"isParent": true,
				"isDeleted": false,
				"isReplyOfRecomment": false,
				"n4LikeNo": 0,
				"isLike": false
			},
			{
				"n4BoardSN": 402653189,
				"n4ArticleSN": 2,
				"n4CommentSN": 4,
				"n4ParentCommentSN": 1,
				"maskGameCode": 94224,
				"n8MemberSN": 167962959,
				"strWriterID": "a9359",
				"strWriterName": "운영자",
				"strWriterInfo": "",
				"strCommentContent": "첫번째댓글의 대댓글",
				"dtWriteDate": "2020-07-23T17:06:28.2",
				"dtModifyDate": "0001-01-01T00:00:00",
				"strIP": null,
				"strParentWriterName": "운영자",
				"isParent": false,
				"isDeleted": false,
				"isReplyOfRecomment": false,
				"n4LikeNo": 0,
				"isLike": false
			}
		],
		"n4ArticleSN": 2 // 부모 게시글 고유 번호
	},
	"PrevPage": , // 
	"isPrevPage": , // 
	"NextPage": , // 
	"isNextPage": , // 
	"TotalRowCount": 4, // 조회한 대댓글 수
	"TotalPageCount":  // 
}
```

## 2. 대댓글 작성 /api/Board/AddReComment
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/AddReComment
```

### Parameters
```json
{
	"n4BoardSN": 402653189, // 게시판 번호
	"n4ArticleSN": 2, // 부모 게시글 고유 번호
	"n4CommentSN": 5, // 0: 신규 작성, Number: 대댓글이면 부모 댓글 고유 번호
	"strComment": "댓글내용1" // 대댓글 내용
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 부모 게시글 고유 번호 |
| n4CommentSN | int | Y | 댓글 고유 번호<br>0: 신규 작성<br>Number: 대댓글이면 부모 댓글 고유 번호 |
| strComment | string | Y | 댓글 내용 |

### Responses
* **`ResultCode`**: 대댓글 작성, 수정 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 대댓글 작성, 수정 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```

## 3. 대댓글 삭제 /api/Board/RemoveReComment
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/RemoveReComment
```

### Parameters
```json
{
	"n4BoardSN": 402653189, // 게시판 번호
	"n4ArticleSN": 2, // 부모 게시글 고유 번호
	"n4CommentSN": 8, // 대댓글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 부모 게시글 고유 번호 |
| n4CommentSN | int | Y | 대댓글 고유 번호 |

### Responses
* **`ResultCode`**: 대댓글 삭제 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 댓글 삭제 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```
