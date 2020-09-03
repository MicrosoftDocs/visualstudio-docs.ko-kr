---
title: Boundsrules로 제한 셰이프 위치 및 크기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672721"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules로 모양 위치 및 크기 제한
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*범위 규칙* 은 셰이프의 크기와 위치에 대 한 제한을 정의 하는 클래스입니다. 사용자가 도형의 모서리나 면을 끄는 동안 반복적으로 호출 되는 메서드를 제공 합니다.

 다음 예제에서는 사각형 도형을 가로 또는 세로의 고정 크기 막대로 제한 합니다. 사용자가 모서리나 옆면을 끌면 윤곽선은 높이와 너비의 두 허용 된 구성 사이에서 대칭 이동 됩니다.

 범위 규칙은에서 파생 된 클래스입니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> . 규칙의 인스턴스는 다음 모양으로 만들어집니다.

```
using Microsoft.VisualStudio.Modeling.Diagrams; ...
public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}
/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

 원하는 경우 위치와 크기를 모두 제한할 수 있습니다.

## <a name="see-also"></a>관련 항목
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [변경 내용에 대한 대응 및 전파](../modeling/responding-to-and-propagating-changes.md)
