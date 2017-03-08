---
title: "ヘルプ コンテンツ マネージャーのオーバーライド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e8657d2ff12e911286fd120d3d19e16aed838db6
ms.lasthandoff: 02/22/2017

---
# <a name="help-content-manager-overrides"></a>ヘルプ コンテンツ マネージャーのオーバーライド
レジストリを変更することで、Visual Studio IDE のヘルプ ビューアーとヘルプ関連の機能の既定の動作を変更できます。  
  
|タスク|レジストリ キー|値と定義|  
|----------|------------------|--------------------------|  
|一意のサービス エンドポイントを定義する|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService: *HTTPValueForTheServiceEndpoint*。|  
|オンラインまたはオフラインの既定を定義する|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp: ローカル ヘルプを指定するには `0`、オンライン ヘルプを指定するには `1` を入力します。|  
|一意の F1 エンドポイントを定義する|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl: *HTTPValueForTheServiceEndpoint*|  
|Override BITS ジョブの優先順位をオーバーライドする|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (64-bit コンピューターの場合)\Microsoft\Help\v2.2|BITSPriority: **foreground**、**high**、**normal**、**low** のいずれかの値を使います。|  
|オンライン (および IDE オンライン オプション) を無効にする|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (64 ビット コンピューターの場合)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled: オンライン ヘルプ コンテンツへのアクセスを無効にするには 1 を設定します。|  
|コンテンツの管理を無効にする|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (64 ビット コンピューターの場合)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled: ヘルプ ビューアーの **[コンテンツの管理]** タブを無効にするには 1 を設定します。|  
|ネットワーク共有上のローカル コンテンツ ストアを指定する|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|  
|Visual Studio 機能の最初の起動時にコンテンツのインストールを無効にする。|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (64 ビット コンピューターの場合)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection: Visual Studio の最初の開始時に構成されるヘルプ機能を無効にするには 1 を設定します。|  
  
## <a name="see-also"></a>関連項目  
 [ヘルプ ビューアーの管理者ガイド](../ide/help-viewer-administrator-guide.md)
