---
title: ソース管理プラグインの互換性に関する警告をオフにする |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d90ab2553eb69a5ea429dec3848c2aecd5fa86a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978803"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>方法: ソース管理プラグインの互換性に関する警告をオフにします。
ソース管理を使用する場合、ユーザーはいくつかの互換性に関する警告を表示可能性があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 表示される警告は、ソース管理プラグインの機能に依存し、以下で説明として無効にすることができます。  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>警告を無効にします。Visual Studio での最適なソース管理の統合を確認するには"するには」  
  
- 次のレジストリ エントリ (必要な場合は、値を追加する) を設定します。  
  
   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**  
  
   すべての警告が表示されます以外[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]プラグイン。  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>警告を無効にします。「インストールされているソース管理プロバイダーは、すべての機能をサポートしていません」  
  
-   (必要な場合は、値を追加する)、次の 2 つのレジストリ値を設定します。  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**  
  
    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**  
  
     ソース管理プラグインがサポートしない場合に明示的に再入の複数のプロジェクト (ファイルとプロジェクトの 1 つだけで、一度にことを確認できます) の場合は、この警告が表示されます。  
  
     再入をサポートすることをお勧め (`SCC_CAP_REENTRANT`機能)。 この警告は削除するされます。 ただし、このサポートができない場合、これらのレジストリ エントリを設定できます。  
  
## <a name="see-also"></a>関連項目  
 [機能フラグ](../extensibility/capability-flags.md)