---
title: 코드 맵 내보내기 및 저장
ms.date: 05/16/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef7f72010623d20e79a327877a512f0b7352bac5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542573"
---
# <a name="share-code-maps"></a>코드 맵 공유

코드 맵은 Visual Studio 프로젝트의 일부로, 이미지 또는 XPS 파일로 저장할 수 있습니다.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>다른 Visual Studio 사용자와 코드 맵 공유

**파일** 메뉴를 사용하여 맵을 저장합니다.

또는

맵을 특정 프로젝트의 일부로 저장 하려면 맵 도구 모음에서 **공유**  >  **이동 \<CodeMapName> **을 선택 하 고 맵을 저장할 프로젝트를 선택 합니다.

![맵을 다른 프로젝트로 이동](../modeling/media/codemapsmovemapmenu.png)

Visual Studio는 맵을 Visual Studio Enterprise 및 Visual Studio Professional의 다른 사용자와 공유할 수 있는 *.dgml* 파일로 저장 합니다.

> [!NOTE]
> Visual Studio Professional 사용자와 맵을 공유하기 전에 모든 그룹을 확장하고, 숨겨진 노드와 그룹 간 링크를 표시하고, 삭제된 노드 중 다른 작업자가 맵 상에서 볼 수 있도록 하려는 노드를 검색합니다. 그렇지 않으면 다른 사용자가 이러한 항목을 볼 수 없습니다.
>
> 모델링 프로젝트에 있거나 모델링 프로젝트에서 다른 위치로 복사된 맵을 저장할 때 다음 오류가 발생할 수 있습니다.
>
> "프로젝트 디렉터리 외부에 *fileName* 을 저장할 수 없습니다. 연결된 항목이 지원되지 않습니다."
>
> Visual Studio에서 오류가 표시되지만 저장된 버전이 만들어집니다. 이 오류가 발생하지 않게 하려면 모델링 프로젝트 외부에 맵을 만듭니다. 그런 다음 원하는 위치에 그래프를 저장할 수 있습니다. 파일을 솔루션의 다른 위치에 복사하고 저장해 보는 것으로는 문제가 해결되지 않습니다.

## <a name="export-a-code-map-as-an-image"></a>코드 맵을 이미지로 내보내기

코드 맵을 이미지로 내보내면 Microsoft Word 또는 PowerPoint와 같은 다른 응용 프로그램으로 복사할 수 있습니다.

1. 코드 맵 도구 모음에서 **Share**  >  **전자 메일을 이미지로** 공유 또는 **이미지 복사**를 선택 합니다.

2. 이미지를 다른 애플리케이션에 붙여넣습니다.

## <a name="export-the-map-as-an-xps-file"></a>지도를 XPS 파일로 내보내기

코드 맵을 XPS 파일로 내보내면 Internet Explorer와 같은 XML 또는 XAML 뷰어에서 볼 수 있습니다.

1. 코드 맵 도구 모음에서 **Share**  >  **휴대용 xps로 전자 메일** 공유 또는 **휴대용 xps로 저장**을 선택 합니다.

2. 파일을 저장할 위치를 찾습니다.

3. 코드 맵 이름을 지정합니다. 파일 **형식** 상자가 **xps 파일 ( \* .xps)** 로 설정 되어 있는지 확인 합니다. **저장**을 선택합니다.

## <a name="see-also"></a>추가 정보

- [코드 맵으로 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
