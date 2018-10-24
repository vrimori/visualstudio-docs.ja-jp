---
title: '方法: メッセージ ビューでメッセージの検索 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: f9c00eea2034651298ff62bc50741971fc0369a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844914"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>方法: メッセージ ビューでメッセージを検索する
メッセージ ビューで特定のメッセージを検索するには、検索条件として、ハンドル、型、またはメッセージ ID を使用します。 これらのいずれか、または組み合わせ: 有効な検索条件になります。 検索の最初の方向も指定できます。 ダイアログ ボックスのフィールドは、現在選択されているメッセージの属性を事前に読み込まれます。  
  
### <a name="to-search-for-a-message-in-messages-view"></a>メッセージ ビューでメッセージを検索するには  
  
1. そのため、ウィンドウを整列 Spy++ は、アクティブな[メッセージ ビュー](../debugger/messages-view.md)ウィンドウが表示されます。  
  
2. **検索**] メニューの [選択**メッセージの検索**します。  
  
    [メッセージ検索 ダイアログ ボックス](../debugger/message-search-dialog-box.md)が開きます。  
  
3. ドラッグ、**ファインダー ツール**目的の枠。 このツールをドラッグすると、**メッセージ検索** ダイアログ ボックスでは、選択したウィンドウの詳細が表示されます。  
  
   - または  
  
     確認するメッセージが含まれるウィンドウのハンドルがあれば、入力に、**処理**テキスト ボックス。  
  
   - または  
  
     メッセージの種類やメッセージ ID が必要な場合を選択してから、**型**と**メッセージ**ドロップダウン メニューでは、オフにし、**処理**テキスト ボックス。  
  
4. 値を指定しないすべてのフィールドをオフにします。  
  
   > [!TIP]
   >  画面の煩雑さを減らすためには、選択、 **Spy++ を非表示**オプション。 このオプションは、主な spy++ ウィンドウだけを非表示、**ウィンドウ検索**ダイアログ ボックスで、他のアプリケーションの上に表示します。 クリックすると、spy++ のメイン ウィンドウが復元**OK**または**キャンセル**、またはオフにすると、 **spy++ を非表示にする**オプション。  
  
5. 選択**を**または**ダウン**方向を検索します。  
  
6. **[OK]** をクリックします。  
  
   一致するメッセージが見つかると、メッセージ ビュー ウィンドウで強調表示されます。 参照してください[メッセージ ビューを](../debugger/messages-view.md)します。