---
title: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ce76c72bad138a5c6c40afe717aadafec02c677
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015272"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기
  다음 절차에서는 사용자 지정 SharePoint 사이트 열 또는 *필드*를 만드는 방법 및 사이트 열을 사용 하는 내용 유형을 보여 줍니다. 또한 새 콘텐츠 형식을 사용 하는 목록을 만드는 방법도 보여 줍니다.

 이 연습에는 다음 작업이 포함됩니다.

- [사용자 지정 사이트 열을 만듭니다](#create-custom-site-columns).

- [사용자 지정 콘텐츠 형식을 만듭니다](#create-a-custom-content-type).

- [목록을 만듭니다](#create-a-list).

- [응용 프로그램을 테스트](#test-the-application)합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원 되는 버전의 Windows 및 SharePoint

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>사용자 지정 사이트 열 만들기
 이 예에서는 병원에서 환자를 관리 하기 위한 목록을 만듭니다. 먼저 다음과 같이에서 SharePoint 프로젝트를 만들고 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 여기에 사이트 열을 추가 해야 합니다.

#### <a name="to-create-the-project"></a>프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.
::: moniker range="=vs-2017"
2. **새 프로젝트** 대화 상자의 **Visual c #** 또는 **Visual Basic**에서 **Office/SharePoint** 노드를 확장 한 다음 **SharePoint 솔루션**을 선택 합니다.

3. **템플릿** 창에서 설치 된 sharepoint의 특정 버전에 대 한 **sharepoint 빈 프로젝트** 를 선택 합니다. 예를 들어 SharePoint 2016을 설치한 경우 **sharepoint 2016-빈 프로젝트** 템플릿을 선택 합니다.  

4. 프로젝트의 이름을 **클리닉**으로 변경한 다음 **확인** 단추를 선택 합니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 대화 상자에서 새 사용자 지정 필드 항목을 추가할 로컬 SharePoint 사이트의 URL을 입력 하거나 기본 위치 (SystemName)를 사용 합니다 `http://<` *SystemName* `>/)` .

6. **이 SharePoint 솔루션의 신뢰 수준을 선택** 하십시오. 섹션에서 기본 값인 **샌드박스 솔루션으로 배포**를 사용 합니다.

     샌드박스가 적용 된 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

7. **마침** 단추를 선택합니다. 이제 프로젝트가 **솔루션 탐색기**에 나열 됩니다.
::: moniker-end
::: moniker range=">=vs-2019"
2.  **새 프로젝트 만들기** 대화 상자에서 설치 된 sharepoint의 특정 버전에 대 한 **sharepoint 빈 프로젝트** 를 선택 합니다. 예를 들어 SharePoint 2016을 설치한 경우 **sharepoint 2016-빈 프로젝트** 템플릿을 선택 합니다.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 프로젝트의 이름을 **클리닉**로 변경한 다음 **만들기** 단추를 선택 합니다.

4. **디버깅에 사용할 사이트 및 보안 수준 지정** 대화 상자에서 새 사용자 지정 필드 항목을 추가할 로컬 SharePoint 사이트의 URL을 입력 하거나 기본 위치 (SystemName)를 사용 합니다 `http://<` *SystemName* `>/)` .

5. **이 SharePoint 솔루션의 신뢰 수준을 선택** 하십시오. 섹션에서 기본 값인 **샌드박스 솔루션으로 배포**를 사용 합니다.

     샌드박스가 적용 된 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

6. **마침** 단추를 선택합니다. 이제 프로젝트가 **솔루션 탐색기**에 나열 됩니다.
::: moniker-end

#### <a name="to-add-site-columns"></a>사이트 열을 추가 하려면

1. 새 사이트 열을 추가 합니다. 이렇게 하려면 **솔루션 탐색기**에서 **클리닉** 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **Add**  >  **새 항목**추가를 선택 합니다.

2. **새 항목 추가** 대화 상자에서 **사이트 열**을 선택 하 고 이름을 **PatientName**로 변경한 다음 **추가** 단추를 선택 합니다.

3. 사이트 열의 *Elements.xml* 파일에서 **형식** 설정을 **텍스트로**그대로 두고 **그룹** 설정을 **클리닉 사이트 열**로 변경 합니다. 완료 되 면 사이트 열의 *Elements.xml* 파일은 다음 예제와 같습니다.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > 사이트 열의 이름에 카멜식 대/소문자를 사용 하는 경우 Visual Studio는 DisplayName에 자동으로 공백을 추가 합니다.
    > SharePoint에 솔루션을 배포 하려고 할 때 문제가 발생할 수 있으므로 사이트 열 이름에 공백을 사용 하지 않는 것이 좋습니다.

4. 동일한 절차를 사용 하 여 두 개 이상의 사이트 열을 프로젝트에 추가 합니다. **PatientID** (type = "Integer") 및 **doctorname** (type = "Text"). 해당 그룹 값을 **클리닉 사이트 열**로 설정 합니다.

## <a name="create-a-custom-content-type"></a>사용자 지정 콘텐츠 형식 만들기
 다음으로, 이전 절차에서 만든 사이트 열을 포함 하는 콘텐츠 형식 (연락처 콘텐츠 형식에 따라)을 만듭니다. 콘텐츠 형식을 기존 콘텐츠 형식으로 기반으로 하 여 기본 콘텐츠 형식에서 새 콘텐츠 형식에 사용할 여러 사이트 열을 제공 하기 때문에 시간을 절약할 수 있습니다.

#### <a name="to-create-a-custom-content-type"></a>사용자 지정 콘텐츠 형식을 만들려면

1. 프로젝트에 콘텐츠 형식을 추가 합니다. 이렇게 하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. **템플릿** 창에서 **콘텐츠 형식** 템플릿을 선택 하 고 이름을 **환자 정보**로 변경한 다음 **추가** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 열립니다.

5. **이 콘텐츠 형식이 상속 되어야 하는 기본 콘텐츠 형식** 목록에서 새 콘텐츠 형식의 기반으로 사용할 콘텐츠 형식으로 **연락처** 를 선택 하 고 **마침** 단추를 선택 합니다.

     이렇게 하면 이전에 정의한 사이트 열 외에도 연락처 콘텐츠 형식의 다른 잠재적으로 유용한 사이트 열에 액세스할 수 있습니다.

6. 콘텐츠 형식 디자이너가 표시 되 면 **열** 탭에서 이전에 정의한 세 개의 사이트 열 ( **환자 이름**, **환자 ID**및 **의사 이름**)을 추가 합니다. 이러한 열을 추가 하려면 **표시 이름**에서 사이트 열 목록의 첫 번째 목록 상자를 선택한 다음 목록에서 각 사이트 열을 한 번에 하나씩 선택 합니다.

    > [!TIP]
    > 사이트 열을 더 빠르게 선택 하려면 열 이름의 처음 몇 글자를 입력 하 여 목록을 필터링 합니다.

7. 3 개의 사용자 지정 사이트 열 외에도 사이트 열 목록에서 **주석** 사이트 열을 추가 합니다.

8. **환자 이름** 및 **환자 ID** 사이트 열에 필요한 확인란을 선택 하 **여 필수 필드** 를 만듭니다.

9. **콘텐츠 형식** 탭에서 콘텐츠 형식 이름이 **환자**정보 인지 확인 하 고 설명을 **환자 정보 카드**로 변경 합니다.

10. **그룹 이름을** **클리닉 콘텐츠 형식**으로 변경 하 고 다른 설정은 기본값으로 둡니다.

11. 메뉴 모음에서 **파일**  >  **모두 저장**을 선택 하 고 콘텐츠 형식 디자이너를 닫습니다.

## <a name="create-a-list"></a>목록 만들기
 이제 새 콘텐츠 형식 및 사이트 열을 사용 하는 목록을 만듭니다.

#### <a name="to-create-a-list"></a>목록을 만들려면

1. 프로젝트에 목록을 추가 합니다. 이렇게 하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 합니다.

4. **템플릿** 창에서 **목록** 템플릿을 선택 하 고 이름을 **환자**로 변경한 다음 **추가** 단추를 선택 합니다.

5. 설정 **에 따라 목록 사용자 지정** 을 **기본값 (사용자 지정 목록)** 으로 두고 **마침** 단추를 선택 합니다.

6. 목록 디자이너에서 **콘텐츠** 형식 단추를 선택 하 여 **콘텐츠 형식 설정** 대화 상자를 표시 합니다.

7. 새 행을 선택 하 고 콘텐츠 형식 목록에서 **환자 정보** 콘텐츠 형식을 선택한 다음 **확인** 단추를 선택 합니다.

     이렇게 하면 **환자 정보** 콘텐츠 형식의 모든 사이트 열이 목록에 추가 됩니다.

8. 다음을 제외 하 고 목록에 있는 모든 사이트 열을 삭제 합니다.

    - 환자 ID

    - 환자 이름

    - 집 전화

    - 전자 메일

    - 의사 이름

    - 주석

9. **열 표시 이름**에서 빈 행을 선택 하 고, 사용자 지정 목록 열을 추가 하 고, 이름을 **병원**으로 지정 합니다. 데이터 형식을 **텍스트 한 줄**로 유지 합니다.

     사용자 지정 목록 열은이 목록에만 적용 됩니다. 사용자 지정 목록 열을 목록에 추가 하면 목록에 추가 된 모든 열을 포함 하 여 새 목록 내용 유형이 생성 되 고 기본 목록으로 설정 됩니다.

    > [!TIP]
    > 사이트 열 목록에서 열을 선택 하면 기존 사이트 열이 사용 됩니다. 그러나 목록에서 열을 선택 하지 않고 열 이름 값을 입력 하면 동일한 이름의 열이 목록에 이미 있는 경우에도 사용자 지정 목록 열이 생성 됩니다.

     필요에 따라 사용자 지정 목록 열의 데이터 형식을 한 **줄**로 설정 하는 대신이 열에 대 한 데이터 형식을 조회로 설정 하 고 테이블 또는 다른 목록에서 해당 값을 검색할 수 있습니다. 조회 열에 대 한 자세한 내용은 [SharePoint 2010의 관계 나열](/previous-versions/msp-n-p/ff798514(v=pandp.10)) 및 [조회 및 목록 관계](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14))를 참조 하세요.

10. **환자 ID** 및 **환자 이름** 상자 옆에 있는 **필수** 확인란을 선택 합니다.

11. **뷰 탭에서** 빈 행을 선택 하 여 뷰를 만듭니다. **보기 이름** 열 아래에 있는 빈 행에 **환자 정보** 를 입력 합니다.

     **보기** 탭에서 SharePoint 목록에 표시할 열을 지정할 수 있습니다.

12. 새 **환자 정보** 행을 선택한 다음 **기본값으로 설정** 단추를 선택 합니다.

     이제 목록의 기본 보기가 새 뷰로 표시 됩니다.

13. 다음 열을 **선택한 열** 목록에 다음 순서로 추가 합니다.

    - 환자 ID

    - 환자 이름

    - 집 전화

    - 전자 메일

    - 의사 이름

    - 병원

    - 주석

14. **속성** 목록에서 **정렬 및 그룹화** 속성을 선택 하 고 줄임표 단추 ![줄임표 아이콘](../sharepoint/media/ellipsisicon.gif "가변 매개 변수 아이콘") 을 선택 하 여 **정렬 및 그룹화** 대화 상자를 표시 합니다.

15. **열 이름** 목록에서 **환자 이름**을 선택 하 고 **정렬** 열이 **오름차순**으로 설정 되었는지 확인 한 다음 **확인** 단추를 선택 합니다.

## <a name="test-the-application"></a>애플리케이션 테스트
 이제 사용자 지정 사이트 열, 콘텐츠 형식 및 목록이 준비 되었으므로 SharePoint에 배포 하 고 응용 프로그램을 실행 하 여 테스트 합니다.

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. 메뉴 모음에서 **파일**  >  **모두 저장**을 선택 합니다.

2. **F5** 키를 선택 하 여 응용 프로그램을 실행 합니다.

     응용 프로그램이 컴파일되고 해당 기능이 SharePoint에 배포 되 고 활성화 됩니다.

3. 빠른 탐색 모음에서 **환자** 링크를 선택 하 여 **환자** 목록을 표시 합니다.

     목록의 열 이름은의 **보기** 탭에서 입력 한 열과 일치 해야 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. **새 항목 추가** 링크를 선택 하 여 환자 정보 카드를 만듭니다.

5. 필드에 정보를 입력 한 다음 **저장** 단추를 선택 합니다.

     새 레코드가 목록에 표시 됩니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [방법: 사용자 지정 필드 형식 만들기](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [콘텐츠 형식](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [열](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
