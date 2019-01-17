---
title: Just-in-time で、デバッグ オプション ダイアログ ボックス |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 05a1cc9e4847b9ffa2c873b137c35bfbf6f83f83
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968116"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>[Just-In-Time] ([オプション] ダイアログ ボックス - [デバッグ])
**[Just-In-Time]** ページを使用するには、**[ツール]** メニューの **[オプション]** をクリックします。 **[オプション]** ダイアログ ボックスの **[デバッグ]** ノードを展開し、**[Just-In-Time]** をクリックします。 このページでは、マネージド コード、ネイティブ コード、およびスクリプトでの Just-In-Time デバッグを有効にできます。 詳細については、「[Just-In-Time デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)」を参照してください。  
  
 Just-In-Time デバッグは次のプログラムの種類で有効です。  
  
- マネージド  
  
- ネイティブ  
  
- スクリプト  
  
  Just-In-Time デバッグは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で起動されたプログラムをデバッグするための手法です。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で作成されたプログラムを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 環境の外部で実行できます。 Just-In-Time デバッグを有効にすると、クラッシュの発生時に、デバッグを実行するかどうかを確認するダイアログ ボックスが表示されます。  
  
## <a name="associated-warnings"></a>関連する警告  
 **[オプション]** ダイアログ ボックスでこのページを開いたときに、次のような警告メッセージが表示される場合があります。  
  
 **別のデバッガーが Just-In-Time デバッガーとして登録されています。修復するには、Just-In-Time デバッグを有効にするか、または Visual Studio の修復を実行してください。**  
  
 このメッセージは、他のデバッガー (古いバージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーなど) が Just-In-Time デバッガーとして設定されている場合に表示されます。  
  
 次のメッセージが表示されることもあります。  
  
 **Just-In-Time デバッグの登録エラーが検出されました。修復するには、Just-In-Time デバッグを有効にするか、または Visual Studio の修復を実行してください。**  
  
 これらの警告のいずれかが表示されている場合、問題が解決されるまでの間、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] で Just-In-Time デバッグを行うには管理者特権が必要になります。 この場合、管理者以外の権限で Just-In-Time デバッグを有効にしようとすると、次のメッセージが表示されます。  
  
 **アクセスが拒否されました。管理者に Just-In-Time デバッグを有効にしてもらうか、または Visual Studio のインストールを修復してください。**  
  
## <a name="see-also"></a>「  
 [[デバッグ] ([オプション] ダイアログ ボックス)](../debugger/debugging-options-dialog-box.md)   
 [方法: デバッガー設定を指定する](../debugger/how-to-specify-debugger-settings.md)