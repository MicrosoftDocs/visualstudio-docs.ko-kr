---
title: '방법: 개인 갤러리에 대한 원자 피드 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711005"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>방법: 개인 갤러리에 대한 원자 피드 만들기
확장이 포함된 인트라넷 위치에 RSS(Atom) 피드를 만들고 **확장 및 업데이트에 피드를** 개인 갤러리로 추가할 수 있습니다. 자세한 내용은 [Private galleries](../extensibility/private-galleries.md)(전용 갤러리)를 참조하세요.

## <a name="create-an-atom-feed"></a>원자 피드 만들기
 Atom 피드를 개인 갤러리로 만들려면 먼저*확장자(.vsix* 파일)를 폴더에 수집합니다. 원하는 경우 하위 폴더로 구성할 수 있습니다. 또한 다음 리소스가 필요합니다.

- 확장프로그램을 개인 갤러리로 사용할 수 있게 하는 *atom.xml* 파일입니다. *atom.xml* 파일을 **확장 및 업데이트에**연결하는 방법에 대한 자세한 내용은 [개인 갤러리를](../extensibility/private-galleries.md)참조하십시오.

- 확장명(예: 스크린샷)에서 추출된 이미지 파일이 포함된 폴더입니다. *atom.xml* 파일에는 이러한 이미지에 대한 상대 링크가 포함되어 있으므로 **확장 및 업데이트에서**사용할 수 있습니다.

  예를 들어 다음 두 확장을 폴더에 수집했다고 가정합니다.

- 빈 VSIX 프로젝트 템플릿인 *Template_Wizard_239.vsix.*

- *선택=* 선택한 단어의 모든 인스턴스를 강조 표시하는 도구입니다.

  *atom.xml* 파일의 내용은 다음 예제와 유사합니다.

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

 두 링크 태그는 이미지의 생성된 폴더에 있는 스크린샷을 참조합니다.

## <a name="see-also"></a>참조
- [프라이빗 갤러리](../extensibility/private-galleries.md)
