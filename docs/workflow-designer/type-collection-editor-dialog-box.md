---
title: "[型コレクション エディター] ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8e4b794a623c3a0218e44773da6bdb6c76612816
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="type-collection-editor-dialog-box"></a>[型コレクション エディター] ダイアログ ボックス
**型コレクション エディター**既知の型を追加する ダイアログ ボックスを使用して、**送信**と**受信**アクティビティ。 ジェネリック型引数に追加するこのダイアログ ボックスを使用しても、 **InvokeMethod**アクティビティ。 使用する場合、**送信**と**受信**既知の型を追加するアクティビティ、**型コレクション エディター**  ダイアログ ボックスには、一意である型の追加が必要です。 かどうか、重複する型が追加されをクリックして変更をコミット**OK**、エラー メッセージが返されます。 使用する場合、 **InvokeMethod**にジェネリック型引数を追加するアクティビティ、**型コレクション エディター**  ダイアログ ボックスでは重複する型を追加します。  
  
> [!NOTE]
>  [!含める[crabout](/dotnet/framework/wcf/feature-details/data-contract-known-types)です。  
  
 次の表は、ユーザー インターフェイス (UI) 要素の**型コレクション** ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**型リスト**|追加または削除された型のリスト。|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>[型コレクション エディター] を表示するには  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Send アクティビティおよび Receive アクティビティの [型コレクション エディター] を表示するには  
  
1.  選択、**送信**または**受信**デザイン ビューでアクティビティ。  
  
2.  キーを押して**F4**を呼び出すこと、**プロパティ**ウィンドウです。  
  
3.  **プロパティ** ウィンドウで、省略記号ボタンをクリックして、 **KnownTypes**プロパティです。  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod アクティビティの [型コレクション エディター] を表示するには  
  
1.  選択、 **InvokeMethod**デザイン ビューでアクティビティ。  
  
2.  キーを押して**F4**を呼び出すこと、**プロパティ**ウィンドウです。  
  
3.  **プロパティ** ウィンドウで、省略記号ボタンをクリックして、 **GenericTypeArguments**プロパティです。