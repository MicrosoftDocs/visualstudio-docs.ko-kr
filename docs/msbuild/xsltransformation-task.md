---
title: XslTransformation 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d23799e5ce5bf391915ac459c69c27b990211f0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094546"
---
# <a name="xsltransformation-task"></a>XslTransformation 작업

XSLT 또는 컴파일된 XSLT 및 출력을 사용하여 XML 입력을 출력 디바이스 또는 파일로 변환합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `XslTransformation` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`OutputPaths`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> XML 변환에 대한 출력 파일을 지정합니다.|
|`Parameters`|선택적 `String` 매개 변수입니다.<br /><br /> 매개 변수를 XSLT 입력 문서로 지정합니다.  각 매개 변수를 `<Parameter Name="" Value="" Namespace="" />`로 저장하는 원시 XML을 제공합니다.|
|`XmlContent`|선택적 `String` 매개 변수입니다.<br /><br /> XML 입력을 문자열로 지정합니다.|
|`XmlInputPaths`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> XML 입력 파일을 지정합니다.|
|`XslCompiledDllPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 컴파일된 XSLT를 지정합니다.|
|`XslContent`|선택적 `String` 매개 변수입니다.<br /><br /> XSLT 입력을 문자열로 지정합니다.|
|`XslInputPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> XSLT 입력 파일을 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예에서는 XSL 변환 파일 *transform.xslt*를 사용하여 xml 파일 `$(XmlInputFileName)`을 수정합니다. 변환된 XML은 `$(IntermediateOutputPath)output.xml`에 기록됩니다. XSL 변환에서 입력 매개 변수로 `$(Parameter1)`을 사용합니다.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>참조

- [XSLT 매개 변수](/dotnet/standard/data/xml/xslt-parameters)
- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
