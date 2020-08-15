# 설문조사 게시글 API
설문조사 게시글에 대한 API 안내입니다.
><span style="color:red;font-weight:bold">일부 내용 확인 중입니다.</span>

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Poll/GetList** | 게시글 목록 조회 |
| `GET` | **/api/Poll/GetInfo** | 단일 게시글 조회 |
| `GET` | **/api/Poll/GetPrevInfo** | 이전 게시글 조회 |
| `GET` | **/api/Poll/GetNextInfo** | 다음 게시글 조회 |
| `GET` | **/api/Poll/GetQuestionList** | 특정 설문 질문 조회 |
| `GET` | **/api/Poll/GetAnswerInfo** | 참여 정보 조회 |
| `GET` | **/api/Poll/GetPollAnswerInfo** | 사용자별 참여 정보 조회 |
| `POST` | **/api/Poll/SetAnswer** | 설문 참여 |

## 1. 게시글 목록 조회 /api/Poll/GetList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetList
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4PageNo": 1, // 조회 페이지 번호
	"n1PageSize": 10, // 한 페이지에 보여줄 게시글 개수
	"n1PageSeparate": 10 // 한 페이지에 보여줄 페이지 번호 개수
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4PageNo | int | Y | 조회 페이지 번호 |
| n1PageSize | int | Y | 한 페이지에 보여줄 게시글 개수 |
| n1PageSeparate | int | Y | 한 페이지에 보여줄 페이지 번호 개수 |

### Responses
```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"n4BoardSN": 1207959563, // 게시판 고유 번호
			"n4ArticleSN": 3, // 게시글 고유 번호
			"n8WriterUserSN": 167962959, // 작성자 NEXON SN
			"n4WriterServerCode": 94224, // 작성자 서버 코드(GWMS 등록 시 게임 고유 코드)
			"n4WriterCharacterSN": 0, // 작성자 캐릭터 고유 번호
			"dtWriteDate": "2020-07-21T10:00:01.717", // 게시글 작성일
			"maskGameCode_writer": 94224, // 게임 고유 코드
			"n4GameCode": 0, // 게임 코드
			"strArticleTitle": "당신이 제일 좋아 하는사람은 누구입니까", // 게시글 제목
			"strArticleContent": "ㅋㅋㅋㅂㅂㅂㅁㅁㅁㅁ", // 게시글 내용
			"strWriterName": "1", // 작성자 캐릭터 등 ID
			"strWriterInfo": "", // 작성자 기타 정보
			"isAttachFile": false, // 게시글 파일 첨부 여부
			"isAttachImage": false, // 게시글 이미지 첨부 여부
			"isSysopWrite": false, // (사용하지 않음)
			"n4ReadCount": 1, // 조회수
			"n4ArticleCategorySN": 0, // 카테고리 번호
			"n4ArticleSubCategorySN": 0, // 서브 카테고리 번호
			"n4ArticleCategory2SN": 0, // 2차 카테고리 번호
			"n4CommentCount": 0, // 댓글수
			"n4TotalSimpleCommentCount": 0, // 댓글수
			"n4PositiveRecommendCount": 0, // 추천수
			"n4NegativeRecommendCount": 0, // 비추천수
			"n4PositiveRecommendPoint": 0, // 추천 포인트
			"n4NegativeRecommendPoint": 0, // 비추천 포인트
			"isNotice": false, // 공지 여부
			"dtActiveStart": "2019-02-04T00:00:00", // 설문조사 시작일
			"dtActiveEnd": "2021-05-09T00:00:00", // 설문조사 종료일
			"n4TotalAnswerCount": 5, // 설문 참여자수
			"isNotComment": false // 댓글 작성 가능 여부
		},
		{
			"n4BoardSN": 1207959563,
			"n4ArticleSN": 2,
			"n8WriterUserSN": 1275225307,
			"n4WriterServerCode": 94224,
			"n4WriterCharacterSN": 0,
			"dtWriteDate": "2020-07-01T10:16:49.333",
			"maskGameCode_writer": 94224,
			"n4GameCode": 0,
			"strArticleTitle": "zzzzz",
			"strArticleContent": "zzzzz",
			"strWriterName": "1",
			"strWriterInfo": "",
			"isAttachFile": false,
			"isAttachImage": false,
			"isSysopWrite": false,
			"n4ReadCount": 0,
			"n4ArticleCategorySN": 0,
			"n4ArticleSubCategorySN": 0,
			"n4ArticleCategory2SN": 0,
			"n4CommentCount": 0,
			"n4TotalSimpleCommentCount": 0,
			"n4PositiveRecommendCount": 0,
			"n4NegativeRecommendCount": 0,
			"n4PositiveRecommendPoint": 0,
			"n4NegativeRecommendPoint": 0,
			"isNotice": false,
			"dtActiveStart": "2020-07-01T10:17:00",
			"dtActiveEnd": "2020-07-31T10:16:00",
			"n4TotalAnswerCount": 0,
			"isNotComment": false
		}
	],
	"PrevPage": , // 
	"isPrevPage": , // 
	"NextPage": , // 
	"isNextPage": , // 
	"TotalRowCount": 2, // 조회한 게시글 수
	"TotalPageCount":  //
}
```

## 2. 단일 게시글 조회 /api/Poll/GetInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetInfo
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 3 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": {
		"n4BoardSN": 1207959563,
		"n4ArticleSN": 3,
		"n8WriterUserSN": 167962959,
		"n4WriterServerCode": 0,
		"n4WriterCharacterSN": 0,
		"dtWriteDate": "2020-07-21T10:00:01.717",
		"maskGameCode_writer": 94224,
		"n4GameCode": 0,
		"strArticleTitle": "당신이 제일 좋아 하는사람은 누구입니까",
		"strArticleContent": "ㅋㅋㅋㅂㅂㅂㅁㅁㅁㅁ",
		"strWriterName": "1",
		"strWriterInfo": "",
		"isAttachFile": false,
		"isAttachImage": false,
		"isSysopWrite": false,
		"n4ReadCount": 3,
		"n4ArticleCategorySN": 0,
		"n4ArticleSubCategorySN": 0,
		"n4ArticleCategory2SN": 0,
		"n4CommentCount": 0,
		"n4TotalSimpleCommentCount": 0,
		"n4PositiveRecommendCount": 0,
		"n4NegativeRecommendCount": 0,
		"n4PositiveRecommendPoint": 0,
		"n4NegativeRecommendPoint": 0,
		"isNotice": false,
		"dtActiveStart": "2019-02-04T00:00:00",
		"dtActiveEnd": "2021-05-09T00:00:00",
		"n4TotalAnswerCount": 5,
		"isNotComment": true
	}
}
```

## 3. 이전 게시글 조회 /api/Poll/GetPrevInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetPrevInfo
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 2, // 게시글 고유 번호
	"n4PageNo": 1, // 조회 페이지 번호
	"n1PageSize": 10 // 한 페이지에 보여줄 게시글 개수
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| n4PageNo | int | Y | 조회 페이지 번호 |
| n1PageSize | int | Y | 한 페이지에 보여줄 게시글 개수 |

### Responses
* **`ResultCode`**: 이전 게시글 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
* **`ResultData`**: 이전 게시글 Object List

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"n4BoardSN": 1207959563,
			"n4ArticleSN": 3,
			"n8WriterUserSN": 167962959,
			"n4WriterServerCode": 0,
			"n4WriterCharacterSN": 0,
			"dtWriteDate": "2020-07-21T10:00:01.717",
			"maskGameCode_writer": 94224,
			"n4GameCode": 0,
			"strArticleTitle": "당신이 제일 좋아 하는사람은 누구입니까",
			"strArticleContent": "ㅋㅋㅋㅂㅂㅂㅁㅁㅁㅁ",
			"strWriterName": "1",
			"strWriterInfo": "",
			"isAttachFile": false,
			"isAttachImage": false,
			"isSysopWrite": false,
			"n4ReadCount": 3,
			"n4ArticleCategorySN": 0,
			"n4ArticleSubCategorySN": 0,
			"n4ArticleCategory2SN": 0,
			"n4CommentCount": 0,
			"n4TotalSimpleCommentCount": 0,
			"n4PositiveRecommendCount": 0,
			"n4NegativeRecommendCount": 0,
			"n4PositiveRecommendPoint": 0,
			"n4NegativeRecommendPoint": 0,
			"isNotice": false,
			"dtActiveStart": "2019-02-04T00:00:00",
			"dtActiveEnd": "2021-05-09T00:00:00",
			"n4TotalAnswerCount": 5,
			"isNotComment": false
		}
	]
}
```

## 4. 다음 게시글 조회 /api/Poll/GetNextInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetNextInfo
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 2, // 게시글 고유 번호
	"n4PageNo": 1, // 조회 페이지 번호
	"n1PageSize": 10 // 한 페이지에 보여줄 게시글 개수
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| n4PageNo | int | Y | 조회 페이지 번호 |
| n1PageSize | int | Y | 한 페이지에 보여줄 게시글 개수 |

### Responses
* **`ResultCode`**: 이전 게시글 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
* **`ResultData`**: 이전 게시글 Object List

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"n4BoardSN": 1207959563,
			"n4ArticleSN": 2,
			"n8WriterUserSN": 1275225307,
			"n4WriterServerCode": 0,
			"n4WriterCharacterSN": 0,
			"dtWriteDate": "2020-07-01T10:16:49.333",
			"maskGameCode_writer": 94224,
			"n4GameCode": 0,
			"strArticleTitle": "zzzzz",
			"strArticleContent": "zzzzz",
			"strWriterName": "1",
			"strWriterInfo": "",
			"isAttachFile": false,
			"isAttachImage": false,
			"isSysopWrite": false,
			"n4ReadCount": 0,
			"n4ArticleCategorySN": 0,
			"n4ArticleSubCategorySN": 0,
			"n4ArticleCategory2SN": 0,
			"n4CommentCount": 0,
			"n4TotalSimpleCommentCount": 0,
			"n4PositiveRecommendCount": 0,
			"n4NegativeRecommendCount": 0,
			"n4PositiveRecommendPoint": 0,
			"n4NegativeRecommendPoint": 0,
			"isNotice": false,
			"dtActiveStart": "2020-07-01T10:17:00",
			"dtActiveEnd": "2020-07-31T10:16:00",
			"n4TotalAnswerCount": 0,
			"isNotComment": false
		}
	]
}
```

## 5. 특정 설문 질문 조회 /api/Poll/GetQuestionList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetQuestionList
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 3 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
><span style="color:red;font-weight:bold">Response 내용 확인 중입니다.</span>

* **`ResultValue`**: 특정 설문 질문 조회 정상 수행 시 0을 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"n4BoardSN": 1207959563, // 게시판 고유번호
			"n4ArticleSN": 3, // 게시글 고유번호
			"n1QuestionNo": , // 설문 보기 항목 고유 값
			"strName": , // 설문 보기 텍스트 ,
			"strDescription": , // 설문 보기 설명글,
			"n4TotalAnswerCount": , // 선택 보기 응답 값
		}
	],
	"TotalRowCount": 0
}
```

## 6. 참여 정보 조회 /api/Poll/GetAnswerInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetAnswerInfo
```

### Parameters
><span style="color:red;font-weight:bold">Parameters 내용 확인 중입니다.</span>

```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 1, // 게시글 고유 번호
	"n4NexonSN": 167962959 // 설문 참여자 NEXON SN
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| n4NexonSN | int | Y | 설문 참여자 NEXON SN |

### Responses
><span style="color:red;font-weight:bold">Response 내용 확인 중입니다.</span>

* **`ResultCode`**: 참여 정보 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
* **`ResultData`**: 설문 참여 정보 Object

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": {
		"n1QuestionNo_Answer": 2, // 설문 참여 문항 번호
		"dtDateCreate": "2020-07-21T14:29:59.827" // 설문 참여일
	}
}
```

## 7. 사용자별 참여 정보 조회 /api/Poll/GetPollAnswerInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Poll/GetPollAnswerInfo
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 3, // 게시글 고유 번호
	"n4NexonSN": 167962959 // 설문 참여자 NEXON SN
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| n4NexonSN | int | Y | 설문 참여자 NEXON SN |

### Responses
* **`ResultCode`**: 사용자별 참여 정보 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
* **`ResultData`**: 사용자별 설문 참여 정보 Object

```json
{
	`"ResultCode": 0`,
	"ResultMessage": "success",
	"ResultData": {
		"oidBoard": 1207959563, // 게시판 고유 번호
		"oidArticle": 3, // 게시글 고유 번호
		"maskGameCode": 94224, // 게임 고유 코드
		"oidUser": 167962959, // 설문 참여자 NEXON SN
		"QuestionNo_Answer": 2, // 설문 참여 문항 번호
		"dateCreate": "2020-07-21T14:29:59.827" // 설문 참여일
	}
}
```

## 8. 설문 참여 /api/Poll/SetAnswer
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Poll/SetAnswer
```

### Parameters
```json
{
	"n4BoardSN": 1207959563, // 게시판 고유 번호
	"n4ArticleSN": 3, // 게시글 고유 번호
	"n1QuestionAnswerNo": 2, // 설문 참여 문항 번호
	"n4NexonSN": 167962121 // 설문 참여자 NEXON SN
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| n1QuestionAnswerNo | byte| Y | 설문 참여 문항 번호 |
| n4NexonSN | int | Y | 설문 참여자 NEXON SN |

### Responses
* **`ResultCode`**: 설문 참여 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환
