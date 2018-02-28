---
title: "SetCurrentThread コマンド | Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 24a3f7d50d90769fe64b3657a0327eb8c96b7b42
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-thread-command"></a>SetCurrentThread コマンド
指定したスレッドを現在のスレッドとして設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 必須。 スレッドをそのインデックスで選択します。  
  
## <a name="example"></a>例  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)