---
title: Print コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c72f6668e6babab6bd62cfb0e9a6ca8632df2a84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763571"
---
# <a name="print-command"></a>Print コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
  
## <a name="see-also"></a>「  
 [Evaluate Statement コマンド](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
