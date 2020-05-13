---
title: CodeLens에서 코드 변경 내용 및 기타 기록 찾기
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9859366f6e4b9a0d1c219adc2080e6415b1e44a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588657"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>CodeLens에서 코드 변경 내용 및 기타 기록 찾기

CodeLens를 통해 코드에 대한 정보를 찾는 동안 편집기에서 나가지 않고&ndash;계속 작업에 집중할 수 있습니다. 코드 조각 참조, 코드 변경 내용, 연결된 버그, 작업 항목, 코드 검토 및 단위 테스트를 확인할 수 있습니다.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens는 Visual Studio Community Edition에서 사용할 수 있지만 *소스 제어*는 이 버전에서 사용할 수 없습니다.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens는 Visual Studio Enterprise 및 Professional 버전에서만 사용할 수 있습니다. Visual Studio Community 버전에서는 사용할 수 없습니다.

::: moniker-end

솔루션에서 코드의 개별 부분을 사용하는 위치 및 방법 확인:

![코드 편집기의 CodeLens 표시기](../ide/media/codelens-overview.png)

편집기를 종료하지 않고 코드 변경에 대해 팀에 문의:

![CodeLens - 팀에 문의](../ide/media/codelens-contact-info.png)

확인하려는 지표를 선택하거나 CodeLens를 설정 또는 해제하려면 **도구** > **옵션** > **텍스트 편집기** > **모든 언어** > **CodeLens**로 이동합니다.

## <a name="find-references-to-your-code"></a>코드에 대한 참조 찾기

C# 또는 Visual Basic 코드에 대한 참조를 찾을 수 있습니다.

1. **참조** 표시기를 선택하거나 **Alt**+**2**를 누릅니다.

   ![CodeLens 참조](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > 표시기에 **0 참조**가 표시된 경우 C# 또는 Visual Basic 코드의 참조가 없습니다. 하지만 *.xaml* 및 *.aspx* 파일 등 다른 항목의 참조가 있을 수 있습니다.

2. 참조 코드를 보려면 목록에서 참조 위에 마우스를 놓습니다.

   ![CodeLens - 참조 피킹](../ide/media/codelens-peek-reference.png)

3. 참조가 포함된 파일을 열려면 참조를 두 번 클릭합니다.

### <a name="code-maps"></a>코드 맵

이 코드와 해당 참조 간의 관계를 확인하려면 [코드 맵을 만듭니다](../modeling/map-dependencies-across-your-solutions.md). 코드 맵 바로 가기 메뉴에서 선택 **모든 참조 표시**를 선택합니다.

![CodeLens - 코드 맵의 참조](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>코드에서 변경 내용 찾기

코드 기록을 검사하여 코드에 수행된 작업을 확인합니다. 또는 다른 분기의 변경 내용이 코드에 어떤 영향을 미칠 수 있는지 잘 파악할 수 있도록 변경 내용을 코드에 병합하기 전에 검토합니다.

다음이 필요합니다.

- Visual Studio Enterprise 또는 Professional Edition

- Azure DevOps Services, Team Foundation Server 2013 이상 또는 Git

- 코드 편집기에서 팀에 연락하려는 경우 [비즈니스용 Skype](/skypeforbusiness/)

TFVC(Team Foundation 버전 제어) 또는 Git으로 저장된 C# 또는 Visual Basic 코드의 경우 클래스 및 메서드 수준에서 CodeLens 세부 정보를 가져옵니다(*코드 요소 수준* 표시기). Git 리포지토리가 TfGit에서 호스트되는 경우 TFS 작업 항목에 대한 링크도 가져올 수 있습니다.

![코드 요소 수준 표시기](../ide/media/codelens-element-level-indicators.png)

*.cs* 또는 *.vb* 이외 파일 형식의 경우, 창 맨 아래의 한 지점에서 전체 파일에 대한 CodeLens 세부 정보를 가져옵니다(*파일 수준* 표시기).

![파일 수준 CodeLens 표시기](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>코드 요소 수준 표시기

코드 요소 수준 표시기를 통해 코드를 변경한 사람 및 변경된 내용을 확인할 수 있습니다. 코드 요소 수준 표시기는 C# 및 Visual Basic 코드에 대해 제공됩니다.

Team Foundation Server 또는 Azure DevOps Services에서 TFVC(Team Foundation 버전 제어)를 사용하는 경우에 표시됩니다.

![CodeLens: TFVC에서 코드에 대한 변경 기록 가져오기](../ide/media/codelens-code-changes.png)

기본 기간은 지난 12 개월입니다. 코드가 Team Foundation Server에 저장되는 경우 [TFSConfig 명령](/azure/devops/server/command-line/tfsconfig-cmd)을 [CodeIndex 명령](../ide/codeindex-command.md) 및 **/indexHistoryPeriod** 플래그와 함께 실행하여 기간을 변경할 수 있습니다.

1년 이상 전의 변경 내용을 포함하여 모든 변경 내용에 대한 자세한 기록을 보려면 **모든 파일 변경 내용 표시**를 선택합니다.

![모든 코드 변경 내용 표시](../ide/media/codelens-show-all-file-changes.png)

**기록** 창이 열립니다.

![모든 코드 변경 내용에 대한 기록 창](../ide/media/codelenscodechangeshistory.png)

파일이 Git 리포지토리에 있고 코드 요소 수준 변경 표시기를 선택하면 다음이 표시됩니다.

![CodeLens: Git에서 코드에 대한 변경 기록 가져오기](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>파일 수준 표시기

창 맨 아래의 파일 수준 표시기에서 전체 파일에 대한 변경 내용을 찾습니다.

![CodeLens: 코드 파일 세부 정보 가져오기](../ide/media/codelens-file-level.png)

> [!NOTE]
> 파일 수준 표시기는 C# 및 Visual Basic 코드에는 제공되지 않습니다.

변경 내용에 대한 자세한 정보를 얻으려면 해당 항목을 마우스 오른쪽 단추로 클릭합니다. TFVC 또는 Git을 사용하는지에 따라 파일의 버전을 비교하고 세부 정보를 보고 변경 집합을 추적하고 선택한 버전의 파일을 가져오고 해당 변경 내용을 만든 이에게 메일을 보낼 수 있는 옵션을 사용할 수 있습니다. 이러한 세부 정보 중 일부는 **팀 탐색기**에 표시됩니다.

시간별로 코드를 변경한 사용자를 확인할 수도 있습니다. 이는 팀의 변경 내용에서 패턴을 찾고 해당 영향을 평가하는 데 도움이 될 수 있습니다.

![CodeLens: 코드 변경 내용 기록을 그래프로 보기](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>현재 분기에서 변경 내용 찾기

안정적인 코드가 손상되는 위험을 줄이기 위해 팀에 여러 분기(Main 분기 및 자식 개발 분기)가 있을 수 있습니다.

![CodeLens: 코드가 분기된 시점 찾기](../ide/media/codelensfirstbranchconceptual.png)

**Alt**+**6**을 눌러 Main 분기에서 코드를 변경한 사용자의 수 및 변경된 내용의 수를 찾을 수 있습니다.

![CodeLens: 분기에서 변경 내용 횟수 찾기](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>코드가 분기된 시점 찾기

코드가 분기된 시점을 찾으려면 자식 분기의 코드로 이동합니다. 그런 다음, **변경** 표시기를 선택하거나 **Alt**+**6**을 누릅니다.

![CodeLens: 코드가 분기된 시점 찾기](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>다른 분기에서 들어오는 변경 내용 찾기

![CodeLens: 다른 분기에서 코드 변경 내용 찾기](../ide/media/codelensbranchchangecheckinconceptual.png)

들어오는 변경 내용을 볼 수 있습니다. 다음 스크린샷에 버그 수정은 “Dev” 분기에서 이루어졌습니다.

![CodeLens: 다른 분기로 체크인된 변경 내용](../ide/media/codelens-branch-changes-dev.png)

다음과 같이 현재 분기(“Main”)를 벗어나지 않고 변경 내용을 검토할 수 있습니다.

![CodeLens: 다른 분기에서 들어온 변경 내용 확인](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>변경 내용이 병합된 경우 찾기

변경 내용이 병합된 시기를 확인할 수 있으므로 분기에 어떤 변경 내용이 포함되는지 확인할 수 있습니다.

![CodeLens - 분기 사이에서 병합된 변경 내용](../ide/media/codelensbranchmergedconceptual.png)

예를 들어 지금 Main 분기의 코드에는 “Dev” 분기의 버그 수정이 반영되어 있습니다.

![CodeLens - 분기 사이에서 병합된 변경 내용](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>들어오는 변경 내용을 로컬 버전과 비교

**Shift**+**F10**을 누르거나 변경 집합을 두 번 클릭하여 들어오는 변경 내용을 로컬 버전과 비교합니다.

![CodeLens: 로컬과 들어오는 변경 내용 비교](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>분기 아이콘

**분기** 열에 있는 아이콘은 분기가 작업 중인 분기와 어떻게 관련되어 있는지를 보여 줍니다.

|**아이콘**|**변경이 발생한 위치:**|
|--------------| - |
|![CodeLens: 현재 분기에서 변경 아이콘](../ide/media/codelensbranchcurrenticon.png)|현재 분기|
|![CodeLens: 부모 분기에서 변경 아이콘](../ide/media/codelensbranchparenticon.png)|부모 분기|
|![CodeLens: 자식 분기에서 변경 아이콘](../ide/media/codelensbranchchildicon.png)|자식 분기|
|![CodeLens: 피어 분기에서 변경 아이콘](../ide/media/codelensbranchpeericon.png)|피어 분기|
|![CodeLens: 먼 분기에서 변경 아이콘](../ide/media/codelensbranchfurtherawayicon.png)|부모, 자식 또는 피어보다 더 먼 분기|
|![CodeLens: 부모에서 병합 아이콘](../ide/media/codelensbranchmergefromparenticon.png)|부모 분기에서 자식 분기로 병합|
|![CodeLens: 자식 분기에서 병합 아이콘](../ide/media/codelensbranchmergefromchildicon.png)|자식 분기에서 부모 분기로 병합|
|![CodeLens: 관련 없는 분기에서 병합 아이콘](../ide/media/codelensbranchmergefromunrelatedicon.png)|관련 없는 분기에서 병합(기본 파일이 없는 병합)|

## <a name="linked-work-items"></a>연결된 작업 항목

**작업 항목** 표시기를 선택하거나 **Alt**+**8**을 눌러 연결된 작업 항목을 찾습니다.

![CodeLens - 특정 코드에 대한 작업 항목 찾기](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>연결된 코드 검토

**검토** 표시기를 선택하여 연결된 코드 검토를 찾습니다. 키보드를 사용하려면 **Alt** 키를 누른 상태에서 **왼쪽 화살표** 또는 **오른쪽 화살표**를 눌러 표시기 옵션을 탐색합니다.

![CodeLens - 코드 검토 요청 보기](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>연결된 버그

**버그** 표시기를 선택하거나 **Alt**+**7**을 눌러 연결된 버그를 찾습니다.

![CodeLens - 변경 집합에 연결된 버그 찾기](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>항목 소유자에게 문의

**만든 이** 표시기를 선택하거나 **Alt**+**5**를 눌러 항목의 만든 이를 찾습니다.

![항목 소유자에게 문의](../ide/media/codelens-contact-item-owner.png)

연락처 옵션을 보려면 항목에 대한 바로 가기 메뉴를 엽니다. Lync 또는 비즈니스용 Skype를 설치한 경우 이러한 옵션이 표시됩니다.

![항목에 대한 연락처 옵션](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>연결된 단위 테스트

**테스트 탐색기**를 열지 않고 C# 또는 Visual Basic 코드에 대한 단위 테스트를 확인할 수 있습니다.

1. 연결된 [단위 테스트 코드](../test/unit-test-your-code.md)가 있는 애플리케이션 코드로 이동합니다.

2. 아직 수행하지 않은 경우 CodeLens 테스트 지표를 로드하도록 애플리케이션을 빌드합니다. 

3. **Alt**+**3**을 눌러 코드에 대한 테스트를 검토합니다.

     ![CodeLens - 코드 편집기에서 테스트 상태 선택](../ide/media/codelens-choose-test-indicator.png)

4. 경고 아이콘 ![경고 아이콘](../ide/media/codelenstestwarningicon.png)테스트가 아직 실행되지 않았으므로 실행합니다.

     ![CodeLens - 아직 실행하지 않은 단위 테스트 보기](../ide/media/codelens-tests-not-yet-run.png)

5. 테스트의 정의를 검토하려면 CodeLens 표시기 창에서 테스트 항목을 두 번 클릭하여 편집기에서 코드 파일을 엽니다.

     ![CodeLens - 단위 테스트 정의로 이동](../ide/media/codelens-unit-test-definition.png)

6. 테스트 결과를 검토하려면 테스트 상태 표시기(![테스트 실패 아이콘](../ide/media/codelenstestfailedicon.png) 또는 ![테스트 성공 아이콘](../ide/media/codelenstestpassedicon.png))를 선택하거나 **Alt**+**1**을 누릅니다.

     ![CodeLens - 단위 테스트 결과 표시](../ide/media/codelens-unit-test-result.png)

7. 이 테스트를 변경한 사용자와 그 수 또는 이 테스트에 대해 수행된 변경 작업 수를 확인하려면 [코드 기록 및 연결된 항목을 찾아보세요](#find-changes-in-your-code).

## <a name="keyboard-shortcuts"></a>바로 가기 키

키보드를 사용하여 표시기를 선택하려면 **Alt** 키를 길게 눌러 관련 숫자 키를 표시한 다음, 선택하려는 표시기에 해당하는 숫자를 누릅니다.

![키보드 액세스 번호](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> **검토** 표시기를 선택하려면 **Alt**를 누른 상태에서 왼쪽 및 오른쪽 화살표 키를 사용하여 탐색합니다.

## <a name="q--a"></a>Q&A

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Q: CodeLens를 끄거나 켜고 확인할 표시기를 선택하려면 어떻게 할까요?

**A:**  참조 지표를 제외하고 지표를 설정하거나 해제할 수 있습니다. **도구** > **옵션** > **텍스트 편집기** > **모든 언어** > **CodeLens**로 이동합니다.

지표가 설정되어 있으면 해당 지표에서 CodeLens 옵션을 열 수도 있습니다.

![CodeLens - 표시기 설정 또는 해제](../ide/media/codelensturnoffonindicatorsfromcode.png)

편집기 창의 맨 아래에 있는 펼침 단추 아이콘을 사용하여 CodeLens 파일 수준 표시기를 켜거나 끕니다.

![파일 수준 표시기 설정 및 해제](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>Q: CodeLens는 어디에 있나요?

**A:** CodeLens는 메서드, 클래스, 인덱서 및 속성 수준에서 C# 및 Visual Basic 코드에 표시됩니다. CodeLens는 기타 모든 형식의 파일에 대해 파일 수준에서 표시됩니다.

- CodeLens가 설정되어 있는지 확인합니다. **도구** > **옵션** > **텍스트 편집기** > **모든 언어** > **CodeLens**로 이동합니다.

- 코드가 TFS에 저장되는 경우 [CodeIndex 명령](../ide/codeindex-command.md) 과 [TFS 구성 명령](/azure/devops/server/command-line/tfsconfig-cmd)을 함께 사용하여 코드 인덱싱이 설정되어 있는지 확인합니다.

- DevOps 관련 지표는 작업 항목이 코드와 링크되어 있는 경우 및 링크된 작업 항목을 열 권한이 있는 경우에만 나타납니다. [팀 멤버 권한](/azure/devops/organizations/security/view-permissions?view=vsts)이 있는지 확인합니다.

- 단위 테스트 지표는 애플리케이션 코드에서 단위 테스트를 하지 않은 경우 나타나지 않습니다. 테스트 상태 지표는 테스트 프로젝트에 자동으로 나타납니다. 애플리케이션 코드에 단위 테스트가 있지만 테스트 표시기가 나타나지 않는 경우 솔루션 빌드를 시도해 보세요(**Ctrl**+**Shift**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens는 Visual Studio Community Edition에서 사용할 수 있지만 *소스 제어*는 이 버전에서 사용할 수 없습니다.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens는 Visual Studio Community Edition에서 사용할 수 없습니다.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Q: 커밋에 대한 작업 항목 정보가 나타나지 않습니다.

**A:** CodeLens가 Azure Boards 또는 TFS의 작업 항목을 찾을 수 없기 때문에 이러한 현상이 발생할 수 있습니다. 작업 항목이 포함된 프로젝트에 연결되어 있으며 해당 작업 항목을 볼 수 있는 권한이 있는지 확인하세요. 커밋 설명에 Azure Boards 또는 TFS의 작업 항목 ID에 대한 잘못된 정보가 포함된 경우 작업 항목 정보가 표시되지 않을 수 있습니다.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>Q: Skype 지표가 나타나지 않습니다.

**A:** 비즈니스용 Skype에 로그인하지 않았거나, 설치하지 않았거나, 지원되는 구성이 없을 경우 Skype 지표가 나타나지 않습니다. 하지만 이메일은 보낼 수 있습니다.

![CodeLens - 변경 집합 소유자에게 메일로 문의](../ide/media/codelenscodesendmailchangesetnolync1.png)

**어떤 Skype 및 Lync 구성이 지원되나요?**

- 비즈니스용 Skype(32비트 또는 64비트)

- Lync 2010 이상 독립형(32비트 또는 64비트) 단, Windows 8.1의 Lync Basic 2013 제외

CodeLens는 다른 버전의 Lync 또는 Skype가 설치되는 것을 지원하지 않습니다. 다른 버전의 Lync 또는 Skype는 Visual Studio의 모든 지역화된 버전에 지역화되지 않을 수 있습니다.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Q: CodeLens의 글꼴과 색을 변경하려면 어떻게 해야 하나요?

**A:** **도구** > **옵션** > **환경** > **글꼴 및 색**으로 이동합니다.

![CodeLens - 글꼴 및 색상 설정 변경](../ide/media/codelensoptionsfontscolorssettings.png)

키보드를 사용하려면

1. **Alt**+**T**+**O**를 눌러 **옵션** 대화 상자를 엽니다.

2. **위쪽 화살표** 또는 **아래쪽 화살표** 를 눌러 **환경** 노드로 이동한 다음 **왼쪽 화살표** 를 눌러 노드를 확장합니다.

3. **아래쪽 화살표** 를 눌러 **글꼴 및 색**으로 이동합니다.

4. **Tab**을 눌러 **설정 표시** 목록으로 이동한 다음, **아래쪽 화살표** 를 눌러 **CodeLens**를 선택합니다.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Q: CodeLens 헤드업 표시를 이동할 수 있습니까?

**A:** 예, ![도킹 아이콘](../ide/media/codelensdockwindow.png)을 선택하여 CodeLens를 창으로 도킹합니다.

![CodeLens 표시기 창의 도킹 단추](../ide/media/codelensselectdockwindow.png)

![도킹된 CodeLens 참조 창](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Q: 지표를 새로 고치려면 어떻게 합니까?

**A:** 지표에 따라 다릅니다.

- **참조**: 이 지표는 코드가 변경될 때 자동으로 업데이트됩니다. **참조** 표시기가 별도의 창으로 도킹된 경우 **새로 고침**을 선택하여 표시기를 새로 고칩니다.

   ![CodeLens 참조의 [새로 고침] 단추](../ide/media/codelensviewreferencesdocked.png)

- **팀**: 오른쪽 클릭 메뉴에서 **CodeLens 팀 지표 새로 고침**을 선택하여 이러한 지표를 새로 고칩니다.

   ![CodeLens 팀 지표 새로 고침 메뉴 항목](../ide/media/codelensrefreshindicatorsfromcode.png)

- **테스트**: [코드에 대한 단위 테스트를 찾아](#associated-unit-tests)**테스트** 지표를 새로 고칩니다.

### <a name="q-whats-local-version"></a>Q: "로컬 버전"이란 무엇인가요?

**A:** **로컬 버전** 화살표는 파일의 로컬 버전에 있는 최신 변경 집합을 가리킵니다. 서버에 최신 변경 집합이 있는 경우, 변경 집합을 정렬하는 순서에 따라 **로컬 버전** 화살표의 위 또는 아래에 나타납니다.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Q: CodeLens가 코드를 처리하여 기록 및 연결된 항목을 표시하는 방법을 관리할 수 있나요?

**A:** 예. 코드가 TFS에 있는 경우 [CodeIndex 명령](../ide/codeindex-command.md)과 [TFS 구성 명령](/azure/devops/server/command-line/tfsconfig-cmd)을 함께 사용합니다.

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>Q: 내 CodeLens 테스트 지표는 더 이상 솔루션을 처음 열 때 내 파일에 나타나지 않습니다. 로드하려면 어떻게 하나요?

**A:** CodeLens 테스트 지표를 가져오는 프로젝트를 다시 빌드하여 파일에서 로드합니다. 성능을 향상시키기 위해 코드 파일을 로드하는 경우 Visual Studio는 테스트 지표에 대한 원본 정보를 더 이상 페치하지 않습니다. 빌드 후에 또는 **테스트 탐색기**를 두 번 클릭하여 테스트로 이동할 때 테스트 지표가 로드됩니다.

## <a name="see-also"></a>참조

- [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md)
