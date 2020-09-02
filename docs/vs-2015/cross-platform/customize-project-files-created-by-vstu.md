---
title: VSTU에서 만든 프로젝트 파일 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 4
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 744e7d89827e169579953474c9e7b37f2dcc653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150994"
---
# <a name="customize-project-files-created-by-vstu"></a>VSTU에서 만든 프로젝트 파일 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Tools for Unity는 프로젝트 파일을 생성하는 동안 Unity 스타일의 콜백을 제공합니다. `VisualStudioIntegration.ProjectFileGeneration` 이벤트로 등록하여 다시 생성될 때마다 프로젝트 파일을 수정합니다.  
  
## <a name="demonstrates"></a>데모  
 Visual Studio Tools for Unity에서 생성한 Visual Studio 프로젝트 파일을 사용자 지정하는 방법  
  
## <a name="example"></a>예제  
  
```csharp  
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
```  
  
## <a name="see-also"></a>참고 항목  
 [예: 로그 콜백](../cross-platform/share-the-unity-log-callback-with-vstu.md)
