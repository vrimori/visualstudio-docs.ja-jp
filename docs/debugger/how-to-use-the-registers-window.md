---
title: "Visual Studio デバッガーでのレジスタの値の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7aa89b6e8d36c3eb47168c8672fb7eea1e3507db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>登録値を表示して、Visual Studio デバッガーの [レジスタ] ウィンドウを使用します。
[レジスタ] ウィンドウがアドレス レベルのデバッグが有効になっている場合にのみ使用できますが、**オプション**ダイアログ ボックスで、**デバッグ**ノード、**全般**カテゴリ。  
  
 **登録**レジスタの内容がウィンドウに表示されます。 保持する場合、**登録**プログラムをステップ実行する、開いたウィンドウで確認できます、コードが実行されるとレジスタ値の変更。 最近変更した値が赤で表示されます。 レジスタの値は編集できます。 詳細については、次を参照してください。[する方法: レジスタ値を編集](../debugger/how-to-edit-a-register-value.md)です。  
  
 、見やすくするために、**登録**レジスタ グループで、プラットフォームやプロセッサによって異なる場合に別に表示ウィンドウの種類。 必要に応じて、グループの表示/非表示を切り替えることができます。 詳細については、次を参照してください。[する方法: レジスタ グループの非表示にすると表示](../debugger/how-to-display-and-hide-register-groups.md)です。  
  
 レジスタおよび [レジスタ] ウィンドウの背後にある概念を大まかな概要については、次を参照してください。[デバッグの基礎: [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-display-the-registers-window"></a>[レジスタ] ウィンドウを表示するには  
  
-   **デバッグ**] メニューの [選択**Windows**を選択し**登録**です。  
  
     デバッガーは動作中であるか、中断モードである必要があります。  
  
    > [!NOTE]
    >  スクリプトまたは SQL アプリケーションのレジスタ情報は表示できません。  
  
## <a name="see-also"></a>参照  
 [デバッグの基礎 : [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)   
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [デバッグの基礎 : [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)