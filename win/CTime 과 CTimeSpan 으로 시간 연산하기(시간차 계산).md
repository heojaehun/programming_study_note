## CTime 과 CTimeSpan 으로 시간 연산하기(시간차 계산)

- 시각을 관리하는 CTime 클래스와 시간을 관리하는 CtimeSpan을 이용하여 시간을 연산할 수 있다.
- CTime 클래스는 +, - 연산자를 지원하는데, -연산자의 경우 피연산자로 CTime을 사용하면 두 시각의 시간차를 구할 수 있다. 
- +, - 연산자와 피연산자로 CTimeSpan을 사용하면 특정 시각을 기준으로 일정시간 뒤(-)나 앞(+)의 시각을 계산할 수 있다.

```c++
// from MSDN : http://msdn.microsoft.com/en-us/library/3a34945y.aspx
CTime t1(1999, 3, 19, 22, 15, 0); // 10:15 PM March 19, 1999
CTime t2(1999, 3, 20, 22, 15, 0); // 10:15 PM March 20, 1999
CTimeSpan ts = t2 - t1;             // Subtract 2 CTimes
ATLASSERT(ts.GetTotalSeconds() == 86400L);
ATLASSERT((t1 + ts) == t2);       // Add a CTimeSpan to a CTime.
ATLASSERT((t2 - ts) == t1);       // Subtract a CTimeSpan from a CTime.   


// t1과 t2의 시간차
ts.GetDays(); 			// 두시각의 날짜 차이
ts.GetHours();			// 두시각의 시간 차이 ( –23 ~ 23 )
ts.GetTotalHours();		// 날짜를 시간으로 환산한 두 시각의 총 시간 차이
ts.GetMinutes();		// 두시각의 분 차이 (–59 ~ 59)
ts.GetTotalMinutes();	// 날짜와 시간을 분으로 환산한 두 시각의 총 분 차이	
ts.GetSeconds();		// 두 시각의 초 차이 (–59 ~ 59)
ts.GetTotalSeconds();	// 날짜 시간 분을 초로 환산한 두 시각의 총 초 차이


// CTimeSpan 활용하기 : http://msdn.microsoft.com/en-us/library/h7zw4wy1.aspx
CTimeSpan ts1;  // Uninitialized time value
CTimeSpan ts2a(ts1); // Copy constructor
CTimeSpan ts2b = ts1; // Copy constructor again
CTimeSpan ts3(100); // 100 seconds
CTimeSpan ts4(0, 1, 5, 12);    // 1 hour, 5 minutes, and 12 seconds   


// CTime 에 시간 더하기
t1 += CTimeSpan( 100 ); // ti 에 100초 더하기

// CTime 에 하루 더하기
t1 += CTimeSpan( 1, 0, 0, 0 ); // CTimeSpan( 날짜, 시간, 분, 초 )
```



[참고]: http://neodreamer-dev.tistory.com/231

