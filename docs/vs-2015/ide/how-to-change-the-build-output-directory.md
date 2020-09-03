---
title: '방법: 빌드 출력 디렉터리 변경 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645425"
---
# <a name="how-to-change-the-build-output-directory"></a>방법: 빌드 출력 디렉터리 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트에서 생성된 구성별로(디버그, 릴리스 또는 둘 다) 출력의 위치를 지정할 수 있습니다.

> [!NOTE]
> **설치** 프로젝트가 있는 경우이 문서의 끝에 있는 참고를 참조 하세요.

## <a name="changing-the-build-output-directory"></a>빌드 출력 디렉터리 변경

#### <a name="to-change-the-build-output-directory"></a>빌드 출력 디렉터리를 변경하려면

1. 메뉴 모음에서 **프로젝트**, *Appname* **속성**을 선택합니다. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택할 수도 있습니다.

2. Visual Basic 프로젝트가 있는 경우 **컴파일** 탭을 선택 합니다. Visual c # 프로젝트가 있는 경우 **빌드** 탭을 선택 합니다. C + + 프로젝트 또는 JavaScript 프로젝트가 있는 경우 **일반** 탭을 선택 합니다.

3. 맨 위의 구성 드롭다운에서 출력 파일 위치를 변경하려는 구성(디버그, 릴리스 또는 둘 다)을 선택합니다.

     출력 경로 항목 (Visual Basic의**빌드 출력 경로** , Visual C++의 **출력 디렉터리** , JavaScript 및 c #의 **출력 경로** )을 찾습니다. 프로젝트 디렉터리를 기준으로 새 빌드 출력 디렉터리를 지정합니다.

> [!NOTE]
> 설치 프로젝트의 **출력 파일 이름** 상자는 프로젝트 파일의 위치는 변경하지 않고 Setup.exe 파일의 위치만 변경합니다. 자세한 내용은 **배포 프로젝트 속성 대화 상자, 구성 속성, 빌드**를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [프로젝트 디자이너, 빌드 페이지 (c #)](../ide/reference/build-page-project-designer-csharp.md) [일반 속성 페이지 (프로젝트)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
