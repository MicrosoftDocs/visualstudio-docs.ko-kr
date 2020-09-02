---
title: ClickOnce 배포 API를 사용 하 여 요청 시 위성 어셈블리 다운로드
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34cde3a2444525e48455e445894fd5ab1c66fab8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66262963"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>연습: ClickOnce 배포 API를 사용 하 여 요청 시 위성 어셈블리 다운로드
위성 어셈블리를 사용하면 Windows Forms 애플리케이션을 여러 문화권에 맞게 구성할 수 있습니다. *위성 어셈블리* 는 애플리케이션의 기본 문화권 이외의 문화권을 위한 애플리케이션 리소스가 포함된 어셈블리입니다.

 [ClickOnce 응용 프로그램 지역화](../deployment/localizing-clickonce-applications.md)에서 설명한 대로 동일한 배포 내에 여러 문화권을 위한 여러 위성 어셈블리를 포함할 수 있습니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 기본적으로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 단일 클라이언트에 하나의 위성 어셈블리만 필요한 경우라도 배포의 모든 위성 어셈블리를 클라이언트 컴퓨터에 다운로드합니다.

 이 연습에서는 위성 어셈블리를 선택적 항목으로 표시하고 클라이언트 컴퓨터의 현재 문화권 설정에 필요한 어셈블리만 다운로드하는 방법을 설명합니다. 다음 절차에서는 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]에서 사용할 수 있는 도구를 사용합니다. 또한 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서도 이 작업을 수행할 수 있습니다.  또한 [연습: 디자이너를 사용 하 여 clickonce 배포 api를 사용 하 여 요청 시 위성 어셈블리 다운로드](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) 또는 [연습: 디자이너를 사용 하 여 clickonce 배포 api에서 요청 시 위성 어셈블리 다운로드](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120))를 참조 하세요.

> [!NOTE]
> 테스트를 위해 다음 코드 예제에서는 프로그래밍 방식으로 문화권을 `ja-JP`로 설정합니다. 이 코드를 프로덕션 환경에 맞게 조정하는 방법에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 "다음 단계" 섹션을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 항목에서는 사용자가 Visual Studio를 사용하여 애플리케이션에 지역화된 리소스를 추가하는 방법을 알고 있다고 가정합니다. 자세한 내용은 [연습: Windows Forms 지역화](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))를 참조 하세요.

### <a name="to-download-satellite-assemblies-on-demand"></a>요청 시 위성 어셈블리를 다운로드하려면

1. 요청 시 위성 어셈블리 다운로드 기능을 사용하려면 애플리케이션에 다음 코드를 추가합니다.

    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]

2. [Resgen.exe (리소스 파일 생성기)](/dotnet/framework/tools/resgen-exe-resource-file-generator) 또는을 사용 하 여 응용 프로그램에 대 한 위성 어셈블리를 생성 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다.

3. 애플리케이션 매니페스트를 생성하거나 *MageUI.exe*를 사용하여 기존 애플리케이션 매니페스트를 엽니다. 이 도구에 대 한 자세한 내용은 참조 하세요. [MageUI.exe (매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)합니다.

4. **파일** 탭을 클릭합니다.

5. **줄임표** 단추(**...**)를 클릭하고 *Resgen.exe*를 사용하여 생성한 위성 어셈블리를 비롯한 애플리케이션의 모든 어셈블리와 파일이 포함된 디렉터리를 선택합니다. 위성 어셈블리의 이름은 * \<isoCode>\ApplicationName.resources.dll*형식으로 \<isoCode> 지정 됩니다. 여기서은 RFC 1766 형식의 언어 식별자입니다.

6. **채우기** 를 클릭하여 배포에 파일을 추가합니다.

7. 각 위성 어셈블리의 **옵션** 확인란을 선택합니다.

8. 각 위성 어셈블리의 그룹 필드를 해당 ISO 언어 식별자로 설정합니다. 예를 들어 일본어 위성 어셈블리의 경우 `ja-JP`에서 사용할 수 있는 도구를 사용합니다. 이렇게 하면 1단계에서 추가한 코드를 사용하여 사용자의 <xref:System.Threading.Thread.CurrentUICulture%2A> 속성 설정에 따라 적절한 위성 어셈블리를 다운로드할 수 있습니다.

## <a name="next-steps"></a>다음 단계
 프로덕션 환경에서는 기본적으로 클라이언트 컴퓨터에 올바른 값이 설정되어 있으므로 <xref:System.Threading.Thread.CurrentUICulture%2A> 를 특정 값으로 설정하는 줄을 코드 예제에서 제거해야 할 수 있습니다. 예를 들어 애플리케이션이 일본어 클라이언트 컴퓨터에서 실행될 경우 <xref:System.Threading.Thread.CurrentUICulture%2A> 는 기본적으로 `ja-JP` 입니다. 애플리케이션을 배포하기 전에 이 값을 프로그래밍 방식으로 설정하면 위성 어셈블리를 쉽게 테스트할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 지역화](../deployment/localizing-clickonce-applications.md)
