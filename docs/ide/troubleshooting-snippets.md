---
title: 코드 조각 문제 해결
description: 조각 파일의 잘못된 내용이나 손상된 조각 파일에 의해 일반적으로 발생하는 IntelliSense 코드 조각 문제를 해결하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4012298bdc4edf0c174576c739e67781bfffdade
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479188"
---
# <a name="troubleshoot-snippets"></a>코드 조각 문제 해결

IntelliSense 코드 조각 문제는 코드 조각 파일이 손상되었거나 코드 조각 파일에 잘못된 내용이 있는 등 일반적으로 두 가지 문제로 인해 발생합니다.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>코드 조각은 파일 탐색기에서 Visual Studio 소스 파일로 끌어올 수 없습니다.

- 코드 조각 파일의 XML은 손상되었을 수 있습니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 **XML 편집기** 는 XML 구조에서 문제를 찾을 수 있습니다.

- 코드 조각 파일은 코드 조각 스키마를 준수하지 않을 수 있습니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 **XML 편집기** 는 XML 구조에서 문제를 찾을 수 있습니다.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>코드에는 강조 표시되지 않는 컴파일러 오류가 있습니다.

- 프로젝트 참조를 누락했을 수 있습니다. 코드 조각에 대한 설명서를 검토합니다. 참조가 컴퓨터에 없는 경우 설치해야 합니다. 코드 조각을 삽입하려면 필요한 참조를 프로젝트에 추가해야 합니다. 코드 조각이 참조 정보를 누락한 경우 코드 조각 생성자에 오류로 보고될 수 있습니다.

- 변수는 정의되지 않을 수 있습니다. 코드 조각에서 정의되지 않은 변수는 강조 표시해야 합니다. 그렇지 않으면 코드 조각 작성자에 오류로 보고될 수 있습니다.

## <a name="see-also"></a>참고 항목

- [코드 조각](../ide/code-snippets.md)
