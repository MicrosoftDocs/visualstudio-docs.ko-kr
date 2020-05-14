---
title: 비트맵 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740003"
---
# <a name="bitmap-element"></a>비트맵 요소
비트맵을 정의합니다. 비트맵은 리소스 또는 파일에서 로드됩니다.

## <a name="syntax"></a>구문

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다. GUID/ID 명령 식별자의 GUID입니다.<br /><br /> 비트맵에 대한 guid 특성은 VSPackage 또는 다른 명령 그룹과 연결되지 않습니다.  비트맵 정의에 고유해야 하며 다른 용도로 사용해서는 안 됩니다.|
|레스ID|GUID/ID 명령 식별자의 ID입니다. resID 또는 href 특성이 필요합니다.<br /><br /> resID 특성은 명령 테이블 병합 중에 로드할 비트맵 스트립을 결정하는 정수 리소스 ID입니다.  명령 테이블이 로드될 때 리소스 ID에서 지정한 비트맵은 동일한 모듈의 리소스에서 로드됩니다.|
|사용 목록|resID 특성이 있는 경우 필요합니다. 비트맵 스트립에서 사용 가능한 이미지를 선택합니다.|
|href|비트맵에 대한 경로입니다. resID 또는 href 특성이 필요합니다.<br /><br /> 포함 경로는 결과 바이너리에 포함된 표시된 이미지 파일에 대해 검색됩니다.  명령 테이블 병합 하는 동안 이미지가 복사 되 고 추가 리소스 조회 또는 로드가 필요 하지 않습니다.  usedList 특성이 없는 경우 스트립의 모든 이미지를 사용할 수 있습니다. **참고:**  이미지는 *.bmp,* *.png*및 *.gif를*포함하는 여러 형식 중 하나로 제공 될 수 있습니다.  이전 버전의 컴파일러는 부분 투명도에 대한 알파 정보가 있는 32비트 비트맵 이미지를 지원하지 않았습니다. 이러한 버전의 해결 방법은 *.png* 형식을 사용하는 것입니다.|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[비트맵 요소](../extensibility/bitmaps-element.md)|비트맵 요소를 그룹화합니다.|

## <a name="example"></a>예제

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
