---
title: '방법: MIP 맵을 포함하는 질감 내보내기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55418f40f57e2279100fbb1c9ba4d12fae83a19c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664440"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>방법: 밉 맵을 포함하는 질감 내보내기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이미지 콘텐츠 파이프라인은 프로젝트의 빌드 단계 중에 소스 이미지에서 MIP 맵을 생성할 수 있습니다. 각 MIP 수준의 이미지 콘텐츠를 수동으로 지정할 필요가 없는 경우(이 작업은 특정 효과를 적용하기 위해 수행할 수 있음) 빌드 시 MIP 맵을 생성하면 MIP 맵 콘텐츠가 동기화되지 않고 런타임에 MIP 맵을 생성하는 동안 성능이 저하되지 않습니다.

 이 문서는 다음 활동을 보여 줍니다.

- 이미지 콘텐츠 파이프라인에서 처리할 소스 이미지 구성.

- MIP 맵을 생성하도록 이미지 콘텐츠 파이프라인 구성.

## <a name="exporting-mipmaps"></a>MIP 맵 내보내기
 MIP 매핑은 3차원 게임이나 앱에서 질감이 적용된 표면에 대한 자동 화면 공간 수준 세부 정보를 제공합니다. 이 기능은 샘플링할 때마다 전체 질감을 다운 샘플링할 필요가 없도록 질감의 다운 샘플링된 버전을 미리 계산하여 게임 또는 앱의 렌더링 성능을 개선합니다.

#### <a name="to-export-a-texture-that-has-mipmaps"></a>MIP 맵이 있는 질감을 내보내려면

1. 기본 질감으로 시작합니다. 기존 이미지 파일을 로드 하거나 [방법: 기본 질감 만들기](../designers/how-to-create-a-basic-texture.md)에 설명 된 대로 이미지 파일 하나를 만듭니다. MIP 맵을 지원하려면 너비 및 높이가 둘 다 동일한 2의 거듭제곱인 크기(예: 64x64, 256x256 또는 512x512)의 질감을 지정합니다.

2. 방금 만든 질감 파일이 이미지 콘텐츠 파이프라인에서 처리되도록 구성합니다. **솔루션 탐색기**에서 방금 만든 질감 파일에 대한 바로 가기 메뉴를 열고 **속성**을 선택합니다. **구성 속성**, **일반** 페이지에서 **항목 종류** 속성을 **이미지 콘텐츠 파이프라인**으로 설정합니다. **콘텐츠** 속성이 **예**로 설정되고 **빌드에서 제외**가 **아니요**로 설정되어 있는지 확인하고 **적용** 단추를 선택합니다. **이미지 콘텐츠 파이프라인** 구성 속성 페이지가 표시됩니다.

3. MIP 맵을 생성하도록 이미지 콘텐츠 파이프라인을 구성합니다. **구성 속성**, **이미지 콘텐츠 파이프라인**, **일반** 페이지에서 **Mip 생성** 속성을 **예(/generatemips)** 로 설정합니다.

4. **확인** 단추를 선택합니다.

   프로젝트를 빌드할 때 이미지 콘텐츠 파이프라인은 소스 이미지를 작업 형식에서 지정한 출력 형식으로 변환하고(MIP 수준 포함) 결과는 프로젝트의 출력 디렉터리로 복사됩니다.
