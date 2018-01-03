---
title: "QuickWatch コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bad8605a2a7b9f9606c448680d583c55a2762a75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="quick-watch-command"></a>QuickWatch コマンド
選択または指定したテキストが [[クイック ウォッチ]](../../debugger/watch-and-quickwatch-windows.md) ウィンドウの [式] フィールドに表示されます。 このダイアログ ボックスを利用し、デバッガーが認識する変数または式の現在値やレジスタのコンテンツの現在値を計算できます。 さらに、非定数の変数の値やレジストリのコンテンツの値を変更できます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>引数  
 `text`  
 任意。 **[クイック ウォッチ]** ダイアログ ボックスに追加するテキスト。  
  
## <a name="remarks"></a>コメント  
 `text` を省略した場合、カーソルで現在選択されているテキストや単語がウォッチ ウィンドウに追加されます。  
  
## <a name="example"></a>例  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio でウォッチ ウィンドウとクイック ウォッチ ウィンドウを使用して変数のウォッチ ポイントを設定する](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)