---
title: ClickOnce 디자이너를 사용 하 여 요청 시 위성 어셈블리 다운로드
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f510ef4ad81188997e1d572e7aa3b52b65883269
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263410"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>연습: 디자이너를 사용 하 여 ClickOnce 배포 API에서 요청 시 위성 어셈블리 다운로드
위성 어셈블리를 사용하면 Windows Forms 애플리케이션을 여러 문화권에 맞게 구성할 수 있습니다. *위성 어셈블리* 는 애플리케이션의 기본 문화권 이외의 문화권을 위한 애플리케이션 리소스가 포함된 어셈블리입니다.

 [ClickOnce 응용 프로그램 지역화](../deployment/localizing-clickonce-applications.md)에서 설명한 대로 동일한 배포 내에 여러 문화권을 위한 여러 위성 어셈블리를 포함할 수 있습니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 기본적으로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 단일 클라이언트에 하나의 위성 어셈블리만 필요한 경우라도 배포의 모든 위성 어셈블리를 클라이언트 컴퓨터에 다운로드합니다.

 이 연습에서는 위성 어셈블리를 선택적 항목으로 표시하고 클라이언트 컴퓨터의 현재 문화권 설정에 필요한 어셈블리만 다운로드하는 방법을 설명합니다.

> [!NOTE]
> 테스트를 위해 다음 코드 예제에서는 프로그래밍 방식으로 문화권을 `ja-JP`로 설정합니다. 이 코드를 프로덕션 환경에 맞게 조정하는 방법에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 "다음 단계" 섹션을 참조하세요.

### <a name="to-mark-satellite-assemblies-as-optional"></a>위성 어셈블리를 선택 항목으로 표시하려면

1. 프로젝트를 빌드합니다. 이렇게 하면 지역화할 모든 문화권에 대한 위성 어셈블리가 생성됩니다.

2. 솔루션 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

3. **게시** 탭을 클릭하고 **애플리케이션 파일**을 클릭합니다.

4. **모든 파일 표시** 확인란을 선택하여 위성 어셈블리를 표시합니다. 기본적으로 모든 위성 어셈블리는 배포에 포함되고 이 대화 상자에 표시됩니다.

     위성 어셈블리의 이름은 * \<isoCode>\ApplicationName.resources.dll*형식으로 \<isoCode> 지정 됩니다. 여기서은 RFC 1766 형식의 언어 식별자입니다.

5. 각 언어 식별자에 대해 **다운로드 그룹** 목록에서 **새로 만들기**를 클릭합니다. 다운로드 그룹 이름을 요청하는 메시지가 표시되면 언어 식별자를 입력합니다. 예를 들어 일본어 위성 어셈블리의 경우 다운로드 그룹 이름을 지정 `ja-JP` 합니다.

6. **애플리케이션 파일** 대화 상자를 닫습니다.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>C\#에서 요청 시 위성 어셈블리를 다운로드하려면

1. *Program.cs* 파일을 엽니다. 솔루션 탐색기에서 이 파일을 표시하지 않으려면 프로젝트를 선택하고 **프로젝트** 메뉴에서 **모든 파일 표시**를 클릭합니다.

2. 다음 코드를 사용하여 해당하는 위성 어셈블리를 다운로드하고 애플리케이션을 시작합니다.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Visual Basic에서 요청 시 위성 어셈블리를 다운로드하려면

1. 애플리케이션에 대한 **속성** 창에서 **애플리케이션** 탭을 클릭합니다.

2. 탭 페이지 아래쪽에서 **애플리케이션 이벤트 보기**클릭합니다.

3. *Applicationevents .vb* 파일의 시작 부분에 다음 가져오기를 추가 합니다.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. `MyApplication` 클래스에 다음 코드를 추가합니다.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>다음 단계
 프로덕션 환경에서는 기본적으로 클라이언트 컴퓨터에 올바른 값이 설정되어 있으므로 <xref:System.Threading.Thread.CurrentUICulture%2A>를 특정 값으로 설정하는 줄을 코드 예제에서 제거해야 할 수 있습니다. 예를 들어 애플리케이션이 일본어 클라이언트 컴퓨터에서 실행될 경우 <xref:System.Threading.Thread.CurrentUICulture%2A> 는 기본적으로 `ja-JP` 입니다. 애플리케이션을 배포하기 전에 이 값을 프로그래밍 방식으로 설정하면 위성 어셈블리를 쉽게 테스트할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [연습: ClickOnce 배포 API를 사용 하 여 요청 시 위성 어셈블리 다운로드](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [ClickOnce 애플리케이션 지역화](../deployment/localizing-clickonce-applications.md)
