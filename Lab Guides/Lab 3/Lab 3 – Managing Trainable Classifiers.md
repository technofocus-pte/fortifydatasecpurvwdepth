# 실습 3 – Trainable Classifiers 관리하기

## 목표:

Contoso Ltd. 테넌트에는 나중에 여러 재무 관련 문서 및 보고서를 저장하는
데 사용될 SharePoint 사이트 모음이 포함되어 있습니다. 이러한 문서의
특성으로 인해 이러한 파일을 인식하고 레이블을 지정하기 위해 학습 가능한
classifier를 생성해야 합니다. 이를 위해 사용자 지정 학습 가능한
classifier를 활성화하고 이 실습에서 새 classifier를 생성할 것입니다.

## 연습 1 – Trainable classifier 생성하기

이 작업에서는 Patti는 trainable classifier를 생성하고 Contoso Ltd에서
생성하고 저장한 일반적인 데이터를 식별하기 위해 다른 SharePoint 사이트를
선택할 것입니다.

1.  **Microsoft Edge**에서 **New InPrivate Window**를
    열고`https://purview.microsoft.com` 로 이동하고 사용자
    이름`PattiF@WWLx``{TENANTPREFIX}.onmicrosoft.com` 및 리소스 탭에
    제공된 사용자 암호를 사용하여 **Patti Fernandez** 로 로그인하세요.

2.  왼쪽 탐색에서**Solutions** \> **Data Loss Prevention**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

컴퓨터 설명의 스크린샷 자동으로 생성됨

3.  왼쪽 창에서 **Classifiers**를 확장하세요. 하위 탐색
    창에서**Trainable Classifiers** 를 선택하세요. 새 classifier를
    생성하기 위해 **+ Create trainable classifier**를 선택하세요.

![](./media/image2.png)

4.  **Name and describe your trainable classifier** 페이지에서 다음
    정보를 입력하세요:

    - 이름: `Contoso Company Data`

    - 설명:
      `Trainable classifier for company data produced and stored by Contoso Ltd.`

5.  **Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

컴퓨터 설명의 스크린샷 자동으로 생성됨

8.  오른쪽 창을 열기 위해**Choose sites**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

컴퓨터 설명의 스크린샷 자동으로 생성됨

9.  다음SharePoint 사이트를 선택하여**Add**를 선택하세요.

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

![](./media/image5.png)

10. 선택한 사이트가 목록에 표시될 때까지 기다렸다가**Next**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

컴퓨터 설명의 스크린샷 자동으로 생성됨

11. **Source of the negative sample content page**에서**Learn** 사이트를
    선택하여**Next**를 선택하세요.

12. 설정을 검토하여**Create trainable classifier**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

컴퓨터 설명의 스크린샷 자동으로 생성됨

13. Your trainable classifier was created 메시지가 표시되면 **Done**를
    선택하세요.

현재 선택한 SharePoint 사이트의 문서 및 파일을 분석하고 있으며 최대
24시간이 걸릴 수 있습니다. 준비가 되면 다음을 수행할 수 있습니다.

- Classifier를 테스트하기

- Classifier를 검토하기

- Classifier를 게시하기

추가 검토를 위해 이미 존재하는 classifier를 탐색할 수 있습니다.

## 요약:

Contoso Ltd.의 기존 SharePoint 사이트에 저장된 파일과 일치하는 사용자
지정 trainable classifier를 성공적으로 생성했습니다.
