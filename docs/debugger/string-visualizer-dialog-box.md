---
title: 문자열 시각화 도우미 대화 상자 | Microsoft Docs
description: Visual Studio에서 디버그하는 동안 기본 제공 문자열 시각화 도우미 대화 상자를 사용하여 문자열을 표시합니다.
ms.date: 10/10/2018
ms.custom: contperf-fy21q4
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85092f6a339fdaaa3ddaa56112cc351d8b8e9bdc
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640847"
---
# <a name="string-visualizer-dialog-box"></a>문자열 시각화 도우미 대화 상자

Visual Studio에서 디버그하는 동안 기본 제공 문자열 시각화 도우미를 사용하여 문자열을 볼 수 있습니다. 문자열 시각화 도우미는 데이터 팁 또는 디버거 창에 너무 긴 문자열을 보여 줍니다. 또한 잘 구성되지 않은 문자열을 식별하는 데 도움이 될 수 있습니다.

기본 제공되는 문자열 시각화에는 [텍스트](#text-string-data), [XML](#xml-string-data), [HTML](#html-string-data), [JSON](#json-string-data) 옵션이 포함되어 있습니다. 또한 **Autos** 또는 다른 디버거 창에서 [DataSet, DataTable, DataView](../debugger/dataset-visualizer-dialog-box.md) 개체와 같은 몇 가지 다른 유형에 대한 기본 제공 시각화 도우미를 열 수 있습니다.

> [!NOTE]
> 시각화 도우미에서 XAML 또는 WPF UI 요소를 검사해야 하는 경우 [디버그하는 동안 XAML 속성 검사](../xaml-tools/inspect-xaml-properties-while-debugging.md) 또는 [WPF 트리 시각화 도우미 사용 방법](../debugger/how-to-use-the-wpf-tree-visualizer.md)을 참조하세요.

문자열 시각화 도우미를 열려면 디버그 중에 일시 중지해야 합니다. 일반 텍스트, XML, HTML 또는 JSON 문자열 값이 있는 변수를 마우스로 가리켜 돋보기 아이콘 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘")을 선택합니다.

## <a name="uielement-list"></a>UI 요소 목록

**식** 필드는 마우스로 가리키는 변수나 식을 표시합니다.

**값** 필드는 문자열 값을 표시합니다. 빈 **값** 은 선택한 시각화 도우미가 문자열을 인식할 수 없음을 의미합니다. 예를 들어 **XML 시각화 도우미** 는 XML 태그나 JSON 문자열이 없는 텍스트 문자열에 대해 빈 **값** 을 표시합니다. 선택한 시각화 도우미가 인식할 수 없는 문자열을 보려면 대신 **텍스트 시각화 도우미** 를 선택하세요. **텍스트 시각화 도우미** 는 일반 텍스트를 표시합니다.

### <a name="text-string-data"></a>텍스트 문자열 데이터

**텍스트 시각화 도우미** 는 일반 텍스트를 표시합니다. C++ 문자열에 사용자 지정 형식 지정이 필요한 경우 [Natvis 시각화](../debugger/create-custom-views-of-native-objects.md)를 만듭니다.

![텍스트 문자열 시각화](../debugger/media/dbg-string-visualizer-text.png "텍스트 문자열 시각화")

### <a name="json-string-data"></a>JSON 문자열 데이터

잘 구성된(Well-Formed) JSON 문자열은 JSON 시각화 도우미에서 다음 일러스트레이션과 비슷하게 나타납니다. 잘 구성되지 않은 JSON은 오류 아이콘(또는 인식할 수 없는 경우 공백)을 표시할 수 있습니다. JSON 오류를 식별하려면 문자열을 복사하여 [JSLint](https://www.jslint.com/) 같은 JSON 린팅 도구에 붙여넣으세요.

![JSON 문자열 시각화 도우미](../debugger/media/dbg-tips-string-visualizer-json.png "JSON 문자열 시각화 도우미")

### <a name="xml-string-data"></a>XML 문자열 데이터

잘 구성된 XML 문자열은 XML 시각화 도우미에서 다음 일러스트레이션과 비슷하게 나타납니다. 잘 구성되지 않은 XML은 태그 없이 표시되거나 인식할 수 없는 경우 공백을 표시할 수 있습니다.

![XML 문자열 시각화 도우미](../debugger/media/dbg-string-visualizers-xml.png "XML 문자열 시각화 도우미")

### <a name="html-string-data"></a>HTML 문자열 데이터

잘 구성된 HTML 문자열은 다음 일러스트레이션처럼 브라우저에서 렌더링된 것처럼 나타납니다. 잘 구성되지 않은 HTML은 일반 텍스트로 표시될 수 있습니다.

![HTML 문자열 시각화 도우미](../debugger/media/dbg-string-visualizers-html.png "HTML 문자열 시각화 도우미")

## <a name="see-also"></a>참조

- [사용자 지정 시각화 도우미 만들기(C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Mac용 Visual Studio의 데이터 시각화](/visualstudio/mac/data-visualizations)