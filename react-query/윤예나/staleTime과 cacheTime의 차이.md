## staleTime
* 데이터가 fresh 상태로 유지되는 시간이다.
* 해당 시간이 지나면 stale 상태가 되고 stale일 때 데이터를 새로 페칭한다.
* fresh 상태에서는 쿼리가 다시 mount 되어도 데이터 페칭을 하지 않는다.
* default 타임은 0초이다.

## cacheTime
* inactive 상태인 캐시 데이터가 메모리에 남아있는 시간이다.
* 이 시간이 지나면 캐시 데이터는 가비지 컬렉터에 의해 메모리에서 제거된다.
* default 타임은 5분이다.