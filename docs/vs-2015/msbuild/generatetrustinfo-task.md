---
title: GenerateTrustInfo 작업 | Microsoft Docs
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccbe11cefa730264e523390a0844086d6fb03ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149582"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기본 매니페스트, `TargetZone` 및 `ExcludedPermissions` 매개 변수에서 애플리케이션 신뢰를 생성합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `GenerateTrustInfo` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`ApplicationDependencies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 종속 어셈블리를 지정합니다.|  
|`BaseManifest`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 애플리케이션 신뢰를 생성할 기본 매니페스트를 지정합니다.|  
|`ExcludedPermissions`|선택적 `String` 매개 변수입니다.<br /><br /> 영역 기본 권한 집합에서 제외할 하나 이상의 세미콜론으로 구분된 권한 ID 값을 지정합니다.|  
|`TargetZone`|선택적 `String` 매개 변수입니다.<br /><br /> 컴퓨터 정책에서 가져온 영역 기본 권한 집합을 지정합니다.|  
|`TrustInfoFile`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 애플리케이션 보안 신뢰 정보가 포함된 파일을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
