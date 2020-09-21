---
title: 디자이너를 사용 하 여 요청 시 어셈블리 다운로드 (ClickOnce API)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4451f5f4075d512c76119faceb02d2a92fff120c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809265"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>연습: 디자이너를 사용 하 여 ClickOnce 배포 API에서 요청 시 어셈블리 다운로드
기본적으로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션에 포함된 모든 어셈블리는 애플리케이션을 처음 실행할 때 다운로드됩니다. 그러나 소수의 사용자가 사용하는 애플리케이션의 일부가 있을 수 있습니다. 이 경우 해당 형식 중 하나를 만들 때에만 어셈블리를 다운로드하고자 할 수 있습니다. 다음 연습에서는 애플리케이션의 특정 어셈블리를 "선택 사항"으로 표시하는 방법 및 공용 언어 런타임에서 요청할 때 <xref:System.Deployment.Application> 네임스페이스에 있는 클래스를 사용하여 이를 다운로드하는 방법을 설명합니다.

> [!NOTE]
> 이 절차를 사용하려면 완전 신뢰 상태에서 애플리케이션을 실행해야 합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 클릭합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="create-the-projects"></a>프로젝트 만들기

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Visual Studio와 함께 요청 시 어셈블리를 사용하는 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 새 Windows Forms 프로젝트를 만듭니다. **파일** 메뉴에서 **추가**를 가리키고 **새 프로젝트**를 클릭합니다. 대화 상자에서 **클래스 라이브러리** 프로젝트를 선택하고 이름을 `ClickOnceLibrary`로 지정합니다.

   > [!NOTE]
   > Visual Basic에서 이 프로젝트의 루트 네임스페이스를 `Microsoft.Samples.ClickOnceOnDemand` 로 변경하거나 선택한 네임스페이스로 변경하려면 프로젝트 속성을 수정하는 것이 좋습니다. 편의상 이 연습의 두 프로젝트는 네임스페이스가 동일합니다.

2. `DynamicClass` 라는 이름의 단일 속성으로 `Message`라는 이름의 클래스를 정의합니다.

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

3. **솔루션 탐색기**에서 Windows Forms 프로젝트를 선택합니다. <xref:System.Deployment.Application> 어셈블리에 참조를 추가하고 `ClickOnceLibrary` 프로젝트에 프로젝트 참조를 추가합니다.

   > [!NOTE]
   > Visual Basic에서 이 프로젝트의 루트 네임스페이스를 `Microsoft.Samples.ClickOnceOnDemand` 로 변경하거나 선택한 네임스페이스로 변경하려면 프로젝트 속성을 수정하는 것이 좋습니다. 편의상 이 연습의 두 프로젝트는 동일한 네임스페이스에 있습니다.

4. 폼을 마우스 오른쪽 단추로 클릭하고 메뉴에서 **코드 보기** 를 클릭한 후 폼에 다음 참조를 추가합니다.

    [!code-csharp[ClickOnceOnDemand#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.cs)]
    [!code-vb[ClickOnceOnDemand#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

5. 요청 시 이 어셈블리를 다운로드하려면 다음 코드를 추가합니다. 이 코드에서는 제네릭 <xref:System.Collections.DictionaryBase.Dictionary%2A> 클래스를 사용하여 어셈블리 집합을 그룹 이름에 매핑하는 방법을 보여 줍니다. 이 연습에서는 단일 어셈블리만 다운로드하므로 그룹에 어셈블리가 하나뿐입니다. 실제 애플리케이션에서는 애플리케이션의 단일 기능과 관련된 모든 어셈블리를 동시에 다운로드할 수도 있습니다. 매핑 테이블을 사용하면 한 기능에 속한 모든 DLL을 다운로드 그룹 이름과 연결하여 이 작업을 손쉽게 수행할 수 있습니다.

    [!code-csharp[ClickOnceOnDemand#2](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.cs)]
    [!code-vb[ClickOnceOnDemand#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

6. **보기** 메뉴에서 **도구 상자**를 클릭합니다. <xref:System.Windows.Forms.Button> 도구 상자 **에서 폼으로** 을 끌어옵니다. 단추를 두 번 클릭하고 다음 코드를 <xref:System.Windows.Forms.Control.Click> 이벤트 처리기에 추가합니다.

    [!code-csharp[ClickOnceOnDemand#3](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.cs)]
    [!code-vb[ClickOnceOnDemand#3](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.vb)]

## <a name="mark-assemblies-as-optional"></a>어셈블리를 선택 사항으로 표시

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Visual Studio를 사용하여 ClickOnce 애플리케이션에서 어셈블리를 선택 사항으로 표시하려면

1. **솔루션 탐색기** 에서 Windows Forms 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다. **게시** 탭을 선택합니다.

2. **애플리케이션 파일** 단추를 클릭합니다.

3. *ClickOnceLibrary.dll*에 대한 목록을 찾습니다. **게시 상태** 드롭다운 상자를 **포함**으로 설정합니다.

4. **그룹** 드롭다운 상자를 확장하고 **새로 만들기**를 선택합니다. `ClickOnceLibrary` 라는 이름을 새 그룹 이름으로 입력합니다.

5. [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)에 설명 된 대로 응용 프로그램을 계속 게시 합니다.

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>매니페스트 생성 및 편집 도구 — 그래픽 클라이언트(MageUI.exe)를 사용하여 ClickOnce 애플리케이션에서 어셈블리를 선택 사항으로 표시하려면

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)에 설명 된 대로 매니페스트를 만듭니다.

2. MageUI.exe를 닫기 전에 배포의 애플리케이션 매니페스트를 포함하는 탭을 선택하고 해당 탭에서 **파일** 탭을 선택합니다.

3. 애플리케이션 파일의 목록에서 ClickOnceLibrary.dll을 찾고 **파일 형식** 열을 **없음**으로 설정합니다. **그룹** 열에 `ClickOnceLibrary.dll`을 입력합니다.

## <a name="test-the-new-assembly"></a>새 어셈블리 테스트

요청 시 어셈블리를 테스트하려면

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]로 배포된 애플리케이션을 시작합니다.

2. 기본 폼이 나타나면 <xref:System.Windows.Forms.Button>을 누릅니다. 메시지 상자 창에 "Hello, World!"라는 문자열이 표시됩니다.

## <a name="see-also"></a>참조

- <xref:System.Deployment.Application.ApplicationDeployment>
