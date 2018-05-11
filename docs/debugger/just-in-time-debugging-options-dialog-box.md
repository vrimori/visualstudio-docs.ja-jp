---
title: Just-in-time、デバッグ オプション ダイアログ ボックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7be7dacbe7b3b89b8bdc09515c23d7597e7e55e5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="just-in-time-debugging-options-dialog-box"></a>[Just-In-Time] ([オプション] ダイアログ ボックス - [デバッグ])
アクセスする、**ジャスト イン タイム** ページに移動して、**ツール**メニューをクリックして**オプション**です。 **オプション** ダイアログ ボックスで、展開、**デバッグ**ノード**ジャスト イン タイム**です。 このページでは、マネージ コード、ネイティブ コード、およびスクリプトでの Just-In-Time デバッグを有効にできます。 詳細については、次を参照してください。 [Just-In-Time デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)です。  
  
 Just-In-Time デバッグは次のプログラムの種類で有効です。  
  
-   マネージ  
  
-   ネイティブ  
  
-   スクリプト  
  
 Just-In-Time デバッグは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で起動されたプログラムをデバッグするための手法です。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で作成されたプログラムを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境の外部で実行できます。 Just-In-Time デバッグを有効にすると、クラッシュの発生時に、デバッグを実行するかどうかを確認するダイアログ ボックスが表示されます。  
  
## <a name="associated-warnings"></a>関連する警告  
 このページにアクセスすると、**オプション**ダイアログ ボックスで、次のように警告メッセージを表示する場合があります。  
  
 **別のデバッガーは、ジャスト イン タイムのようを登録したデバッガーです。修復するには、ジャスト イン タイムのデバッグまたは Visual Studio の修復を実行を有効にします。**  
  
 このメッセージは、他のデバッガー (古いバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーなど) が Just-In-Time デバッガーとして設定されている場合に表示されます。  
  
 次のメッセージが表示されることもあります。  
  
 **Just-in-time デバッグの登録エラーが検出されました。修復するには、ジャスト イン タイムのデバッグまたは Visual Studio の修復を実行を有効にします。**  
  
 表示される場合、これらの警告のいずれかの時点でのみでデバッグ[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]問題を解決するまで、管理者特権が必要です。 この場合、管理者以外の権限で Just-In-Time デバッグを有効にしようとすると、次のメッセージが表示されます。  
  
 **アクセスが拒否されました。デバッグしておくことを管理者ジャスト イン タイムを有効にする、または Visual Studio のインストールを修復します。**  
  
## <a name="see-also"></a>関連項目  
 [デバッグ オプション ダイアログ ボックス](../debugger/debugging-options-dialog-box.md)   
 [方法: デバッガー設定を指定する](../debugger/how-to-specify-debugger-settings.md)