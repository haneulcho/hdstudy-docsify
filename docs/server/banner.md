# 배너 API
배너에 대한 API 안내입니다.

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Banner/GetList** | 배너 목록 조회 |

## 1. 배너 목록 조회 /api/Banner/GetList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Banner/GetList
```

### Parameters
```json
{
	"n4CmsCode": 362, // CMS 고유 번호
	"n4PageNo": 1, // 조회 페이지 번호
	"n1PageSize": 10, // 한 페이지에 보여줄 배너 개수
	"dateActiveDate": "2020-07-24T05:47:02.967Z", // 해당 일자 검색 기본 값(조회일을 기준으로 활성화된 배너 조회)
	"n1OrderingType": 0 // 배너 정렬 옵션
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4CmsCode | int | Y | CMS 고유 번호 |
| n4PageNo | int | Y | 조회 페이지 번호 |
| n1PageSize | int | Y | 한 페이지에 보여줄 배너 개수 |
| dateActiveDate | string | Y | 해당 일자 검색 기본 값(조회일을 기준으로 활성화된 배너 조회) |
| n1OrderingType | int | N | 배너 정렬 옵션<br>0: 기본 정렬 |

### Responses
* **`ResultCode`**: 배너 목록 조회 정상 수행 시 0을 반환
* **`ResultMessage`**: 성공, 실패 시 메시지 반환

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"oidCMS": 362, // CMS 고유 번호
			"n4ArrayIndex": 14, // 배너 순서
			"dateActiveStartDate": "2020-07-01T00:00:00", // 배너 노출 시작일
			"dateActiveEndDate": "2020-09-25T00:00:00", // 배너 노출 종료일
			"dateCreate": "2020-07-24T15:42:32.303", // 배너 등록일
			"dateLastModified": "2020-07-24T15:43:10.723", // 배너 수정일
			"maskGameCode_writer": 94224, // 게임 고유 코드
			"oidUser_writer": 167962959, // 작성자 NEXON SN
			"dn_strLocalID_writer": "a9359", // 작성자 NEXON ID
			"strWriterName": "음휘승", // 작성자 캐릭터 등 ID
			"strContents": "http://s.nx.com/test", // 배너 이미지 경로
			"strURL": "11", // 배너 링크 URL
			"codeLinkTarget": 1, // 링크 유형
			"n1Priority": 1, // 배너 우선순위
			"codeContentsSubType": 0, // ???
			"strSummary": "11|1|1|1|", // 구분자(|)로 구분되는 요약 데이터
			"codeSex": 0, // (사용안함)
			"isApplyNxcom": 0, // (사용안함)
			"isApplyKart": 0, // (사용안함)
			"isApplyWarRock": 0, // (사용안함)
			"isApplyBigShot": 0, // (사용안함)
			"isApplyRunia": 0, // (사용안함)
			"isApplyZera": 0, // (사용안함)
			"n2AgeLimitMin": 0, // (사용안함)
			"n2AgeLimitMax": 0, // (사용안함)
			"isDefaultContent": 0 // 기본 컨텐츠 여부
		},
		{
			"oidCMS": 362,
			"n4ArrayIndex": 13,
			"dateActiveStartDate": "2020-07-24T00:00:00",
			"dateActiveEndDate": "2020-07-31T00:00:00",
			"dateCreate": "2020-07-24T15:40:10.24",
			"dateLastModified": "2020-07-24T15:40:10.24",
			"maskGameCode_writer": 94224,
			"oidUser_writer": 167962959,
			"dn_strLocalID_writer": "a9359",
			"strWriterName": "음휘승",
			"strContents": "http://s.nx.com/test",
			"strURL": "/community/teratv/view.aspx?seq=22222AUxypiJMnFw&categoryID=1&listType=A",
			"codeLinkTarget": 1,
			"n1Priority": 1,
			"codeContentsSubType": 0,
			"strSummary": "1|2|3|4|",
			"codeSex": 0,
			"isApplyNxcom": 0,
			"isApplyKart": 0,
			"isApplyWarRock": 0,
			"isApplyBigShot": 0,
			"isApplyRunia": 0,
			"isApplyZera": 0,
			"n2AgeLimitMin": 0,
			"n2AgeLimitMax": 0,
			"isDefaultContent": 0
		}
	],
	"TotalRowCount": 2
}
```
