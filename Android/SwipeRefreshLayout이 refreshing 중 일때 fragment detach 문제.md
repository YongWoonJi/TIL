# SwipeRefreshLayout이 refreshing 중 일때 fragment detach 문제

https://stackoverflow.com/questions/27057449/when-switch-fragment-with-swiperefreshlayout-during-refreshing-fragment-freezes

두가지 방법이 있다
1. onPause나 onDestroyView

        if (mSwipeRefreshLayout!=null) {
            mSwipeRefreshLayout.setRefreshing(false);
            mSwipeRefreshLayout.destroyDrawingCache();
            mSwipeRefreshLayout.clearAnimation();
        }
    

2. 레이아웃 xml에 가장 바깥 레이아웃에 SwipeRefreshLayout이 아닌 Framelayout을 넣는다
