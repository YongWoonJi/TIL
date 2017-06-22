# Stable Id를 이용한 RecyclerView 성능 향상

http://www.kmshack.kr/2016/09/hasstableids%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-recyclerview-%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81%EB%B2%95/

HasStableIds사용을 통해 데이터 바인드 시 onBindViewHolder()를 최적화 되게 호출할 수 있다.

HasStableIds는 Adapter.setHasStableIds(boolean)을 통해 설정할 수 있으며, 사용하는 경우 어댑터의 getItemId(int)를 반드시 구현해야 작동한다.

기존의 notifyDataSetChanged() 호출 시 onBindViewHolder(view, int)는 현재 보이고 있는 포지션이 모두 호출되지만 StableId를 사용하게 된다면 이미 호출된 고정된 ID를 제외한 위치가 호출된다. notifyDataSetChanged()를 하였음에도 변경되는 ID만을 골라 해당 포지션만 onBindViewHolder(view, int)를 호출하게 됨으로 그만큼 성능은 향상된다.
