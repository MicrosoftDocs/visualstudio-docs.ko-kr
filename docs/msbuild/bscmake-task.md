---
title: BscMake 작업 | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668d42cdb0bc5cfb8dd344aab51ad0c66a838cd2
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634515"
---
# <a name="bscmake-task"></a>BscMake 작업

> [!IMPORTANT]
> BscMake는 더 이상 Visual Studio IDE에서 사용되지 않습니다. Visual Studio 2008부터 찾아보기 정보는 *Solution* 폴더의 *.sdf* 파일에 자동으로 저장됩니다.

 Microsoft Browse Information Maintenance Utility 도구(*bscmake.exe*)를 래핑합니다.  *bscmake.exe* 도구는 컴파일하는 동안 만들어진 소스 브라우저 파일( *.sbr*)에서 찾아보기 정보 파일( *.bsc*)을 빌드합니다. **개체 브라우저**를 사용하여 *.bsc* 파일을 볼 수 있습니다. 자세한 내용은 [BSCMAKE 참조](/cpp/build/reference/bscmake-reference)를 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 표에서는 **BscMake** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수는 명령줄 옵션에 해당합니다.

|매개 변수|설명|
|---------------|-----------------|
|**AdditionalOptions**|선택적 **문자열** 매개 변수입니다.<br /><br /> 명령줄에 지정된 것처럼 옵션 목록입니다. 예: /\<option1> /\<option2> /\<option#>. 이 매개 변수를 사용하여 다른 **BscMake** 작업 매개 변수로 표현되지 않는 옵션을 지정합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](/cpp/build/reference/bscmake-options)의 옵션을 참조하세요.|
|**OutputFile**|선택적 **문자열** 매개 변수입니다.<br /><br /> 기본 출력 파일 이름을 재정의하는 파일 이름을 지정합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](/cpp/build/reference/bscmake-options)의 **/o** 옵션을 참조하세요.|
|**PreserveSBR**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 비증분 빌드를 수행합니다. 전체 비증분 빌드는 *.bsc* 파일이 있는지 여부에 관계 없이 발생하고 *.sbr* 파일이 잘리지 않도록 방지합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](/cpp/build/reference/bscmake-options)의 **/n** 옵션을 참조하세요.|
|**Sources**|선택적 **ITaskItem[]** 매개 변수입니다.<br /><br /> 작업에서 사용하고 내보낼 수 있는 MSBuild 소스 파일 항목의 배열을 정의합니다.|
|**SuppressStartupBanner**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.<br /><br /> 자세한 내용은 [BSCMAKE 옵션](/cpp/build/reference/bscmake-options)의 **/NOLOGO** 옵션을 참조하세요.|
|**TrackerLogDirectory**|선택적 **문자열** 매개 변수입니다.<br /><br /> 추적기 로그용 디렉터리를 지정합니다.|

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
