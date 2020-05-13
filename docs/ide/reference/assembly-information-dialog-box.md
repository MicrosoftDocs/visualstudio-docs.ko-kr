---
title: 어셈블리 정보 대화 상자
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae70a2bf989b73dedc5becaac6f4b49bd0108730
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595789"
---
# <a name="assembly-information-dialog-box"></a>어셈블리 정보 대화 상자

어셈블리 정보 대화 상자는 프로젝트에서 자동으로 만들어진 AssemblyInfo 파일에 저장된 .NET Framework 글로벌 어셈블리 특성의 값을 지정하는 데 사용됩니다. 솔루션 탐색기에서 AssemblyInfo 파일은 Visual Basic 프로젝트의 **내 프로젝트** 노드에 있습니다(확인하려면 **모든 파일 표시** 클릭). C# 프로젝트의 경우 **속성** 아래에 있습니다. 자세한 내용은 [특성(C#)](/dotnet/csharp/programming-guide/concepts/attributes/index)을 참조하세요.

이 대화 상자에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음, **프로젝트** 메뉴에서 **속성**을 선택합니다. **애플리케이션** 페이지에서 **어셈블리 정보** 단추를 선택합니다.

## <a name="uielement-list"></a>UIElement 목록

**제목**\
어셈블리 매니페스트의 제목을 지정합니다. <xref:System.Reflection.AssemblyTitleAttribute>에 해당합니다.

**Description**\
어셈블리 매니페스트의 선택적 설명을 지정합니다. <xref:System.Reflection.AssemblyDescriptionAttribute>에 해당합니다.

**회사**\
어셈블리 매니페스트의 회사 이름을 지정합니다. <xref:System.Reflection.AssemblyCompanyAttribute>에 해당합니다.

레지스트리에서 회사의 기본값을 설정하거나 변경할 수 있습니다. Windows 버전에 따라 **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** 또는 **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** 키에서 **RegisteredOrganization** 값을 찾습니다.

**제품**\
어셈블리 매니페스트의 제품 이름을 지정합니다. <xref:System.Reflection.AssemblyProductAttribute>에 해당합니다.

**저작권**\
어셈블리 매니페스트의 저작권 표시를 지정합니다. <xref:System.Reflection.AssemblyCopyrightAttribute>에 해당합니다.

**상표**\
어셈블리 매니페스트의 상표를 지정합니다. <xref:System.Reflection.AssemblyTrademarkAttribute>에 해당합니다.

**어셈블리 버전**\
어셈블리의 버전을 지정합니다. <xref:System.Reflection.AssemblyVersionAttribute>에 해당합니다.

**파일 버전**\
Win32 파일 버전 리소스에 대해 특정 버전을 사용하도록 컴파일러에 지시하는 버전 번호를 지정합니다. <xref:System.Reflection.AssemblyFileVersionAttribute>에 해당합니다.

**GUID**\
어셈블리를 식별하는 고유 GUID입니다. 프로젝트를 만들면 Visual Studio에서 어셈블리의 GUID를 생성합니다. <xref:System.Guid>에 해당합니다.

**Neutral Language**\
어셈블리에서 지원하는 문화권을 지정합니다. <xref:System.Resources.NeutralResourcesLanguageAttribute>에 해당합니다. 기본값은 **(없음)** 입니다.

**어셈블리를 COM에 노출**\
어셈블리 내의 형식을 COM에서 사용할 수 있는지 여부를 지정합니다. <xref:System.Runtime.InteropServices.ComVisibleAttribute>에 해당합니다.

> [!NOTE]
> .NET Framework 클래스 라이브러리에서 NuGet 패키지를 생성할 때 이러한 속성을 설정하는 방법에 대한 자세한 내용은 [패키지의 프로젝트 속성 구성](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [특성](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
