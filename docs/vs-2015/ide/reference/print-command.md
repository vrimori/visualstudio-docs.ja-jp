---
title: Print コマンド | Microsoft Docs
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
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e742b1fa6a25525d33e7b8a6fcb321cfea86f693
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232753"
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
 必須。 評価対象の式または表示対象のテキストです。  
  
## <a name="remarks"></a>Remarks  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



