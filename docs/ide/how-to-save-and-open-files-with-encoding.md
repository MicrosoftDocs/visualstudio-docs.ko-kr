---
title: '방법: 인코딩을 사용하여 파일 저장 및 열기'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1e562771567a6ff4f9dc35c9e98ceb5441a074
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596179"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>방법: 인코딩을 사용하여 파일 저장 및 열기

양방향 언어를 지원하기 위해 특정 문자 인코딩을 사용하여 파일을 저장할 수 있습니다. Visual Studio에 파일이 제대로 표시되도록 파일을 열 때 인코딩을 지정할 수 있습니다.

## <a name="to-save-a-file-with-encoding"></a>인코딩을 사용하여 파일을 저장하려면

1. **파일** 메뉴에서 **다른 이름으로 파일 저장**을 선택하고 **저장** 단추 옆의 드롭다운 단추를 클릭합니다.

     **고급 저장 옵션** 대화 상자가 표시됩니다.

2. **인코딩**에서 파일에 사용할 인코딩을 선택합니다.

3. 선택적으로 **줄 끝**에서 줄 끝 문자의 형식을 선택합니다.

     파일을 다른 운영 체제의 사용자와 교환하려는 경우 이 옵션이 유용합니다.

     알고 있는 특정 방법으로 인코딩된 파일을 사용하려면 파일을 열 때 해당 인코딩을 사용하도록 Visual Studio에 알릴 수 있습니다. 사용할 방법은 파일이 프로젝트에 포함되는지에 따라 달라집니다.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>프로젝트에 포함된 인코딩된 파일을 열려면

1. **솔루션 탐색기**에서 파일을 마우스 오른쪽 단추로 클릭하고 **연결 프로그램**을 선택합니다.

2. **연결 프로그램** 대화 상자에서 파일을 열 편집기를 선택합니다.

     양식 편집기와 같은 대부분의 Visual Studio 편집기에서는 인코딩을 자동 검색하고 적절하게 파일을 엽니다. 인코딩을 선택할 수 있는 편집기를 선택하면 **인코딩** 대화 상자가 표시됩니다.

3. **인코딩** 대화 상자에서 편집기에서 사용해야 하는 인코딩을 선택합니다.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>프로젝트에 포함되지 않은 인코딩된 파일을 열려면

1. **파일** 메뉴에서 **열기**를 가리키고 **파일** 또는 **웹 파일**을 선택하고 나서 열 파일을 선택합니다.

2. **열기** 단추 옆의 드롭다운 단추를 클릭하고 **연결 프로그램**을 선택합니다.

3. 이전 절차에서 2단계 및 3단계를 수행합니다.

## <a name="see-also"></a>참고 항목

- [인코딩 및 줄 바꿈](encodings-and-line-breaks.md)
- [인코딩 및 Windows Forms 전역화](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [세계화 및 지역화 애플리케이션](../ide/globalizing-and-localizing-applications.md)
