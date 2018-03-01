---
title: "GoTo コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 53c45ccf528375bc31b4d61fd6af0193aa295e6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-command"></a>GoTo コマンド
指定した行にカーソルを移動します。  
  
## <a name="syntax"></a>構文  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>引数  
 `linenumber`  
 任意。 移動先の行番号を表す整数。  
  
## <a name="remarks"></a>コメント  
 行番号は 1 から始まります。 `linenumber` の値が 1 未満の場合は、最初の行が表示されます。 `linenumber` の値が最終行の値より大きい場合は、最後の行が表示されます。  
  
 `linenumber` の値が指定されていない場合は、**[指定行へ移動]** ダイアログ ボックスが表示されます。  
  
 このコマンドのエイリアスは GoToLn です。  
  
## <a name="example"></a>例  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)