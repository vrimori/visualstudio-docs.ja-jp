---
title: "方法: 非表示のデバッガー コマンドを復元 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 561fa92e9797bd3a4343a4f2c6e23bd1e91ccab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-restore-hidden-debugger-commands"></a>方法 : 非表示のデバッガー コマンドを復元する
Visual Studio をセット アップするときに、既定の IDE 設定で主要なプログラム言語を選択するように指示されます。 言語によっては、既定の IDE 設定で一部のデバッガー コマンドが非表示のことがあります。  
  
 既定の IDE 設定で非表示のデバッガー機能を使用するには、次の手順でコマンドをメニューに表示します。  
  
### <a name="to-restore-hidden-debugger-commands"></a>非表示のデバッガー コマンドを復元するには  
  
1.  プロジェクトを開き、[、**ツール**] メニューのをクリックして**カスタマイズ**です。  
  
2.  **カスタマイズ**ダイアログ ボックスで、をクリックして、**コマンド**タブです。  
  
3.  **メニュー バー:**ドロップダウン リストで、select、**デバッグ**復元されたコマンドを記述するメニュー。  
  
4.  クリックして、**コマンドを追加しています.**ボタンをクリックします。  
  
5.  **コマンドの追加**ボックスで、をクリックし、追加するコマンドを選択**OK**です。  
  
6.  前の手順を繰り返して、ブレークポイントを追加します。  
  
7.  をクリックして**閉じる**メニューにコマンドの追加が完了したらです。  
  
    > [!WARNING]
    >  メニュー項目によっては、デバッガーが特殊なモード (実行モードまたは中断モード) のときにのみ表示されます。 そのため、この手順でコマンドを追加しても、すぐに表示されないことがあります。  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>[ユーザー設定] ダイアログ ボックスから使用できないコマンドを復元する  
 特に階層メニューに含まれるいくつかのコマンドをから復元することはできません、**カスタマイズ** ダイアログ ボックス。 このようなコマンドを復元するには、IDE 設定の新しいコレクションをインポートする必要があります。  
  
#### <a name="to-import-new-ide-settings"></a>新しい IDE 設定をインポートするには  
  
1.  **ツール** メニューのをクリックして**インポートおよびエクスポート設定**です。  
  
2.  **のインポートとエクスポートの設定ウィザードへようこそ** ページで、をクリックして**選択された環境設定をインポート**、クリックして**次へ**です。  
  
3.  **現在の設定を保存**ページで、既存の設定を保存し、をクリックするかどうかを決定**次**です。  
  
4.  **インポートする設定のコレクションを選択して**] ページの [、**既定の設定の**フォルダーを使用するコマンドが含まれる開発設定のコレクションを選択します。 選択するコレクションがわからない場合**全般的な開発設定**または**Visual C 開発設定**、ほとんどのデバッガー コマンドを提供します。  
  
5.  **[次へ]**をクリックします。  
  
6.  **をインポートする設定を選択**] ページの [**オプション**、確認**デバッグ**が選択されています。 この設定をインポートしないのであれば、他のチェック ボックスはオフにします。  
  
7.  **[完了]**をクリックします。  
  
8.  **インポートの完了**] ページで、[設定のリセットに関連付けられているエラーを確認**詳細**です。  
  
9. **[閉じる]**をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)