---
title: 개체 스타일 수정
titleSuffix: Blend for Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f38bfc7a6899ff1d61b8103204bb58df5c5106a6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "82921126"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>Blend for Visual Studio에서 개체 스타일 수정

개체를 사용자 지정하는 가장 쉬운 방법은 **속성** 창에서 속성을 설정하는 방법입니다.

설정이나 설정 그룹을 다시 사용하려면 다시 사용할 수 있는 리소스를 만듭니다. 이러한 리소스로는 *스타일*, *템플릿* 또는 사용자 지정 색 등을 들 수 있습니다. 또한 해당 상태에 따라 컨트롤이 다르게 표시되도록 할 수 있습니다. 예를 들어 사용자가 단추를 클릭할 때 단추가 녹색으로 바뀝니다.

## <a name="brushes-modify-the-appearance-of-an-object"></a>브러시: 개체의 모양 수정

모양을 변경하려는 경우 브러시를 개체에 적용합니다.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>개체에 반복되는 이미지 또는 패턴 그리기

*타일 브러시*를 사용하여 개체에 반복되는 이미지나 패턴을 그릴 수 있습니다.

타일 브러시를 만들려면 *이미지 브러시*, *드로잉 브러시* 또는 *비주얼 브러시* 리소스를 만들어 시작합니다.

이미지를 사용하여 이미지 브러시를 만듭니다. 다음 그림은 이미지 브러시, 바둑판식 이미지 브러시 및 대칭 이동 이미지 브러시를 보여 줍니다.

![이미지 브러시](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![이미지 브러시 바둑판식](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![대칭 이동 이미지 브러시](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

패스나 도형 등과 같은 벡터 드로잉을 사용하여 드로잉 브러시를 만듭니다. 다음 그림은 드로잉 브러시, 바둑판식 드로잉 브러시 및 대칭 이동 드로잉 브러시를 보여 줍니다.

![드로잉 브러시](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![바둑판식 드로잉 브러시](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![대칭 이동 드로잉 브러시](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

컨트롤에서 단추 등과 같은 비주얼 브러시를 만듭니다. 다음 그림은 비주얼 브러시, 바둑판식 비주얼 브러시를 보여 줍니다.

![비주얼 브러시](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![비주얼 브러시 바둑판식](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>스타일 및 템플릿: 컨트롤 간 일관된 모양과 느낌 만들기

컨트롤의 모양 및 동작을 한 번 디자인하고 해당 디자인을 다른 컨트롤에 적용하여 컨트롤의 모양과 동작을 개별적으로 유지 관리하지 않아도 됩니다.

**스타일을 사용해야 하나요?**: 기본 속성(예: 단추 색)을 설정하려면 *스타일*을 사용합니다. 스타일을 컨트롤에 적용한 후에도 컨트롤을 수정할 수 있습니다.

**템플릿을 사용해야 하나요?**: 컨트롤의 구조를 변경하려는 경우 *템플릿*을 사용합니다. 그래픽이나 로고를 단추로 변환한다고 가정해 보면 템플릿을 컨트롤에 적용한 후에는 컨트롤을 수정할 수 없습니다.

### <a name="create-a-template-or-style"></a>템플릿 또는 스타일 만들기

두 가지 방법으로 템플릿을 만들 수 있습니다. 아트보드의 모든 개체를 컨트롤로 변환하거나 기존 컨트롤의 템플릿을 기준으로 설정할 수 있습니다.

모든 개체를 컨트롤 템플릿으로 변환하려면 개체를 선택한 후 **도구** 메뉴에서 **컨트롤로 만들기**를 선택합니다.

기존 컨트롤의 템플릿을 기준으로 설정하려면 아트보드에서 개체를 선택합니다. 그런 다음 아트보드 상단에서 이동 경로 탐색 단추를 선택하고 **템플릿 편집**을 선택한 다음 **복사본 편집** 또는 **빈 항목 만들기**를 선택합니다.

![템플릿 편집 메뉴](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

스타일을 만들려면 개체를 선택하고 **개체** 메뉴에서 **스타일 편집**을 선택한 후 **복사본 편집**이나 **빈 항목 만들기**를 선택합니다.

- 컨트롤의 기본 스타일이나 템플릿으로 시작하려면 **복사본 편집**을 선택합니다.

- 처음부터 다시 시작하려면 **빈 항목 만들기**를 선택합니다.

**현재 항목 편집** 옵션은 이미 만든 스타일이나 템플릿을 편집하는 경우에만 표시됩니다. 기본 시스템 템플릿을 사용하는 컨트롤에 대해서는 표시되지 않습니다.

**스타일 리소스 만들기** 대화 상자에서 나중에 사용할 수 있도록 스타일이나 템플릿의 이름을 지정하거나 해당 유형의 모든 컨트롤에 스타일이나 템플릿을 적용할 수 있습니다.

![스타일 리소스 만들기 대화 상자](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> 일부 유형의 컨트롤에 대해서는 스타일이나 템플릿을 만들 수는 없습니다. 컨트롤에서 스타일이나 템플릿을 지원하지 않는 경우 아트보드 위에 이동 경로 탐색 단추가 표시되지 않습니다.
> 기본 문서의 편집 범위로 돌아오려면 **범위 되돌리기** ![범위 되돌리기 아이콘](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png)을 클릭합니다.

### <a name="apply-a-style-or-template-to-a-control"></a>컨트롤에 스타일이나 템플릿 적용

[개체 및 타임라인](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) 창에서 개체를 마우스 오른쪽 단추로 클릭하고 **템플릿 편집**을 선택한 다음, **리소스 적용**을 선택합니다.

![리소스 적용 메뉴](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>컨트롤의 기본 스타일이나 템플릿 복원

컨트롤을 선택 하 고 * * 속성 * * * * 창에서 **스타일** 또는 **템플릿** 속성을 찾습니다. **고급 옵션**을 선택한 다음, 바로 가기 메뉴에서 **다시 설정**을 클릭합니다.

## <a name="visual-states"></a>시각적 상태

시각적 상태를 사용하여 해당 상태에 따라 컨트롤의 모양을 변경할 수 있습니다. 컨트롤에는 사용자 상호 작용에 따라 여러 시각적 모양이 포함될 수 있습니다. 예를 들어 사용자가 클릭하거나 애니메이션 실행 시 단추가 녹색으로 바뀌도록 설정할 수 있습니다. 전환을 사용하여 시각적 상태 간의 시간을 줄이거나 늘릴 수 있습니다.

![마우스를 위에 놓았을 때 상태](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**짧은 비디오 보기:** ![재생 단추](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Manage the state of your WPF controls](https://www.youtube.com/watch?v=m0PlkF5i6uw)(WPF 컨트롤 상태 관리).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>리소스: 색, 스타일 및 템플릿을 만들고 나중에 다시 사용

프로젝트의 모든 항목을 리소스로 변환할 수 있습니다. 리소스는 애플리케이션의 다른 위치에 다시 사용할 수 있는 단순한 개체입니다. 예를 들어 색을 한 번 만들어 리소스로 만든 후 해당 색을 여러 개체에 사용할 수 있습니다. 이러한 모든 개체의 색을 변경하려면 색 리소스를 변경하기만 하면 됩니다.

![색을 리소스로 변환 단추](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![색 리소스 만들기 대화 상자](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>참고 항목

- [Blend for Visual Studio를 사용하여 UI 만들기](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
