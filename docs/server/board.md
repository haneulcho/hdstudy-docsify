# 게시글 API
게시글에 대한 API 안내입니다.

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Board/GetList** | 게시글 목록 조회 |
| `GET` | **/api/Board/GetInfo** | 단일 게시글 조회 |
| `POST` | **/api/Board/WriteArticle** | 게시글 작성 |
| `POST` | **/api/Board/RemoveArticle** | 게시글 삭제 |
| `POST` | **/api/Board/RecommendArticle** | 게시글 추천 |
| `POST` | **/api/Board/DisRecommendArticle** | 게시글 비추천 |
| `POST` | **/api/Board/SetReportArticle** | 게시글 신고 |
| `POST` | **/api/Board/SetImageUpload** | 게시글 이미지 첨부(multipart/form-data) |

## 1. 게시글 목록 조회 /api/Board/GetList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetList
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4PageNo": 1, // 조회 페이지 번호
	"n1PageSize": 20, // 한 페이지에 보여줄 게시글 개수
	"n1PageSeparate": 10, // 한 페이지에 보여줄 페이지 번호 개수
	"SearchType": "writer", // 검색 기준
	"strSearchText": "1", // 검색어
	"n4ArticleCategorySN": 0, // 카테고리 번호
	"n4ArticleSubCategorySN": 0, // 서브 카테고리 번호
	"n4ArticleCategory2SN": 0, // 2차 카테고리 번호
	"n1codeOrderingType": 0 // 게시글 정렬 옵션
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4PageNo | int | Y | 조회 페이지 번호 |
| n1PageSize | int | Y | 한 페이지에 보여줄 게시글 개수 |
| n1PageSeparate | int | N | 한 페이지에 보여줄 페이지 번호 개수 |
| SearchType | string | N | 검색 기준<br>title: 제목으로 검색<br>writer: 작성자로 검색 |
| strSearchText | string | N | 검색어 |
| n4ArticleCategorySN | int | N | 카테고리 번호 |
| n4ArticleSubCategorySN | int | N | 서브 카테고리 번호 |
| n4ArticleCategory2SN | int | N | 2차 카테고리 번호 |
| n1codeOrderingType | int | N | 게시글 정렬 옵션<br>0: 기본 정렬<br>1: 날짜 내림차순<br>2: 날짜 오름차순<br>3: 내림차순<br>4: 오름차순 |

### Responses
maskArticleProperty는 리스트의 Article 요소에 대한 대표 속성입니다.  
게시판에 해당되는 속성에서 상속되며, 공지 여부 / 숨김글 여부 / 댓글 사용여부 등이 대표적입니다.

* **`ResultCode`**: 게시글 작성, 수정 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"maskArticleProperty": {
				"isNotice": false, // 공지 여부
				"isAnswered": false, // 응답 여부(사용안함)
				"isBestAward": false, // 베스트글 여부
				"isPunished": false, // 재제 여부
				"isAcceptedByAdmin": false, // 관리 관련(사용안함)
				"isCompletedByAdmin": false, // 관리 관련(사용안함)
				"isRequiredCheckByAdmin": false, // 관리 관련(사용안함)
				"isConfirmBySuperAdmin": false, // 관리 관련(사용안함)
				"isDisableComment": false, // 댓글 활성화 여부
				"isViewInMainPage": false, // 메인 페이지 노출 여부
				"isHidden": false, // 숨김글 여부
				"isNotComment": true // 댓글 작성 가능 여부
			},
			"n4BoardSN": 335544325, // 게시판 고유 번호
			"n4ArticleSN": 16, // 게시글 고유 번호
			"dtWriteDate": "2017-03-13T17:56:57.663", // 게시글 작성일
			"n4ArticleCategorySN": 0, // 카테고리 번호
			"strArticleCategoryName": "", // 카테고리명
			"n4ArticleSubCategorySN": 0, // 서브 카테고리 번호
			"strArticleSubCategoryName": "", // 서브 카테고리명
			"n4ArticleCategory2SN": 0, // 2차 카테고리 번호
			"strArticleCategory2Name": "", // 2차 카테고리명
			"maskGameCode": 94224, // 게임 고유 코드
			"n4WriterSN": 1963442407, // 작성자 NEXON SN
			"strWriterID": "nxpt31", // 작성자 NEXON ID
			"strWriterName": "1", // 작성자 캐릭터 등 ID
			"strWriterInfo": "", // 작성자 기타 정보
			"n2WriterLevel": 0, // 작성자 캐릭터 레벨
			"n4WriterExp": 0, // 작성자 경험치
			"n8ThumbnailFileSN": 0, // 게시글 이미지 포함 시 썸네일 생성 번호
			"strArticleTitle": "엘소드 통계 테스트14", // 게시글 제목
			"strArticleSomeContent": "", // 게시글 내용 요약
			"strArticleContent": null, // 게시글 본문
			"n4ReadCount": 7, // 조회수
			"n4CommentCount": 0, // 댓글수
			"n4CommentCount2": 0, // 댓글수2
			"n4PositiveRecommendCount": 0, // 추천수
			"n4NegativeRecommendCount": 0, // 비추천수
			"n4PositiveRecommendPoint": 0, // 추천 포인트
			"n4NegativeRecommendPoint": 0, // 비추천 포인트
			"strDelegatedData": "", // 게시글 작성 시 구분자(|)로 구분되는 임시 데이터
			"isNotice": false, // 공지 여부
			"isNotComment": true // 댓글 작성 가능 여부
		}
	],
	"PrevPage": , // 
	"isPrevPage": , // 
	"NextPage": , // 
	"isNextPage": , // 
	"TotalRowCount": , // 조회한 게시글 수
	"TotalPageCount":  //
} 
```

## 2. 단일 게시글 조회 /api/Board/GetInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetInfo
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4ArticleSN": 14, // 게시글 고유 번호
	"isWantIncReadCount": true, // 조회 시 조회수 증감 구분
	"isWantArticleContent": true, // 조회 시 본문 취득 구분
	"SearchType": "writer", // 검색 기준
	"strSearchText": "0", // 검색어
	"isCustomOrdering": false, //
	"n4ArticleCategorySN": 0, // 카테고리 번호
	"n4ArticleSubCategorySN": 0, // 서브 카테고리 번호
	"n4ArticleCategory2SN": 0 // 2차 카테고리 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| isWantIncReadCount | bool | N | 조회 시 조회수 증감 구분 |
| isWantArticleContent | bool | N | 조회 시 본문 취득 구분 |
| SearchType | string | N | 검색 기준<br>title: 제목으로 검색<br>writer: 작성자로 검색 |
| strSearchText | string | N | 검색어 |
| isCustomOrdering | bool | N | - |
| n4ArticleCategorySN | int | N | 카테고리 번호 |
| n4ArticleSubCategorySN | int | N | 서브 카테고리 번호 |
| n4ArticleCategory2SN | int | N | 2차 카테고리 번호 |

### Responses
maskArticleProperty는 리스트의 Article 요소에 대한 대표 속성입니다.  
게시판에 해당되는 속성에서 상속되며, 공지 여부 / 숨김글 여부 / 댓글 사용여부 등이 대표적입니다.

* **`Info 모델`**: 질의된 현재 게시글의 Article 내역
* **`Prev 모델`**: 질의된 현재 게시글 기준 바로 앞 Article 내역
* **`Next 모델`**: 질의된 현재 게시글 기준 바로 뒤 Article 내역

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": {
		"Info": {
			"maskArticleProperty": {
				"isNotice": false,
				"isAnswered": false,
				"isBestAward": false,
				"isPunished": false,
				"isAcceptedByAdmin": false,
				"isCompletedByAdmin": false,
				"isRequiredCheckByAdmin": false,
				"isConfirmBySuperAdmin": false,
				"isDisableComment": false,
				"isViewInMainPage": false,
				"isHidden": false,
				"isNotComment": true
			},
			"n4BoardSN": 335544325,
			"n4ArticleSN": 14,
			"dtWriteDate": "2017-03-13T17:56:45.73",
			"n4ArticleCategorySN": 0,
			"strArticleCategoryName": "",
			"n4ArticleSubCategorySN": 0,
			"strArticleSubCategoryName": "",
			"n4ArticleCategory2SN": 0,
			"strArticleCategory2Name": "",
			"maskGameCode": 94224,
			"n4WriterSN": 1963442407,
			"strWriterID": "nxpt31",
			"strWriterName": "1",
			"strWriterInfo": "",
			"n2WriterLevel": 0,
			"n4WriterExp": 0,
			"n8ThumbnailFileSN": 0,
			"strArticleTitle": "엘소드 통계 테스트12",
			"strArticleSomeContent": "",
			"strArticleContent": "엘소드 통계 테스트12",
			"n4ReadCount": 6,
			"n4CommentCount": 0,
			"n4CommentCount2": 0,
			"n4PositiveRecommendCount": 0,
			"n4NegativeRecommendCount": 0,
			"n4PositiveRecommendPoint": 0,
			"n4NegativeRecommendPoint": 0,
			"strDelegatedData": "",
			"isNotice": false,
			"isNotComment": true
		}, // Info
		"Prev": {
			"maskArticleProperty": {
				"isNotice": false,
				"isAnswered": false,
				"isBestAward": false,
				"isPunished": false,
				"isAcceptedByAdmin": false,
				"isCompletedByAdmin": false,
				"isRequiredCheckByAdmin": false,
				"isConfirmBySuperAdmin": false,
				"isDisableComment": false,
				"isViewInMainPage": false,
				"isHidden": false,
				"isNotComment": true
			},
			"n4BoardSN": 335544325,
			"n4ArticleSN": 15,
			"dtWriteDate": "2017-03-13T17:56:51.323",
			"n4ArticleCategorySN": 0,
			"strArticleCategoryName": "",
			"n4ArticleSubCategorySN": 0,
			"strArticleSubCategoryName": "",
			"n4ArticleCategory2SN": 0,
			"strArticleCategory2Name": "",
			"maskGameCode": 94224,
			"n4WriterSN": 1963442407,
			"strWriterID": "nxpt31",
			"strWriterName": "1",
			"strWriterInfo": "",
			"n2WriterLevel": 0,
			"n4WriterExp": 0,
			"n8ThumbnailFileSN": 0,
			"strArticleTitle": "엘소드 통계 테스트13",
			"strArticleSomeContent": "",
			"strArticleContent": null,
			"n4ReadCount": 4,
			"n4CommentCount": 0,
			"n4CommentCount2": 0,
			"n4PositiveRecommendCount": 0,
			"n4NegativeRecommendCount": 0,
			"n4PositiveRecommendPoint": 0,
			"n4NegativeRecommendPoint": 0,
			"strDelegatedData": "",
			"isNotice": false,
			"isNotComment": true
		}, // Prev
		"Next": {
			"maskArticleProperty": {
				"isNotice": false,
				"isAnswered": false,
				"isBestAward": false,
				"isPunished": false,
				"isAcceptedByAdmin": false,
				"isCompletedByAdmin": false,
				"isRequiredCheckByAdmin": false,
				"isConfirmBySuperAdmin": false,
				"isDisableComment": false,
				"isViewInMainPage": false,
				"isHidden": false,
				"isNotComment": true
			},
			"n4BoardSN": 335544325,
			"n4ArticleSN": 13,
			"dtWriteDate": "2017-03-13T17:56:40.173",
			"n4ArticleCategorySN": 0,
			"strArticleCategoryName": "",
			"n4ArticleSubCategorySN": 0,
			"strArticleSubCategoryName": "",
			"n4ArticleCategory2SN": 0,
			"strArticleCategory2Name": "",
			"maskGameCode": 94224,
			"n4WriterSN": 1963442407,
			"strWriterID": "nxpt31",
			"strWriterName": "1",
			"strWriterInfo": "",
			"n2WriterLevel": 0,
			"n4WriterExp": 0,
			"n8ThumbnailFileSN": 0,
			"strArticleTitle": "엘소드 통계 테스트11",
			"strArticleSomeContent": "",
			"strArticleContent": null,
			"n4ReadCount": 0,
			"n4CommentCount": 0,
			"n4CommentCount2": 0,
			"n4PositiveRecommendCount": 0,
			"n4NegativeRecommendCount": 0,
			"n4PositiveRecommendPoint": 0,
			"n4NegativeRecommendPoint": 0,
			"strDelegatedData": "",
			"isNotice": false,
			"isNotComment": true
		} // Next
	} // ResultData
}
```

## 3. 게시글 작성 /api/Board/WriteArticle
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/WriteArticle
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4ArticleSN": 0, // 게시글 고유 번호
	"strArticleTitle": "나는 관대하다", // 게시글 제목
	"strArticleContent": "I am generous", // 게시글 내용
	"n4ArticleCategorySN": 0, // 카테고리 번호
	"n4ArticleSubCategorySN": 0, // 서브 카테고리 번호
	"n4ArticleCategory2SN": 0, // 2차 카테고리 번호
	"strDelegatedData": "0|111|ㄹㄹㄹㄹ|F", // 구분자(|)로 구분되는 임시 데이터
	"IsMustAttachImage": false, // 이미지 포함 여부
	"isUseDelegatedData": true, // 임시 데이터 포함 여부
	"ThumbnailFile": {}, // 썸네일 파일 정보 Model
	"arrEditorFileList": [] // 에디터 썸네일 파일 정보 Model
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | N | 게시글 고유 번호 |
| strArticleTitle | string | Y | 게시글 제목 |
| strArticleContent | string | Y | 게시글 내용 |
| n4ArticleCategorySN | int | N | 카테고리 번호 |
| n4ArticleSubCategorySN | int | N | 서브 카테고리 번호 |
| n4ArticleCategory2SN | int | N | 2차 카테고리 번호 |
| strDelegatedData | string | N | 구분자`(|)`로 구분되는 임시 데이터 |
| IsMustAttachImage | bool | N | 이미지 포함여부 |
| isUseDelegatedData | bool | N | 임시 데이터 포함 여부 |
| ThumbnailFile | object | N | 썸네일 파일 정보 Model |
| arrEditorFileList | array | N | 에디터 썸네일 파일 정보 Model |

### Responses
* **`ResultCode`**: 게시글 작성, 수정 정상 수행 시 0을 반환
* **`ResultNewPostID`**: 신규 작성이면 새로 생성한 articleSN 값을 반환 / 수정이면 기존글 articleSN 값을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 게시글 작성, 수정 정상 수행 시 0을 반환
	"ResultNewPostID": 26, // 신규 작성이면 새로 생성한 articleSN 값 반환, 수정이면 기존글 articleSN 값 반환
	"ResultMessage": "success",
	"ResultData": null // 성공, 실패 시 메시지 반환
}
```

## 4. 게시글 삭제 /api/Board/RemoveArticle
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/RemoveArticle
```

### Parameters
```json
{
	"n4BoardSN": 335544325, // 게시판 고유 번호
	"n4ArticleSN": 25 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
* **`ResultCode`**: 게시글 삭제 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 게시글 삭제 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```

## 5. 게시글 추천 /api/Board/RecommendArticle
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/RecommendArticle
```

### Parameters
```json
{
	"n4BoardSN": 402653189, // 게시판 고유 번호
	"n4ArticleSN": 1 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
* **`ResultCode`**: 게시글 추천 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 게시글 추천 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```

## 6. 게시글 비추천 /api/Board/DisRecommendArticle
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/DisRecommendArticle
```

### Parameters
```json
{
	"n4BoardSN": 402653189, // 게시판 고유 번호
	"n4ArticleSN": 4 // 게시글 고유 번호
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |

### Responses
* **`ResultCode`**: 게시글 비추천 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 게시글 비추천 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```

## 7. 게시글 신고 /api/Board/SetReportArticle
### Request URL `[POST]`
```
http://test-m.elsword.nexon.com/api/Board/SetReportArticle
```

### Parameters
```json
{
	"n4BoardSN": 402653189, // 게시판 고유 번호
	"n4ArticleSN": 2, // 게시글 고유 번호
	"n1ReportSubType": 1, // 신고 사유
	"txtEtcReason": "111111", // 기타 신고 이유
	"strTargetUrl": "22222" // 
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4BoardSN | int | Y | 게시판 고유 번호 |
| n4ArticleSN | int | Y | 게시글 고유 번호 |
| n1ReportSubType | int | Y | 신고 사유 |
| txtEtcReason | string | Y | 기타 신고 이유 |
| strTargetUrl | string | Y | - |

### Responses
* **`ResultCode`**: 게시글 신고 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 게시글 신고 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```

## 8. 게시글 이미지 첨부 /api/Board/SetImageUpload
### Request URL `[POST] multipart/form-data`
```
http://test-m.elsword.nexon.com/api/Board/SetImageUpload
```

### Parameters
```
view-source:http://test-m.elsword.nexon.com/home/UplaodTest 참고
```

```javascript
// httpRequest.Files 확인 후 내용 삽입 예정
```

### Responses
* **`ResultCode`**: 게시글 이미지 첨부 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0, // 게시글 이미지 첨부 정상 수행 시 0을 반환
	"ResultMessage": "success", // 성공, 실패 시 메시지 반환
	"ResultData": null
}
```
