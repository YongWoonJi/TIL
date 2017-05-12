# EditText 밑줄 변경

1.Drawble xml을 생성

        <?xml version="1.0" encoding="utf-8"?>
        <layer-list xmlns:android="http://schemas.android.com/apk/res/android">
            <item>
                <shape android:shape="rectangle">
                    <!-- Draw a 2dp width border around shape -->
                    <stroke
                        android:color="#ff1e0c"
                        android:width="2dp"
                        />
                </shape>
            </item>
            <!-- Overlap the left, top and right border using background color  -->
            <item
                android:bottom="2dp"
                >
                <shape android:shape="rectangle">
                    <solid android:color="#fffbce"/>
                </shape>
            </item>
        </layer-list>

2.EditText의 Background속성을 생성한 Drawable로 바꿔준다
