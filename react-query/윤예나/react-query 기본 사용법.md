## 기본 셋팅

- QueryClientProvider 를 최상단에서 감싸주어야 한다.
- 쿼리 인스턴스를 생성한 후 client={queryClient}를 prop으로 전달해준다.

```
import { QueryClient, QueryClientProvider } from "react-query";

const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Home />
    </QueryClientProvider>
  );
}
```

## 쿼리 키

- 쿼리 키를 기반으로 데이터 캐싱을 관리한다.
- v4부터 무조건 배열로 지정해야 한다.

```
useQuery(['todos'], ...)
```

- 쿼리가 변수에 의존하는 경우 쿼리 키에도 해당 변수를 추가해주어야 한다.

```
const { data, isLoading, error } = useQuery(['todos', id], () => axios.get(`http://.../${id}`));
```

## 쿼리 함수

- 두 번째 인자로 Promise를 반환하는 함수를 넣어준다.

```
useQuery('todos', fetchTodos);
useQuery(['todos', todoId], () => fetchTodoById(todoId));
```

## 쿼리 옵션

### enabled

- 쿼리가 자동으로 실행되지 않게 설정하는 옵션이다.
- 아래의 코드는 id가 존재할 때만 쿼리 요청을 한다는 의미

```const { data } = useQuery(
  ['todos', id],
  () => fetchTodoById(id),
  {
    enabled: !!id,
  }
);
```

### retry

- 실패한 쿼리를 재시도하는 옵션
- 타입: boolean | number
- 쿼리 실패 시 기본적으로 3번 재시도=
- true로 설정하면 쿼리 실패 시 무한 재시도, false로 설정하면 재시도를 하지 않는다.

### staleTime

- 데이터가 fresh 상태로 유지되는 시간
- 해당 시간이 지나면 stale 상태가 된다.
- default staleTime은 0초
- fresh 상태에서는 쿼리가 다시 mount 되어도 fetch가 실행되지 않는다.

### cacheTime

- inactive 상태인 캐시 데이터가 메모리에 남아있는 시간
- 이 시간이 지나면 캐시 데이터는 가비지 컬렉터에 의해 메모리에서 제거됨
- default cacheTime 은 5분

### refetchOnMount

- **데이터가 stale 상태일 경우** 마운트 때 refetch 실행
- 타입: boolean | "always"
- default true
- always 로 설정하면 마운트 때마다 매번 refetch 실행

### refetchOnWindowFocus

- **데이터가 stale 상태일 경우** 윈도우 포커싱 때 refetch 실행
- 타입: boolean | "always"
- 예를 들어, 크롬에서 다른 탭을 눌렀다가 다시 원래 보던 중인 탭을 눌렀을 때도 이 경우에 해당한다.
- 심지어 F12로 개발자 도구 창을 켜서 네트워크 탭이든, 콘솔 탭이든 개발자 도구 창에서 놀다가 페이지 내부를 다시 클릭했을 때도 이 경우에 해당한다.
- default true
- always로 설정하면 항상 윈도우 포커싱 될 때마다 refetch 실행
- staleTime이 0초 이상으로 설정되어 있을 경우(= fresh한 상태), 그 시간 동안은 refetchOnWindowFocus가 true여도 데이터를 새로 페칭하지 않는다.

### refetchOnReconnect

- **데이터가 stale 상태일 경우** 재연결될 때 refetch 실행
- 타입: boolean | "always"
- default true
- always 로 설정하면 재연결될 때마다 매번 refetch 실행
