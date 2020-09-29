---
title: 스냅샷 디버깅 FAQ | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8afc67b92a943dd571847bb1a00fb7e4db4514b
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851101"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Visual Studio의 스냅샷 디버깅에 대해 자주 묻는 질문

다음은 스냅샷 디버거를 사용하여 라이브 Azure 애플리케이션을 디버그할 때 나올 수 있는 질문 목록입니다.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>스냅샷 생성 시 어떤 성능 저하가 발생하나요?

스냅샷 디버거는 앱의 스냅샷을 캡처할 때 앱 프로세스를 포크하고 포크된 복사본을 일시중단합니다. 스냅샷을 디버그하는 경우 포크된 프로세스 복사본에 대해 디버그합니다. 이 프로세스는 10~20밀리초밖에 안 걸리지만 앱의 전체 힙을 복사하지는 않습니다. 페이지 테이블만 복사하고 페이지를 쓰기 작업 중 복사하도록 설정합니다. 힙의 앱 개체 중 일부가 변경되면 해당 페이지가 복사됩니다. 따라서 각 스냅샷은 메모리 내 비용을 적은 양만 차지합니다(대부분 앱의 경우 대략 수백 킬로바이트).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>확장형 Azure App Service(내 앱의 인스턴스가 여러 개)가 있는 경우는 어떻게 되나요?

앱 인스턴스가 여러 개인 경우 모든 단일 인스턴스에 snappoint가 적용됩니다. 지정된 조건으로 적중된 첫 번째 snappoint만 스냅샷을 만듭니다. snappoint가 여러 개인 경우 이후의 스냅샷은 첫 번째 스냅샷을 만든 인스턴스와 동일한 인스턴스에서 가져옵니다. 출력 창으로 보낸 logpoint는 한 인스턴스의 메시지만 보여 주는 반면, 애플리케이션 로그로 보낸 logpoint는 모든 인스턴스의 메시지를 보냅니다.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>스냅샷 디버거가 기호를 로드하는 방법은 무엇인가요?

스냅샷 디버거를 사용하려면 로컬 또는 Azure App Service에 배포된 애플리케이션에 대해 일치하는 기호가 있어야 합니다. (포함 PDB는 현재 지원되지 않습니다.) 스냅샷 디버거는 자동으로 Azure App Service에서 기호를 다운로드합니다. Visual Studio 2017 버전 15.2부터 Azure App Service에 배포하는 경우 앱의 기호도 배포합니다.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>스냅샷 디버거가 내 애플리케이션의 릴리스 빌드에 대해 작동하나요?

예, 스냅샷 디버거는 릴리스 빌드에 대해 작동하도록 설계되었습니다. snappoint가 함수에 배치되면 해당 함수가 디버그 버전으로 다시 컴파일되어 디버그할 수 있게 됩니다. 스냅샷 디버거를 중지하면 해당 릴리스 빌드 버전에 대해 함수를 반환합니다.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>logpoint가 내 프로덕션 애플리케이션에서 부작용을 일으킬 수 있나요?

아니요, 앱에 추가하는 모든 로그 메시지는 가상으로 평가됩니다. 애플리케이션에서 어떠한 부작용도 일으킬 수 없습니다. 하지만 일부 네이티브 속성은 logpoint로 액세스할 수 없습니다.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>내 서버가 로드 중인 경우 스냅샷 디버거가 작동하나요?

예, 로드 중인 서버에 대해 스냅샷 디버깅이 작동할 수 있습니다. 스냅샷 디버거는 서버에 사용 가능한 메모리가 적은 상황에서는 스냅샷을 제한하고 캡처하지 않습니다.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>스냅샷 디버거를 제거하는 방법은 무엇인가요?

다음 단계를 사용하여 App Service에서 스냅샷 디버거 사이트 확장을 제거할 수 있습니다.

1. Visual Studio 또는 Azure Portal에서 클라우드 탐색기를 통해 App Service를 끕니다.
1. App Service의 Kudu 사이트(즉, yourappservice.**scm**.azurewebsites.net)로 이동한 후 **사이트 확장**으로 이동합니다.
1. 스냅샷 디버거 사이트 확장에서 X를 클릭하여 제거합니다.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>스냅샷 디버거 세션 중에 포트가 열려 있는 이유는 무엇인가요?

Azure에서 생성된 스냅샷을 디버그하려면 스냅샷 디버거에서 일련의 포트를 열어야 하며 이러한 포트는 원격 디버깅에 필요한 포트와 동일합니다. [여기에서 포트 목록을 찾을 수 있습니다](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>원격 디버거 확장을 사용하지 않도록 설정하려면 어떻게 해야 하나요??

App Services:
1. Azure Portal을 통해 App Service의 원격 디버거 확장을 사용하지 않도록 설정합니다.
2. Azure Portal > 애플리케이션 서비스 리소스 블레이드 > ‘애플리케이션 설정’
3. ‘디버깅’ 섹션으로 이동하고 ‘원격 디버깅’에 대해 ‘끄기’ 단추를 클릭합니다.  

AKS:
1. Dockerfile을 업데이트하여 [Docker 이미지에서 Visual Studio 스냅샷 디버거](https://github.com/Microsoft/vssnapshotdebugger-docker)에 해당하는 섹션을 제거합니다.
2. 수정된 Docker 이미지를 다시 빌드하고 다시 배포합니다.

가상 머신/가상 머신 확장 집합의 경우 다음과 같이 원격 디버거 확장, 인증서, KeyVault 및 인바운드 NAT 풀을 제거합니다.

1. 원격 디버거 확장 제거

   가상 머신 및 가상 머신 확장 집합의 원격 디버거를 사용하지 않도록 설정하는 방법에는 여러 가지가 있습니다.

      - 클라우드 탐색기를 통해 원격 디버거를 사용하지 않도록 설정

         - 클라우드 탐색기 > 가상 머신 리소스 > 디버깅 사용 안 함(클라우드 탐색기에서 가상 머신 확장 집합에 디버깅을 사용하지 않도록 설정하는 기능이 없음).

      - PowerShell 스크립트/Cmdlet을 사용하여 원격 디버거를 사용하지 않도록 설정

         가상 머신:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         가상 머신 확장 집합:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Azure Portal을 통해 원격 디버거를 사용하지 않도록 설정
         - Azure Portal > 가상 머신/가상 머신 확장 집합 리소스 블레이드 > 확장
         - Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger 확장 제거

         > [!NOTE]
         > 가상 머신 확장 집합 - 포털에서 DebuggerListener 포트 제거를 허용하지 않습니다. Azure PowerShell을 사용해야 합니다. 자세한 내용은 다음을 참조하십시오.

2. 인증서 및 Azure KeyVault 제거

   가상 머신 또는 가상 머신 확장 집합의 원격 디버거 확장을 설치하는 경우 Azure 가상 머신/가상 머신 확장 집합 리소스를 사용하여 Visual Studio 클라이언트를 인증하기 위해 클라이언트 인증서와 서버 인증서가 둘 다 생성됩니다.

   - 클라이언트 인증서

      Cert:/CurrentUser/My/에 있는 자체 서명된 인증서입니다.

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      PowerShell을 통해 머신에서 이 인증서를 제거할 수 있습니다.

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - 서버 인증서
      - 해당 서버 인증서 지문은 Azure KeyVault에 비밀로 배포됩니다. Visual Studio는 가상 머신 또는 가상 머신 확장 집합 리소스에 해당하는 지역에서 접두사 MSVSAZ*를 사용하여 KeyVault를 찾거나 만들려고 시도합니다. 따라서 해당 지역에 배포된 모든 가상 머신 또는 가상 머신 확장 집합 리소스는 동일한 KeyVault를 공유합니다.
      - 서버 인증서 지문 비밀을 삭제하려면 Azure Portal로 이동하고 리소스를 호스트하는 동일한 지역에서 MSVSAZ* KeyVault를 찾습니다. `remotedebugcert<<ResourceName>>` 레이블이 지정된 비밀을 삭제합니다.
      - 또한 PowerShell을 통해 리소스에서 서버 비밀을 삭제해야 합니다.

      가상 머신:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      가상 머신 확장 집합:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. 모든 DebuggerListener 인바운드 NAT 풀 제거(가상 머신 확장 집합에만 해당)

   원격 디버거는 확장 집합의 부하 분산 장치에 적용되는 DebuggerListener 인바운드 NAT 풀을 도입합니다.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>스냅샷 디버거를 사용하지 않도록 설정하려면 어떻게 해야 하나요?

App Service:
1. Azure Portal을 통해 App Service의 스냅샷 디버거를 사용하지 않도록 설정합니다.
2. Azure Portal > 애플리케이션 서비스 리소스 블레이드 > ‘애플리케이션 설정’
3. Azure Portal에서 다음 앱 설정을 삭제하고 변경 내용을 저장합니다.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > 애플리케이션 설정이 변경되면 앱이 다시 시작됩니다. 애플리케이션 설정에 관한 자세한 내용은 [Azure Portal에서 App Service 앱 구성](/azure/app-service/web-sites-configure)을 참조하세요.

AKS:
1. Dockerfile을 업데이트하여 [Docker 이미지에서 Visual Studio 스냅샷 디버거](https://github.com/Microsoft/vssnapshotdebugger-docker)에 해당하는 섹션을 제거합니다.
2. 수정된 Docker 이미지를 다시 빌드하고 다시 배포합니다.

가상 머신/가상 머신 확장 집합:

스냅샷 디버거를 사용하지 않도록 설정하는 방법에는 여러 가지가 있습니다.
- 클라우드 탐색기 > 가상 머신/가상 머신 확장 집합 리소스 > 진단 사용 안 함

- Azure Portal > 가상 머신/가상 머신 확장 집합 리소스 블레이드 > 확장 > Microsoft.Insights.VMDiagnosticsSettings 확장 제거

- [Az PowerShell](/powershell/azure/overview)의 PowerShell Cmdlet

   가상 머신:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   가상 머신 확장 집합:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>참조

- [Visual Studio의 디버깅](../debugger/index.yml)
- [스냅샷 디버거를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)
- [스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Virtual Machines\Virtual Machines Scale Sets 디버그](../debugger/debug-live-azure-virtual-machines.md)
- [스냅샷 디버거를 사용하여 라이브 ASP.NET Azure Kubernetes 디버그](../debugger/debug-live-azure-kubernetes.md)
- [스냅샷 디버깅에 대한 문제 해결 및 알려진 문제](../debugger/debug-live-azure-apps-troubleshooting.md)
