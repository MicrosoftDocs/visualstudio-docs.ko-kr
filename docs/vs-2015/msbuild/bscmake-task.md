---
title: BscMake 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684540"
---
# <a name="bscmake-task"></a>BscMake 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

중요]
> bscmake는 더 이상 Visual Studio IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 정보는 솔루션 폴더의 .sdf 파일에 자동으로 저장됩니다.  
  
 Microsoft Browse Information Maintenance Utility 도구(bscmake.exe)를 래핑합니다.  bscmake.exe 도구는 컴파일하는 동안 만들어진 소스 브라우저 파일(.sbr)에서 찾아보기 정보 파일(.bsc)을 빌드합니다. **개체 브라우저**를 사용하여 .bsc 파일을 볼 수 있습니다. 자세한 내용은 [BSCMAKE 참조](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13)를 참조 하세요.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 **BscMake** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수는 명령줄 옵션에 해당합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|**AdditionalOptions**|선택적 **문자열** 매개 변수입니다.<br /><br /> 명령줄에 지정된 것처럼 옵션 목록입니다. 예: "/*옵션 1 마이그레이션*  / *옵션 2 마이그레이션*  / *option #*". 이 매개 변수를 사용하여 다른 **BscMake** 작업 매개 변수로 표현되지 않는 옵션을 지정합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)의 옵션을 참조 하세요.|  
|**OutputFile**|선택적 **문자열** 매개 변수입니다.<br /><br /> 기본 출력 파일 이름을 재정의하는 파일 이름을 지정합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)의 **/o** 옵션을 참조 하세요.|  
|**PreserveSBR**|선택적 **부울** 매개 변수입니다.<br /><br /> `true`인 경우 비증분 빌드를 수행합니다. 전체 비증분 빌드는 .bsc 파일이 있는지 여부에 관계 없이 발생하고 .sbr 파일이 잘리지 않도록 방지합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)의 **/n** 옵션을 참조하세요.|  
|**원본**|선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 작업에서 사용하고 내보낼 수 있는 MSBuild 소스 파일 항목의 배열을 정의합니다.|  
|**SuppressStartupBanner**|선택적 **부울** 매개 변수입니다.<br /><br /> `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)의 **/NOLOGO** 옵션을 참조하세요.|  
|**TrackerLogDirectory**|선택적 **문자열** 매개 변수입니다.<br /><br /> 추적기 로그용 디렉터리를 지정합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>관련 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)
