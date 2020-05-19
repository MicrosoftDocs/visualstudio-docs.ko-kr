---
title: XML 편집기와 XML 스키마 디자이너 통합
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a9220d84e2fb1a15545d1a880b0084952da77f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592583"
---
# <a name="integration-with-xml-editor"></a>XML 편집기와의 통합

XML 스키마 디자이너는 XML 편집기와 통합되었습니다. XML 편집기에서 XSD 파일을 수정하는 경우 [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)에 변경 내용이 반영됩니다. [그래프 뷰](../xml-tools/graph-view.md) 또는 [콘텐츠 모델 뷰](../xml-tools/content-model-view.md)가 열려 있는 경우 이러한 뷰에도 변경 내용이 반영됩니다. 다음 방법을 사용하여 XML 스키마 디자이너와 XML 편집기 간을 탐색할 수 있습니다.

- XML 편집기에서 노드를 마우스 오른쪽 단추로 클릭한 다음, **XML 스키마 탐색기에 표시**를 선택합니다.

- 그래프 뷰 및 **XML 스키마 탐색기**에서 노드를 두 번 클릭하거나 노드를 마우스 오른쪽 단추로 클릭하고 **코드 보기**를 선택합니다. 콘텐츠 모델 뷰에서 노드를 마우스 오른쪽 단추로 클릭하고 **코드 보기**를 선택합니다.

다음 스크린샷에서는 **XML 스키마 탐색기**에 열린 XML 스키마를 보여 줍니다. **XML 스키마 탐색기**에서는 스키마 집합을 트리 뷰로 표시합니다. XML 편집기에서는 **XML 스키마 탐색기**에서 현재 활성화되어 있는 노드의 텍스트 뷰를 표시합니다.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

코드를 XML 편집기 및 그래픽 디자이너에서 나란히 보는 것이 유용한 경우도 있습니다. 두 파일을 동시에 보려면 XML 편집기의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **뷰 디자이너**를 선택합니다. Visual Studio Windows 메뉴에서 **새 가로(또는 세로) 탭 그룹**을 선택합니다.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>참조

- [XML 스키마 탐색기](../xml-tools/xml-schema-explorer.md)
