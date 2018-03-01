---
title: "Print コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bba20817c03b7ff542c3af11a440ad8e619f5567
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="print-command"></a>Print コマンド
式を評価するか、指定したテキストを表示します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>引数  
 `text`  
 必須。 評価対象の式または表示対象のテキストです。  
  
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
  
## <a name="see-also"></a>参照  
 [Evaluate Statement コマンド](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)