---
title: Visual Studio 구독에서 제품 키 찾고 요청하기 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 07/30/2020
ms.topic: conceptual
description: Visual Studio 구독에서 제품 키를 찾고 요청하며 내보내는 방법을 알아봅니다.
ms.openlocfilehash: e9be61db1f72684dcff12d015ec5180607b41977
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250736"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Visual Studio 구독에서 제품 키 찾고 요청하기
이 문서에서는 https://my.visualstudio.com/productkeys 에서 제품 키를 찾고 요청하며 내보내는 방법을 설명합니다.  일반 정품 및 볼륨 라이선스 버전의 키, 일일 제품 키 요청 제한, 키를 사용한 제품 정품 인증 방법에 대한 자세한 내용은 [제품 키 개요](product-keys.md)를 참조하세요.

## <a name="locating-and-claiming-product-keys"></a>제품 키 찾기 및 요청
제품 키를 보려면 Visual Studio 구독에 로그인해야 합니다. 개별 제품 키는 아래 표시된 것처럼 [다운로드](https://my.visualstudio.com/downloads) 페이지에서 특정 제품에 대한 파란색 **키 가져오기** 링크를 선택하여 확인할 수 있습니다.  또한 모든 키는 [제품 키](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) 페이지에서 전체적으로 사용할 수도 있습니다. 단일 제품에 대해 여러 키가 있는 경우 다운로드를 위해 [메모] 열에 해당 정보가 표시되어 사용해야 할 키를 식별하는 데 도움이 됩니다.
> [!div class="mx-imgBorder"]
> ![다운로드 페이지에서 키 가져오기](_img/product-keys/download-get-key.png "임의의 다운로드 정보 페이지에서 키 가져오기를 선택하여 해당 제품에 대한 키를 가져옵니다.")

일부 제품은 한 번에 다운로드할 수 있도록 여러 버전이 번들로 구성되어 있습니다. 이러한 경우 입력하는 제품 키에 따라 설치되는 제품 버전이 결정됩니다.
일부 키는 "정적" 키와 같이 자동으로 제공되며, 정품 인증이 필요하지 않으므로 필요한 만큼 여러 번 사용할 수 있습니다. 다른 키는 제품에 대한 **키 가져오기** 링크를 선택하여 요청해야 합니다.

제품에 따라 다양한 키 유형을 사용할 수 있습니다.

### <a name="product-key-types"></a>제품 키 유형

|    키 유형           |    설명                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    해당 없음                    |    이 제품을 설치하는 데 필요한 키가 없습니다.                                                       |
|    일반 정품                     |    일반 정품 키는 복수 정품 인증을 허용하며, 제품의 일반 정품 빌드에 사용됩니다. 대부분의 경우 키당 10회의 정품 인증이 허용되지만, 동일한 컴퓨터에서 더 자주 정품 인증이 허용됩니다.                                                       |
|    복수 정품 인증        |    MAK(복수 정품 인증 키)를 사용하면 여러 곳에 설치한 제품을 동일한 키로 정품 인증할 수 있습니다. MAK는 대체로 제품의 볼륨 라이선스 버전에 사용됩니다. 일반적으로 구독당 MAK 하나만 제공됩니다.    |
|    정적 정품 인증 키    |    정적 정품 인증 키는 정품 인증이 필요하지 않은 제품에 제공되며, 설치 수에 관계없이 사용할 수 있습니다.                                                                                                                  |
|    사용자 지정 키                 |    사용자 지정 키는 제품을 정품 인증하거나 설치하기 위한 특별한 작업 또는 정보를 제공합니다.                                                                                                                                                                |
|    VA 1.0                     |    MAK와 비슷한 복수 정품 인증 키입니다.                                                                                                                                                                                                 |
|    OEM 키                    |    복수 정품 인증이 가능한 OEM(주문자 상표 부착 방식) 키입니다.                                                                                                                                                                       |
|    DreamSpark 일반 정품 키    |    DreamSpark용 일반 정품 키이며, 한 번의 정품 인증만 허용합니다. DreamSpark 일반 정품 키는 일괄적으로 발급되며, 주로 학생들이 사용하기 위한 것입니다.                                                                                     |
|    DreamSpark 랩 키         |    DreamSpark 프로그램에 대한 랩용 키이며, 여러 번의 정품 인증을 허용합니다. DreamSpark 랩 키는 대학의 컴퓨터실에서 사용하기 위한 것입니다.                                                                                       |
|    DreamSpark MAK 키         |    DreamSpark 프로그램 고객이 사용하기 위한 MAK 키입니다.                                                                                                                                                                                                  |
|

제품에 대한 다운로드 페이지에서 키를 요청하거나 [제품 키](https://my.visualstudio.com/productkeys) 페이지에서 필요한 키를 검색할 수 있습니다.

### <a name="claiming-product-keys"></a>제품 키 요청
활성 구독이 있는 구독자만 제품을 다운로드하고 제품 키를 요청할 수 있습니다.  구독이 활성화되어 있는 동안 [제품 키](https://my.visualstudio.com/productkeys) 페이지에서 요청한 키를 내보낼 수 있습니다.

제품 키를 요청하려면
1. Visual Studio 구독에 로그인합니다.  제품을 다운로드하거나 제품 키를 요청하려면 로그인해야 합니다.
2. [제품 키](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) 탭을 선택합니다.
3. 제품 키는 제품 이름별 사전순으로 나열됩니다.  원하는 제품의 이름으로 스크롤하거나 페이지 위쪽의 검색 표시줄을 사용하여 검색할 수 있습니다.
> [!div class="mx-imgBorder"]
> ![제품 키 검색](_img/product-keys/search-keys.png "원하는 제품으로 스크롤하거나 검색 상자를 사용하여 제품을 빠르게 찾을 수 있습니다.")
   
이 예에서는 검색 표시줄을 사용하여 Visual Studio Enterprise 2019에 대한 제품 키를 찾습니다.
여기에는 몇 가지 버전이 나열되어 있습니다.  각각의 키는 이미 Visual Studio Enterprise 2019 버전 16.0 및 16.1에 대해 요청된 상태입니다.  두 버전에 대해 서로 다른 유형의 키를 여전히 추가로 사용할 수 있습니다. **메모** 열에서 요청한 키에 대한 간단한 메모를 기록할 수 있습니다.  **요청됨** 열의 날짜와 함께 이 메모를 사용하면 요청한 키를 추적할 수 있습니다.  예를 들어 키를 사용하여 제품 설치를 정품 인증할 때 메모를 만들 수 있습니다.

### <a name="exporting-your-claimed-keys"></a>요청한 키 내보내기
자동으로 "요청됨"으로 표시된 정적 및 다른 키 중에서 선택한 많은 항목과 함께 요청한 모든 키 목록을 내보낼 수 있습니다.

> [!IMPORTANT]
> 구독이 만료되면 더 이상 새 키를 요청하거나 요청한 키를 내보낼 수 없습니다.

키를 내보내려면 제품 키 페이지의 오른쪽 끝에 있는 **모든 키 내보내기** 링크를 선택하면 됩니다.  KeysExport.xml이라는 제목의 .xml 파일이 만들어지고, 파일을 열거나 저장할 수 있는 옵션이 표시됩니다.  .xml 파일을 처리할 수 있는 애플리케이션으로 파일을 열어야 합니다.  예를 들어 Excel에서 파일을 읽기 전용 통합 문서로 열 수 있습니다.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
소프트웨어를 다운로드하고 키를 사용할 준비가 되면 https://my.visualstudio.com/downloads 로 이동하세요.  소프트웨어 다운로드에 대한 자세한 내용은 [다운로드 개요](download-software.md)를 참조하세요.