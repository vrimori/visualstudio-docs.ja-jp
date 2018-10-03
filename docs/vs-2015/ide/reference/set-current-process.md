---
title: SetCurrentProcess | Microsoft ドキュメント
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5281d1c0d926d8d6acdedf323649216c74a4cab9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538661"
---
# <a name="set-current-process"></a>SetCurrentProcess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[設定の現在のプロセス](https://docs.microsoft.com/visualstudio/ide/reference/set-current-process)します。  
  
  
指定されたプロセスをデバッガーでアクティブなプロセスとして設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 必須。 プロセスのインデックスです。  
  
## <a name="remarks"></a>Remarks  
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。 `SetCurrentProcess` コマンドを使用すると、アクティブなプロセスを設定できます。  
  
## <a name="example"></a>例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)



