---
title: SetCurrentThread コマンド | Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3a3ccd860088c38b84b805a54ee17d50240b2e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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