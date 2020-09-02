---
title: Templates Groupid 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699073"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 요소(Visual Studio 템플릿)
항목 템플릿이 표시되는 프로젝트 종류를 지정합니다. 이 요소는 [Showbydefault (Visual Studio 템플릿)](../extensibility/showbydefault-visual-studio-templates.md) 가로 설정 된 경우에 중요 `false` 합니다. [Showbydefault (Visual Studio 템플릿)](../extensibility/showbydefault-visual-studio-templates.md) 가로 설정 된 경우 `true` 모든 프로젝트 형식에서 항목 템플릿을 사용할 수 있습니다.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>구문

```
<TemplateGroupID> ... </TemplateGroupID>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트는 항목 템플릿 범주에 대한 식별자를 지정합니다.

## <a name="remarks"></a>설명
 `TemplateGroupID`는 요소입니다.

 요소 값은 `TemplateGroupID` 프로젝트 시스템 등록 (HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio \\ *\<version number>* \projects)과 함께 \\ **새 항목 추가** 대화 상자에 표시 되는 템플릿을 필터링 하는 데 사용 됩니다.

|Visual C++ 값|의미|
|------------------------|-------------|
|VC-Native|네이티브 프로젝트에 사용됩니다. 프로젝트 형식을 확인할 수 없는 경우에는 기본값입니다.|
|VC-Managed|관리되는(/clr) 프로젝트에 사용됩니다.|
|VC-Windows|Windows 플랫폼(네이티브/관리/저장소)을 대상으로 하는 모든 프로젝트에 사용됩니다.|
|WinRT-Native-UAP|Windows 10 스토어 프로젝트에 사용됩니다.|
|CodeSharing-Native|공유 항목 프로젝트에 사용됩니다.|
|WinRT-Native-6.3|Windows 8.1 스토어 프로젝트에 사용됩니다.|
|WinRT-Native-Phone-6.3|Windows Phone 8.1 프로젝트에 사용됩니다.|
|WinRT-Native|Windows 8.0 스토어 프로젝트에 사용됩니다.|
|VC-Android|Android 프로젝트에 사용됩니다.|

## <a name="see-also"></a>추가 정보
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
