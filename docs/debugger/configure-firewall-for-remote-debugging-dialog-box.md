---
title: リモート デバッグ ダイアログ ボックスのファイアウォールの構成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a7346d9398ab9743319661efffdaf3f1f4b89b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018606"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>[リモート デバッグのファイアウォールの構成] ダイアログ ボックス
このダイアログ ボックスは、Windows ファイアウォールによってデバッガーがネットワーク経由で情報を受信できないときに表示されます。 リモート デバッグを続行するには、デバッガーが情報を受信できるようにファイアウォールに穴を開ける必要があります。  
  
> [!CAUTION]
>  ファイアウォールに穴を開けると、ファイアウォールによってセキュリティ上の脅威がブロックされなくなるため、コンピューターが脅威にさらされる可能性があります。 リモート デバッグのための穴を開けると、Visual Studio 2015 のポート 4020 と 4021 のブロックが解除されます。 その他のバージョンの Visual Studio では、他のポート番号を使用します。 詳細については、次を参照してください。 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)します。 また、デバッガーが追加のポートを開くことができるようになります。 詳細については、次を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)します。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **リモート デバッグを取り消す**  
 リモート デバッグをキャンセルします。 コンピューターのセキュリティ設定はそのままの状態で保持されます。  
  
 **ローカル ネットワーク (サブネット) 上のコンピューターからのリモート デバッグは制限しない**  
 ローカル サブネット上のコンピューターのリモート デバッグを有効にします。 これにより、ローカル サブネット上のコンピューターが脆弱になることがありますが、引き続きファイアウォールによってサブネットの外部から入ってくる情報がブロックされます。  
  
 **すべてのコンピューターからのリモート デバッグを制限しない**  
 ネットワーク上のすべての場所にあるコンピューターのリモート デバッグを有効にします。 この設定では、セキュリティが最も低くなります。  
  
## <a name="see-also"></a>関連項目
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [Remote Debugging](../debugger/remote-debugging.md)  
 [デバッグ用ユーザー インターフェイス リファレンス](../debugger/debugging-user-interface-reference.md)
