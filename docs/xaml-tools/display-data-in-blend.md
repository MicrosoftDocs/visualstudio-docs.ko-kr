---
title: XAML UI에서 샘플 데이터 시각화
titleSuffix: Blend for Visual Studio
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0614552bbbadd9a472e0780db6f277d423446966
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2020
ms.locfileid: "82921234"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Blend for Visual Studio에서 데이터 표시

페이지의 레이아웃을 사용자 지정할 때 디자이너에서 예제 데이터를 볼 수 있습니다. 예제 데이터는 처음부터 새로 또는 기존 클래스를 사용하여 생성할 수 있습니다. 예제 데이터를 실행시 앱에 표시되는 *라이브 데이터*에 연결할 수도 있습니다.

> [!NOTE]
> Blend의 **데이터** 패널은 .NET Framework를 대상으로 하는 프로젝트에만 지원 됩니다. .NET Core를 대상으로 하는 UWP 프로젝트 또는 프로젝트에 대해서는 지원 되지 않습니다. 

## <a name="generate-sample-data"></a>샘플 데이터 생성

예제 데이터를 생성하려면 XAML 문서를 엽니다. **데이터** 패널에서 **예제 데이터 만들기** ![예제 데이터 아이콘 만들기](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) 단추를 클릭한 다음, **새 예제 데이터**를 선택합니다.

**데이터** 패널에서 데이터 구조를 정의한 다음 모든 페이지의 UI 요소에 바인딩합니다.

![데이터 패널](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

앱 실행 시 예제 데이터가 페이지에 표시되도록 하려면 **데이터 원본 옵션** ![데이터 원본 옵션 아이콘](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png)을 선택한 다음, **애플리케이션 실행 시 사용**을 선택합니다.

![애플리케이션 메뉴 항목 실행 시 사용](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**짧은 비디오 보기:** ![재생 아이콘](../designers/media/bldadminconsoleinitialconfigicon.PNG) [처음부터 예제 데이터 만들기](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

## <a name="generate-sample-data-from-a-class"></a>클래스에서 예제 데이터 생성

데이터 구조를 설명하는 클래스를 이미 만들었으면 이 클래스에서 예제 데이터를 생성할 수 있습니다.

클래스에서 예제 데이터를 생성하려면 XAML 문서를 열고 **데이터** 패널에서 **예제 데이터 만들기** ![예제 데이터 아이콘 만들기](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) 단추를 클릭한 다음, **클래스에서 예제 데이터 만들기**를 클릭합니다.

**짧은 비디오 보기:** ![재생 아이콘](../designers/media/bldadminconsoleinitialconfigicon.PNG) [일부 데이터 바인딩을 Blend와 혼합](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>참고 항목

- [Blend for Visual Studio를 사용하여 UI 만들기](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
