---
title: 비주얼 스튜디오 템플릿 매니페스트 스키마 참조 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697982"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>비주얼 스튜디오 템플릿 매니페스트 스키마 참조
이 스키마는 Visual Studio 프로젝트 또는 항목 템플릿에 대해 생성된 Visual Studio 템플릿*매니페스트(.vstman)* 파일의 형식을 설명합니다. 스키마는 템플릿에 대한 위치 및 기타 관련 정보도 설명합니다.

 : 별도의 항목 및 프로젝트 템플릿 디렉터리가 있으므로 매니페스트에는 항목 및 프로젝트 템플릿이 혼합되어서는 안 됩니다.

> [!IMPORTANT]
> 이 매니페스트는 Visual Studio 2017에서 시작할 수 있습니다.

## <a name="vstemplatemanifest-element"></a>VS템플릿매니페스트 요소
 매니페스트의 루트 요소입니다.

### <a name="attributes"></a>특성

- **버전**: 템플릿 매니페스트의 버전을 나타내는 문자열입니다. 필수 사항입니다.

- **로캘**: 템플릿 매니페스트의 로캘 또는 로캘을 나타내는 문자열입니다. 로캘 값은 모든 템플릿에 적용됩니다. 각 로캘에 대해 별도의 매니페스트를 사용해야 합니다. (선택 사항)

### <a name="child-elements"></a>자식 요소

- **VS템플릿 컨테이너** 선택적.

- **VS템플릿디르** 선택적.

### <a name="parent-element"></a>부모 요소
 없음

## <a name="vstemplatecontainer"></a>VS템플릿 컨테이너
 템플릿의 컨테이너는 요소를 매니페스트합니다. 매니페스트에는 정의하는 각 템플릿에 대해 하나의 템플릿 컨테이너가 있습니다.

### <a name="attributes"></a>특성
 **VSTemplateType**: 템플릿 (또는)의`"Project"` `"Item"` `"ProjectGroup"`형식을 지정하는 문자열 값입니다. 필수

### <a name="child-elements"></a>자식 요소

- **상대적 패스온 디스크**: 디스크에 있는 템플릿 파일의 상대 경로입니다. 이 위치는 **새 프로젝트** 또는 **새 항목** 대화 상자에 표시된 템플릿 트리에서 템플릿의 배치도 정의합니다. 디렉터리 및 개별 파일로 배포된 템플릿의 경우 이 경로는 템플릿 파일이 포함된 디렉터리를 참조합니다. *.zip* 파일로 배포된 템플릿의 경우 이 경로는 *.zip* 파일의 경로여야 합니다.

- **VS템플릿헤더: 헤더를 설명하는 [템플릿데이터](../extensibility/templatedata-element-visual-studio-templates.md) 요소입니다.

### <a name="parent-element"></a>부모 요소
 **VS템플릿 매니페스트**

## <a name="vstemplatedir"></a>VS템플릿디르
 템플릿이 있는 디렉터리에 대해 설명합니다. 매니페스트에는 여러 **VSTemplateDir** 항목을 포함하여 지역화된 이름을 제공하고 디렉토리가 템플릿 범주 트리에서 모양을 제어하는 정렬 순서를 지정할 수 있습니다.

 설계로 인해 **VSTemplateDir** 항목은 로캘이 지정되지 않은 매니페스트에만 표시되어야 합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

- **상대 경로**: 템플릿의 경로입니다. 경로당 하나의 항목만 있을 수 있으므로 첫 번째 항목은 모든 매니페스트에서 승리합니다.

- **지역화된 이름**: 지역화된 이름을 지정하는 **NameDescriptionIcon** 요소입니다. (선택 사항)

- **정렬 순서**: 정렬 순서를 지정하는 문자열입니다. (선택 사항)

- **ParentFolderOverrideName**: 상위 폴더의 재정의된 이름입니다. (선택 사항) 이 요소에는 **이름을** 지정하는 문자열 값인 Name 특성이 있습니다.

### <a name="parent-element"></a>부모 요소
 **VS템플릿 매니페스트**

## <a name="namedescriptionicon"></a>이름 설명아이콘
 지역화된 템플릿의 이름과 설명을 지정합니다. 참조 **지역화이름** 위의.

### <a name="attributes"></a>특성

- **패키지**: 패키지를 지정하는 문자열 값입니다. (선택 사항)

- **ID**: ID를 지정하는 문자열 값입니다. (선택 사항)

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-element"></a>부모 요소
 **지역화된 이름**

## <a name="examples"></a>예
 다음 코드는 프로젝트 템플릿 *.vstman* 파일의 예입니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 다음 코드는 항목 템플릿 *.vstman* 파일의 예입니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
