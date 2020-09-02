---
title: XDCMake 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c16c92b41aa0635ecb24d83e30e2c347620b2c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675533"
---
# <a name="xdcmake-task"></a>XDCMake 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 문서 주석(.xdc) 파일을 .xml 파일에 병합하는 XML 문서 도구(xdcmake.exe)를 래핑합니다.  
  
 Visual C++ 소스 코드에 문서 주석을 제공하고 [/doc](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) 컴파일러 옵션을 사용하여 컴파일할 때 .xdc 파일이 생성됩니다. 자세한 내용은 xdcmake.exe에 대한 [XDCMake 참조](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [XML 문서 생성기 도구 속성 페이지](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) 및 명령줄 도움말 옵션(**/?**)을 참조하세요.  
  
## <a name="remarks"></a>설명  
 기본적으로 xdcmake.exe 도구는 몇 가지 명령줄 옵션을 지원합니다. **/old** 명령줄 옵션을 지정하면 추가 옵션이 지원됩니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 **XDCMake** 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|선택적 **String[]** 매개 변수입니다.<br /><br /> 병합할 추가.xdc 파일을 하나 이상 지정합니다.<br /><br /> 자세한 내용은 [XML 문서 생성기 도구 속성 페이지](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)의 **추가 문서 파일** 설명을 참조하세요. xdcmake.exe에 대한 **/old** 및 **/Fs** 명령줄 옵션도 참조하세요.|  
|**AdditionalOptions**|선택적 **String** 매개 변수입니다.<br /><br /> 명령줄에 지정된 것처럼 옵션 목록입니다. 예를 들면 "*/ch1/option1/option #*"입니다. 이 매개 변수를 사용하여 다른 **XDCMake** 작업 매개 변수로 표현되지 않는 옵션을 지정합니다.<br /><br /> 자세한 내용은 xdcmake.exe에 대한 [XDCMake 참조](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [XML 문서 생성기 도구 속성 페이지](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) 및 명령줄 도움말(**/?**)을 참조하세요.|  
|**DocumentLibraryDependencies**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true` 및 현재 프로젝트가 솔루션의 정적 라이브러리(.lib) 프로젝트에 대한 종속성을 가진 경우 그 라이브러리 프로젝트의 .xdc 파일은 현재 프로젝트의 .xml 파일에 포함됩니다.<br /><br /> 자세한 내용은 [XML 문서 생성기 도구 속성 페이지](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)의 **문서 라이브러리 종속성** 설명을 참조하세요.|  
|**OutputFile**|선택적 **String** 매개 변수입니다.<br /><br /> 기본 출력 파일 이름을 재정의합니다. 기본 이름은 첫 번째로 처리되는 .xdc 파일의 이름에서 파생됩니다.<br /><br /> 자세한 내용은 **/out:** `filename` [XDCMake 참조](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)의/out: 옵션을 참조 하세요. xdcmake.exe에 대한 **/old** 및 **/Fo** 명령줄 옵션도 참조하세요.|  
|**ProjectName**|선택적 **String** 매개 변수입니다.<br /><br /> 현재 프로젝트의 이름.|  
|**SlashOld**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`이면 추가 xdcmake.exe 옵션이 활성화됩니다.<br /><br /> 자세한 내용은 xdcmake.exe에 대한 **/old** 옵션을 참조하세요.|  
|**Sources**|필수 `ITaskItem[]` 매개 변수입니다.<br /><br /> 작업에서 사용하고 내보낼 수 있는 MSBuild 소스 파일 항목의 배열을 정의합니다.|  
|**SuppressStartupBanner**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.<br /><br /> 자세한 내용은 [XDCMake 참조](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)의 **/nologo** 옵션을 참조하세요.|  
|**TrackerLogDirectory**|선택적 **String** 매개 변수입니다.<br /><br /> 추적기 로그용 디렉터리를 지정합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)
