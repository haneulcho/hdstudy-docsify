# Vuex 활용 가이드
Vuex 코드 작성, 활용 안내입니다.  
Vuex에 대한 기본 사용법은 [Vuex 공식 문서](https://vuex.vuejs.org/kr/)를 참조하세요.

이 가이드는 엘소드 모바일 프로젝트에 필요한 부분을 바탕으로 최소한의 코드 작성 기준을 정리했습니다.

## 1. API로 가져온 데이터는 Vuex에 담기
BoardContents.vue 파일과 BoardComments.vue 파일이 있습니다. 이 두 파일에서 게시글과 댓글 목록 데이터를 공유해야 합니다. 이 데이터는 외부 API로 가져와 컴포넌트에 전달해야 하는데요. Vuex를 사용하면 여러 컴포넌트가 같은 데이터를 공유할 수 있습니다.

.vue 파일 methods 곳곳에 흩어진 API Request를 모두 Vuex actions에 모아 처리하고, 처리 후 결과 데이터(ex. boardPosts, boardComments)를 Vuex State에 담습니다. 그리고 이 State를 Getters에서 특정 조건에 따라 필터링하거나 그대로 사용합니다.

이렇게 API 데이터를 중앙에 모아두면 브라우저 개발자 도구에서 데이터의 생성, 제거 흐름을 추적하기 쉽습니다.

## 2. 상태를 가져올 때 state 대신 getters 사용하기
공식 문서에 따르면 Vuex 상태를 mutations 내에서만 변경하라고 권장합니다. 마찬가지로 컴포넌트에서 Vuex 상태를 가져올 때 직접 state에 접근하지 않고 getters를 computed에 매핑하여 사용하도록 합니다.

```javascript
// Good
computed: {
	boardPosts() {
		return this.$store.state.boardPosts
	}
}
```

```javascript
// Even Better
computed: {
	boardPosts() {
		return this.$store.getters.boardPosts
	}
}
```

## 3. .vue 파일에서 컴포넌트 바인딩 헬퍼 사용하기
Vuex는 접두어 map을 넣어 컴포넌트에서 쉽게 state, mutations, actions, getters를 사용할 수 있는 헬퍼 메서드를 제공합니다. 컴포넌트 바인딩 헬퍼에는 `mapState, mapMutations, mapActions, mapGetters, createNamespacedHelpers` 5종류가 있습니다.

웬만하면 mutations는 actions 안에서 호출하고 state 대신 getters를 사용하도록 합니다.  
**컴포넌트 안에서는 mapActions, mapGetters 2가지 헬퍼를 주로 사용합니다.**  
**컴포넌트 단위에서 API 후처리(ex. 에러 헨들링)가 필요하지 않다면 mapActions를 사용합니다.**

```javascript
// Good
computed: {
	boardPosts() {
		return this.$store.getters.boardPosts
	},
	boardComments() {
		return this.$store.getters.boardComments
	},
	filteredBoardComments() {
		return this.$store.getters.filteredBoardComments
	}
},
methods: {
	fetchPosts() {
		this.$store.dispatch.fetchPosts()
	},
	fetchComments() {
		this.$store.dispatch.fetchComments()
	}
}
```

```javascript
// Even Better
import { mapGetters, mapActions } from 'vuex'

computed: {
	...mapGetters([ 'boardPosts', 'boardComments', 'filteredBoardComments' ])
},
methods: {
	// 후처리가 필요 없고 단독 호출할 경우 mapActions 활용 가능
	...mapActions([ 'fetchPosts', 'fetchComments' ])
}
```

## 4. 연관있는 부분 모아 모듈로 만들기
서로 관련있는 부분을 모아 모듈로 만듭니다. 예를 들면, 게시글 가져오기, 댓글 가져오기, 게시글 작성하기, 게시글 삭제하기, 댓글 추천하기 기능 등 게시판과 관련된 코드를 모두 board.store.js에 모아 Vuex 모듈에 등록합니다.

store 폴더 안에 modules 폴더를 생성하고 auth.store.js, board.store.js, character.store.js 처럼 파일명에 .store 접미어를 붙여 파일이 Vuex 모듈임을 설정합니다.

Vuex Store modules 객체에 **`import한 [filename].store.js 파일을 모듈이름: import한 파일이름으로 지정`**하면 Vuex 모듈이 생성됩니다.

```javascript
// store/modules/auth.store.js
const state = {
	user: null
}

const mutations = {
	SET_CURRENT_USER(state, payload) {
		state.user = payload.user
	}
}

const actions = {
	signIn({ commit }, payload) {
		const res = AUTH.signIn(payload)
		commit('SET_CURRENT_USER', res.data)
	}
}

const getters = {
	currentUser: (state) => state.user
}

export default {
	namespaced: true,
	state,
	mutations,
	actions,
	getters
}
```

```javascript
// store/index.js
import Vue from 'vue'
import Vuex from 'vuex'

import authModule from './modules/auth.store.js'
import boardModule from './modules/board.store.js'
import characterModule from './modules/character.store.js'

Vue.use(Vuex)

export default new Vuex.Store({
	modules: {
		auth: authModule,
		board: boardModule,
		character: characterModule
	}
})
```

```javascript
// components/BoardList.vue 중 일부
import { mapGetters, mapActions } from 'vuex'

computed: {
	...mapGetters(
		'board', [ 'boardPosts', 'boardComments', 'filteredBoardComments' ]
	),
	...mapGetters(
		'auth', [ 'user' ]
	),
},
methods: {
	...mapActions(
		'board', [ 'fetchPosts', 'fetchComments' ]
	),
	...mapActions(
		'auth', [ 'signIn' ]
	)
}
```

## 5. modules 객체에 filename.store.js 모듈 자동 등록하기
모듈 파일이 늘어나면 Vuex Store modules 객체에 import한 파일을 각각 추가하기 번거롭습니다.


<span style="color:red;font-weight:bold">modules 폴더 안에 filename.store.js 파일을 모아 외부로 노출하는 index.js 파일을 만들고, 이 index.js 파일을 store/index.js 에서 불러 modules에 등록합니다.</span>

이렇게 하면 store/index.js 파일을 수정하지 않고 모듈을 자동 등록할 수 있습니다.

```javascript
// store 폴더 구조
store
│  ├─index.js
│  └─modules
│          index.js // filename.store.js 파일들을 store/index.js의 modules에 자동 등록
│          auth.store.js
│          board.store.js
│          character.store.js
```

```javascript
// store/modules/index.js
const storeModuleFiles = require.context('.', false, /\.store\.js$/)
const modules = {}

storeModuleFiles.keys().forEach((filename) => {
	if (filename === './index.js') {
		return
	}

	const moduleName = filename.replace(/(\.\/|\.store\.js)/g,'').replace(/^\w/, c => c.toLowerCase())

	modules[moduleName] = storeModuleFiles(filename).default || storeModuleFiles(filename)
})

export default modules
```

```javascript
// store/index.js
import Vue from 'vue'
import Vuex from 'vuex'

import modules from './modules'

Vue.use(Vuex)

export default new Vuex.Store({
	modules
})
```
