---
title: 자동화 모델 사용 | 마이크로 소프트 문서
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
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704226"
---
# <a name="using-the-automation-model"></a>자동화 모델 사용
VSPackage를 자동화에 연결한 후 <xref:EnvDTE.DTEClass.GetObject%2A> <xref:EnvDTE._DTE> 개체에서 메서드를 호출하고 검색할 개체를 나타내는 문자열을 전달하여 속성 및 메서드를 가져올 수 있습니다.

## <a name="obtaining-project-objects"></a>프로젝트 객체 구하기
 다음은 자동화 소비자가 프로젝트 자동화 개체를 가져오는 방법을 보여 주는 두 가지 코드 예제입니다. DTE 개체를 얻는 방법에 대한 자세한 내용은 [DTE 및 DTE2 개체에 대한 참조 를 얻는 방법을](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)참조하십시오.

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

 이 시점에서 특정 VSPackage의 일부인 표준 프로젝트 개체를 사용하여 계층 구조 모델을 아래로 이동할 수 있습니다.

 다음 코드 예제에서는 사용자 지정 프로젝트 형식의 속성인 사용자 지정 개체를 얻는 방법을 보여 주입니다.

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 다음 코드는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **도구** 메뉴의 환경 **일반** 옵션의 모든 속성 이름을 나열합니다.

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>참조
- <xref:EnvDTE.DTEClass.GetObject%2A>
