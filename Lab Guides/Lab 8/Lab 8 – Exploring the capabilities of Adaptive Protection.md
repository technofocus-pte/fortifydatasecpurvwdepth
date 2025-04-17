# 실습 8 – Adaptive Protection의 기능 살펴보기

## 연습 1 – Adaptive Protection 설정하기

### 작업 1 – Adaptive Protection에 대한 위험 수준을 설정하기

1.  Microsoft Edge에서 새 InPrivate 창을 열고
    `https://purview.microsoft.com` 로 이동하고 관리자 텐넌트를 사용하여
    로그인하세요.

2.  탐색 바에서 **Solutions** \> **Insider risk** **management**로
    이동하세요.

![](./media/image1.png)

3.  하위 탐색에서 **Adaptive Protection (Preview)**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  **Adaptive Protection**를 활성화하는 동안 빠른 시작 옵션을 사용했기
    때문에 2개의 DLP 정책이 생성된 것을 볼 수 있습니다.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

5.  이제 하위 메뉴에서 **Risk levels for Adaptive Protection**을
    클릭하고 드롭다운에서 **Data leaks by a user**을 선택하세요.

![BrokenImage](./media/image4.png)


6.  Under **Define conditions for risk levels**에서**Elevated**  위험의
    경우 **User performs at least 3 data exfiltration activities,
    each…**를 선택하세요. **Moderate** 위험의 경우 **User performs at
    least 2 data exfiltration activities, each…**를 선택하세요.
    **Minor** 위험의 경우** User performs at least 1 data exfiltration
    activities, each…**를 선택하세요. **Save**를 클릭하세요.

![BrokenImage](./media/image5.png)



7.  마찬가지로, Insider risk management에서 사용 가능한 모든 정책에 대한
    조건을 사용자 지정할 수 있습니다.

8.  이제 각 수준에 대한 DLP 정책을 사용자 지정할 수 있습니다.

### 작업 2 – Adaptive Protection의 각 위험 수준에 대한 기본 DLP 정책을 탐색하기

1.  Adaptive Protection에서DLP 정책을 선택하고 Endpoint DLP용 Adaptive
    Protection Policy을 선택하세요.

![BrokenImage](./media/image6.png)


2.  **Edit**를 선택하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image7.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

3.  **Customize advanced DLP rules**에 도달할 때까지Next를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  각 위험 수준에 대한 규칙 및 조건을 확인하세요. **Next**를
    클릭하세요.

5.  **Policy mode** 페이지에서**Turn it on right away** 근처의 라디오
    버튼을 선택하세요. **Next**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  **Submit**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

7.  단계를 반복하여 Teams용 Adaptive Protection Policy 및 Exchange DLP에
    대한 정책을 활성화하세요.

8.  현재로서는 규칙이나 정책을 생성하지 않지만 실습을 완료한 후 사용
    가능한 다양한 옵션을 탐색할 수 있습니다.
