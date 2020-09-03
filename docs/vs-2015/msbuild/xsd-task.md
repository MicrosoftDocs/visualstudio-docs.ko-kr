---
title: XSD 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c9dcc0d09887cacca7e6cdaa2e4f2b719c6451c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826240"
---
# <a name="xsd-task"></a>XSD 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

소스에서 스키마 또는 클래스 파일을 생성하는 XML 스키마 정의 도구(xsd.exe)를 래핑합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 **XSD** 작업의 매개 변수에 대해 설명합니다.  
  
- **AdditionalOptions**  
  
     선택적 **문자열** 매개 변수입니다.  
  
     명령줄에 지정된 것처럼 옵션 목록입니다. 예를 들면 "*/ch1/option1/option #*"입니다. 이 매개 변수를 사용하여 다른 **XSD** 작업 매개 변수로 표현되지 않는 옵션을 지정합니다.  
  
- **GenerateFromSchema**  
  
  선택적 **문자열** 매개 변수입니다.  

  지정한 스키마에서 생성되는 유형을 지정합니다.  

  각각 XSD 옵션에 해당하는 다음 값 중 하나를 지정합니다.  

  - **클래스**  -  **/classes**  

  - **데이터 집합**  -  **/데이터 집합**  
  
- **언어**  
  
     선택적 **문자열** 매개 변수입니다.  
  
     생성된 코드에 사용할 프로그래밍 언어를 지정합니다.  
  
     **CS**(C#, 기본값), **VB**(Visual Basic) 또는 **JS**(JScript) 중에서 선택합니다. `System.CodeDom.Compiler.CodeDomProvider Class`를 구현하는 클래스의 정규화된 이름을 지정할 수도 있습니다.  
  
- **Namespace**  
  
     선택적 **문자열** 매개 변수입니다.  
  
     생성된 형식에 대한 런타임 네임스페이스를 지정합니다.  
  
- **원본**  
  
     필수 `ITaskItem[]` 매개 변수입니다.  
  
     작업에서 사용하고 내보낼 수 있는 MSBuild 소스 파일 항목의 배열을 정의합니다.  
  
- **SuppressStartupBanner**  
  
     선택적 **부울** 매개 변수입니다.  
  
     `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.  
  
- **TrackerLogDirectory**  
  
     선택적 **문자열** 매개 변수입니다.  
  
     추적기 로그용 디렉터리를 지정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)
