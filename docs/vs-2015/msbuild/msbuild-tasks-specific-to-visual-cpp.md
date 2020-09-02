---
title: Visual C++ 관련 MSBuild 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 452c3b408ab6471963124e61bc803e99eb6be80d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686914"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Visaul C++ 관련 MSBuild 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

작업은 빌드 프로세스 동안 실행되는 코드를 제공합니다. Visual C++가 설치되면 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]와 함께 설치되는 작업 외에 다음 작업을 사용할 수 있습니다. 자세한 내용은 [MSBuild (Visual C++) 개요](https://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca)를 참조 하세요.  
  
 각 작업에 대한 매개 변수 외에도 모든 작업에는 다음과 같은 매개 변수가 있습니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Condition`|선택적 `String` 매개 변수입니다.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 엔진이 이 작업이 실행될지 여부를 결정하는 데 사용하는 `Boolean` 식입니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 지원되는 조건에 대한 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|  
|`ContinueOnError`|선택적 매개 변수입니다. 다음 값 중 하나를 포함할 수 있습니다.<br /><br /> -   **WarnAndContinue** 또는 **true**. 작업이 실패할 경우 [Target](../msbuild/target-element-msbuild.md) 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 경고로 처리됩니다.<br />-   **ErrorAndContinue**. 작업이 실패할 경우 `Target` 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 오류로 처리됩니다.<br />-   **ErrorAndStop** 또는 **false**(기본값). 작업이 실패할 경우 `Target` 요소의 나머지 작업이 실행되지 않고 전체 `Target` 요소와 빌드가 실패한 것으로 간주됩니다.<br /><br /> .NET Framework 4.5 이전 버전은 `true` 및 `false` 값만 지원합니다.<br /><br /> 자세한 내용은 [방법: 작업의 오류 무시를](../msbuild/how-to-ignore-errors-in-tasks.md)참조 하세요.|  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[BscMake 작업](../msbuild/bscmake-task.md)|Microsoft Browse Information Maintenance Utility 도구(bscmake.exe)를 래핑합니다.|  
|[CL 작업](../msbuild/cl-task.md)|Visual C++ 컴파일러 도구(cl.exe)를 래핑합니다.|  
|[CPPClean 작업](../msbuild/cppclean-task.md)|Visual C++ 프로젝트가 빌드될 때 MSBuild가 만드는 임시 파일을 삭제합니다.|  
|[LIB 작업](../msbuild/lib-task.md)|Microsoft 32비트 라이브러리 관리자 도구(lib.exe)를 래핑합니다.|  
|[작업 연결](../msbuild/link-task.md)|Visual C++ 링커 도구(link.exe)를 래핑합니다.|  
|[MIDL 작업](../msbuild/midl-task.md)|MIDL(Microsoft 인터페이스 정의 언어) 컴파일러 도구(midl.exe)를 래핑합니다.|  
|[MT 작업](../msbuild/mt-task.md)|Microsoft 매니페스트 도구(mt.exe)를 래핑합니다.|  
|[RC 작업](../msbuild/rc-task.md)|Microsoft Windows 리소스 컴파일러 도구(rc.exe)를 래핑합니다.|  
|[SetEnv 작업](../msbuild/setenv-task.md)|지정된 환경 변수의 값을 설정하거나 삭제합니다.|  
|[VCMessage 작업](../msbuild/vcmessage-task.md)|빌드 중에 경고 메시지 및 오류 메시지를 로깅합니다.|  
|[XDCMake 작업](../msbuild/xdcmake-task.md)|XML 문서 주석(.xdc) 파일을 .xml 파일에 병합하는 XML 문서 도구(xdcmake.exe)를 래핑합니다.|  
|[XSD 작업](../msbuild/xsd-task.md)|소스에서 스키마 또는 클래스 파일을 생성하는 XML 스키마 정의 도구(xsd.exe)를 래핑합니다.|  
|[MSBuild 참조](../msbuild/msbuild-reference.md)|MSBuild 시스템 요소에 대해 설명합니다.|  
|[작업](../msbuild/msbuild-tasks.md)|결합되어 빌드를 생성할 수 있는 코드 단위인 작업에 대해 설명합니다.|  
|[작업 작성](../msbuild/task-writing.md)|작업을 만드는 방법을 설명합니다.|
