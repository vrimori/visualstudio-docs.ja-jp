---
title: "Start コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8eb0efae140613c6caa7bd71d72e0ce4cda37db8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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