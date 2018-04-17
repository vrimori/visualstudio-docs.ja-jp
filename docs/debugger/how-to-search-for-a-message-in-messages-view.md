---
title: '方法: メッセージ ビューでメッセージの検索 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ec04e45d1383e767e2fe1079ac8a38c8b4d7ec0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>方法: メッセージ ビューでメッセージを検索する
検索条件として、ハンドル、型、またはメッセージの ID を使用してメッセージ ビューで特定のメッセージを検索できます。 これらのいずれか、または組み合わせ: 有効な検索条件になります。 検索の最初の方向も指定することができます。 ダイアログ ボックスのフィールドは、現在選択されているメッセージの属性を持つプリロードされてです。  
  
### <a name="to-search-for-a-message-in-messages-view"></a>メッセージ ビューでメッセージを検索するには  
  
1.  ウィンドウを整列するようにその spy++ と、アクティブな[メッセージ ビュー](../debugger/messages-view.md)ウィンドウが表示されます。  
  
2.  **検索**] メニューの [選択**メッセージの検索**です。  
  
     [メッセージ検索 ダイアログ ボックス](../debugger/message-search-dialog-box.md)が開きます。  
  
3.  ドラッグ、**ファインダー ツール**目的のウィンドウの上です。 このツールをドラッグすると、**メッセージ検索** ダイアログ ボックスでは、選択したウィンドウの詳細が表示されます。  
  
     - または  
  
     場合を確認するメッセージがウィンドウのハンドルがある場合は、入力に、**処理**テキスト ボックス。  
  
     - または  
  
     メッセージ タイプおよびメッセージ ID が必要な場合を選択してから、**型**と**メッセージ**ドロップダウン メニューをオフにし、**処理**テキスト ボックス。  
  
4.  値を指定しないすべてのフィールドをオフにします。  
  
    > [!TIP]
    >  見やすくするために画面を選択して、 **Spy++ を非表示**オプション。 このオプションを非表示に、spy++ メイン ウィンドウ、だけ残して、**ウィンドウ検索**他のアプリケーションの上に表示されるダイアログ ボックス。 クリックすると、Spy++ でのメイン ウィンドウを復元**[ok]**または**キャンセル**、またはクリアすると、 **spy++ を非表示に**オプション。  
  
5.  選択**を**または**ダウン**検索の方向。  
  
6.  **[OK]**をクリックします。  
  
 一致するメッセージを検出すると、メッセージの表示 ウィンドウで強調表示されます。 参照してください[メッセージ ビュー](../debugger/messages-view.md)です。