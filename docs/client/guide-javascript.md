# 유용한 자바스크립트
생각날 때매다 내용을 추가합니다.

## 1. 함수 사용
### 함수 선언은 const 키워드 쓰기
자바스크립트는 같은 이름 함수가 여러 번 정의되면 마지막에 정의한 함수만 실행합니다.  
함수를 선언할 때는 재선언, 재할당이 불가능하도록 const 키워드를 사용합니다.

```javascript
const myFunc = () => {
	console.log('myFunc 함수 호출')
}

myFunc()
```

### 기본 파라미터 활용하기
새로운 데이터를 불러 리스트를 갱신하는 함수가 있습니다. 이 함수에 원하는 값을 파라미터로 전달하면 서버에서 조건에 부합하는 데이터를 보내줍니다. 만약 조건에 부합하는 데이터가 없다면 어떻게 될까요?

보통 '데이터가 없습니다.'와 같은 안내 메시지를 출력하게 되는데, 기본 파라미터를 활용해서 데이터가 없을 경우 기본값에 해당하는 새 데이터를 리스트에 전달합니다.

```javascript
// Before
const myFunc = (boardId, page) => {
	if (!page || typeof page === 'undefined') {
		page = 1
	}
	console.log(page)
}

myFunc('notice')
```

```javascript
// After
const myFunc = (boardId, page = 1) => {
	console.log(page)
}

myFunc('notice')
```

### 결과를 반환할 때는 'Early Return' 하기
errorCode 값에 의해 안내 문구를 반환하는 함수가 있습니다.  
대개 초기 변수를 선언하고 if/else if/else 조건에 맞게 안내 문구를 재할당한 후, 제일 마지막 줄에서 최종 결과를 반환합니다.

return 키워드를 사용하면 함수 내의 구문이 return 키워드를 맞닥뜨리는 순간 상황을 종료하고 return 키워드 이후 내용을 실행하지 않습니다. 따라서 앞의 예나 Form 유효성 검증을 좀 더 유연하게 처리하고, 코드 가독성을 높일 수 있습니다.

```javascript
// Before
const getMessage = (code) => {
	let msg = ''

	if (code === 404) {
		msg = '페이지를 찾을 수 없음'
	} else if (code === 503) {
		msg = '서버 에러'
	} else if (code === 401) {
		msg = '인증 에러'
	} else {
		msg = '성공'
	}

	return msg
}

let errorCode = 404
getMessage(errorCode)
```

```javascript
// After
const getMessage = (code) => {
	if (code === 404) {
		return '페이지를 찾을 수 없음'
	}
	if (code === 503) {
		return '서버 에러'
	}
	if (code === 401) {
		return '인증 에러'
	}

	return '성공'
}

let errorCode = 404
getMessage(errorCode)
```

## 2. 배열 사용
### 배열 생성은 되도록 리터럴 방식 쓰기

```javascript
// new 키워드 방식
let fruits = new Array()
fruits[0] = '사과'
fruits[1] = '딸기'
fruits[2] = '배'
```

```javascript
// 배열 리터럴 방식
let fruits = [ '사과', '딸기', '배' ]
```

### 배열 합치기는 전개 연산자 쓰기

```javascript
let array1 = [ 1, 2, true ]
let array2 = [ 4, false, 6, ...array1 ]

array2.forEach((value, index) => console.log(`array2[${index}]: ${value}`))

// array2[0]: 4
// array2[1]: false
// array2[2]: 6
// array2[3]: 1
// array2[4]: 2
// array2[5]: true
```

## 3. 객체 사용
### 객체 속성 복사는 비구조화 연산자(=전개 연산자) 쓰기
비구조화 연산자를 쓰면 객체를 복사하면서 속성에 새로운 값을 할당할 수 있습니다.

```javascript
// Object.assign 사용
let originalObject = {
	name: '하늘',
	age: 30
}

let secondObject = {}
Object.assign(secondObject, originalObject)
```

```javascript
// 비구조화 연산자(destructuring operator) 사용
let originalObject = {
	name: '하늘',
	age: 30
}

let secondObject = { ...originalObject } // { name: '하늘', age: 30 }

// 객체 속성을 복사하면서 새로운 값 할당하기
let thirdObject = { ...originalObject, name: '도원' } // { name: '도원', age: 30 }
```

### 비구조화 할당으로 함수 파라미터에 전달된 객체 값 쉽게 접근하기
함수의 파라미터로 객체를 전달한 경우, 비구조화 할당을 사용하면 객체의 원하는 값을 쉽게 가져올 수 있습니다.  
예를 들면, Vuex의 actions는 아래 속성을 지닌 context 객체를 파라미터로 받습니다.

```javascript
{
	state,      // store.state와 같습니다. 또는 모듈에 있는 경우 로컬 state를 의미합니다.
	rootState,  // store.state와 같습니다. 모듈 안에만 존재합니다.
	commit,     // store.commit와 같습니다.
	dispatch,   // store.dispatch와 같습니다.
	getters,    // store.getters와 같습니다. 또는 모듈에 있는 로컬 getters를 의미합니다.
	rootGetters // store.getters와 같습니다. 모듈 안에만 존재합니다.
}
```

context.commit('increment') 구문으로 context 객체의 commit 속성에 직접 접근해 increment mutation을 호출해도 되지만, **비구조화 할당(원하는 객체 속성을 중괄호로 묶어 사용)을 써서 context.commit('increment') 구문을 context를 생략하여 `commit('increment')`로 줄일 수 있습니다.**

```javascript
const store = new Vuex.Store({
	state: {
		count: 0
	},
	mutations: {
		increment(state) {
			state.count++
		},
		decrement(state) {
			state.count--
		}
	},
	actions: {
		// 일반적인 사용 예
		increment(context) {
			context.commit('increment')
		},
		// 비구조화 할당을 사용한 예
		increment({ dispatch }) {
			// context.dispatch('decrement')
			dispatch('decrement')
		},
		decrement({ commit }) {
			// context.commit('decrement')
			commit('decrement')
		}
	}
})
```

