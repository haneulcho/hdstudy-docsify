# 공지사항 게시글 API
공지사항 게시글에 대한 API 안내입니다.

## 전체 URL 모아보기
| Method | URL | Description |
| :----: | ---- | ---- |
| `GET` | **/api/Notice/GetList** | 게시글 목록 조회 |
| `GET` | **/api/Notice/GetInfo** | 단일 게시글 조회 |

## 1. 게시글 목록 조회 /api/Notice/GetList
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Board/GetList
```

### Parameters
```json
{
	"n4NoticeArticleCategorySN": 0, // 게시판 고유 번호
	"n4PageNo": 1, // 조회 페이지 번호
	"n1PageSize": 10, // 한 페이지에 보여줄 게시글 개수
	"n1PageSeparate": 10, // 한 페이지에 보여줄 페이지 번호 개수
	"strSearch": "" // 제목으로 검색할 검색어
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4NoticeArticleCategorySN | int | Y | 게시판 고유 번호 |
| n4PageNo | int | Y | 조회 페이지 번호 |
| n1PageSize | int | Y | 한 페이지에 보여줄 게시글 개수 |
| n1PageSeparate | int | Y | 한 페이지에 보여줄 페이지 번호 개수 |
| strSearch | string | Y | 제목으로 검색할 검색어 |

### Responses
```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": [
		{
			"BoardSN": 1, // 고정 번호
			"ArticleSN": 108102, // 게시글 고유 번호
			"WriteDate": "2020-07-17T18:56:11.25", // 게시글 작성일
			"EditDate": "2020-07-17T18:56:11.25", // 게시글 수정일
			"ArticleTitle": "패치노트 스타일 (크롬)", // 게시글 제목
			"ArticleContent": "&nbsp;\n\n\n안녕하세요? 두리GM입니다.\n\n\n2020년 6월 25일(목) 업데이트 소식을 안내해드립니다.\n\n\n&nbsp;\n\n\n\n \n\n\n\n2020년&nbsp;6월&nbsp;25일(목)&nbsp;오전 4시 55분 ~&nbsp;오전&nbsp;10시\n10분&nbsp;(총&nbsp;5시간 10분)\n\n\n-&nbsp;넥슨 점검:&nbsp;없음\n\n\n-&nbsp;정식 서비스 서버 점검:&nbsp;오전&nbsp;4시 55분&nbsp;~&nbsp;오전&nbsp;10시 10분\n\n\n- 유리/호동 서버 점검: 오전 7시 30분 ~ 오전 11시\n\n\n&nbsp; * 유리/호동 서버 신규 서버 장비 교체 및 증설 작업을 진행합니다.\n\n\n&nbsp; * 유리/호동 서버를 제외한 다른 서버는 오전 10시 10분에 점검이 종료될 예정입니다.\n\n\n-&nbsp;테스트 서버 점검:&nbsp;오전 4시 55분\n~ 오전 7시 30분\n\n\n-&nbsp;홈페이지/캐시샵 점검: 오전 5시\n~ 오전 10시 30분\n\n\n&nbsp;\n\n", // 게시글 내용
			"ServiceNameList": null, // (사용안함)
			"WriteUserName": "", // 작성자명
			"NoticeCode": 1, // 카테고리 번호
			"NoticeCodeName": "[공지]", // 카테고리명
			"ReadCount": 9 // 조회수
		},
		{
			"BoardSN": 1,
			"ArticleSN": 108101,
			"WriteDate": "2020-07-17T18:36:54.953",
			"EditDate": "2020-07-17T18:54:30.2",
			"ArticleTitle": "패치노트 스타일",
			"ArticleContent": "&nbsp;\n안녕하세요? 두리GM입니다.\n2020년 6월 25일(목) 업데이트 소식을 안내해드립니다.\n&nbsp;\n\n2020년&nbsp;6월&nbsp;25일(목)&nbsp;오전 4시 55분 ~&nbsp;오전&nbsp;10시\n10분&nbsp;(총&nbsp;5시간 10분)\n-&nbsp;넥슨 점검:&nbsp;없음\n-&nbsp;정식 서비스 서버 점검:&nbsp;오전&nbsp;4시 55분&nbsp;~&nbsp;오전&nbsp;10시 10분\n- 유리/호동 서버 점검: 오전 7시 30분 ~ 오전 11시\n&nbsp; * 유리/호동 서버 신규 서버 장비 교체 및 증설 작업을 진행합니다.\n&nbsp; * 유리/호동 서버를 제외한 다른 서버는 오전 10시 10분에 점검이 종료될 예정입니다.\n-&nbsp;테스트 서버 점검:&nbsp;오전 4시 55분\n~ 오전 7시 30분\n-&nbsp;홈페이지/캐시샵 점검: 오전 5시\n~ 오전 10시 30분\n&nbsp;\n\n배너 추후 추가 예정\n-\n7월 바람모험 이벤트\n202",
			"ServiceNameList": null,
			"WriteUserName": "",
			"NoticeCode": 1,
			"NoticeCodeName": "[공지]",
			"ReadCount": 9
		}
	],
	"PrevPage": , // 
	"isPrevPage": , // 
	"NextPage": , // 
	"isNextPage": , // 
	"TotalRowCount": 45620, // 페이징 처리를 위한 게시글 데이터 총 개수
	"TotalPageCount":  //
}
```

## 2. 단일 게시글 조회 /api/Notice/GetInfo
### Request URL `[GET]`
```
http://test-m.elsword.nexon.com/api/Notice/GetInfo
```

### Parameters
```json
{
	"n4NoticeArticleSN": 107168, // 게시글 고유 번호
	"isUpdateReadCount": true, // 조회 시 조회수 증감 구분
	"dtWriteDate": "2015-05-14T17:17:56.78", // 게시글 작성일(이전, 다음 게시글 추출에 사용)
	"noticeArticleCategorySN": 0, // 카테고리 번호
	"strTitleSearch": "" // 제목으로 검색할 검색어
}
```

| 속성 | 타입 | 필수여부 | 설명 |
| ---- | :----: | :----: | ---- |
| n4NoticeArticleSN | int | Y | 게시글 고유 번호 |
| isUpdateReadCount | bool | Y | 조회 시 조회수 증감 구분 |
| dtWriteDate | string | Y | 게시글 작성일(이전, 다음 게시글 추출에 사용) |
| noticeArticleCategorySN | int | Y | 카테고리 번호 |
| strTitleSearch | string | N | 제목으로 검색할 검색어 |

### Responses
* **`Info 모델`**: 질의된 현재 게시글의 Article 내역
* **`Prev 모델`**: 질의된 현재 게시글 기준 바로 앞 Article 내역
* **`Next 모델`**: 질의된 현재 게시글 기준 바로 뒤 Article 내역

```json
{
	"ResultCode": 0,
	"ResultMessage": "success",
	"ResultData": {
		"ArticlePageType": 0,
		"Info": {
			"BoardSN": 1,
			"ArticleSN": 107168,
			"WriteDate": "2015-05-15T10:03:59.953",
			"EditDate": "2015-05-15T10:03:59.953",
			"ArticleTitle": "05/14(목) 클라이언트 패치 안내 (오후 10:21) ",
			"ArticleContent": "<DIV id=G_ctnArticleInfo_vrHtmlEditor_strArticleContent_Viewer>\r\n<P style=\"MARGIN: 0cm 0cm 0pt\" class=MsoNormal><STRONG><SPAN style=\"FONT-FAMILY: 돋움; mso-bidi-font-family: 굴림\"><FONT color=#000000>안녕하세요<SPAN lang=EN-US>. GM</SPAN>리엘입니다<SPAN lang=EN-US>.<BR><BR></SPAN></FONT></SPAN></STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\" lang=EN-US>05/14(</SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\">목<SPAN lang=EN-US>) </SPAN>클라이언트 패치가 진행되었습니다<SPAN lang=EN-US>.<BR></SPAN>게임 이용에 참고 부탁드립니다<SPAN lang=EN-US>.<BR><BR></SPAN></SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: #086aef\" lang=EN-US>* </SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: #086aef\">게임 접속 종료 후 다시 접속하시면 자동으로 패치를 받아<SPAN lang=EN-US><BR></SPAN>수정된 버전으로 게임을 이용하실 수 있습니다<SPAN lang=EN-US>.<BR><BR></SPAN></SPAN><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; mso-bidi-font-family: 굴림\" lang=EN-US>&lt;</SPAN></STRONG><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; mso-bidi-font-family: 굴림\">패치 일정<SPAN lang=EN-US>&gt;</SPAN></SPAN></STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\" lang=EN-US><BR>2015</SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\">년<SPAN lang=EN-US> 05</SPAN>월<SPAN lang=EN-US> 14</SPAN>일<SPAN lang=EN-US>(</SPAN>목<SPAN lang=EN-US>) </SPAN>오후 10시 21분<BR><BR></SPAN><A name=OLE_LINK1><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: #8497ad; mso-bidi-font-family: 굴림\" lang=EN-US>&lt;</SPAN></STRONG></A><SPAN style=\"mso-bookmark: OLE_LINK1\"></SPAN><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; mso-bidi-font-family: 굴림\">패치 내용<SPAN lang=EN-US>&gt;<BR></SPAN></SPAN></STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\" lang=EN-US>1. </SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\">대전 맵 [가르파이 모래폭풍]에서 연속으로 점프를 할 경우 일부 점프가 되지 않는 문제가 수정되었습니다.</SPAN></P>\r\n<P style=\"MARGIN: 0cm 0cm 0pt\" class=MsoNormal><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\"><SPAN lang=EN-US><BR><BR></SPAN></SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; FONT-SIZE: 10pt; mso-bidi-font-family: 굴림; mso-ansi-language: EN-US; mso-fareast-language: KO; mso-bidi-language: AR-SA; mso-font-kerning: 0pt\">언제나 즐거운 모험이 가득한 엘소드가 되도록 노력하겠습니다<SPAN lang=EN-US>.<BR></SPAN>감사합니다<SPAN lang=EN-US>.</SPAN></SPAN></P></DIV>",
			"ServiceNameList": null,
			"WriteUserName": "뱅HNAK",
			"NoticeCode": 2,
			"NoticeCodeName": "[패치]",
			"ReadCount": 2728
		},
		"Prev": {
			"BoardSN": 1,
			"ArticleSN": 107168,
			"WriteDate": "2015-05-15T10:03:59.953",
			"EditDate": "2015-05-15T10:03:59.953",
			"ArticleTitle": "05/14(목) 클라이언트 패치 안내 (오후 10:21) ",
			"ArticleContent": "<DIV id=G_ctnArticleInfo_vrHtmlEditor_strArticleContent_Viewer>\r\n<P style=\"MARGIN: 0cm 0cm 0pt\" class=MsoNormal><STRONG><SPAN style=\"FONT-FAMILY: 돋움; mso-bidi-font-family: 굴림\"><FONT color=#000000>안녕하세요<SPAN lang=EN-US>. GM</SPAN>리엘입니다<SPAN lang=EN-US>.<BR><BR></SPAN></FONT></SPAN></STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\" lang=EN-US>05/14(</SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\">목<SPAN lang=EN-US>) </SPAN>클라이언트 패치가 진행되었습니다<SPAN lang=EN-US>.<BR></SPAN>게임 이용에 참고 부탁드립니다<SPAN lang=EN-US>.<BR><BR></SPAN></SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: #086aef\" lang=EN-US>* </SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: #086aef\">게임 접속 종료 후 다시 접속하시면 자동으로 패치를 받아<SPAN lang=EN-US><BR></SPAN>수정된 버전으로 게임을 이용하실 수 있습니다<SPAN lang=EN-US>.<BR><BR></SPAN></SPAN><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; mso-bidi-font-family: 굴림\" lang=EN-US>&lt;</SPAN></STRONG><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; mso-bidi-font-family: 굴림\">패치 일정<SPAN lang=EN-US>&gt;</SPAN></SPAN></STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\" lang=EN-US><BR>2015</SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\">년<SPAN lang=EN-US> 05</SPAN>월<SPAN lang=EN-US> 14</SPAN>일<SPAN lang=EN-US>(</SPAN>목<SPAN lang=EN-US>) </SPAN>오후 10시 21분<BR><BR></SPAN><A name=OLE_LINK1><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: #8497ad; mso-bidi-font-family: 굴림\" lang=EN-US>&lt;</SPAN></STRONG></A><SPAN style=\"mso-bookmark: OLE_LINK1\"></SPAN><STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; mso-bidi-font-family: 굴림\">패치 내용<SPAN lang=EN-US>&gt;<BR></SPAN></SPAN></STRONG><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\" lang=EN-US>1. </SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\">대전 맵 [가르파이 모래폭풍]에서 연속으로 점프를 할 경우 일부 점프가 되지 않는 문제가 수정되었습니다.</SPAN></P>\r\n<P style=\"MARGIN: 0cm 0cm 0pt\" class=MsoNormal><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black\"><SPAN lang=EN-US><BR><BR></SPAN></SPAN><SPAN style=\"FONT-FAMILY: 돋움; COLOR: black; FONT-SIZE: 10pt; mso-bidi-font-family: 굴림; mso-ansi-language: EN-US; mso-fareast-language: KO; mso-bidi-language: AR-SA; mso-font-kerning: 0pt\">언제나 즐거운 모험이 가득한 엘소드가 되도록 노력하겠습니다<SPAN lang=EN-US>.<BR></SPAN>감사합니다<SPAN lang=EN-US>.</SPAN></SPAN></P></DIV>",
			"ServiceNameList": null,
			"WriteUserName": "뱅HNAK",
			"NoticeCode": 2,
			"NoticeCodeName": "[패치]",
			"ReadCount": 2728
		},
		"Next": {
			"BoardSN": 1,
			"ArticleSN": 107149,
			"WriteDate": "2015-05-14T12:20:21.547",
			"EditDate": "2015-07-03T19:38:41.483",
			"ArticleTitle": "(완료) 05/14(목) 넥슨 쿠폰결제 오류 안내",
			"ArticleContent": "<DIV id=G_ctnArticleInfo_vrHtmlEditor_strArticleContent_Viewer>\r\n<P><SPAN style=\"FONT-SIZE: 9pt; FONT-FAMILY: 돋움; COLOR: rgb(125,125,125)\">안녕하세요. 넥슨 회원 여러분. </SPAN></P>\r\n<P><SPAN style=\"FONT-SIZE: 9pt; FONT-FAMILY: 돋움; COLOR: rgb(125,125,125)\">&nbsp;</P>\r\n<P></P>\r\n<P>아래 안내 드린 오류가 현재는 수정되어 </P>\r\n<P>정상적인 서비스 이용이 가능합니다.</P>\r\n<P></P>\r\n<P><STRONG><BR>- 시간:</STRONG> <STRONG>05월 14일(목) 오전 09시 ~ 12시 45분(완료)</STRONG></P>\r\n<P></P>\r\n<P><BR>해당 시간 서비스를 이용하시고자 했던 고객님들과<BR>오류 발생으로 불편을 겪으신 고객님들께 진심으로 사과 드립니다.</P>\r\n<P></P>\r\n<P>&nbsp;</P>\r\n<P>감사합니다.</P></SPAN>\r\n<P></P>\r\n<P><SPAN style=\"FONT-SIZE: 9pt; FONT-FAMILY: 돋움; COLOR: rgb(125,125,125)\"><BR>------------------------------------------------------</SPAN></P>\r\n<P>&nbsp;</P>\r\n<P>안녕하세요. 넥슨 회원 여러분.</P>\r\n<P><BR>현재 넥슨캐시 결제서비스 중 쿠폰 결제에 오류가 발생되어</P>\r\n<P>넥슨캐시 핀번호 등 쿠폰 결제 서비스 이용이 가능하지 않습니다.</P>\r\n<P>&nbsp;</P>\r\n<P>빠르게 오류 수정 중이며 </P>\r\n<P>서비스가 정상화 되면 다시 안내 드리겠습니다.</P>\r\n<P>&nbsp;</P>\r\n<P>이용에 불편을 드려&nbsp;너무 죄송합니다.</P>\r\n<P>&nbsp;</P>\r\n<P>감사합니다. </P></DIV>",
			"ServiceNameList": null,
			"WriteUserName": "ellff",
			"NoticeCode": 1,
			"NoticeCodeName": "[공지]",
			"ReadCount": 13880
		},
		"PageNumber": 0
	}
}
```
