---
title: 기본 이름 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712314"
---
# <a name="defaultname-element-visual-studio-templates"></a>기본 이름 요소(비주얼 스튜디오 템플릿)
Visual Studio 프로젝트 시스템이 프로젝트 또는 항목을 만들 때 생성할 이름을 지정합니다.

 \<VS템플릿 \<> 기본 \<이름>> 템플릿데이터 데이터

## <a name="syntax"></a>구문

```
<DefaultName>
    Default Project Name
</DefaultName>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 이 텍스트는 프로젝트 또는 항목의 기본 이름을 지정합니다.

## <a name="remarks"></a>설명
 `DefaultName`는 선택적 요소입니다.

 프로젝트의 경우 이 요소는 디스크에 프로젝트를 저장하는 디렉터리 이름을 지정합니다. 항목의 경우 원본 파일의 파일 이름을 지정합니다.

 프로젝트 또는 항목을 만들 때 **새 프로젝트** 대화 상자 또는 **새 항목 추가** 대화 상자에서 사용할 수 있는 **이름** 옵션을 사용하여 기본 이름을 수정할 수 있습니다.

 프로젝트 시스템에서 프로젝트 또는 항목에 대한 기본 이름을 생성하지 않으려면 [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) 요소를 `False`로 설정합니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 클래스에 대 한 표준 항목 템플릿에 대 한 메타 데이터를 보여 줍니다.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
