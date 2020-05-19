---
title: 디버거에서 데이터의 사용자 지정 뷰 만들기 | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568996"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Visual Studio 디버거에서 데이터의 사용자 지정 뷰 만들기(C#, Visual Basic, C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버거는 프로그램의 상태를 검사하고 수정하는 다수의 도구를 제공합니다. 이러한 도구의 대부분은 중단 모드에서만 작동합니다.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>변수 창 및 DataTip에서 데이터의 사용자 지정 뷰 만들기

 많은 [디버거 창](../debugger/debugger-windows.md)(예: **자동** 및 **조사식** 창)에서 변수를 검사할 수 있습니다. C++ 형식, 관리 개체 및 고유한 형식이 디버거 변수 창 및 [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)에 표시되는 방식을 사용자 지정할 수 있습니다. 자세한 내용은 [C++ 개체의 사용자 지정 뷰 만들기](../debugger/create-custom-views-of-native-objects.md) 및 [관리 개체의 사용자 지정 뷰 만들기](../debugger/create-custom-views-of-managed-objects.md)를 참조하세요.

## <a name="create-custom-visualizers"></a>사용자 지정 시각화 도우미 만들기

 시각화 도우미는 개체 또는 변수의 내용을 의미 있는 방식으로 볼 수 있도록 합니다. Visual Studio 디버거에서 시각화 도우미는 돋보기 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘") 아이콘을 사용하여 열 수 있는 다양한 창을 나타냅니다. 예를 들어, HTML 시각화 도우미에서는 HTML 문자열이 브라우저에서 어떻게 해석되고 표시되는지 볼 수 있습니다. DataTip, **조사식** 창, **자동** 창 또는 **로컬** 창 대화 상자에서 시각화 도우미에 액세스할 수 있습니다. **간략한 조사식** 대화 상자도 시각화 도우미를 제공합니다. 자세한 내용은 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)를 참조하세요.

## <a name="see-also"></a>참조

- [디버거 소개](../debugger/debugger-feature-tour.md)
- [명령 창](../ide/reference/command-window.md)
- [디버거 보안](../debugger/debugger-security.md)
