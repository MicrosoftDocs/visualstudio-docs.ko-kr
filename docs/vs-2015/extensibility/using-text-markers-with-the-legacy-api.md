---
title: 레거시 API에서 텍스트 표식 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695471"
---
# <a name="using-text-markers-with-the-legacy-api"></a>레거시 API에서 텍스트 표식 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 마커는 텍스트 영역의 표시 및 동작에 영향을 줄 수 있는 버퍼의 부동 텍스트 범위입니다. 마커는 중단점, 책갈피, 물결선 및 읽기 전용 지역을 포함 합니다. 텍스트 표식은 기본적으로 구문 색 지정과 다릅니다. 구문 색 지정은 텍스트 영역과 연결 된 언어 구문을 빠르게 전달할 수 있는 방법입니다. 구문 색 지정은 일반적으로 Windows에서 화면을 다시 칠하는 경우 속도가 중요 한 경우에 필요 합니다. 구문 색 지정은 텍스트 색만 변경 합니다. 텍스트 표식은 다른 많은 텍스트 속성을 변경할 수 있습니다. 텍스트 표식은 "float" 하 고 특수 한 동작 및 색 지정을 적용할 수 있습니다.  
  
 텍스트 표식과 관련 된 성능 오버 헤드로 인해 텍스트 버퍼에 대 한 많은 표식을 만들지 않습니다. 각 표식은 사용자가 버퍼 콘텐츠를 편집할 때마다 업데이트 됩니다.  
  
> [!NOTE]
> 사용자는 표시 되는 표식 형식의 색을 변경할 수 있지만 셰이프 및 스타일은 변경할 수 없습니다. 자세한 내용은 [옵션 대화 상자, 환경, 글꼴 및 색](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)을 참조 하세요.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)|핵심 편집기에서 제공 하는 표준 텍스트 표식 유형을 텍스트 뷰에 추가 하는 방법에 대해 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|[방법: 오류 표식 구현](../extensibility/how-to-implement-error-markers.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]빨강 물결선 밑줄을 사용 하 여 오류를 나타내는 데 사용 되는 표식의 인스턴스를 구현 하는 방법을 설명 합니다.|  
|[방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)|텍스트 뷰에 사용자 지정 텍스트 표식 유형을 만들고 추가 하는 방법을 설명 합니다.|  
|[방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)|텍스트 표식을 추가 하는 방법에 대해 설명 합니다.|  
|[핵심 편집기 내부](../extensibility/inside-the-core-editor.md)|핵심 편집기의 기능을 설명 하 고 핵심 편집기를 사용자 지정 하는 방법에 대 한 세부 정보를 제공 합니다.|  
|[편집기 기능](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|핵심 편집기에서 사용할 수 있는 기능에 대해 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
  
## <a name="reference"></a>참조  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 편집기에 의해 미리 정의 되거나 VSPackage에서 등록 되었는지 여부에 관계 없이 특정 텍스트 표식 유형에 대 한 정보를 가져오기 위한 일관 된 메커니즘을 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 2 차원 좌표를 사용 하 여 텍스트 버퍼에서 텍스트 표식의 위치에 대 한 액세스를 제공 하 고 해당 위치를 조정 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 텍스트 표식을 관리 하는 메서드를 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]IDE 및 텍스트 마커를 조정 하는 데 사용 되는 기타 프로세스에 대 한 콜백을 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 추가 콜백을 제공 하 여 인터페이스를 통해 사용할 수 있는 기능을 확장 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 추가 콜백을 제공 하 여 인터페이스를 통해 사용할 수 있는 기능을 확장 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 표식 유형을 사용 하 여 다른 표식 유형이 동일한 색상 집합을 공유 하는지 여부를 결정할 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 핵심 편집기에서 텍스트 표식의 컨텍스트를 제공 합니다. 핵심 편집기에 있는 각 텍스트 표식 형식의 경우 IDE에서 별도의 개체를 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 문자 모양에서 끌어서 놓기 편집을 지 원하는 표식에 대해 제공 되는 처리기입니다. 문자 모양은 표식의 위치를 나타내는 아이콘입니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>텍스트 표식을 다른 vspackage에 제공 하는 서비스에서 인터페이스를 반환 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 1 차원 좌표를 사용 하 여 텍스트 버퍼에서 텍스트 표식의 위치에 대 한 액세스를 제공 하 고 해당 위치를 조정 합니다. 가능 하면이 인터페이스를 사용 하지 마십시오.
