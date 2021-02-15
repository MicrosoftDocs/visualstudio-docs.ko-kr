---
title: MSBuild 프로젝트 파일 스키마 참조 | Microsoft Docs
description: 사용 가능한 특성 및 자식 요소가 포함된 모든 MSBuild XML 스키마 요소를 나열한 표입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3451101d6ab2483960731281763167c0cd1629c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918986"
---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild 프로젝트 파일 스키마 참조

이 항목에서는 사용 가능한 특성 및 자식 요소가 포함된 모든 MSBuild XML 스키마 요소의 표를 제공합니다.

 MSBuild는 프로젝트 파일을 사용하여 빌드 엔진에 빌드할 내용 및 빌드 방법을 지시합니다. MSBuild 프로젝트 파일은 MSBuild XML 스키마를 준수하는 XML 파일입니다. 이 섹션에서는 MSBuild의 XML 스키마 정의( *.xsd*) 파일에 대해 설명합니다.

MSBuild 프로젝트 파일의 스키마 링크는 Visual Studio 2017 이상에서 필요하지 않습니다. 있다면 Visual Studio 버전에 관계없이 ` http://schemas.microsoft.com/developer/msbuild/2003`이어야 합니다.

## <a name="msbuild-xml-schema-elements"></a>MSBuild XML 스키마 요소

 다음 표에는 모든 MSBuild XML 스키마 요소와 해당 자식 요소 및 특성이 나와 있습니다.

|요소|자식 요소|특성|
|-------------|--------------------|----------------|
|[Choose 요소(MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|
|[Import 요소(MSBuild)](../msbuild/import-element-msbuild.md)|--|조건<br /><br /> Project|
|[ImportGroup 요소](../msbuild/importgroup-element.md)|가져오기|조건|
|[Item 요소(MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|조건<br /><br /> 제외<br /><br /> 포함<br /><br /> 제거|
|[ItemDefinitionGroup 요소(MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|조건|
|[ItemGroup 요소(MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|조건|
|[ItemMetadata 요소(MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|조건|
|[OnError 요소(MSBuild)](../msbuild/onerror-element-msbuild.md)|--|조건<br /><br /> ExecuteTargets|
|[Otherwise 요소(MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output 요소(MSBuild)](../msbuild/output-element-msbuild.md)|--|조건<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[매개 변수 요소](../msbuild/parameter-element.md)|--|출력<br /><br /> ParameterType<br /><br /> 필수|
|[ParameterGroup 요소](../msbuild/parametergroup-element.md)|*매개 변수*|--|
|[Project 요소(MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> 가져오기<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Target<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> Sdk<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions 요소(MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property 요소(MSBuild)](../msbuild/property-element-msbuild.md)|--|조건|
|[PropertyGroup 요소(MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*속성*|조건|
|[Sdk 요소(MSBuild)](../msbuild/sdk-element-msbuild.md)|--|이름<br /><br /> 버전|
|[Target 요소(MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> 조건<br /><br /> DependsOnTargets<br /><br /> 입력<br /><br /> KeepDuplicateOutputs<br /><br /> 이름<br /><br /> outputs<br /><br /> 반환|
|[Target의 Task 요소(MSBuild)](../msbuild/task-element-msbuild.md)|출력|조건<br /><br /> ContinueOnError<br /><br /> *매개 변수*|
|[UsingTask의 Task 요소(MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Evaluate|
|[UsingTask 요소(MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Task|AssemblyFile<br /><br /> AssemblyName<br /><br /> 조건<br /><br /> TaskFactory<br /><br /> TaskName|
|[When 요소(MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|조건|

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [조건](../msbuild/msbuild-conditions.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
