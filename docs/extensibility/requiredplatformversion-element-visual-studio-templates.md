---
title: RequiredPlatformVersion 요소(Visual Studio 템플릿)
titleSuffix: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3873a8107c60802edd07b567d65205a37dc213
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741678"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 요소 (Visual Studio 템플릿)

프로젝트 템플릿이 제대로 작동 하는 데 필요한 운영 체제의 최소 버전을 지정 합니다. 이 요소는 앱을 만드는 프로젝트 템플릿에 사용 됩니다 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

 `RequiredPlatformVersion`값은 운영 체제의 버전과 직접 비교 됩니다. `RequiredPlatformVersion`이 운영 체제 버전 보다 높으면 템플릿이 **새 프로젝트** 대화 상자에 표시 되지 않습니다. 이상에 대 한 템플릿을 지정 하려면를 [!INCLUDE[win8](../debugger/includes/win8_md.md)] `RequiredPlatformVersion` 6.2.0로 설정 합니다. 이상에 대 한 템플릿을 지정 하려면를 [!INCLUDE[win81](../debugger/includes/win81_md.md)] `RequiredPlatformVersion` 6.3.0로 설정 합니다.

 = 8을 지정 하는 템플릿은 `RequiredPlatformVersion` 이전 고객 템플릿과 호환 됩니다 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

 .Vstemplate 템플릿 데이터 .... TargetPlatformName RequiredPlatformVersion

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
|[템플릿 플랫폼 이름](../extensibility/templatedata-element-visual-studio-templates.md)|프로젝트 템플릿의 대상 플랫폼을 지정합니다.|

## <a name="text-value"></a>텍스트 값

 텍스트 값은 필수입니다.

## <a name="remarks"></a>설명

 이 텍스트는 템플릿에 필요한 최소 운영 체제 버전을 지정 합니다.

## <a name="example"></a>예

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

## <a name="see-also"></a>참고 항목

- [TargetPlatformName 요소 (Visual Studio 템플릿)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
