---
title: リモート デバッグ ダイアログ ボックスのファイアウォールの構成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e53e4573de1fb80d33b387e97b6ddd23b54bbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548938"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>[リモート デバッグのファイアウォールの構成] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[リモート デバッグ ダイアログ ボックスのファイアウォールの構成](https://docs.microsoft.com/visualstudio/debugger/configure-firewall-for-remote-debugging-dialog-box)します。  
  
このダイアログ ボックスは、Windows ファイアウォールによってデバッガーがネットワーク経由で情報を受信できないときに表示されます。 リモート デバッグを続行するには、デバッガーが情報を受信できるようにファイアウォールに穴を開ける必要があります。  
  
> [!CAUTION]
>  ファイアウォールに穴を開けると、ファイアウォールによってセキュリティ上の脅威がブロックされなくなるため、コンピューターが脅威にさらされる可能性があります。 リモート デバッグのための穴を開けると、Visual Studio 2015 のポート 4020 と 4021 のブロックが解除されます。 その他のバージョンの Visual Studio では、他のポート番号を使用します。 詳細については、次を参照してください。 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)します。 また、デバッガーが追加のポートを開くことができるようになります。 詳細については、次を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)します。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **リモート デバッグを取り消す**  
 リモート デバッグをキャンセルします。 コンピューターのセキュリティ設定はそのままの状態で保持されます。  
  
 **ローカル ネットワーク (サブネット) 上のコンピューターからのリモート デバッグをブロック解除します。**  
 ローカル サブネット上のコンピューターのリモート デバッグを有効にします。 これにより、ローカル サブネット上のコンピューターが脆弱になることがありますが、引き続きファイアウォールによってサブネットの外部から入ってくる情報がブロックされます。  
  
 **任意のコンピューターからのリモート デバッグをブロック解除します。**  
 ネットワーク上のすべての場所にあるコンピューターのリモート デバッグを有効にします。 この設定では、セキュリティが最も低くなります。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバイスのリモート ツールをセットアップします。](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [デバッグ用ユーザー インターフェイス リファレンス](../debugger/debugging-user-interface-reference.md)



