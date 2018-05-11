---
title: Start コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a4c372d3f384eeaa0ac137188e325ccde777cd4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="start-command"></a>Start コマンド
スタートアップ プロジェクトのデバッグを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>引数  
 `address`  
 任意。 プログラムの実行を中断するアドレス。ソース コードでのブレークポイントに似ています。 この引数は、デバッグ モードでのみ有効です。  
  
## <a name="remarks"></a>コメント  
 **Start** コマンドを実行すると、指定したアドレスまで RunToCursor 操作が実行されます。  
  
## <a name="example"></a>例  
 この例では、デバッガーを起動し、発生した例外はすべて無視されます。  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)