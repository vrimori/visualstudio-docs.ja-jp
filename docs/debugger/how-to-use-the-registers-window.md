---
title: Visual Studio デバッガーでのレジスタの値の表示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f236bf43d3667cd4263d205c4588593a973824d
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257170"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>登録の値を表示し、[レジスタ] ウィンドウで、Visual Studio デバッガーを使用して (C#、C++、Visual Basic、 F#)
[レジスタ] ウィンドウにアドレス レベルのデバッグが有効な場合にのみ使用できますが、**オプション**ダイアログ ボックスで、**デバッグ**ノード、**全般**カテゴリ。  
  
 **登録**レジスタの内容がウィンドウが表示されます。 保持する場合、**登録**ウィンドウにプログラムをステップ実行すると開く、表示できる、コードが実行されるとレジスタ値の変更。 最近変更した値が赤で表示されます。 レジスタの値は編集できます。 詳細については、次を参照してください。[方法: レジスタ値を編集](../debugger/how-to-edit-a-register-value.md)します。  
  
 、見やすくするために、**登録**ウィンドウは、プラットフォームやプロセッサによって異なるグループにレジスタを編成型。 必要に応じて、グループの表示/非表示を切り替えることができます。 詳細については、次を参照してください。[方法: レジスタ グループの非表示にすると表示](../debugger/how-to-display-and-hide-register-groups.md)します。  
  
 レジスタおよびレジスタ ウィンドウの背後にある概念について大まかな概要については、次を参照してください。[デバッグの基礎: [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-display-the-registers-window"></a>[レジスタ] ウィンドウを表示するには  
  
-   **デバッグ**] メニューの [選択**Windows**、選び、**登録**(選択または**Ctrl** + **Alt**  +  **G**)。  
  
     デバッガーは動作中であるか、中断モードである必要があります。  
  
    > [!NOTE]
    >  スクリプトまたは SQL アプリケーションのレジスタ情報は表示できません。  
  
## <a name="see-also"></a>関連項目  
 [デバッグの基礎 : [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)   
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [デバッグの基礎 : [レジスタ] ウィンドウ](../debugger/debugging-basics-registers-window.md)