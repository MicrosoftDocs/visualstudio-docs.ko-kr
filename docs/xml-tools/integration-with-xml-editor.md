---
title: XML 편집기와 XML 스키마 디자이너 통합
description: XML 스키마 디자이너와 XML 편집기 간의 통합에 대해 알아보고 한쪽에서 변경한 내용이 다른 쪽에 반영되는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe1bfcd422dbfc5f010ae7819e2fccbeafb8227
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934626"
---
# <a name="integration-with-xml-editor"></a>XML 편집기와의 통합

XML 스키마 디자이너는 XML 편집기와 통합되었습니다. XML 편집기에서 XSD 파일을 수정하는 경우 [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)에 변경 내용이 반영됩니다. [그래프 뷰](../xml-tools/graph-view.md) 또는 [콘텐츠 모델 뷰](../xml-tools/content-model-view.md)가 열려 있는 경우 이러한 뷰에도 변경 내용이 반영됩니다. 다음 방법을 사용하여 XML 스키마 디자이너와 XML 편집기 간을 탐색할 수 있습니다.

- XML 편집기에서 노드를 마우스 오른쪽 단추로 클릭한 다음, **XML 스키마 탐색기에 표시** 를 선택합니다.

- 그래프 뷰 및 **XML 스키마 탐색기** 에서 노드를 두 번 클릭하거나 노드를 마우스 오른쪽 단추로 클릭하고 **코드 보기** 를 선택합니다. 콘텐츠 모델 뷰에서 노드를 마우스 오른쪽 단추로 클릭하고 **코드 보기** 를 선택합니다.

다음 스크린샷에서는 **XML 스키마 탐색기** 에 열린 XML 스키마를 보여 줍니다. **XML 스키마 탐색기** 에서는 스키마 집합을 트리 뷰로 표시합니다. XML 편집기에서는 **XML 스키마 탐색기** 에서 현재 활성화되어 있는 노드의 텍스트 뷰를 표시합니다.

![XML 편집기 창의 XML 노드와 XML 스키마 탐색기 창의 스키마 집합 트리 뷰를 보여 주는 Visual Studio 프로젝트의 스크린샷](../xml-tools/media/xsddesignerwithxmleditor.gif)

코드를 XML 편집기 및 그래픽 디자이너에서 나란히 보는 것이 유용한 경우도 있습니다. 두 파일을 동시에 보려면 XML 편집기의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **뷰 디자이너** 를 선택합니다. Visual Studio Windows 메뉴에서 **새 가로(또는 세로) 탭 그룹** 을 선택합니다.

![뷰 디자이너 창, XML 편집기 창 및 XML 스키마 탐색기 창을 보여 주는 Visual Studio 프로젝트의 스크린샷](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>참조

- [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)
