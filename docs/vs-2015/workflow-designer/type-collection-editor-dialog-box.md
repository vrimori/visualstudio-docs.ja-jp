---
title: '[型コレクション エディター] ダイアログ ボックス |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 34b8129b5a0b1fe27a7e4e6c178ddace638e5ffc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536361"
---
# <a name="type-collection-editor-dialog-box"></a>[型コレクション エディター] ダイアログ ボックス
**型コレクション エディター**既知の型に追加する ダイアログ ボックスを使用、**送信**と**受信**アクティビティ。 ジェネリック型引数に追加するこのダイアログ ボックスを使用しても、 **InvokeMethod**アクティビティ。 使用すると、**送信**と**受信**既知の型を追加するアクティビティ、**型コレクション エディター**  ダイアログ ボックスに追加すると、一意である型が必要です。 重複する型が追加され、クリックして、変更をコミット**OK**、エラー メッセージが返されます。 使用すると、 **InvokeMethod** 、ジェネリック型引数を追加するアクティビティ、**型コレクション エディター**ダイアログ ボックスでは重複する型を追加します。  
  
> [!NOTE]
>  [!INCLUDE[crabout](../includes/crabout-md.md)] 既知の型を参照してください[Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)します。  
  
 次の表に、ユーザー インターフェイス (UI) 要素の**型コレクション** ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**型リスト**|追加または削除された型のリスト。|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>[型コレクション エディター] を表示するには  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Send アクティビティおよび Receive アクティビティの [型コレクション エディター] を表示するには  
  
1.  選択、**送信**または**受信**デザイン ビューでのアクティビティ。  
  
2.  キーを押して**F4**を起動、**プロパティ**ウィンドウ。  
  
3.  **プロパティ**ウィンドウで、省略記号ボタンをクリックして、 **KnownTypes**プロパティ。  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod アクティビティの [型コレクション エディター] を表示するには  
  
1.  選択、 **InvokeMethod**デザイン ビューでのアクティビティ。  
  
2.  キーを押して**F4**を起動、**プロパティ**ウィンドウ。  
  
3.  **プロパティ**ウィンドウで、省略記号ボタンをクリックして、 **GenericTypeArguments**プロパティ。