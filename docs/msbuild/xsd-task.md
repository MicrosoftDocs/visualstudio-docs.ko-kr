---
title: XSD 작업 | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 217e045a731efa1fe3ba1dda63e89eca685d4b75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630784"
---
# <a name="xsd-task"></a>XSD 작업

소스에서 스키마 또는 클래스 파일을 생성하는 XML 스키마 정의 도구(*xsd.exe*)를 래핑합니다.

> [!NOTE]
> Visual Studio 2017부터 *xsd.exe*에 대한 C++ 프로젝트 지원이 사용되지 않습니다. *CppCodeProvider.dll*을 수동으로 GAC에 추가하여 **Microsoft.VisualC.CppCodeProvider** API를 계속 사용할 수 있습니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 **XSD** 작업의 매개 변수에 대해 설명합니다.

- **AdditionalOptions**

     선택적 **String** 매개 변수입니다.

     명령줄에 지정된 것처럼 옵션 목록입니다. 예를 들어 /\<option1> /\<option2> /\<option#>을 참조하십시오. 이 매개 변수를 사용하여 다른 **XSD** 작업 매개 변수로 표현되지 않는 옵션을 지정합니다.

- **GenerateFromSchema**

  선택적 **String** 매개 변수입니다.

  지정한 스키마에서 생성되는 유형을 지정합니다.

  각각 XSD 옵션에 해당하는 다음 값 중 하나를 지정합니다.

  - **클래스** -  **/classes**

  - **데이터 세트** -  **/dataset**

- **언어**

     선택적 **String** 매개 변수입니다.

     생성된 코드에 사용할 프로그래밍 언어를 지정합니다.

     **CS**(C#, 기본값), **VB**(Visual Basic) 또는 **JS**(JScript) 중에서 선택합니다. `System.CodeDom.Compiler.CodeDomProvider Class`를 구현하는 클래스의 정규화된 이름을 지정할 수도 있습니다.

- **Namespace**

     선택적 **String** 매개 변수입니다.

     생성된 형식에 대한 런타임 네임스페이스를 지정합니다.

- **Sources**

     필수 `ITaskItem[]` 매개 변수입니다.

     작업에서 사용하고 내보낼 수 있는 MSBuild 소스 파일 항목의 배열을 정의합니다.

- **SuppressStartupBanner**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.

- **TrackerLogDirectory**

     선택적 **String** 매개 변수입니다.

     추적기 로그용 디렉터리를 지정합니다.

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
