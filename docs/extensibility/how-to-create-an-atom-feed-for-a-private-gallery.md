---
title: '방법: 전용 갤러리에 대 한 Atom 피드 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 269161e831fdb176dbfea844e951597efb467312
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905851"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>방법: 전용 갤러리에 대 한 Atom 피드 만들기
확장이 포함 된 인트라넷 위치로 Atom (RSS) 피드를 만들고, 피드를 전용 갤러리로 **확장 및 업데이트** 에 추가할 수 있습니다. 자세한 내용은 [Private galleries](../extensibility/private-galleries.md)(전용 갤러리)를 참조하세요.

## <a name="create-an-atom-feed"></a>Atom 피드 만들기
 Atom 피드를 전용 갤러리로 만들려면 먼저 확장 (*.vsix* 파일)을 폴더에 수집 합니다. 원하는 경우 하위 폴더로 구성할 수 있습니다. 또한 다음 리소스도 필요 합니다.

- 확장을 전용 갤러리로 사용할 수 있도록 하는 *atom.xml* 파일입니다. *atom.xml* 파일을 **확장 및 업데이트**에 연결 하는 방법에 대 한 자세한 내용은 [개인 갤러리](../extensibility/private-galleries.md)를 참조 하세요.

- 확장에서 추출 된 이미지 파일이 들어 있는 폴더입니다 (예: 스크린 샷). *atom.xml* 파일에는 **확장 및 업데이트**에서 사용할 수 있도록 이러한 이미지에 대 한 상대 링크가 들어 있습니다.

  예를 들어 폴더에 다음 두 개의 확장을 수집 했다고 가정 합니다.

- *Template_Wizard_239 .vsix*, 빈 vsix 프로젝트 템플릿입니다.

- *Selectionhighlight 표시 합니다. vsix*는 선택한 단어의 모든 인스턴스를 강조 표시 하는 도구입니다.

  *atom.xml* 파일의 내용은 다음 예제와 유사 합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 두 링크 태그는 생성 된 이미지 폴더의 스크린 샷을 나타냅니다.

## <a name="see-also"></a>추가 정보
- [전용 갤러리](../extensibility/private-galleries.md)
