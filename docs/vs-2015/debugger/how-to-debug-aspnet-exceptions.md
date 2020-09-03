---
title: '방법: ASP.NET 예외 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ccd8c399bd92bd98307d44aff913c30390033c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205432"
---
# <a name="how-to-debug-aspnet-exceptions"></a>방법: ASP.NET 예외 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

예외 디버깅은 강력한 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 개발하는 데 중요한 요소입니다. 예외를 디버그하는 방법에 관한 일반적인 내용은 [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)를 참조하세요.  
  
 처리되지 않은 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 예외를 디버깅하려면 디버거에서 실행을 중지해야 합니다. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 런타임에는 최상위 예외 처리기가 있습니다. 따라서 디버거는 처리되지 않은 예외에서 기본적으로 중단되지 않습니다. 예외가 throw될 경우 중단하고 디버거를 시작하려면 **다음 예외가 발생할 경우 중단: Throw됨** 설정을 **예외** 대화 상자에서 특정 예외에 대해 선택해야 합니다.  
  
 내 코드만 옵션을 설정한 경우 **다음 예외가 발생할 경우 중단: Throw됨**을 사용하면 .NET Framework 메서드 또는 다른 시스템 코드에서 예외가 throw되는 즉시 디버거에서 실행을 중단하지 않습니다. 이러한 경우 디버거의 실행은 비시스템 코드를 적중해야 중단됩니다. 그러므로 예외가 발생할 때 시스템 코드를 단계별로 수행할 필요가 없습니다.  
  
 내 코드만 옵션을 사용할 경우 더 유용한 다른 옵션인 **다음 예외가 발생할 경우 중단: 사용자가 처리하지 않음**도 사용할 수 있습니다. 예외에 대해 이 설정을 선택하면 디버거는 사용자 코드에서 예외를 catch하여 처리하지 않는 경우에 한해서만 사용자 코드에서 실행을 중단합니다. 이렇게 설정할 경우 최상위 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 예외 처리기가 사용자가 작성하지 않은 코드에 있기 때문에 해당 처리기의 결과가 무시됩니다.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>내 코드만 옵션을 사용하여 ASP.NET 예외 디버깅을 설정하려면  
  
1. **디버그** 메뉴에서 **예외**를 클릭합니다.  
  
     **예외** 대화 상자가 표시됩니다.  
  
2. **Common Language Runtime Exceptions** 행에서 **Throw**되거나 **사용자가 처리하지 않음**을 선택합니다.  
  
     **사용자가 처리하지 않음** 설정을 사용하려면 **내 코드만**을 사용하도록 설정해야 합니다.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>최상의 방법으로 ASP.NET 예외 처리를 수행하려면  
  
- 예측 가능하며 처리 방법을 알고 있는 예외를 throw할 수 있는 코드의 바깥쪽에 `try … catch` 블록을 배치합니다. 예를 들어 응용 프로그램에서 XML Web Services를 호출 하거나 SQL Server에 직접 호출 하는 경우 해당 코드는 **try ... catch** 블록은 발생할 수 있는 많은 예외를 발생 시킬 수 있습니다.
