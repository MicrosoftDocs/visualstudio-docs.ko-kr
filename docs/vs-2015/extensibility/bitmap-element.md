---
title: Bitmap 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184739"
---
# <a name="bitmap-element"></a>Bitmap 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

비트맵을 정의 합니다. 비트맵은 리소스 또는 파일에서 로드 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.<br /><br /> 비트맵에 대 한 guid 특성은 VSPackage 또는 다른 명령 그룹과 연결 되지 않습니다.  비트맵 정의에서 고유 해야 하며 다른 용도로 사용 하면 안 됩니다.|  
|Resid로|GUID/ID 명령 식별자의 ID입니다. Resid로 또는 href 특성이 필요 합니다.<br /><br /> Resid로 특성은 명령 테이블을 병합 하는 동안 로드할 비트맵 스트립을 결정 하는 정수 리소스 ID입니다.  명령 테이블을 로드 하는 경우 리소스 ID로 지정 된 비트맵이 동일한 모듈의 리소스에서 로드 됩니다.|  
|usedList|Resid로 특성이 있는 경우 필수입니다. 비트맵 스트립에서 사용 가능한 이미지를 선택 합니다.|  
|href|비트맵의 경로입니다. Resid로 또는 href 특성이 필요 합니다.<br /><br /> 결과 이진 파일에 포함 된 지정 된 이미지 파일에 대 한 포함 경로를 검색 합니다.  명령 테이블을 병합 하는 동안 이미지가 복사 되 고 추가 리소스 조회 또는 로드가 필요 하지 않습니다.  UsedList 특성이 없으면 스트립의 모든 이미지를 사용할 수 있습니다. **참고:**  이미지는 .bmp, .png 및 .gif를 포함 하는 여러 형식 중 하나로 제공 될 수 있습니다.  이전 버전의 컴파일러에서는 부분 투명도에 대 한 알파 정보를 포함 하는 32 비트 비트맵 이미지를 지원 하지 않았습니다. 이러한 버전에 대 한 해결 방법은 .png 형식을 사용 하는 것입니다.|  
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[Bitmaps 요소](../extensibility/bitmaps-element.md)|비트맵 요소를 그룹화 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
