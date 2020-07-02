---
title: 도형 및 패스 그리기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9eba4e5bfef052f7a82c3148f5628eff9413180
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542209"
---
# <a name="draw-shapes-and-paths"></a>도형 및 패스 그리기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML 디자이너에서 *도형* 은 일반적인 도형이 맞습니다. (예: 사각형, 원, 또는 타원). *패스* 는 도형의 보다 유연한 버전으로 도형의 모양을 변경하거나 도형을 결합하는 등 작업을 수행하여 새 도형을 만들 수 있습니다.

 도형 및 패스는 벡터 그래픽을 사용하여 고해상도 디스플레이에 맞게 조정됩니다. 벡터 그래픽에 대해 자세히 알아보려면 [What are Vector Graphics](https://www.youtube.com/watch?v=MoCSwF0n-io) (벡터 그래픽이란) 또는 [vector graphics](https://www.webopedia.com/TERM/V/vector_graphics.html)(벡터 그래픽)를 참조하세요.

 **항목 내용**

- [도형 그리기](#Shape)

- [패스 그리기](#Path)

- [도형을 패스로 변환](#Convert)

- [패스 결합](#Combine)

- [복합형 패스 만들기](#Compound)

- [클리핑 패스 만들기](#Clipping)

## <a name="draw-a-shape"></a><a name="Shape"></a>도형 그리기
 도형은 **자산** 패널에 있습니다.

 ![자산 패널의 셰이프 범주](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")

 아트보드에 원하는 모든 도형을 끕니다. 그런 다음 도형에서 핸들을 사용하여 비율 크기를 조정하고 회전, 이동하거나 도형을 기울일 수 있습니다.

 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")

## <a name="draw-a-path"></a><a name="Path"></a>패스 그리기
 패스는 일련의 연결된 선 및 곡선입니다. 패스를 사용하여 **자산** 패널에서 사용할 수 없는, 흥미로운 도형을 만들 수 있습니다.

 선, 펜 또는 연필을 사용하여 패스를 그릴 수 있습니다. 이러한 도구는 **도구** 패널에 있습니다.

 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbbb21-be83-4cf6-903b-3a49f00c9860")

### <a name="draw-a-straight-line"></a>직선 그리기
 **펜** 도구 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")나 **줄** 도구 ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")를 사용합니다.

 **펜 도구 사용** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")

 아트보드에서 한 번 클릭하여 시작 점을 정의한 후 다시 클릭하여 줄의 끝을 정의합니다.

 **줄 도구 사용** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")

 아트보드에서 줄을 시작할 위치에서 마우스를 끌어 줄을 끝낼 지점에서 마우스를 놓습니다.

### <a name="draw-a-curve"></a>곡선 그리기
 **펜** 도구 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")를 사용합니다.

 아트보드에서 한 번 클릭하여 줄의 시작 점을 정의한 후 마우스 포인터를 클릭한 상태에서 끌어 원하는 곡선을 만듭니다.

 패스를 닫으려면 줄에서 처음 지점을 클릭합니다.

### <a name="change-the-shape-of-a-curve"></a>곡선의 모양 변경
 **직접 선택** 도구 ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362")를 사용합니다.

 도형을 클릭하고 도형에서 아무 점을 마우스로 끌어 곡선 모양을 변경합니다.

### <a name="draw-a-free-form-path"></a>자유형 패스 그리기
 **연필** 도구 ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd")를 사용합니다.

 아트보드에서 실제 연필을 사용하는 것처럼 자유형 패스를 그립니다.

### <a name="remove-part-of-a-path"></a>패스의 일부 제거
 **직접 선택** 도구 ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362")를 사용합니다.

 삭제할 세그먼트가 있는 패스를 선택한 후 **삭제** 단추를 클릭합니다.

### <a name="remove-a-point-in-a-path"></a>패스에서 점 제거
 **선택** 도구  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")및 **펜** 도구 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")를 사용합니다.

 **선택** 도구  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") 를 사용하여 패스를 선택합니다. 그런 다음 **펜** 도구를 사용 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") 하 여 제거 하려는 점을 클릭 합니다.

### <a name="add-a-point-to-a-path"></a>패스에 점 추가
 **선택** 도구  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")및 **펜** 도구 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")를 사용합니다.

 **선택** 도구  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") 를 사용하여 패스를 선택합니다. **펜** 도구를 사용 ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") 하 여 패스에서 점을 추가할 위치를 클릭 합니다.

## <a name="convert-a-shape-to-a-path"></a><a name="Convert"></a>도형을 패스로 변환
 패스를 수정하는 방법과 같은 방법으로 도형을 수정하려면 도형을 패스로 변환합니다.

 **짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [패스 사용: 도형을 패스로 변환](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="combine-paths"></a><a name="Combine"></a>패스 결합
 패스 및 도형을 하나의 패스로 결합할 수 있습니다.

 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")

|이미지|설명|이미지|설명|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|결합하기 전의 두 도형|![](../designers/media/b1-4.png "B1_4")|Intersect|
|![](../designers/media/b1-2.png "B1_2")|통합|![](../designers/media/b1-5.png "B1_5")|겹침 제외|
|![](../designers/media/b1-3.png "B1_3")|나누기|![](../designers/media/b1-6.png "B1_6")|빼기|

 **짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [패스 사용: 패스 결합](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a><a name="Compound"></a>복합형 패스 만들기
 복합형 패스를 만들 때 패스의 교차되는 부분은 결과에서 제외되며, 결과 패스는 맨 아래 패스의 시각적 속성을 사용합니다.

 복합형 패스를 만든 후 언제든지 분리할 수 있습니다.

 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")

 **짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [패스 사용: 복합형 패스 만들기](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a><a name="Clipping"></a>클리핑 패스 만들기
 클리핑 패스는 다른 개체에 적용되는 패스나 도형이며, 개체에서 클리핑 패스를 벗어나는, 마스킹된 개체 부분을 숨깁니다.

 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")

 **짧은 비디오 보기:** ![설치된 기능 구성](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [패스 사용: 클리핑 패스 만들기](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>참고 항목
 [Blend for Visual Studio를 사용하여 UI 만들기](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
