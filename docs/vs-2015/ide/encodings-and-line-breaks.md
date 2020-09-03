---
title: 인코딩 및 줄 바꿈 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2e1b13cc101ea4d7609633fd9c11bf87946d7b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665731"
---
# <a name="encodings-and-line-breaks"></a>인코딩 및 줄 바꿈
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 **파일/고급 저장 옵션** 설정을 사용하여 원하는 줄 바꿈 문자의 형식을 결정할 수 있습니다. 같은 설정을 사용하여 파일의 인코딩을 변경할 수도 있습니다.

> [!NOTE]
> 특정 형식의 개발 설정(Visual Basic, F#, 웹 개발)이 있는 경우 메뉴에서 **고급 저장 옵션**을 확인할 수 없습니다. 설정(예: 일반)을 변경하려면 **도구/설정 가져오기 및 내보내기**를 엽니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

 Visual Studio에서 다음 문자는 줄 바꿈으로 해석됩니다.

- CRLF: 캐리지 리턴 + 줄 바꿈, 유니코드 문자 000D + 000A

- LF: 줄 바꿈, 유니코드 문자 000A

- NEL: 다음 줄, 유니코드 문자 0085

- LS: 줄 구분 기호, 유니코드 문자 2028

- PS: 단락 구분 기호, 유니코드 문자 2029

  다른 애플리케이션에서 복사되는 텍스트는 원래 인코딩 및 줄 바꿈 문자를 유지합니다. 예를 들어 메모장에서 텍스트를 복사하고 Visual Studio의 텍스트 파일로 붙여넣으면 텍스트에는 메모장의 텍스트와 같은 설정이 포함됩니다.

  다른 줄 바꿈 문자가 포함된 파일을 열 경우 일치하지 않는 줄 바꿈 문자를 정규화할지 여부 및 선택할 줄 바꿈 형식을 묻는 대화 상자가 표시될 수 있습니다.
