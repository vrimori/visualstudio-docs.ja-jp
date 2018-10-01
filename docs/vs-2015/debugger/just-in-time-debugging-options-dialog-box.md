---
title: Just-in-time で、デバッグ オプション ダイアログ ボックス |Microsoft Docs
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
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8675bc383a492f4d7ca762fa052a0e6174fe01bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537903"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>[Just-In-Time] ([オプション] ダイアログ ボックス - [デバッグ])
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Just ポイントイン タイムをデバッグするには、オプション ダイアログ ボックス](https://docs.microsoft.com/visualstudio/debugger/just-in-time-debugging-options-dialog-box)します。  
  
アクセスする、**ジャスト イン タイム** ページに移動して、**ツール**メニューをクリックします**オプション**します。 **オプション** ダイアログ ボックスで、展開、**デバッグ**ノード**ジャスト イン タイム**します。 このページでは、マネージド コード、ネイティブ コード、およびスクリプトでの Just-In-Time デバッグを有効にできます。 詳細については、次を参照してください。 [Just-In-Time デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)します。  
  
 Just-In-Time デバッグは次のプログラムの種類で有効です。  
  
-   マネージド  
  
-   ネイティブ  
  
-   スクリプト  
  
 Just-In-Time デバッグは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の外部で起動されたプログラムをデバッグするための手法です。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で作成されたプログラムを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境の外部で実行できます。 Just-In-Time デバッグを有効にすると、クラッシュの発生時に、デバッグを実行するかどうかを確認するダイアログ ボックスが表示されます。  
  
## <a name="associated-warnings"></a>関連する警告  
 このページにアクセスした場合、**オプション**ダイアログ ボックスで、このような警告メッセージが表示する場合があります。  
  
 **別のデバッガーが自体として登録時にだけデバッガー。修復するには、ジャストイン タイムをデバッグまたは Visual Studio の修復を実行を有効にします。**  
  
 このメッセージは、他のデバッガー (古いバージョンの [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デバッガーなど) が Just-In-Time デバッガーとして設定されている場合に表示されます。  
  
 次のメッセージが表示されることもあります。  
  
 **Just-in-time デバッグの登録エラーが検出されました。修復するには、ジャストイン タイムをデバッグまたは Visual Studio の修復を実行を有効にします。**  
  
 表示された場合、これらの警告のいずれかの Just ポイントイン タイムを使用したデバッグ[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]問題を解決するまでに管理者特権が必要です。 この場合、管理者以外の権限で Just-In-Time デバッグを有効にしようとすると、次のメッセージが表示されます。  
  
 **アクセスが拒否されました。管理者ジャスト イン タイムを有効にするデバッグ、または Visual Studio のインストールを修復します。**  
  
## <a name="see-also"></a>関連項目  
 [デバッグ オプション ダイアログ ボックス](../debugger/debugging-options-dialog-box.md)   
 [方法: デバッガー設定を指定する](../debugger/how-to-specify-debugger-settings.md)



