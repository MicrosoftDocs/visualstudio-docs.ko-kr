---
title: 필수플랫폼버전 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701490"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>필수 플랫폼버전 요소(비주얼 스튜디오 템플릿)
프로젝트 템플릿이 올바르게 작동하는 데 필요한 운영 체제의 최소 버전을 지정합니다. 이 요소는 앱을 만드는 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 프로젝트 템플릿에 사용됩니다.

 이 `RequiredPlatformVersion` 값은 운영 체제 버전과 직접 비교됩니다. 운영 체제 버전보다 높으면 새 프로젝트 대화 상자에 템플릿이 나타나지 않습니다. **New Project** `RequiredPlatformVersion` 에 대한 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 템플릿을 지정하려면 `RequiredPlatformVersion` 6.2.0으로 설정합니다. 에 대한 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 템플릿을 지정하려면 `RequiredPlatformVersion` 6.3.0으로 설정합니다.

 =8을 `RequiredPlatformVersion`지정하는 템플릿은 이전 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 고객 템플릿과 호환됩니다.

 VS 템플릿 템플릿 데이터 ..... 대상 플랫폼 이름 필수 플랫폼버전

## <a name="syntax"></a>구문

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 없음

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[템플릿플랫폼 이름](../extensibility/templatedata-element-visual-studio-templates.md)|프로젝트 템플릿의 대상 플랫폼을 지정합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

## <a name="remarks"></a>설명
 이 텍스트는 템플릿에 필요한 최소 운영 체제 버전을 지정합니다.

## <a name="example"></a>예제
 이 예제에서는 프로젝트 템플릿이 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 이상을 대상으로 하도록 지정합니다.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조
- [대상 플랫폼 이름 요소(비주얼 스튜디오 템플릿)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
