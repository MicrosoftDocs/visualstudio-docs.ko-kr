---
title: XML 리터럴과 XML 스키마 탐색기와의 통합
description: Visual Studio의 XML 스키마 탐색기에서 XML 리터럴에 대한 지원을 사용하여 XML 조각을 Visual Basic 코드에 직접 통합하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 57a29998-c6e8-48ac-bdb0-5788e73f9164
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46020dc8423da617deb8f4f70c2a159b4a32014
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851545"
---
# <a name="integration-of-xml-literals-with-xml-schema-explorer"></a>XML 리터럴과 XML 스키마 탐색기와의 통합

Visual Basic에서는 XML 리터럴을 지원하므로 XML 조각을 Visual Basic 코드에 직접 통합할 수 있습니다. 자세한 내용은 [XML 리터럴 개요](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-overview)를 참조하세요.

## <a name="how-to"></a>방법

Visual Basic 프로젝트의 XSD 파일에 XML 리터럴이 들어 있는 경우 **XML 스키마 탐색기** 에서 XML 스키마 집합을 볼 수 있습니다. XML 리터럴과 연결된 스키마 집합을 보려면 XML 리터럴 또는 XML 네임스페이스 가져오기에서 XML 노드를 마우스 오른쪽 단추로 클릭하고 **스키마 탐색기에 표시** 를 선택합니다.

![스키마 탐색기 명령의 샷이 강조 표시된 XML 노드에 대한 상황에 맞는 메뉴를 보여 주는 Visual Basic 프로젝트 창의 스크린샷](../xml-tools/media/vbxmlliteralswithxmlschemaexplorer1.gif)

이렇게 하면 **XML 스키마 탐색기** 가 Visual Basic 파일과 나란히 열립니다.

![XML 스키마 탐색기 및 솔루션 탐색기가 오른쪽 창에 열려 있음을 보여 주는 Visual Basic 프로젝트 창의 스크린샷](../xml-tools/media/vbxmlliteralswithxmlschemaexplorer2.gif)

## <a name="see-also"></a>참조

- [방법: XML 리터럴과 함께 XML 스키마 디자이너 사용](../xml-tools/how-to-use-the-xml-schema-designer-with-xml-literals.md)
