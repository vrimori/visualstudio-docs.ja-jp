---
title: '方法: ソース管理プラグインの互換性に関する警告をオフにする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e77bfb81df5b9c30ae6b99076480f8ff72cd27a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273508"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>方法: ソース管理プラグインの互換性に関する警告をオフにします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ソース管理を使用する場合、ユーザーはいくつかの互換性に関する警告を表示可能性があります[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 表示される警告は、ソース管理プラグインの機能に依存し、以下で説明として無効にすることができます。  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>警告を無効にする:"に、Visual Studio を使用した最適なソース管理の統合を確認します"  
  
-   次のレジストリ エントリ (必要な場合は、値を追加する) を設定します。  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001  
  
     すべての警告が表示されます以外[!INCLUDE[vsvss](../includes/vsvss-md.md)]プラグイン。  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>警告を無効にする:「インストールされているソース管理プロバイダーは、すべての機能 をサポートしていません」  
  
-   (必要な場合は、値を追加する)、次の 2 つのレジストリ値を設定します。  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider dword:00000000 を =  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001  
  
     ソース管理プラグインがサポートしない場合に明示的に再入の複数のプロジェクト (ファイルとプロジェクトの 1 つだけで、一度にことを確認できます) の場合は、この警告が表示されます。  
  
     再入をサポートすることをお勧め (`SCC_CAP_REENTRANT`機能)。 この警告は削除するされます。 ただし、このサポートができない場合、これらのレジストリ エントリを設定できます。  
  
## <a name="see-also"></a>関連項目  
 [機能フラグ](../extensibility/capability-flags.md)

