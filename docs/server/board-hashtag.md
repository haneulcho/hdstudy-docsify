# 해시태그 API
해시태그 대한 API 안내입니다.

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Board/GetHashTagList** | 해시태그 목록 조회 |
| `GET` | **/api/Board/GetHashTagInfo** | 해시태그 조회 |
| `POST` | **/api/Board/CreateHashTag** | 해시태그 작성 |
| `POST` | **/api/Board/DeleteHashTag** | 해시태그 삭제 |


## 1. 해시태그 목록 조회 /api/Board/GetHashTagList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetHashTagList
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"strHashTag": "", // 
	"n1PageSize": "", // 
	"n1PageSeparate": "", // 
	"n8HashValue": "", // 
	"n8MemberSN": "" // 
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| strHashTag | string | Y |  |
| n1PageSize | int | Y |  |
| n1PageSeparate | int | Y |  |
| n8HashValue | int | Y |  |
| n8MemberSN | int | N |  |

### Responses
* **`ResultCode`**: 해시태그 목록 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": {

	}, // ResultData
	"PrevPage": "",
	"isPrevPage": "",
	"NextPage": "",
	"isNextPage": "",
	"TotalRowCount": "",
	"TotalPageCount": ""
}
```

## 2. 해시태그 조회 /api/Board/GetHashTagInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetHashTagInfo
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4ArticleSN": 2 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
* **`ResultCode`**: 해시태그 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": {

	} // ResultData
}
```

## 3. 해시태그 작성 /api/Board/CreateHashTag
### Request URL `[POST]]`
```
http://test-m.elsword.nexon.com/api/Board/CreateHashTag
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4ArticleSN": 2, // 게시글 고유 번호
	"strHashTags": "#하늘" // 해시태그 내용
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| strHashTags | string | Y | 해시태그 내용 |

### Responses
* **`ResultCode`**: 해시태그 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success"
}
```

## 4. 해시태그 삭제 /api/Board/DeleteHashTag
### Request URL `[POST]]`
```
http://test-m.elsword.nexon.com/api/Board/DeleteHashTag
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4ArticleSN": 2 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
* **`ResultCode`**: 해시태그 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success"
}
```
