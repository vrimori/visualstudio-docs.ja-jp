---
title: "方法 : エディター モードを管理する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 71566f11a069d266ded2aebe02bbf388cf00730e
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="how-to-manage-editor-modes"></a>方法 : エディター モードを管理する
Visual Studio のコード エディターは、さまざまな表示モードで表示できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="enabling-full-screen-mode"></a>全画面表示モードを有効にする  
 **全画面表示**モードを有効にすると、すべてのツール ウィンドウを非表示にして、ドキュメント ウィンドウだけを表示することができます。  
  
#### <a name="to-enable-full-screen-mode"></a>全画面表示モードを有効にするには  
  
-   **全画面表示**モードを開始または終了するには、Alt + Shift + Enter キーを押します。  
  
     または  
  
-   **[コマンド]** ウィンドウで `View.Fullscreen` コマンドを実行します。  
  
## <a name="enabling-virtual-space-mode"></a>仮想空白モードを有効にする  
 **仮想空白**モードでは、各コード行の末尾に空白が挿入されます。 コードの横に一貫してコメントを入れる場合は、このチェック ボックスをオンにします。  
  
#### <a name="to-enable-virtual-space-mode"></a>仮想空白モードを有効にするには  
  
1.  **[ツール]** メニューの **[オプション]** を選択します。  
  
2.  **[テキスト エディター]** フォルダーを展開し、**[すべての言語]** を選択してこのオプションをグローバルに設定するか、または特定の言語フォルダーを選択します  (たとえば、Visual Basic でのみ行番号を表示するには、[テキスト エディター] で [Basic] を選択します)。  
  
3.  **[全般]** オプションを選択し、**[設定]** で **[仮想空白文字を使用]** を選択します。  
  
    > [!NOTE]
    >  **列の選択**モードで**仮想空白文字**が有効になります。 **仮想空白**モードを有効にしないと、挿入ポイントは行の末尾から次の行の先頭文字に直接移動します。  
  
## <a name="see-also"></a>関連項目  
 [エディターのカスタマイズ](../ide/customizing-the-editor.md)   
 [Visual Studio のウィンドウ レイアウトをカスタマイズする](../ide/customizing-window-layouts-in-visual-studio.md)   
 [[フォントおよび色] ([オプション] ダイアログ ボックス - [環境])](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
