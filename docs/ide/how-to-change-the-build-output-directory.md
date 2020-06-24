---
title: '방법: 빌드 출력 디렉터리 변경'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4c2f2445bc7139c5bbc80a35905e24c319c9dfa
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284648"
---
# <a name="how-to-change-the-build-output-directory"></a>방법: 빌드 출력 디렉터리 변경

구성별로(디버그, 릴리스 또는 둘 다) 프로젝트에서 생성된 출력의 위치를 지정할 수 있습니다.

## <a name="change-the-build-output-directory"></a>빌드 출력 디렉터리 변경

1. 프로젝트 속성 페이지를 열려면 **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

2. 프로젝트 형식에 따라 적절한 탭을 선택합니다.

   - C#의 경우 **빌드** 탭을 선택합니다.
   - Visual Basic의 경우 **컴파일** 탭을 선택합니다.
   - C++ 또는 JavaScript의 경우 **일반** 탭을 선택합니다.

3. 맨 위의 구성 드롭다운에서 출력 파일 위치를 변경하려는 구성(**디버그**, **릴리스** 또는 **둘 다**)을 선택합니다.

4. 페이지의 출력 경로 항목을 찾습니다. &mdash;프로젝트 유형에 따라 달라집니다.

   - C# 및 JavaScript 프로젝트의 **출력 경로**
   - Visual Basic 프로젝트의 **빌드 출력 경로**
   - Visual C++ 프로젝트의 **출력 디렉터리**

   (루트 프로젝트 디렉터리에 대해 절대 또는 상대로) 출력을 생성할 경로를 입력하거나, **찾아보기**를 선택하여 해당 폴더를 찾아봅니다.

   ![Visual Studio C#프로젝트의 출력 경로 속성](media/output-path.png)
   
   > [!NOTE]
   > 일부 프로젝트는 기본적으로 빌드 경로에 프레임워크와 런타임을 포함합니다. 이 설정을 변경하려면 **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 파일 편집**을 선택하여 다음을 추가합니다.
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> 지정한 위치에 출력이 생성되지 않는 경우 Visual Studio의 메뉴 모음에서 선택하여 해당 구성(예를 들어 **디버그** 또는 **릴리스**)을 빌드 중인지 확인합니다.
>
> ![Visual Studio 2019의 빌드 구성 선택기](media/build-configuration-chooser.png)

## <a name="see-also"></a>참고 항목

- [빌드 페이지, 프로젝트 디자이너(C#)](../ide/reference/build-page-project-designer-csharp.md)
- [일반 속성 페이지(프로젝트)](/cpp/build/reference/general-property-page-project)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
