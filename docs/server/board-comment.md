# 댓글 API
댓글에 대한 API 안내입니다.

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Board/GetCommentList** | 댓글 목록 조회 |
| `POST` | **/api/Board/AddComment** | 댓글 작성 |
| `POST` | **/api/Board/RemoveComment** | 댓글 삭제 |

## 1. 댓글 목록 조회 /api/Board/GetCommentList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetCommentList
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 번호
	"n4ArticleSN": 26, // 부모 게시글 고유 번호
	"n4CommentPageNo": 1, // 조회 페이지 번호
	"n1CommentPageSize": 10, // 한 페이지에 보여줄 댓글 개수
	"n1PageSeparate": 10 // 한 페이지에 보여줄 페이지 번호 개수
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 부모 게시글 고유 번호 |
| n4CommentPageNo | int | Y | 조회 페이지 번호 |
| n1CommentPageSize | int | Y | 한 페이지에 보여줄 댓글 개수 |
| n1PageSeparate | int | Y | 한 페이지에 보여줄 댓글 페이지 번호 개수 |

### Responses
* **`ResultCode`**: 댓글 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
* **`ResultData`**: 댓글 목록 Object List

```json
{
	"ResultValue": 0,
	"ResultMessage": "success",
	"ResultData": {
		"List": [
			{
				"n4BoardSN": 335544325, // 게시판 고유 번호
				"n4ArticleSN": 26, // 부모 게시글 고유 번호
				"n4CommentSN": 3, // 댓글 고유 번호
				"maskGameCode": 94224, // 게임 고유 코드
				"n4WriterSN": 167962959, // 작성자 NEXON SN
				"strWriterID": "a9359", // 작성자 NEXON ID
				"strWriterName": "1", // 작성자 캐릭터 등 ID
				"strWriterInfo": "", // 작성자 기타 정보
				"strCommentContent": "지쟈스", // 댓글 내용
				"dtWriteDate": "2020-07-23T15:09:09.56" // 댓글 작성일
			},
			{
				"n4BoardSN": 335544325,
				"n4ArticleSN": 26,
				"n4CommentSN": 2,
				"maskGameCode": 94224,
				"n4WriterSN": 167962959,
				"strWriterID": "a9359",
				"strWriterName": "1",
				"strWriterInfo": "",
				"strCommentContent": "시져스",
				"dtWriteDate": "2020-07-23T15:09:05.397"
			},
			{
				"n4BoardSN": 335544325,
				"n4ArticleSN": 26,
				"n4CommentSN": 1,
				"maskGameCode": 94224,
				"n4WriterSN": 167962959,
				"strWriterID": "a9359",
				"strWriterName": "1",
				"strWriterInfo": "",
				"strCommentContent": "고저스",
				"dtWriteDate": "2020-07-23T15:09:00.597"
			}
		],
		"n4ArticleSN": 26 // 부모 게시글 고유 번호
	},
	"PrevPage": , // 
	"isPrevPage": , // 
	"NextPage": , // 
	"isNextPage": , // 
	"TotalRowCount": 3, // 조회한 댓글 수
	"TotalPageCount":  // 
}
```

## 2. 댓글 작성 /api/Board/AddComment
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/AddComment
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 번호
	"n4ArticleSN": 26, // 부모 게시글 고유 번호
	"strComment": "yyyyyyy" // 댓글 내용
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 부모 게시글 고유 번호 |
| strComment | string | Y | 댓글 내용 |

### Responses
* **`ResultCode`**: 댓글 작성, 수정 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 댓글 작성, 수정 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```

## 3. 댓글 삭제 /api/Board/RemoveComment
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/RemoveComment
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 번호
	"n4ArticleSN": 26, // 부모 게시글 고유 번호
	"n4CommentSN": 5 // 댓글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 부모 게시글 고유 번호 |
| n4CommentSN | int | Y | 댓글 고유 번호 |

### Responses
* **`ResultCode`**: 댓글 삭제 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 댓글 삭제 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```
