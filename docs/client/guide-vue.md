# Vue 파일 작성 가이드
엘소드 모바일 프로젝트에서 꼭 지켜야 할 코드 작성 안내입니다.

## 1. 컴포넌트 속성은 kebab-case를, props 선언은 camelCase를
자바스크립트에서는 대부분 카멜 케이스(첫글자는 소문자로 시작하며 띄어쓰기나 단어 사이를 대문자로 구분하는 방법, 낙타의 등을 닮아 카멜이라 표현)를 사용합니다. 클래스명을 작성할 때는 파스칼 케이스(카멜 케이스와 유사, 첫글자는 대문자로 시작)를 사용합니다.

반면, HTML에서는 각 요소의 속성에 케밥 케이스(띄어쓰기나 단어 사이를 -로 구분하는 방법, 막대에 꽂힌 케밥을 아아 케밥이라 표현)를 사용합니다.

Vue.js는 `<template>`과 `<script>`에 사용한 카멜 케이스와 케밥 케이스를 자동 변환합니다. 컴포넌트 속성과 props 선언에 어떤 표기 방식을 사용할지 걱정하지 않아도 된다는 말이죠.

그러나 협업에서 이런 장점이 혼동을 주기도 합니다. 엘소드 모바일 프로젝트에서는 컴포넌트 이름, 변수, 속성명, 메서드명, 클래스명 등을 작성하는 데 몇 가지 규칙을 정했습니다.

| 구분 | 형식 | 예 |
| ---- | :----: | ---- |
| 컴포넌트명 | 파스칼 케이스 | `<BoardList />` |
| 컴포넌트 속성 | 케밥 케이스 | `<BoardList board-id="335544325" />` |
| props 선언 | 카멜 케이스 | `boardId: Number` |

```vue
<!-- Bad -->
<template>
	<board-list boardId="335544325" />
</template>

<script>
import BoardList from '@/components/BoardList.vue'
export default {
	components: {
		'BoardList'
	},
	props: {
		'board-id': Number
	}
}
</script>
```

```vue
<!-- Good -->
<template>
	<BoardList board-id="335544325" />
</template>

<script>
import BoardList from '@/components/BoardList.vue'
export default {
	components: {
		'BoardList'
	},
	props: {
		boardId: Number
	}
}
</script>
```

## 2. props는 type, required, validator를 포함해 자세히 쓰기
부모 컴포넌트에서 자식 컴포넌트로 속성을 전달할 때, 자식 컴포넌트의 props는 type를 포함해 최대한 자세히 작성합니다. 같은 속성 이름을 가졌더라도 그 유형이 Number냐 String이냐에 따라 오류가 발생하기도 합니다. 프로젝트 규모가 클수록 이런 오류는 추적이 어려워집니다.

**단순 array 대신 type(기본), required(기본), validator(선택)를 포함해 props를 작성합니다.**

```vue
<!-- Bad -->
<script>
export default {
	props: ['boardId']
}
</script>
```

```vue
<!-- Good -->
<script>
export default {
	props: {
		boardId: {
			type: Number,
			required: true,
			validator: (value) => value < 1000 // boardId가 1000 미만이면 유효값으로 인정
		}
	}
}
</script>
```

## 3. v-for와 v-if를 함께 쓰지 않기
특정 조건을 만족하는 요소를 반복하려면 v-for와 v-if를 같이 쓰는 대신 computed 속성을 사용해야 합니다.  
v-for는 v-if보다 처리 우선순위가 높아 조건을 검사하기 전 모든 요소를 순회합니다. 따라서 일부 요소가 변경되면 조건과 관계없이 다시 처음부터 모든 요소를 순회합니다.

요소가 많으면 많을수록 불필요한 반복이 늘어납니다. 이를 방지하기 위해 **특정 조건을 만족하는 요소를 먼저 computed 안에서 반환한 후, 반환한 값을 v-for로 반복해야 합니다.**

```vue
<!-- Bad -->
<template>
	<ul>
		<li
			v-for="user in users"
			v-if="user.isActive"
			:key="user.id"
		>
			{{ user.name }}
		</li>
	</ul>
</template>

<script>
export default {
	data: () => ({
		users: [
			{ id: 1, isActive: true },
			{ id: 2, isActive: false },
			{ id: 3, isActive: true }
		]
	})
}
</script>
```

```vue
<!-- Good -->
<template>
	<ul v-if="activeUsers">
		<li
			v-for="user in activeUsers"
			:key="user.id"
		>
			{{ user.name }}
		</li>
	</ul>
</template>

<script>
export default {
	data: () => ({
		users: [
			{ id: 1, isActive: true },
			{ id: 2, isActive: false },
			{ id: 3, isActive: true }
		]
	}),
	computed: {
		activeUsers() {
			return this.users.filter((user) => user.isActive)
		}
	}
}
</script>
```

## 4. template 안에 복잡한 수식 넣지 않기
`<template>` 안에 수식이 필요하다면 computed 또는 methods를 사용합니다. 

```vue
<!-- Bad -->
<template>
	<div>
		{{
			fullName.split(' ').map(function (word) {
				return word[0].toUpperCase() + word.slice(1)
			}).join(' ')
		}}
	</div>
</template>

<script>
export default {
	data: () => ({
		fulllName: 'Haneul Cho'
	})
}
</script>
```

```vue
<!-- Good -->
<template>
	<div>
		{{ normalizedFullName }}
	</div>
</template>

<script>
export default {
	data: () => ({
		fulllName: 'Haneul Cho'
	}),
	computed: {
		normalizedFullName() {
			return this.fullName.split(' ').map((word) => word[0].toUpperCase() + word.slice(1)).join(' ')
		}
	}
}
</script>
```

## 5. v-on은 `@`으로, v-bind는 `:`으로, v-slot은 `#`으로 쓰기
**`<template>` 안에서 v-on, v-bind, v-slot과 @, :, #의 축약법을 혼용하지 않습니다.**  
아예 축약을 하지 않거나 모두 축약을 하는 등 한 가지 방법을 선택해야 합니다. 엘소드 모바일 프로젝트에서는 모두 축약하여 사용합니다.

```vue
<!-- Bad -->
<template>
	<input
		v-bind:value="age"
		v-on:focus="handleFocused"
	>

	<template v-slot:header>
		Header content
	</template>
</template>
```

```vue
<!-- Good -->
<template>
	<input
		:value="age"
		@focus="handleFocused"
	>

	<template #header>
		Header content
	</template>
</template>
```

## 6. 같은 method를 created와 watch에 함께 쓰지 않기
fetchData()라는 메서드가 있습니다. 이 메서드는 컴포넌트가 초기화되거나 특정 값이 변화하면 재호출 하여 데이터를 갱신해야 합니다. fetchData()를 created와 watch에서 동시 호출해야 할까요?  

**watch에 immediate 속성을 true로 설정합니다. 다음으로 handler() 안에서 fetchData()를 호출합니다. 이렇게 하면 created에 fetchData를 호출한 것과 동일한 결과를 얻을 수 있습니다.** watch handler()의 매개변수인 newVal, oldVal을 활용하면 특정 값의 직전 값과 갱신 값을 비교해서 처리할 수 있습니다. 얼마나 좋게요?

```vue
<!-- Bad -->
<script>
export default {
	created() {
		this.fetchData()
	},
	watch: {
		'$route.params': 'fetchData'
	},
	methods: {
		fetchData() {
			console.log('데이터 호출')
		}
	}
}
</script>
```

```vue
<!-- Good -->
<script>
export default {
	watch: {
		'$route.params': {
			handler(newVal, oldVal) {
				this.fetchData()
			},
			deep: true,
			immediate: true
		}
	},
	methods: {
		fetchData() {
			console.log('데이터 호출')
		}
	}
}
</script>
```