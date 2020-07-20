---
title: 진단 데이터 및 시스템에서 생성된 로그
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f3774a816ca31bfcdd4013d35dadbb1737e5ab
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387254"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio에서 수집한 시스템에서 생성된 로그

Visual Studio는 [Visual Studio 사용자 환경 개선 프로그램](visual-studio-experience-improvement-program.md)을 통해 문제를 해결하고 제품의 품질을 향상시키기 위해 시스템에서 생성된 로그를 수집합니다. 이 문서에서는 어떤 유형의 데이터가 수집되고 어떻게 사용되는지에 대한 몇 가지 정보를 제공합니다. 확장 프로그램 작성자가 실수로 개인 정보나 중요한 정보를 노출하지 않도록 하는 방법에 대한 팁도 제공합니다.

## <a name="types-of-collected-data"></a>수집되는 데이터의 유형

Visual Studio에서는 크래시, UI 응답 없음 및 높은 CPU 또는 메모리 사용량에 대해 시스템에서 생성된 로그를 수집합니다. 제품 설치 또는 사용 중 발생하는 오류에 대한 정보도 수집합니다. 수집되는 데이터는 오류에 따라 다르며, 스택 추적, 메모리 덤프 및 예외 정보를 포함할 수 있습니다.

- CPU 사용량이 많고 응답이 없는 경우 관련 Visual Studio 스레드의 스택 추적이 수집됩니다.

- 일부 스레드의 스택 추적으로 문제의 근본 원인(예: 크래시, 응답 없음 또는 높은 메모리 사용량)을 확인할 수 없는 경우 메모리 ‘덤프’를 수집합니다. 덤프는 오류가 발생한 프로세스의 상태를 나타냅니다.

- 디스크의 파일에 쓰려고 시도하는 중에 발생한 오류와 같은 예기치 않은 오류 상황이 발생한 경우 예외에 대한 정보를 수집합니다. 정보에는 예외의 이름, 예외가 발생한 스레드의 스택 추적, 예외와 관련된 메시지 및 특정 예외와 관련된 기타 정보가 포함됩니다.

   다음과 같은 수집된 데이터의 예에서는 예외 이름, 스택 추적 및 예외 메시지를 보여 줍니다.

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>시스템에서 생성된 로그 사용 방법

오류의 근본 원인을 확인하는 워크플로는 오류 유형 및 심각도에 따라 달라집니다.

### <a name="error-classification"></a>오류 분류

로그에 따라 오류를 분류하고 계산하여 조사의 우선 순위를 지정합니다. 예를 들어 “System.IO.FileStream.Init”의 “System.IO.\__Error.WinIOError”가 \<x> 버전의 제품에서 500번 발생했으며 해당 버전에서 발생률이 가장 높은 경우가 있습니다.

### <a name="work-items-for-tracking"></a>추적할 작업 항목

우선 순위가 지정된 개별 오류에 대한 작업 항목이 생성되고 조사를 위해 엔지니어에게 할당됩니다. 이러한 작업 항목에는 일반적으로 오류 유형과 관련된 분류, 우선 순위 및 진단 정보가 포함됩니다. 이 정보는 오류에 대해 수집된 시스템 생성 로그에서 파생됩니다. 예를 들어 크래시에 대한 작업 항목에는 크래시가 발생하는 스택 추적이 포함될 수 있습니다.

### <a name="error-investigation"></a>오류 조사

엔지니어는 작업 항목에서 사용 가능한 정보를 사용하여 오류의 근본 원인을 확인합니다. 작업 항목에 있는 것보다 더 많은 정보가 필요한 경우가 있습니다. 이 경우 수집된 원래의 시스템 생성 로그를 참조합니다. 예를 들어 엔지니어는 제품 크래시를 파악하기 위해 메모리 덤프를 검사할 수 있습니다.

## <a name="tips-for-extension-authors"></a>확장 프로그램 작성자를 위한 팁

확장 프로그램 작성자는 해당 모듈, 유형 및 메서드 이름에 개인 정보 또는 기타 민감한 정보를 사용하지 않음으로써 개인 정보 노출을 제한해야 합니다. 스택의 해당 코드에서 크래시 또는 유사한 오류 조건이 발생하면 해당 정보가 시스템에서 생성된 로그의 일부로 수집됩니다.

## <a name="opt-out-of-data-collection"></a>데이터 수집 옵트아웃

데이터 수집 목적과 데이터의 액세스 및 보존에 대한 제약 조건을 고려할 때 Visual Studio 및 Windows의 기본 개인 정보 설정을 사용하는 것이 좋습니다. 그러나 Visual Studio 환경 개선 프로그램을 [옵트아웃](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out)할 수 있습니다. 모든 프로그램에 대해 시스템에서 생성된 로그 수집을 옵트아웃하려면 [Windows 10의 진단, 피드백 및 개인 정보](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)를 참조하세요. 옵션은 사용 중인 Windows 버전에 따라 달라질 수 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio 사용자 환경 개선 프로그램](visual-studio-experience-improvement-program.md)
- [Windows 10의 진단, 피드백 및 개인 정보](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)