---
title: 디버깅 - 데이터 시각화
description: 디버깅은 프로그래밍의 공통적인 필수 부분입니다. Mac용 Visual Studio에는 편리한 디버깅을 위한 전체 기능 모음이 포함되어 있습니다. 이 문서에서는 디버거에서 개체를 검사할 때 볼 수 있는 다양한 데이터 시각화를 살펴보겠습니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 3355b81406d2b510dc13604a026bcd014bf9dbcb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984764"
---
# <a name="data-visualizations"></a>데이터 시각화

Mac용 Visual Studio에는 디버거에 대한 UI 지원이 포함되어 있으므로 디버그하는 동안 변수, 필드 또는 속성의 값을 시각화할 수 있습니다. 이러한 데이터 시각화 도우미는 색 구조체의 색을 표시하는 등 확장된 버전의 데이터를 표시하고 개발자가 알려진 구조를 검사할 수 있게 합니다.

디버그 **로컬** 패드의 시각화 도우미는 사용자가 행을 마우스로 가리킬 때 값 오른쪽에 표시되는 미리 보기 아이콘을 클릭하면 표시할 수 있습니다.

![로컬 패드](media/data-visualizations-image9.png)

아래 목록에는 Mac용 Visual Studio에서 디버그할 때 제공되는 여러 가지 새로운 시각화가 나와 있습니다.

## <a name="point"></a>Point
iOS 및 Mac의 CGPoint 또는 Point/PointF는 디버그 패드에 X 및 Y 값을 표시하는 튜플로 렌더링됩니다.

![포인트 시각화](media/data-visualizations-image10.png)

## <a name="size"></a>크기
iOS 및 Mac의 CGSize 또는 Size/SizeF는 사각형으로 렌더링됩니다. 크기가 250px 이상으로 확장될 때까지 크기가 조정되고, 250px 이상이 되면 최대 크기가 250px인 사각형으로 크기가 조정됩니다.

[크기 시각화](media/data-visualizations-image11.png)

## <a name="rectangle"></a>직사각형
iOS 및 Mac의 Rectangle/RectangleF 또는 CGRect는 크기와 원점을 표시합니다. Size와 마찬가지로, 크기가 250px 이상으로 확장될 때까지 크기가 조정됩니다.

![사각형 시각화](media/data-visualizations-image12.png)

## <a name="coordinate"></a>좌표
좌표는 위치를 중심에 고정하여 지도에 그려집니다.

[좌표 시각화](media/data-visualizations-image13.png)

## <a name="color"></a>색
UIColor, CGColor, Color 속성을 표시하고 색 미리 보기, RGBA 구성 요소, 색상-채도-명도 값, 색의 16진수 값을 설명합니다.

![색 시각화](media/data-visualizations-image14.png)

## <a name="images"></a>이미지

미디어는 최대 250px 크기까지 확장되도록 렌더링되며, 이미지가 250px를 초과하면 크기가 적절하게 조정됩니다.

![이미지 시각화](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>베지어 곡선

이 시각화 도우미는 `NSBezierPath`를 표시합니다.

![베지어 곡선 시각화](media/data-visualizations-image16.png)

## <a name="string"></a>String

100자 미만의 문자열은 미리 보기 없이 전체 내용이 표시됩니다. 더 긴 문자열은 미리 보기에 전체 내용이 표시됩니다. 문자열은 편집 가능하며, 아래 그림과 같이 시각화 도우미에 있는 편집 단추를 사용하여 미리 보기 또는 문자열 값 편집기에서 문자열 값을 편집할 수 있습니다.

![문자열 시각화](media/data-visualizations-image17.png)

### <a name="small-strings"></a>작은 문자열:
![작은 문자열 시각화](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>중간 길이 문자열:
![중간 문자열 시각화](media/data-visualizations-image19.png)

### <a name="editor"></a>편집기:

![편집기 시각화](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable은 모든 값을 열거합니다. **값 표시** 단추를 클릭하면 각 값을 볼 수 있습니다. IEnumerable 옵션은 자체 디버거 시각화 도우미가 있는 `Array`, `ArrayList`, `List<>`, `Dictionary<,>` 등의 개체 값을 표시하지 않습니다.

![IEnumerable 시각화](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>기타 시각화 도우미

자체 인라인 시각화 도우미도 있는 다른 몇 가지 형식은 다음과 같습니다.

![기타 시각화](media/data-visualizations-image23.png)

* **Primitives**
  * 기본 형식의 원시 값을 표시됩니다.
* **Enum**
  * 열거형 형식 한정자 없이 필드 값을 표시합니다.
* **Tuple**
  * (,) 형식으로 표시됩니다.
* **Null**
  * “null” 값을 표시합니다.
* **URL**
  * 클릭 가능한 하이퍼링크를 표시합니다.
* **IntPtr**
  * IntPtr의 16진수 표현을 표시합니다.

## <a name="see-also"></a>참고 항목

- [자동 및 지역 창에서 변수 검사(Windows의 Visual Studio)](/visualstudio/debugger/autos-and-locals-windows)
- [시각화 도우미에서 문자열 보기(Windows의 Visual Studio)](/visualstudio/debugger/string-visualizer-dialog-box)