---
title: 부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기
description: 부하 테스트 API 및 웹 성능 테스트 API로 테스트용 사용자 지정 플러그인을 만들어 기본 제공 기능을 확장하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db91f8f5ccf86d67d01bb56a3a42b66757320500
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442666"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기

사용자 지정 플러그 인은 사용자가 작성하여 부하 테스트 또는 웹 성능 테스트에 연결하는 코드를 사용합니다. 부하 테스트 API 및 웹 성능 테스트 API를 사용하여 테스트용 사용자 지정 플러그 인을 만들어 기본 제공 기능을 확장할 수 있습니다. 부하 테스트에 여러 플러그 인을 추가할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-----------------------|
|**부하 테스트에 대한 사용자 지정 플러그 인 만들기**: 부하 테스트 API를 사용하여 사용자 지정 플러그 인을 만들어 부하 테스트에 더 많은 기능을 추가할 수 있습니다.|-   [방법: 부하 테스트 API 사용](../test/how-to-use-the-load-test-api.md)<br />-   [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)|
|**웹 성능 테스트에 대한 사용자 지정 플러그 인 만들기:** 웹 성능 테스트 API를 사용하여 사용자 지정 플러그 인을 만들어 웹 성능 테스트에 요청 수준을 비롯한 더 많은 기능을 추가할 수 있습니다. 웹 서비스 테스트를 만들 수도 있습니다.<br /><br /> 또한 웹 성능 테스트가 기록된 후 웹 성능 테스트 결과 뷰어에 나타나기 전에 이 웹 성능 테스트를 수정할 수 있는 웹 레코더 플러그 인을 만들 수 있습니다.|-   [방법: 웹 성능 테스트 API 사용](../test/how-to-use-the-web-performance-test-api.md)<br />-   [방법: 웹 성능 테스트 플러그 인 만들기](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [방법: 요청 수준 플러그 인 만들기](../test/how-to-create-a-request-level-plug-in.md)<br />-   [방법: 웹 서비스 테스트 만들기](../test/how-to-create-a-web-service-test.md)<br />-   [방법: 레코더 플러그 인 만들기](../test/how-to-create-a-recorder-plug-in.md)|
|**웹 성능 테스트 결과 뷰어에 UI 기능 추가:** Visual Studio 추가 기능을 사용하여 웹 성능 테스트 결과 뷰어에 더 많은 UI 기능을 추가할 수 있습니다.|-   [방법: 웹 성능 테스트 결과 뷰어에 대한 Visual Studio 추가 기능 만들기](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**사용자 지정 HTTP 본문 편집기 만들기:** 사용자 지정 편집기를 만들어 웹 서비스의 이진 또는 문자열 HTTP XML 응답을 편집할 수 있습니다.|-   [방법: 웹 성능 테스트 편집기에 대한 사용자 지정 HTTP 본문 편집기 만들기](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>참고

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>참조

- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)
