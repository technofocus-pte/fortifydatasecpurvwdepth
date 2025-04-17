# 실습 10 – Information Barriers 구성하기

## 목표:

Contoso에는 *HR, 영업, 마케팅, 연구* 및 *제조*의 *5*개 부서가 있습니다.
업계 규정을 준수하기 위해 일부 부서의 사용자는 다음 표에 나열괸 것 처럼
다른 부서와 통신해서는 안 됩니다:

[TABLE]

이 구조의 경우 Contoso의 계획에는 세 가지 IB 정책이 포함됩니다:

1.  영업팀이 연구와 소통하지 못하도록 고안된IB 정책

2.  연구가 영업과 통신하는 것을 방지하는 또 다른IB 정책.

3.  제조가 HR 및 마케팅 부서와만 통신할 수 있도록 설계된IB 정책.

## 연습 1 – 필수 구성 요소

### 작업 1 – 조직의 사용자에 대한 세그먼트를 생성하기

1.  VM에서 관리자로서**PowerShell**를 실행하세요.

![BrokenImage](./media/image1.png)


2.  다음을 실행하세요:

`Install-Module ExchangeOnlineManagement`

3.  If prompted ‘**Do you want PowerShellGet to install and import the
    NuGet provider now?**’ 및 ‘**Are you sure you want to install the
    modules from ‘PSGallery’?**’가 프롬프트되면 **y**를 입력하고enter를
    누르세요.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  설치가 완료되면 다음 명령을 실행하세요.

`Import-Module ``ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image3.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

5.  다음 명령을 실행하여 Exchange Online와 연결하세요.

`Connect-``IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  실습 환경의 홈 페이지에 제공된 **MOD Administrator** 자격 증명을
    사용하여 로그인하세요.

![BrokenImage](./media/image5.png)


7.  조직 구조를 생성하기 위해 **PowerShell**에서 다음 명령을 하나씩
    실행하세요.

`New-``OrganizationSegment`` -Name "HR" -``UserGroupFilter`` "Department -eq 'HR'"`

![BrokenImage](./media/image6.png)


`New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"`

`New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"`

`New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"`

`New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"`

### 작업 2 – Microsoft Teams에서 범위가 지정된 디렉터리 검색을 활성화하기

이름으로 검색을 켜려면

1.  <https://admin.teams.microsoft.com>로 Microsoft Teams admin center로
    이동하여**Teams** \> **Teams settings**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

2.  **Scope directory search using an Exchange address book policy**
    옆의**Search by name**에서 토글을**On**하세요. **Save**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

## 연습 2 – IB 정책을 생성하기

### 작업 1 – 세그먼트 간의 소통을 차단하기

1.  환경의 리소스 탭에 제공된 MOD Administration의 자격 증명을 사용하여
    Sign into the `https://purview.microsoft.com/` 를 로그인하세요.

2.  왼쪽 탐색창에서 **Solutions** \> **Information barriers**를
    선택하세요.

![](./media/image9.png)

3.  탐색 창에서 **Policies**를 선택하세요. **Policies** 페이지에서 새 IB
    정책을 생성하고 구성하기 위해 **Create policy**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  **Name** 페이지에서 졍책의 이름을—`Sales-Research`를 입력하세요.
    **Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

5.  **Assigned segment** 페이지에서 **Choose segment**. **On Select
    assigned segment for this policy** 창을 선택하고 Sales를 선택하세요.
    선택된 세그먼트를 정책에 추가하기 위해**Add**를 선택하세요.
    세그먼트는 하나만 선택할 수 있습니다.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

6.  **Next**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

7.  **Communication and collaboration**에서 **Blocked**를 선택하세요.
    **Choose segment**를 선택하여**Research**를 선택하고 **Add**를
    선택하세요**.**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

8.  **Communication and collaboration** 페이지에서**Communication and
    collaboration** 필드에 정책 유형을 Blocked로 선택하세요. **Next**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

9.  **Policy status** 페이지에서 활성 정책 상태를 **On**로 전환하세요.
    계속하려면**Next**를 선택하세요.

![BrokenImage](./media/image16.png)


10. **Review your settings** 페이지에서 정책에 대해 선택한 설정과 선택
    항목에 대한 제안이나 경고를 검토하세요. 정책 세그먼트 및 상태를
    변경하기 위해**Edit**를 선택하거나 정책을 생성하기 위해**Submit**를
    선택하세요.

![BrokenImage](./media/image17.png)


11. 정책이 생성되면**Done**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

### 작업 2 – PowerShell로 IB 정책을 생성하기

1.  VM에서 관리자로**PowerShell**를 실행하세요.

![BrokenImage](./media/image1.png)


2.  다음을 실행하세요:

`Import-Module ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image19.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

3.  다음 명령을 실행하여Exchange Online와 연결하세요.

`Connect-``IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

컴퓨터 설명의 스크린샷 자동으로 생성됩니다

4.  실습 환경의 리소스 페이징에 **MOD Administrator** 자격 증명을
    사용하여 로그인하세요.

5.  **Research-Sales**라는 IB 정책을 생성하기 위해 다음 명령을
    실행하세요. 이 정책이 활성화되고 적용되면**Research** 세그먼트에
    있는 사용자 **Sales** 세그먼트의 사용자와 통신하는 것을 방지할 수
    있습니다.

`New-``InformationBarrierPolicy`` -Name "Research-Sales" -``AssignedSegment`` "Research" -SegmentsBlocked "Sales" -State Inactive`

![BrokenImage](./media/image20.png)


6.  **Manufacturing-HRMarketing**라는 IB 정책을 생성하기 위해 다음
    명령을 실행하세요. 이 정책이 활성화되고 적용되면**Manufacturing**는
    **HR** 및 **Marketing**과만 통신할 수 있습니다. HR 및 Marketing은
    다른 세그먼트와의 통신에 제한되지 않습니다.

`New-``InformationBarrierPolicy`` -Name "Manufacturing-``HRMarketing``" -``AssignedSegment`` "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive`

![A computer screen shot of a computer program Description automatically
generated](./media/image21.png)

컴퓨터 프로그램 설명이 자동으로 생성되는 컴퓨터 스크린샷

7.  환경의 홈 페이지에 제공된**MOD Administration** 자격 증명을 사용하여
    `https://purview.microsoft.com/`로 로그인하세요.

8.  왼쪽 탐색 창에서 **Information barriers** \> **Policies**를
    선택하세요. **Policies** 페이지에서. 생성된 정책을 볼 수 있습니다.

![](./media/image22.png)

## 연습 3 – IB 정책을 적용하기

1.  환경의 리소스 탭에 제공된MOD Administration의 자격 증명을 사용하여
    `https://purview.microsoft.com/` 로 로그인하세요.

2.  왼쪽 탐색 창에서 **Information barriers**를 선택하세요.

![](./media/image9.png)

3.  하위 탐색에서 **Policy applications**를 선택하세요. **Apply all
    policies**를 선택하세요.

![](./media/image23.png)

**요약:**

이 실습에서는 IB 정책을 구현하기 위해 세그먼트를 생성하는 방법을
배웠습니다. 서로 다른 부문 가의 통신 및 협업을 허용하거나 차단하여
information barriers를 생성하기 위해 다양한 정책을 생성했습니다.
