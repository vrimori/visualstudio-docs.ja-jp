---
title: Start コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f08baa8c27debf6493ca090a2a5e80f02b3da982
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774456"
---
# <a name="start-command"></a>Start コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>「  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
