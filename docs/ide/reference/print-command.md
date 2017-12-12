---
title: "Print コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eaf5d77da1dbc6e005764087dad338458e7ce8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="print-command"></a>Print コマンド
式を評価するか、指定したテキストを表示します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>引数  
 `text`  
 必須です。 評価対象の式または表示対象のテキストです。  
  
## <a name="remarks"></a>コメント  
 このコマンドのエイリアスとして疑問符 (?) を使用できます。 したがって、たとえば次のコマンド  
  
```  
>Debug.Print expA  
```  
  
 は、次のように記述することもできます。  
  
```  
>? expA  
```  
  
 どちらのコマンドでも、式 `expA` の現在の値が返されます。  
  
## <a name="example"></a>例  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>関連項目  
 [Evaluate Statement コマンド](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)