---
title: JavaScript 및 TypeScript
description: Mac용 Visual Studio의 JavaScript에 대한 지원 정보
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: d2ce3b3cdbf1a4cf1f19956a7327d73c0bb34b62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72807154"
---
# <a name="javascript-and-typescript-support"></a>JavaScript 및 TypeScript 지원

Mac용 Visual Studio에서는 구문 강조 표시, 코드 서식 지정 및 IntelliSense를 통해 JavaScript 및 TypeScript에 대한 지원을 제공합니다.

![typescript 편집기 지원](media/tsjseditor-2019.gif)

JavaScript 작성 방법에 대한 자세한 내용은 [JavaScript 코드 작성](/scripting/javascript/writing-javascript-code) 가이드를 참조하세요.

## <a name="adding-a-javascript-file"></a>JavaScript 파일 추가

JavaScript 파일은 주로 **새 파일** 대화 상자를 통해 ASP.NET Core 프로젝트에 추가됩니다. JavaScript 파일을 추가하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 파일**로 이동합니다.

![프로젝트에 새 파일 추가](media/javascript-image1.png)

**새 파일** 대화 상자에서 **웹 > 빈 JS 파일** 또는 **웹 > TypeScript 파일**을 선택합니다. 이름을 지정한 후 **새로 만들기**를 선택합니다.

![템플릿에서 새 typescript 파일 만들기](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Mac용 Visual Studio는 [JavaScript 언어 서비스](/visualstudio/ide/javascript-intellisense)를 사용하여 코드 작성 시 지능형 코드 완성 기능, 매개 변수 정보, 멤버 목록을 지원하는 IntelliSense를 제공합니다.

Mac용 Visual Studio의 JavaScript IntelliSense는 형식 유추, JSDoc 또는 TypeScript 선언을 기반으로 할 수 있습니다.

- **형식 유추** - 개체의 형식이 주변 코드 컨텍스트에 의해 결정됩니다. 자세한 내용은 Visual Studio의 [형식 유추 기반의 IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference) 관련 섹션을 참조하세요.
- **JSDoc** – 형식 유추가 올바른 형식 정보를 제공하지 않는 경우가 가끔 있습니다. 이 경우 [JSDoc](https://jsdoc.app/about-getting-started.html) 주석을 통해 형식 정보가 명시적으로 제공될 수 있습니다. 자세한 내용은 Visual Studio의 [JSDoc 기반의 IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) 관련 섹션을 참조하세요.
- **TypeScript 선언 파일** – JavaScript IntelliSense에 대한 값을 제공하기 위해 `.d.ts` 파일이 사용됩니다. 이 파일에 선언된 형식은 JSDoc 주석 형식으로 사용할 수 있습니다. 자세한 내용은 Visual Studio의 [TypeScript 선언 파일 기반의 IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) 섹션을 참조하세요.

    ![typescript 정의 파일 추가](media/javascript-type-intellisense-2019.gif)

## <a name="see-also"></a>참고 항목

- [JavaScript Intellisense(Windows의 Visual Studio)](/visualstudio/ide/javascript-intellisense)
