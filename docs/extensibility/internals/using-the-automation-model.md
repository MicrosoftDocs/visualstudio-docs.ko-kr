---
title: Automation 모델 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d014627161666473d3b674f72cfec339a66fdc05
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012492"
---
# <a name="using-the-automation-model"></a>자동화 모델 사용
VSPackage를 automation에 연결한 후에는 <xref:EnvDTE.DTEClass.GetObject%2A> 개체에 대해 메서드를 호출 하 여 <xref:EnvDTE._DTE> 검색할 개체를 나타내는 문자열을 전달 하 여 속성 및 메서드를 가져올 수 있습니다.

## <a name="obtaining-project-objects"></a>프로젝트 개체 가져오기
 다음은 자동화 소비자가 프로젝트 자동화 개체를 가져오는 방법을 보여 주는 두 가지 코드 예제입니다. DTE 개체를 가져오는 방법에 대 한 자세한 내용은 [방법: dte 및 DTE2 개체에 대 한 참조 가져오기](/previous-versions/68shb4dw(v=vs.140))를 참조 하세요.

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 이 시점에서 특정 VSPackage의 일부인 표준 프로젝트 개체를 사용 하 여 계층 모델을 아래로 이동할 수 있습니다.

 다음 코드 예제에서는 사용자 지정 프로젝트 형식의 속성인 사용자 지정 개체를 가져오는 방법을 보여 줍니다.

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 다음 코드는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **도구** 메뉴의 환경 **일반** 옵션에 있는 모든 속성의 이름을 나열 합니다.

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>참고 항목
- <xref:EnvDTE.DTEClass.GetObject%2A>