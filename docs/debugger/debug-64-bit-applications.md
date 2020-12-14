---
title: 64비트 애플리케이션 디버그 | Microsoft Docs
description: Visual Studio를 사용하여 64비트 애플리케이션을 디버그하는 방법을 알아봅니다. 예기치 않은 디버깅 지연 문제를 해결하기 위한 팁이 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29deb50bb57f018d3031ed1065145b6a39abab67
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560449"
---
# <a name="debug-64-bit-applications"></a>64비트 애플리케이션 디버그
로컬 컴퓨터나 원격 컴퓨터에서 실행되는 64비트 애플리케이션을 디버깅할 수 있습니다.

 원격 컴퓨터에서 실행되는 64비트 애플리케이션을 디버그하려면 [Remote Debugging](../debugger/remote-debugging.md)항목을 참조하세요.

 로컬에서 64비트 애플리케이션을 디버그하기 위해 Visual Studio는 64비트 작업자 프로세스(msvsmon.exe)를 사용하여 32비트 Visual Studio 프로세스에서는 수행할 수 없는 하위 수준 작업을 수행합니다.

 .NET Framework 3.5 또는 이전 버전을 사용하는 64비트 프로세스의 경우 혼합 모드 디버깅이 지원되지 않습니다.

## <a name="debug-a-64-bit-application"></a>64비트 애플리케이션 디버그
 64비트 애플리케이션 디버그를 시도하려면

1. Visual Studio 솔루션(예: C# 콘솔 애플리케이션)을 만듭니다.

2. Configuration Manager를 사용하여 구성을 64비트로 설정합니다. 자세한 내용은 [방법: 플랫폼을 대상으로 한 프로젝트 구성](../ide/how-to-configure-projects-to-target-platforms.md)을 참조하세요.

3. 이때 64비트 버전의 원격 디버거(msvsmon.exe)가 시작됩니다. 64비트 구성을 사용하는 솔루션이 열려 있으면 디버거가 실행됩니다.

4. 디버깅을 시작합니다. 사용자 환경은 32비트 구성과 동일합니다. 오류가 발생할 경우 아래의 문제 해결 섹션을 참조하세요.

## <a name="troubleshooting-64-bit-debugging"></a>64비트 디버깅 문제 해결
 다음 오류가 표시될 수 있습니다. “64비트 디버깅 작업이 예상보다 오래 걸리고 있습니다.” 이 경우 Visual Studio에서 64비트 버전의 msvsmon.exe로 요청을 보냈으며, 해당 요청의 결과가 반환되는 데 오랜 시간이 걸렸습니다.

 이 오류의 주요 원인으로는 다음 두 가지가 있습니다.

- 컴퓨터에 설치된 네트워킹 보안 소프트웨어로 인해 네트워킹 스택이 불안정하며 localhost를 통과하는 패킷이 삭제되었습니다. 모든 네트워크 보안 소프트웨어를 사용하지 않도록 설정하고 문제가 해결되는지 확인합니다. 이 방법으로 문제가 해결되면 소프트웨어가 localhost 트래픽을 방해한다고 네트워크 보안 소프트웨어 공급업체에 신고합니다.

- Visual Studio가 응답하지 않는 문제나 다른 성능 문제가 발생하고 있습니다. 문제가 주기적으로 발생하는 경우 Visual Studio(devenv.exe) 및 작업자 프로세스(msvsmon.exe)의 덤프를 수집하여 Microsoft로 보낼 수 있습니다. 문제를 신고하는 방법에 대한 자세한 내용은 [How to Report a Problem with Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)항목을 참조하세요.

## <a name="see-also"></a>참조

- [64비트 애플리케이션](/dotnet/framework/64-bit-apps)
- [64비트용 프로그램 구성](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Visual Studio IDE 64비트 지원](../ide/visual-studio-ide-64-bit-support.md)
- [덤프 파일 사용](../debugger/using-dump-files.md)
- [Remote Debugging](../debugger/remote-debugging.md)