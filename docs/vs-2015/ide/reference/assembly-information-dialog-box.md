---
title: 어셈블리 정보 대화 상자 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661020"
---
# <a name="assembly-information-dialog-box"></a>어셈블리 정보 대화 상자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**어셈블리 정보** 대화 상자는 프로젝트에서 자동으로 만들어진 AssemblyInfo 파일에 저장된 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 전역 어셈블리 특성의 값을 지정하는 데 사용됩니다. **솔루션 탐색기**에서 파일은 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 **내 프로젝트** 노드에 있고(파일을 보려면 **모든 파일 표시** 클릭). [!INCLUDE[csprcs](../../includes/csprcs-md.md)]의 **속성** 아래에 있습니다. 어셈블리 특성에 대한 자세한 내용은 [특성(C# 및 Visual Basic)](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)을 참조하세요.

 이 대화 상자에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너** 가 나타나면 **응용 프로그램** 탭을 클릭 합니다. **응용 프로그램** 페이지에서 **어셈블리 정보** 단추를 클릭 합니다.

## <a name="uielement-list"></a>UI 요소 목록
 **제목** 어셈블리 매니페스트의 제목을 지정합니다. <xref:System.Reflection.AssemblyTitleAttribute>에 해당합니다.

 **설명** 어셈블리 매니페스트의 선택적 설명을 지정합니다. <xref:System.Reflection.AssemblyDescriptionAttribute>에 해당합니다.

 **회사** 어셈블리 매니페스트의 회사 이름을 지정합니다. <xref:System.Reflection.AssemblyCompanyAttribute>에 해당합니다.

 **제품** 어셈블리 매니페스트의 제품 이름을 지정합니다. <xref:System.Reflection.AssemblyProductAttribute>에 해당합니다.

 **저작권** 어셈블리 매니페스트의 저작권 표시를 지정합니다. <xref:System.Reflection.AssemblyCopyrightAttribute>에 해당합니다.

 **상표** 어셈블리 매니페스트의 상표를 지정합니다. <xref:System.Reflection.AssemblyTrademarkAttribute>에 해당합니다.

 **어셈블리 버전** 특성 사용 어셈블리의 버전을 지정합니다. <xref:System.Reflection.AssemblyVersionAttribute>에 해당합니다.

 **파일 버전** Win32 파일 버전 리소스에 대해 특정 버전을 사용하도록 컴파일러에 지시하는 버전 번호를 지정합니다. <xref:System.Reflection.AssemblyFileVersionAttribute>에 해당합니다.

 **GUID** 어셈블리를 식별하는 고유 GUID입니다. 프로젝트를 만들면 Visual Studio에서 어셈블리의 GUID를 생성합니다. <xref:System.Guid>에 해당합니다.

 **중립 언어** 어셈블리에서 지원하는 문화권을 지정합니다. <xref:System.Resources.NeutralResourcesLanguageAttribute>에 해당합니다. 기본값은 **(없음)** 입니다.

 **어셈블리를 COM에 노출** 어셈블리 내의 형식을 COM에서 사용할 수 있는지 여부를 지정합니다. <xref:System.Runtime.InteropServices.ComVisibleAttribute>에 해당합니다.

## <a name="see-also"></a>관련 항목
 [응용 프로그램 페이지, 프로젝트 디자이너 (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md) [특성](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
