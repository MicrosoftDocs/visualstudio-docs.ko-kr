---
title: VCToolTask 클래스 | Microsoft Docs
description: VCToolTask 기본 클래스가 해당 클래스에서 상속되는 작업에 추가하는 여러 매개 변수에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046743"
---
# <a name="vctooltask-base-class"></a>VCToolTask 기본 클래스

다양한 작업은 궁극적으로 <xref:Microsoft.Build.Utilities.Task> 클래스 및 [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) 클래스에서 상속됩니다. 이 클래스는 매개 변수에서 파생되는 작업에 해당 매개 변수 몇 개를 추가합니다. 이러한 매개 변수가 이 문서에 나열되어 있습니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **VCToolTask** 기본 클래스의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|선택적 **Dictionary\<string, ToolSwitch>** 매개 변수입니다.|
|**AdditionalOptions**|선택적 **string** 매개 변수입니다.|
|**EffectiveWorkingDirectory**|선택적 **string** 매개 변수입니다.|
|**EnableErrorListRegex**|선택적 **bool** 매개 변수입니다.<br/><br/>기본값은 `true`입니다.|
|**ErrorListRegex**|선택적 **ITaskItem[]** 매개 변수입니다.|
|**ErrorListListExclusion**|선택적 **ITaskItem[]** 매개 변수입니다.|
|**GenerateCommandLine**|선택적 **string** 매개 변수입니다.<br/><br/>**CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] 및 **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default] 값을 사용합니다.|
|**GenerateCommandLineExceptSwitches**|선택적 **string** 매개 변수입니다.<br/><br/>**string[]** *switchesToRemove* , **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] 및 **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default] 값을 사용합니다.|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)<br/>
[작업](../msbuild/msbuild-tasks.md)
