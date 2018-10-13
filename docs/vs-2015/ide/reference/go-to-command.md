---
title: GoTo コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d23f7b9961f8386fb023fa747a647c14c9cd5db1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303473"
---
# <a name="go-to-command"></a>GoTo コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定した行にカーソルを移動します。  
  
## <a name="syntax"></a>構文  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>引数  
 `linenumber`  
 任意。 移動先の行番号を表す整数。  
  
## <a name="remarks"></a>Remarks  
 行番号は 1 から始まります。 `linenumber` の値が 1 未満の場合は、最初の行が表示されます。 `linenumber` の値が最終行の値より大きい場合は、最後の行が表示されます。  
  
 `linenumber` の値が指定されていない場合は、**[指定行へ移動]** ダイアログ ボックスが表示されます。  
  
 このコマンドのエイリアスは GoToLn です。  
  
## <a name="example"></a>例  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



