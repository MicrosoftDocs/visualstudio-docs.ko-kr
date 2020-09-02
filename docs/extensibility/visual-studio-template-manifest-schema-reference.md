---
title: Visual Studio 템플릿 매니페스트 스키마 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697982"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio 템플릿 매니페스트 스키마 참조
이 스키마는 Visual Studio 프로젝트 또는 항목 템플릿에 대해 생성 되는 Visual Studio 템플릿 매니페스트 (*vstman*) 파일의 형식을 설명 합니다. 또한이 스키마는 템플릿에 대 한 위치 및 기타 관련 정보를 설명 합니다.

 : 별도의 항목 및 프로젝트 템플릿 디렉터리가 있으므로 매니페스트에 항목 템플릿과 프로젝트 템플릿이 혼합 되지 않아야 합니다.

> [!IMPORTANT]
> 이 매니페스트는 Visual Studio 2017부터 사용할 수 있습니다.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest 요소
 매니페스트의 루트 요소입니다.

### <a name="attributes"></a>특성

- **Version**: 템플릿 매니페스트의 버전을 나타내는 문자열입니다. 필수 요소.

- **Locale**: 템플릿 매니페스트의 로캘 또는 로캘을 나타내는 문자열입니다. 로캘 값은 모든 템플릿에 적용 됩니다. 각 로캘에 대해 별도의 매니페스트를 사용 해야 합니다. 선택 사항입니다.

### <a name="child-elements"></a>자식 요소

- **VSTemplateContainer** 필드.

- **VSTemplateDir** 필드.

### <a name="parent-element"></a>부모 요소
 없음

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 템플릿 매니페스트 요소의 컨테이너입니다. 매니페스트에는 정의 하는 각 템플릿에 대 한 템플릿 컨테이너가 하나 있습니다.

### <a name="attributes"></a>특성
 **VSTemplateType**: 템플릿 형식 ( `"Project"` , `"Item"` 또는)을 지정 하는 문자열 값입니다 `"ProjectGroup"` . 필수

### <a name="child-elements"></a>자식 요소

- **RelativePathOnDisk**: 디스크에 있는 템플릿 파일의 상대 경로입니다. 또한이 위치는 **새 프로젝트** 또는 **새 항목** 대화 상자에 표시 된 템플릿 트리에서 템플릿의 배치를 정의 합니다. 디렉터리와 개별 파일로 배포 된 템플릿의 경우이 경로는 템플릿 파일을 포함 하는 디렉터리를 참조 합니다. *.Zip* 파일로 배포 된 템플릿의 경우이 경로는 *.zip* 파일의 경로 여야 합니다.

- * * VSTemplateHeader: 헤더를 설명 하는 [서식 데이터](../extensibility/templatedata-element-visual-studio-templates.md) 요소입니다.

### <a name="parent-element"></a>부모 요소
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 템플릿이 있는 디렉터리에 대해 설명 합니다. 매니페스트는 여러 **VSTemplateDir** 항목을 포함 하 여 지역화 된 이름을 제공 하 고, 디렉터리에 대 한 정렬 순서를 지정 하 여 템플릿 범주 트리에서 해당 모양을 제어할 수 있습니다.

 디자인으로 인해 **VSTemplateDir** 항목은 로캘이 지정 되지 않은 매니페스트에서만 표시 되어야 합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

- **RelativePath**: 템플릿의 경로입니다. 경로 마다 항목이 하나만 있을 수 있으므로 첫 번째 항목은 모든 매니페스트에 대해 승리 합니다.

- **프로그램이 localizedname**: 지역화 된 이름을 지정 하는 **namedescription icon** 요소입니다. 선택 사항입니다.

- **SortOrder**: 정렬 순서를 지정 하는 문자열입니다. 선택 사항입니다.

- **ParentFolderOverrideName**: 부모 폴더의 재정의 된 이름입니다. 선택 사항입니다. 이 요소 **에는 name 특성이 있습니다** .이 특성은 이름을 지정 하는 문자열 값입니다.

### <a name="parent-element"></a>부모 요소
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>Namedescription 아이콘
 지역화 된 템플릿의 이름과 설명을 지정 합니다. 위의 **프로그램이 localizedname** 를 참조 하세요.

### <a name="attributes"></a>특성

- **Package**: 패키지를 지정 하는 문자열 값입니다. 선택 사항입니다.

- **Id**: id를 지정 하는 문자열 값입니다. 선택 사항입니다.

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-element"></a>부모 요소
 **프로그램이 localizedname**

## <a name="examples"></a>예제
 다음 코드는 프로젝트 *vstman* 파일의 예입니다.

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

 다음 코드는 항목 *vstman* 파일의 예입니다.

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
