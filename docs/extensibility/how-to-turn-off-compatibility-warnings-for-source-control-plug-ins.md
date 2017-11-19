---
title: "ソース管理プラグインの互換性に関する警告をオフにする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93db7526e7d6ba3eccf86e8c9769a1d9e9af3519
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>方法: ソース管理プラグインの互換性に関する警告をオフにします。
ソース管理を使用する場合、ユーザーはいくつかの互換性に関する警告を表示可能性があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 表示される警告は、ソース管理プラグインの機能に依存し、以下で説明として無効にすることができます。  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>警告を無効にする: する最適なソース管理の統合で Visual Studio」  
  
-   次のレジストリ エントリ (必要な場合は、値を追加する) を設定します。  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001  
  
     すべての警告が表示されます以外[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]プラグインします。  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>警告を無効にします"インストールされているソース管理プロバイダーは、すべての機能 をサポートしていません"。  
  
-   (必要な場合は、値を追加する)、次の 2 つのレジストリ値を設定します。  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider dword:00000000 を =  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001  
  
     ソース管理プラグインは明示的に再入をサポート複数のプロジェクトに (一度にファイルとプロジェクトの 1 つだけで、確認できます) の場合は、この警告が表示されます。  
  
     再入をサポートすることをお勧め (`SCC_CAP_REENTRANT`機能) です。 この警告が削除するされます。 ただし、このサポートが可能でない場合、これらのレジストリ エントリを設定できます。  
  
## <a name="see-also"></a>関連項目  
 [機能フラグ](../extensibility/capability-flags.md)