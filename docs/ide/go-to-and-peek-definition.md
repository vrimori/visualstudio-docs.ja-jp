---
title: "[定義へ移動] と [定義をここに表示] | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 467d119e67db254b6e15630c08c411bb15283351
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-definition-and-peek-definition"></a>[定義へ移動] と [定義をここに表示]  
[定義へ移動] および [定義をここに表示] 機能を使用すると、型またはメンバーの定義を簡単に表示することができます。

## <a name="go-to-definition"></a>[定義へ移動]  
[定義へ移動] 機能では、型またはメンバーのソースに移動し、新しいタブで結果を開きます。キーボードを使用する場合は、シンボル名内の任意の場所にテキスト カーソルを置いて、**F12** キーを押します。 マウスを使用する場合は、コンテキスト メニューから **[定義へ移動]** を選択するか、以下で説明する **Ctrl-クリック**機能を使用します。  

### <a name="ctrl-click-go-to-definition"></a>Ctrl-クリックの [定義へ移動]  
Visual Studio 2017 バージョン 15.4 の場合、マウスを使用すると、より簡単に [定義へ移動] へすばやくアクセスできます。 **Ctrl** キーを押して、型またはメンバーにカーソルを置くと、シンボルがクリック可能になります。 シンボルの定義にすばやく移動するには、**Ctrl** キーを押してからクリックします。 とても簡単ですね。

![マウス クリックの [定義へ移動] のアニメーション](../ide/media/click_gotodef.gif)

マウス クリックの **[定義へ移動]** の修飾キーを変更するには、**[ツール]**、**[オプション]**、**[テキスト エディター]**、**[全般]** の順に移動し、**[修飾子キーを使用する]** ドロップダウンから **[Alt]** または **[Ctrl+Alt]** を選択します。 **[マウス クリックを有効にして [定義へ移動] を実行する]** チェック ボックスをオフにして、マウス クリックの **[定義へ移動]** を無効にすることもできます。  

![マウス クリックの [定義へ移動] の無効化](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>定義をここに表示
[定義をここに表示] 機能を使用すれば、エディターで現在の場所を離れずに型の定義をプレビューすることができます。 キーボードを使用する場合は、型またはメンバー名内の任意の場所にテキスト カーソルを置いて、**Alt + F12** キーを押します。 マウスを使用する場合は、コンテキスト メニューから **[定義をここに表示]** を選択できます。 Visual Studio 2017 バージョン 15.4 以降では、マウスを使用して定義をピーク表示するという新しい方法があります。 まず、**[ツール]**、**[オプション]**、**[テキスト エディター]**、**[全般]** の順に移動します。 オプションの **[定義をピーク ビューで開く]** を選択し、**[OK]** をクリックして **[オプション]** ダイアログ ボックスを閉じます。  

![マウス クリックの [定義をここに表示] オプションの設定](../ide/media/editor_options_peek_view.png)  

次に、**Ctrl** キー (または **[オプション]** で選択されている修飾キーのいずれか) を押して、型またはメンバーをクリックします。  

![[定義をここに表示] のアニメーション](../ide/media/peek_definition.gif)

ポップアップ ウィンドウから別の定義を表示する場合は、ポップアップの上に表示される円と矢印を使ってナビゲートできる階層リンク パスを開始します。  

詳細については、「[方法: [定義をここに表示] を使用してコードを表示および編集する (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)」を参照してください。  

## <a name="see-also"></a>関連項目  
[コード間の移動](../ide/navigating-code.md)  
[方法: [定義をここに表示] を使用してコードを表示および編集する (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
