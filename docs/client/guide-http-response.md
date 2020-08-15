# API Response 가이드
엘소드 모바일 API Response Key 정의 안내입니다.  
재사용 가능한 컴포넌트(Reusable Components)를 만드려면 API Response 데이터의 Key를 읽기 쉽게 정리하고 통일해야 합니다.
> ex) 글쓴이는 author_name, 작성일은 created_at, 제목은 subject와 같이 재정의

## 1. BOARD API

### 공통 페이징 API
| 기존 속성 | Vue 재설정 속성 | 설명 |
| ---- | ---- | ---- |
| isPrevPage | **hasPrevPage** | `Skip 단위` 이전 페이지 존재 여부 |
| isNextPage | **hasNextPage** | `Skip 단위` 다음 페이지 존재 여부 |
| PrevPage | **prev_page** | `Skip 단위` 이전 페이지 번호 |
| NextPage | **next_page** | `Skip 단위` 다음 페이지 번호 |
| TotalRowCount | **total_count** | 전체 게시글 개수 |
| TotalPageCount | **total_page_count** | 전체 페이지 개수 |

### 게시글 API
| 기존 속성 | Vue 재설정 속성 | 설명 |
| ---- | ---- | ---- |
| maskArticleProperty.isNotice | **isNotice** | 공지 여부 |
| maskArticleProperty.isBestAward | **isBest** | 베스트글 여부 |
| maskArticleProperty.isPunished | **isPunished** | 재제 여부 |
| maskArticleProperty.isDisableComment | **isCommentNotAllowed** | 댓글 활성화 여부 |
| maskArticleProperty.isViewInMainPage | **isFeatured** | 메인 페이지 노출 여부 |
| maskArticleProperty.isHidden | **isBlocked** | 숨김글 여부 |
| maskArticleProperty.isNotComment | **isNotComment** | 댓글 작성 가능 여부 |
| maskGameCode | **gamecode** | 게임 고유 코드 |
| n4BoardSN | **board_id** | 게시판 고유 번호 |
| n4ArticleSN | **id** | 게시글 고유 번호 |
| dtWriteDate | **created_at** | 게시글 작성일 |
| strArticleTitle | **subject** | 게시글 제목 |
| strArticleSomeContent | **summary** | 게시글 내용 요약 |
| strArticleContent | **content** | 게시글 본문 |
| n8ThumbnailFileSN | **thumbnail_id** | 게시글 이미지 포함 시 썸네일 생성 번호 |
| n4ReadCount | **view_count** | 조회수 |
| n4CommentCount | **comment_count** | 댓글수 |
| n4CommentCount2 | **comment2_count** | 댓글수2 |
| n4PositiveRecommendCount | **like_count** | 추천수 |
| n4NegativeRecommendCount | **dislike_count** | 비추천수 |
| n4PositiveRecommendPoint | **like_point** | 추천 포인트 |
| n4NegativeRecommendPoint | **dislike_point** | 비추천 포인트 |
| n4ArticleCategorySN | **category_id** | 카테고리 번호 |
| strArticleCategoryName | **category_name** | 카테고리명 |
| n4ArticleSubCategorySN | **sub_category_id** | 서브 카테고리 번호 |
| strArticleSubCategoryName | **sub_category_name** | 서브 카테고리명 |
| n4ArticleCategory2SN | **category2_id** | 2차 카테고리 번호 |
| strArticleCategory2Name | **category2_name** | 2차 카테고리명 |
| n4WriterSN | **author_sn** | 작성자 NEXON SN |
| strWriterID | **author_id** | 작성자 NEXON ID |
| strWriterName | **author_name** | 작성자 캐릭터 등 ID |
| strWriterInfo | **author_info** | 작성자 기타 정보 |
| n2WriterLevel | **author_level** | 작성자 캐릭터 레벨 |
| n4WriterExp | **author_exp** | 작성자 경험치 |
| strDelegatedData | **extra_data** | 게시글 작성 시 구분자`(|)`로 구분되는 임시 데이터 |

### 댓글 API

문서 준비중입니다.

## 2. NOTICE API

## 3. BANNER API

## 4. POLL API