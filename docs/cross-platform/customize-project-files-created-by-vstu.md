---
title: VSTU에서 만든 프로젝트 파일 사용자 지정 | Microsoft Docs
description: VSTU(Visual Studio Tools for Unity)에서 생성한 프로젝트 파일을 사용자 지정하는 방법을 알아봅니다. C# 코드 예제를 검토합니다.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a2e4abb707f07e0a781460e5efe6996325e5ca00
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039427"
---
# <a name="customize-project-files-created-by-vstu"></a>VSTU에서 만든 프로젝트 파일 사용자 지정
Visual Studio Tools for Unity는 프로젝트 파일을 생성하는 동안 Unity 스타일의 콜백을 제공합니다. `VisualStudioIntegration.ProjectFileGeneration` 이벤트로 등록하여 다시 생성될 때마다 프로젝트 파일을 수정합니다.

## <a name="demonstrates"></a>데모
 Visual Studio Tools for Unity에서 생성한 Visual Studio 프로젝트 파일을 사용자 지정하는 방법

## <a name="example"></a>예제

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>참고 항목
 [예제: 로그 콜백](../cross-platform/share-the-unity-log-callback-with-vstu.md)
