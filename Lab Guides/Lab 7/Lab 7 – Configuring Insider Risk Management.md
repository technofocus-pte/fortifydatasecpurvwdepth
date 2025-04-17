# 실습 7 – Insider Risk Management 구성하기

## 목표:

이 실습에서는 Insider Risk Management 정책을 사용하여Insider Risk
Management를 구성하는 방법을 알아볼 것입니다. 실습 2에서 생성한the
Sensitive Info Type과 실습 5에서 생성한 DLP 정책을 사용하여 위험한
브라우저 사용이나 데이터 도난이나 유출로부터 조직을 보호하는 정책을
생성할 것입니다.

이를 위해 Azure에서 조직의 장치를 나타내는 인프라를 생성할 것입니다.
Azure AD 및 Intune에서 해당 장치을 온보딩하고 MDM 에이전트를 설치하여
해당 컴퓨터에서 경고를 가져오는 데 사용할 수 있도록 하는 방법을 알아볼
것입니다.

## 연습 1: VM 시계를 동기화하기

1.  VM에 로그인한 후windows 아이콘을 선택하세요. **Date and time**를
    검색하여 **Date and time settings**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image1.jpg)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

2.  설정 화면이 열리면 Additional setting에서 **Sync now**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image2.jpg)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

3.  이렇게 하면 자동 동기화가 작동하지 않는 경우를 대비하여 시간을
    동기화하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image3.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

## 연습 2: Insider Risk Management 정책을 생성하기

### 필수 구성 요소

#### 1 단계 – 사용자를Insider risk management 역할 그룹에 추가하기

1.  Microsoft Purview 포털이 열려 있으면 2 단계를 진행하세요. 그렇지
    않으면 the `https://purview.microsoft.com`를 열고**MOD
    Administrator** 자격 증명으로 로그인하세요.

![](./media/image4.png)

2.  탐색에서**Settings**를 선택하고**Role groups**를 선택하세요. **Role
    groups**에서 **Insider Risk Management**를 선택하세요. **Edit**를
    선택하세요. 옆창에서**Edit**를 다시 선택하세요.

![](./media/image5.png)

3.  **Edit Members of the role group** 페이지에서 **Choose users**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  **MOD Admin**, **Patti**, **Megan** 및**Alex** 근처의 있는 확인란을
    선택하세요. **Select**를 선택하세요.

![](./media/image7.png)

5.  **Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  사용자를 역할 그룹에 추가하기 위해 **Save**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

7.  단계를 완료하기 위해 **Done**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

#### 2단계 – Insider risk analytics 인사이트를 활성화하기

1.  Microsoft Purview 포털에서 **Settings**로 이동하고 **Insider risk
    management**를 이돌하세요. **Analytics**로 이동하여 라디오 버튼을
    활성화하고 **Save**를 선택하세요.

![](./media/image11.png)

#### 3 단계 – 디바이스를 온보딩하기

이 배포 시나리오에서는 아직 온보딩되지 않은 장치를 온보딩하고 Windows 10
장치에서 내보자 위험 활동을 검색하려고 합니다.

Insider Risk Policy을 생성하기 위한 필수 구성 요소로 Microsoft Entra
ID에 장치/VM을 등록해야 합니다.

1.  VM에서 windows **Setting**를 여세요.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

2.  **Accounts** \> **Access work or school**로 이동하세요. **Access
    work or school** 페이지에서 **Connect**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

3.  **Set up a work or school account** 프롬픝에서 **Join this device to
    Microsoft Entra ID**를 클릭하세요.

![](./media/image14.png)

4.  로그인 프롬프트에 실습 환경의 리소스 탭에 제공된 **MOD
    Administrator** 자격 증명으로 로그인하세요. 

![A screenshot of a computer Description automatically
generated](./media/image15.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

![Graphical user interface, application, PowerPoint Description
automatically generated](./media/image16.png)

그래픽 사용자 인터페이스, 애플리케이션, PowerPoint 설명이 자동으로
생성됩니다.

5.  프롬프트: **Make sure this is your organization**에서**Join**를
    누르세요.

![Graphical user interface, text, application Description automatically
generated](./media/image17.png)

그래픽 사용자 인터페이스, 텍스트, 애플리케이션 설명이 자동으로
생성됩니다

6.  완료되면 확인 창이**You’re all set!** 표시됩니다. **Done**를
    클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

7.  **Accounts** \> **Access work or school**로 다시 이동하세요.
    **Access work or school** 페이지에서 **Connect**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

8.  **Set up a work or school account** 프롬프트에서 MOD admin 자격
    증명을 사용하여 로그인하세요.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

9.  **Setting up your device** 페이지에서 **Got it**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

10. **Windows settings** \> **Accounts** \> **Access work or school** \>
    **Connected to Contoso MDM** \> **Info** \> **Sync**로 이동하세요.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

![A screenshot of a computer Description automatically
generated](./media/image22.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

11. VM에서 windows 기호를 클릭하세요. 사용자 **Admin**를 선택하여**Sign
    out**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

12. 사용자 화면에서 **Other user**를 선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image24.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

13. 실습 환경의 홈 페이지에서 제공된 O365 자격 증명을 입력하고 **MOD
    Administrator**로 VM에 로그인하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image25.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

14. Windows 설정 앱을 닫으세요. 실습 VM에서 **MOD Administrator** 계정을
    사용하여 to  `https://purview.microsoft.com`에 로그인하세요.

15. **Settings** \> **Device onboarding** \> **Devices**를 선택하세요.

![](./media/image26.png)

16. **Turn on Device onboarding**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

17. **Settings** \> **Device onboarding** \> **Onboarding**에서
    **Download package**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

18. 파일을 마우스 오른쪽 버튼으로 클릭하고 **Extract all…**를
    선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image29.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

![A screenshot of a computer Description automatically
generated](./media/image30.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

19. 완료되면 폴더를 열고 **Administrator** 권한으로 파일을 실행하세요.

![A computer screen with a computer screen Description automatically
generated](./media/image31.png)

컴퓨터 화면 설명이 자동으로 생성된 컴퓨터 화면이 있는 컴퓨터 화면

20. Click on **More info**를 클릭하세요.

![Graphical user interface, application Description automatically
generated](./media/image32.png)

그래픽 사용자 인터페이스, 애플리케이션 설명이 자동으로 생성됩니다

21. **Run anyway**를 클릭하세요.

![A screenshot of a computer error Description automatically
generated](./media/image33.png)

컴퓨터 오류 설명의 스크린샷 자동으로 생성됩니다

22. 명령 프롬프트에서 **Y**를 누르고 Enter 키를 눌러 확인하고 메시지가
    표시되면 계속하세요.

![A screenshot of a computer error Description automatically
generated](./media/image34.png)

컴퓨터 오류 설명의 스크린샷 자동으로 생성됩니다

23. 장치가 온보딩되었다는 메시지가 표시됩니다. Command Prompt에서
    메시지가 In **Press any key to continue …**가 표시되면 아무 키를
    누르세요.

24. Once the Command Prompt가 닫히면 관리자 모드에서 Command Prompt를
    열어 감지 테스트를 실행하고 프롬프트에서 아래 명령을 복사하여
    실행하세요. Command Prompt 창이 자동적으로 닫힙니다.

`powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'`

![Text Description automatically generated](./media/image35.png)

텍스트 설명이 자동으로 생성됩니다

25. 탐색에서 설정을 클릭하여 **settings**을 열고**Devices Onboarding**
    \> **Devices**를 선택하세요.

**참고:** 장치 온보딩을 활성화하는 데 일반적으로 약 60초가 걸리지안 최대
30분까지 걸릴 수 있습니다.

26. **Devices** 목록을 확인할 수 있습니다. 장치를 온보딩할 때까지 목록이
    비어있으며 완료되면 VM이 온보딩된 장치로 나열되는 것을 볼 수
    있습니다.

### 작업 1: Risky Browser Usage을 감지하고 점수를 매기기 위한 조직 차원의 정책을 생성하기

#### 1 단계 – 새로운 정책을 생성하기

1.  이전 작업에서 브라우저 창을 닫은 경우
    the `https://purview.microsoft.com` 열고 Admin 자격 증명으로
    로그인하세요.

2.  **Insider Risk Management**로 이동하여**Policies** 탭을 선택하세요.
    정책 wizard을 열기 위해**Create policy**를 선택하세요.

![](./media/image36.png)

3.  **Choose a policy template** 페이지에서**Risky browser usage
    (preview)**에서**Risky browser usage (preview)**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  모든 사전 요구 사항이 충족되었는지 확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

5.  계속하기 위해**Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  **Name and description** 페이지에서 다음 필드를 완료하세요:

    - Name (필수): `Risky usage of browser`

    - Description
      (선택적): `This is a test policy for the risky browser usage.`

7.  계속하기 위해 **Next**를 선택하세요.

![Graphical user interface, text, application Description automatically
generated](./media/image40.png)

그래픽 사용자 인터페이스, 텍스트, 애플리케이션 설명이 자동으로
생성됩니다

8.  **Choose users, groups, & adaptive scopes** 페이지에서 **All users,
    groups, & adaptive scopes**를 선택하세요. 계속하기 위해 **Next**를
    선택하세요.

9.  **Exclude users and groups** 페이지에서 **Next**를 선택하세요.

10. **Decide whether to prioritize** 페이지에서**I don’t want to specify
    priority content right now**를 선택하세요 (정책을 생성한 후 이
    작업을 수행할 수 있습니다). 계속하기 위해 **Next**를 선택하세요.

![Graphical user interface, text, application Description automatically
generated](./media/image41.png)

그래픽 사용자 인터페이스, 텍스트, 애플리케이션 설명이 자동으로
생성됩니다

11. **Triggers for this policy** 페이지에서**Turn on indicators**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

12. **Choose indicators to turn on**에서**Select all under Risky
    browsing indicators (preview)**를 선택하고 나머지 상자의 선택을
    취소하세요.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

13. 아래로 스크롤하여**Save**를 선택하세요.

14. **Triggers for this policy**의**Select which activities will trigger
    this policy**에서 모든 옵션을 선택하고**Next**를 클릭하세요.

![Graphical user interface, text, application Description automatically
generated](./media/image44.png)

그래픽 사용자 인터페이스, 텍스트, 애플리케이션 설명이 자동으로
**생성됩니다**

15. **Triggering thresholds for this policy** 페이지에서**Use custom
    thresholds (Recommended)**를 선택하여 모든 임계값을 하루에**1**로
    변경하고**Next**를 선택하세요.

![Graphical user interface, application Description automatically
generated](./media/image45.png)

그래픽 사용자 인터페이스, 애플리케이션 설명이 자동으로 생성됩니다

![A screenshot of a computer Description automatically
generated](./media/image46.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

16. **Indicators** 페이지에서**Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

17. **Decide whether to use default or custom indicator thresholds**에서
    **Use default thresholds for all indicators**를 선택하여**Next**를
    선택하세요.

![Graphical user interface, text, application Description automatically
generated](./media/image48.png)

그래픽 사용자 인터페이스, 텍스트, 애플리케이션 설명이 자동으로
생성됩니다

18. **Review settings and finish**에서**Submit**를 선택하세요.

![Graphical user interface, text, application Description automatically
generated](./media/image49.png)

그래픽 사용자 인터페이스, 텍스트, 애플리케이션 설명이 자동으로
생성됩니다

19. **Your policy was created**에서 **Done**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image50.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

20. 탭을 열어 두고 다음 작업을 계속하세요.

#### 2 단계 – 정책 점수 매기기

1.  **Risky usage of browser**라는 정책을 클릭하세요. **Start scoring
    activity for users**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

2.  **Reason** 필드의**Add users to multiple
    policies** 창에서**Testing the policy**를 입력하세요.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

3.  **This should last for (choose between 5 and 30 days)** 필드에
    **10** 일을 선택하세요.

4.  **Search user to add to policies** 필드를 사용하세요. **MOD
    Admin**를 추가하세요. **Start scoring activity**를 클릭하세요.

5.  **Scoring activity for 1 users** 활동을 시작했다는 확인릏 받으면
    **Close**를 클릭하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image53.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

### 작업 2: 퇴사하는 사용자에 의한 데이터 도난

#### 1 단계 – 새로운 정책을 생성하기

1.  이전 작업에서 브라우저 창을 닫은
    경우 `https://purview.microsoft.com` 열고 관리자 자격 증명으로
    로그인하세요.

2.  **Insider Risk Management**로 이동하여 **Policies** 탭을 선택하세요.
    정책wizard을 열기 위해 **Create policy**를 선택하세요.

![](./media/image36.png)

3.  Choose a policy template 페이징에서Data theft의 Data theft by
    departing users를 선택하세요. 계속하려면 Next을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image54.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  **Name and description** 페이지에서 다음 필드를 완료하세요:

    - Name (필수): `Data theft by a user`

    - Description
      (선택적): `This is a test policy for the preventing data theft.`

5.  계속하려면 Next을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image55.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  **Choose users, groups, & adaptive scopes** 페이지에서 **All users,
    groups, & adaptive scopes**를 선택하세요. 계속하려면 **Next**을
    선택하세요.

7.  **Exclude users, groups, & adaptive scopes** 페이지에서 **Next**을
    선택하세요.

8.  **Decide whether to prioritize** 페이지에서 **I want to specify
    priority content**를 선택하세요. **Sensitivity
    labels** 및 **Sensitive info types**의 확인란을 선택하세요.
    계속하려면 **Next**을 선택하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image56.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

9.  **Sensitivity labels to prioritize** 페이지에서 **Add or edit
    sensitivity labels**를 선택하세요. 플라이아웃
    창에서 **Internal/Employee data (HR)**를 선택하여**Add**를
    선택하세요. **Next**를 클릭하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

10. **Sensitive info types to prioritize** 페이지에서 **Add or edit
    sensitive info types**를 선택하세요. 플라이아웃 창에서 **Credit Card
    Number**, **Contoso Employee ID** 및**Contoso Employee EDM**를
    검색하고 선택하세요.  **Add**를 선택하세요. **Next**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image58.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

11. **Decide whether to score only activity with priority content**에서
    **Get alerts for all activity**를 선택하세요. **Next**를 선택하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

12. Triggers for this policy 페이지에서default를 선택하여 Next를
    선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image60.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

13. **Indicators** 페이지에서 프롬프트에서 **Turn on indicators**를
    선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image61.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

14. **Select all under Office indicators**를 선택하여**Save**를
    클릭하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image62.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

15. 모든 옵션을 선택하고**Next**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

16. **Detection options** 페이지에서default를 선택하여 **Next**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

17. **Indicators** 페이지에서 **Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

18. **Decide whether to use default or custom indicator thresholds**에서
    **Customise thresholds**를 선택하여 각 단계에 대해 각각**1**, **2**,
    및 **3**개의 이벤트를 사용한 후 Next를 선택하세요.

![A screenshot of a computer screen Description automatically
generated](./media/image65.png)

컴퓨터 화면의 스크린샷 설명이 자동으로 생성됩니다

19. **Review settings and finish**에서 **Submit**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

20. **Your policy was created**에서 **Done**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

21. 탭을 열어 두고 다음 작업을 계속하세요.

#### 2 단계 – 정책 점수 매기기

1.  **Data theft by a user**이라는 새 정잭을 클릭하세요. **Start scoring
    activity for users**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

2.  **Reason field in the Add users to multiple
    policies** 창에서 **Testing the policy**를 입력하세요.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

3.  **This should last for (choose between 5 and 30
    days)** 필드에서 **10**일을 선택하세요.

4.  **Search user to add to policies** 필드를 사용하세요. **MOD
    Admin**를 추가하세요. **Start scoring activity**를 클릭하세요.

5.  **Scoring activity for 1 users** 활동을 시작했다는 확인을
    받으면 **Close**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

### 작업 3: 사용자에 의한 데이터 유출

#### 1단계 – 새로운 정책을 생성하기

1.  이전 작업에서 브라우저 창을 닫은 경우`https://purview.microsoft.com`
    를 열고 관리자 자격 증명으로 로그인하세요.

2.  **Insider Risk Management**로 이동하고 **Policies** 탭을 선택하세요.
    정책 wizard을 열기 위해**Create policy**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

3.  **Choose a policy template** 페이지의 **Data leaks**에서 **Data
    leaks**를 선택하세요. 계속하려면 **Next**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image70.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  **Name and description** 페이지에서 다음 필드를 완료하세요:

    - Name (필수): `Data leaks by a user`

    - Description
      (선택적): `This is a test policy for preventing data leaks.`

5.  계속하려면 **Next**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  **Choose users and groups** 페이지에서**Include all users and
    groups**를 선탯하세요. 계속하려면 **Next**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

7.  **Exclude users and groups** 페이지에서 **Next**를 선택하세요.

8.  **Decide whether to prioritize** 페이지에서**I want to specify
    priority content**를 선택하세요. **SharePoint sites**, **Sensitivity
    labels** 및 **Sensitive info types**의 확인란을 선택하세요.
    계속하려면 **Next**을 선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image73.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

9.  **SharePoint sites to prioritize** 페이지에서**Add or edit
    SharePoint sites**를 선택하세요. 플라이아웃
    창에서`https://{TENANTPREFIX}.sharepoint.com/sites/ContosoWeb1` 를
    선택하고**Add**를 선택하세요. **Next**를 클릭하세요.

10. **Sensitivity labels to prioritize** 페이지에서**Add or edit
    sensitivity labels**를 선택하세요. 플라이아웃
    창에서**Internal/Employee data (HR)**를 선택하여**Add**를
    선택하세요. **Next**를 선택하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

11. **Sensitive info types to prioritize** 페이지에서**Add or edit
    sensitive info types**를 선택하세요. 플라이아웃 창에서**Credit Card
    Number**, **Contoso Employee ID** 및**Contoso Employee EDM**를
    검색하고 선택하세요.  **Add**를 선택하세요. **Next**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image58.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

12. **Decide whether to score only activity with priority content**에서
    **Get alerts for all activity**를 선택하세요. **Next**를 선택하세요.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

13. **Triggers for this policy** 페이지에서**User performs an
    exfiltration activity** 근처의 라디오 버튼을 선택하세요. Select
    which activities will trigger this policy에서 사용 가능한 모든 옵션
    특히 **Download content from SharePoint**를 선택하세요. **Next**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image74.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

14. **Triggering thresholds for this policy**에서**Use custom
    thresholds**를 선택하세요. 모든 임계값을 **1**로 설정하고**Next**를
    선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image75.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

15. **Indicators** 페이지의 기본 설정을 선택하여 **Next**를 선택하세요.

16. **Decide whether to use default or custom indicator thresholds**에서
    **Customise thresholds**를 선택하고 각 단계에 대해 각각**1**, **2**,
    및 **3**개의 이벤트를 사용한 후 **Next**를 선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image76.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

17. **Review settings and finish**에서**Submit**를 선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image77.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

18. **Your policy was created**에서 **Done**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image78.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

19. 탭을 열어 두고 다음 작업을 계속하세요.

#### 2 단계 – 정책 점수 매기기

1.  **Data leaks by a user**라는 새 정책을 클릭하세요. Select **Start
    scoring activity for users**를 선택하세요.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image79.png)

컴퓨터 화면의 스크린샷: 설명이 중간 신뢰도로 자동으로 생성됩니다

2.  **Reason field in the Add users to multiple policies** 창에서
    Testing the policy를 클릭하세요. **This should last for (choose
    between 5 and 30 days)** 필드에서 **10**일을 선택하세요. **Search
    user to add to policies** 필드를 사용하세요. **MOD Admin**를
    사용하세요. **Start scoring activity**를 클릭하세요.

3.  **Scoring activity for 1 user** 활동을 시작했다는 확인을
    받으면**Close**를 클릭하세요.

Insider risk management 정책을 성공적으로 생성했습니다.

## 요약:

이 실습에서는end-to-end에서 Insider Risk Management를 설정하는 방법을
살펴봤습니다. 사용자 고유의 구독 및 라이선스가 있으면 이 실습 가이드를
사용하여 Purview에서 Adaptive Protection 기능을 탐색하는 데 사용할 수
있는 Insider Risk management 정책에 대한 다양한 경고 (평가판 구독에서는
사용할 수 없는 제한된 데이터가 포함된 이메일 보내기 포함)를 생성하는
데에도 사용할 수 있는 Azure 설정을 생성할 수 있습니다.
